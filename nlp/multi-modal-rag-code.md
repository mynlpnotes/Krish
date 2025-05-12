# Multi Modal RAG - Code

* Libraries not available in windows
* In \[] specify which documents library to be installed
* poppler-utils is used for OCR
* strategy means how images are going to be captured
* We can see all the extracted\_data also (it will be in extracted\_data - all the images that have been downloaded)
* raw\_pdf\_elements will contain sequentially all the elements of the pdf
* When parsing images - suppose if the image is of person then it will come as blank, if the image contains text then it will be parsed

```python
! pip install "unstructured[all-docs]" pillow pydantic lxml matplotlib

!sudo apt-get update
!sudo apt-get install poppler-utils
!sudo apt-get install tesseract-ocr
!sudo apt-get install libtesseract-dev
!pip install unstructured-pytesseract

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
            
 Header
 # ['2 r p A 2 1 ] L C . s c [ 4 v 1 0 4 1 1 . 5 0 0 2 :', '16', '19']
 
 Title

```
