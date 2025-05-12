# Multi Modal RAG Implementation - Code

* Check which models can be used
* From PDF we will be getting text, table and images — This we need to store in vectorDB
  * We can create document object which page\_content, meta\_data
  * For each modality we will be creating summary
  * This summary will be available as page\_content, original text/table/image will be available in meta\_data
  * image will be stored as base64
* Whenever any query comes it will be embedded and then similarity search between page\_content embedding and query embedding will be done
* Based on this relevant docs(page\_content, metadata) will be fetched and sent to LLM model for output generation
* Retriever will  get the relevant document, we will split this documents into text and images in a dictionary
* This context and questions will go to imag\_prompt\_func
  * This will put text and images url in messages as HumanMessage which can be passed to the prompt
*



```python
# Install Libraries
! pip install "unstructured[all-docs]" pillow pydantic lxml matplotlib

!sudo apt-get update
!sudo apt-get install poppler-utils
!sudo apt-get install tesseract-ocr
!sudo apt-get install libtesseract-dev
!pip install unstructured-pytesseract

# Data Parsing
from unstructured.partition.pdf import partition_pdf

raw_pdf_elements=partition_pdf(
    filename="/content/RAG-For-NLP.pdf",
    strategy="hi_res",
    extract_images_in_pdf=True,
    extract_image_block_types=["Image","Table"],
    extract_image_block_to_payload=False,
    extract_image_block_output_dir="extracted_data"
    )
    
Header=[]
Footer=[]
Title=[]
NarrativeText=[]
Text=[]
ListItem=[]
Image=[]
Table=[]
for element in raw_pdf_elements:
  if "unstructured.documents.elements.Header" in str(type(element)):
            Header.append(str(element))
  elif "unstructured.documents.elements.Footer" in str(type(element)):
            Footer.append(str(element))
  elif "unstructured.documents.elements.Title" in str(type(element)):
            Title.append(str(element))
  elif "unstructured.documents.elements.NarrativeText" in str(type(element)):
            NarrativeText.append(str(element))
  elif "unstructured.documents.elements.Text" in str(type(element)):
            Text.append(str(element))
  elif "unstructured.documents.elements.ListItem" in str(type(element)):
            ListItem.append(str(element))
  elif "unstructured.documents.elements.Image" in str(type(element)):
            Image.append(str(element))
  elif "unstructured.documents.elements.Table" in str(type(element)):
            Table.append(str(element))

# Load the model and embedding model
from langchain_google_genai import ChatGoogleGenerativeAI
from langchain_google_genai import GoogleGenerativeAIEmbeddings
from google.colab import userdata
import os

GOOGLE_API_KEY=userdata.get('GOOGLE_API_KEY')
os.environ["GOOGLE_API_KEY"]=GOOGLE_API_KEY

def load_model(model_name):
    if model_name == "gemini-pro":
        return ChatGoogleGenerativeAI(model="gemini-1.5-pro")
    elif model_name == "gemini-1.5-flash":
        return ChatGoogleGenerativeAI(model="gemini-1.5-flash")
    elif model_name == "embedding":
        return GoogleGenerativeAIEmbeddings(model="models/embedding-001")
    else:
        raise ValueError(f"Unsupported model name: {model_name}")

model_text=load_model("gemini-pro")

model_text.invoke("hi")
# AIMessage(content='Hi there! How can I help you today?', 
# additional_kwargs={}, .......)

# Prepare the data for vector DB
## Summary for the text
!pip install langchain_groq
from langchain_core.output_parsers import StrOutputParser
from langchain_core.prompts import ChatPromptTemplate
from langchain_groq import ChatGroq

prompt_text="""You are an assistant tasked with summarizing text for retrieval. \
    These summaries will be embedded and used to retrieve the raw text elements. \
    Give a concise summary of the table or text that is well optimized for retrieval.text: {element} """

prompt=ChatPromptTemplate.from_template(prompt_text)

model=load_model("gemini-pro")

groq_model=ChatGroq(model="deepseek-r1-distill-llama-70b",api_key=GROQ_API_KEY)

summarize_chain = {"element": lambda x: x} |prompt| groq_model | StrOutputParser()

type(NarrativeText) # list
len(NarrativeText) # 20

NarrativeText=NarrativeText[:10] # 10

text_summary=[]
text_summary=summarize_chain.batch(NarrativeText,{"max_concurrency": 5})

import re
clean_text = re.sub(r"<think>.*?</think>\s*", "", text_summary[4], flags=re.DOTALL)

# Summary of tables
prompt_text = """You are an AI Assistant tasked with summarizing tables for retrieval. \
    These summaries will be embedded and used to retrieve the raw table elements. \
    Give a concise summary of the table that is well optimized for retrieval. Table:{element} """

prompt = ChatPromptTemplate.from_template(prompt_text)

summarize_chain = {"element": lambda x: x} | prompt | groq_model | StrOutputParser()

table_summaries = []

table_summaries = summarize_chain.batch(Table, {"max_concurrency": 5})

# Summary of images
import base64
import os
from langchain_core.messages import AIMessage, HumanMessage

def encode_image(image_path):
    with open(image_path, "rb") as image_file:
        return base64.b64encode(image_file.read()).decode("utf-8")
        
image_model = ChatGoogleGenerativeAI(model="gemini-1.5-flash")

def image_summarize(img_base64,prompt):
    chat = ChatGoogleGenerativeAI(model="gemini-1.5-flash")
    msg = chat.invoke(
        [
            HumanMessage(
                content=[
                    {
                    "type": "text",
                     "text": prompt
                     }
                    ,
                    {
                        "type": "image_url",
                        "image_url": {"url": f"data:image/jpeg;base64,{img_base64}"},
                    },
                ]
            )
        ]
    )
    return msg.content

def generate_img_summaries(path):
    """
    Generate summaries and base64 encoded strings for images
    path: Path to list of .jpg files extracted by Unstructured
    """

    # Store base64 encoded images
    img_base64_list = []

    # Store image summaries
    image_summaries = []

    # Prompt
    prompt = """You are an assistant tasked with summarizing images for retrieval. \
    These summaries will be embedded and used to retrieve the raw image. \
    Give a concise summary of the image that is well optimized for retrieval."""

    # Apply to images
    for img_file in sorted(os.listdir(path)):
        if img_file.endswith(".jpg"):
            img_path = os.path.join(path, img_file)
            base64_image = encode_image(img_path)
            img_base64_list.append(base64_image)
            image_summaries.append(image_summarize(base64_image, prompt))


    return img_base64_list, image_summaries

fpath="/content/extracted_data/"

img_base64_list, image_summaries=generate_img_summaries(fpath)

# Store in vectorDB
!pip install -U langchain-community

import uuid
from langchain_core.documents import Document
from langchain.vectorstores import Chroma
from langchain.storage import InMemoryStore
from langchain.retrievers.multi_vector import MultiVectorRetriever

def create_multi_vector_retriever(vectorstore, text_summaries, texts, table_summaries, tables, image_summaries, images):
  store=InMemoryStore()
  id_key="doc_id"

  retriever=MultiVectorRetriever(
      vectorstore=vectorstore,
      docstore=store,
      id_key=id_key,
  )

  def add_documents(retriever, doc_summaries, doc_contents):

      doc_ids = [str(uuid.uuid4()) for _ in doc_contents]

      summary_docs = [
              Document(page_content=summary, metadata={id_key: doc_ids[i]})

              for i, summary in enumerate(doc_summaries)
          ]

      retriever.vectorstore.add_documents(summary_docs)
      retriever.docstore.mset(list(zip(doc_ids, doc_contents)))


  if text_summaries:
        add_documents(retriever, text_summaries, texts)
  if table_summaries:
        add_documents(retriever, table_summaries, tables)
  if image_summaries:
        add_documents(retriever, image_summaries, images)

  return retriever

embedding_model=load_model("embedding")

vectorstore=Chroma(collection_name="MMRAG",embedding_function=embedding_model)

retriever_multi_vector_img = create_multi_vector_retriever(
    vectorstore,
    text_summary,
    NarrativeText,
    table_summaries,
    Table,
    image_summaries,
    img_base64_list,
)

query = "Why We combine a pre-trained retriever ?"

retriever_multi_vector_img.get_relevant_documents(query)

retriever_multi_vector_img.invoke(query)

# For image data processing
import io
import re
from IPython.display import HTML, display
from PIL import Image

def is_image_data(b64data):
    image_signatures = {
        b"\xFF\xD8\xFF": "jpg",
        b"\x89\x50\x4E\x47\x0D\x0A\x1A\x0A": "png",
        b"\x47\x49\x46\x38": "gif",
        b"\x52\x49\x46\x46": "webp",
    }
    try:
        header = base64.b64decode(b64data)[:8]  # Decode and get the first 8 bytes
        for sig, format in image_signatures.items():
            if header.startswith(sig):
                return True
        return False
    except Exception:
        return False
        
def looks_like_base64(sb):
  return re.match("^[A-Za-z0-9+/]+[=]{0,2}$", sb) is not None

def resize_base64_image(base64_string,size=(128,128)):
  # Decode the Base64 string
    img_data = base64.b64decode(base64_string)
    img = Image.open(io.BytesIO(img_data))

    # Resize the image
    resized_img = img.resize(size, Image.LANCZOS)

    # Save the resized image to a bytes buffer
    buffered = io.BytesIO()
    resized_img.save(buffered, format=img.format)

    # Encode the resized image to Base64
    return base64.b64encode(buffered.getvalue()).decode("utf-8")

def split_image_text_types(docs):
    """
    Split base64-encoded images and texts
    """
    b64_images = []
    texts = []

    for doc in docs:
        # Check if the document is of type Document and extract page_content if so
        if isinstance(doc, Document):
            doc = doc.page_content
        if looks_like_base64(doc) and is_image_data(doc):
            doc = resize_base64_image(doc, size=(1300, 600))
            b64_images.append(doc)
        else:
            texts.append(doc)

    return {"images": b64_images, "texts": texts}

def img_prompt_func(data_dict):
  """
  Join the context into a single string
  """
  print(data_dict)
  formatted_texts = "\n".join(data_dict["context"]["texts"])
  messages = []

  # Adding image(s) to the messages if present
  if data_dict["context"]["images"]:
      for image in data_dict["context"]["images"]:
          image_message = {
              "type": "image_url",
              "image_url": {"url": f"data:image/jpeg;base64,{image}"},
          }
          messages.append(image_message)

  # Adding the text for analysis
  text_message = {
      "type": "text",
      "text": (
          "You are a helpful assistant.\n"
          "You will be given a mixed info(s) .\n"
          "Use this information to provide relevant information to the user question. \n"
          f"User-provided question: {data_dict['question']}\n\n"
          "Text and / or tables:\n"
          f"{formatted_texts}"
      ),
  }
  messages.append(text_message)
  return [HumanMessage(content=messages)]


# Generation using chaining
from langchain_core.runnables import RunnablePassthrough, RunnableLambda

def multi_modal_rag_chain(retriever):
  chain=(
      {"context":retriever | RunnableLambda(split_image_text_types),
       "question": RunnablePassthrough()
      }
      | RunnableLambda(img_prompt_func)

      |model
      |StrOutputParser()
  )

  return chain

chain_multimodal_rag = multi_modal_rag_chain(retriever_multi_vector_img)

query1 = ''

chain_multimodal_rag.invoke(query1)



```
