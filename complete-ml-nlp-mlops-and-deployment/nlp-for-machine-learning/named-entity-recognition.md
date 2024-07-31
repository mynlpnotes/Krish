# Named Entity Recognition

*

    ```python
    nltk.download('maxent_ne_chunker')
    nltk.download('words')

    tag_elements = nltk.pos(sentence)
    nltk.ne_chunk(tag_elements).draw()
    # This will show the NER in graph format
    ```
