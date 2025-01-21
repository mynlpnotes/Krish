# 🟢 Named Entity Recognition



*   <mark style="color:purple;background-color:purple;">**ne\_chunk will show NER in graph format**</mark>

    ```python
    nltk.download('maxent_ne_chunker')
    nltk.download('words')

    tag_elements = nltk.pos(sentence)
    nltk.ne_chunk(tag_elements).draw()
    # This will show the NER in graph format
    ```
