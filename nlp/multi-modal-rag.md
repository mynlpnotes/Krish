# Multi Modal RAG

* RAG
  * Data ⇒ Embedding ⇒ VectoDB&#x20;
  * Retriever means whenever any query comes it will perform similarity search on top of DB and get relevant documents
  * This is passed to LLM for generating answer
* Multimodel RAG
  * Different modality — Text, image, table, audio, video etc



* Parsing:
  * We have PDF which has text, images, tables
  * We parse and get data from PDF
  * Documents can be anything pdf, docx, csv, xml, ppt....
  * Different libraries that are used are - docx, pypdf, pymupdf...
  * Langchain also provides us library - unstructured
    * Using this we can parse any document - docx, pdf, ppt, xml, json....
