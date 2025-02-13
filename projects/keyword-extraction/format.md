# Format

You're right to double-check. Let’s go over each format carefully and ensure accuracy in their structure.

***

#### **1. Doccano Format (Span-Based)**

Doccano stores annotations as **character-level spans** in a JSON format. Each label includes **start index, end index, and entity type**.

**Example**

```json
{
  "text": "I want an MBA candidate with 5 to 7 years of experience in sales",
  "labels": [[10, 13, "Education"], [28, 35, "Experience"], [50, 55, "Domain"]]
}
```

* `"labels"` contains a list of entities with their **start and end character positions**.
* `"MBA"` is labeled as **Education** from index `[10, 13]`.
* `"5 to 7 years"` is labeled as **Experience** from index `[28, 35]`.
* `"sales"` is labeled as **Domain** from index `[50, 55]`.

🔹 **Used in:** Annotation tools like Doccano, but needs conversion to a token-level format.

***

#### **2. BIO Format (Token-Level)**

The BIO format assigns a tag **to each token in a sentence**:

* `B-` (Beginning) marks the **first token** of an entity.
* `I-` (Inside) marks **subsequent tokens** of an entity.
* `O` (Outside) means **not part of any entity**.

**Example**

```
I O  
want O  
an O  
MBA B-Education  
candidate O  
with O  
5 B-Experience  
to I-Experience  
7 I-Experience  
years I-Experience  
of O  
experience O  
in O  
sales B-Domain
```

* `"MBA"` is tagged as `B-Education`.
* `"5 to 7 years"` is split into `B-Experience`, `I-Experience`, `I-Experience`, `I-Experience`.
* `"sales"` is tagged as `B-Domain`.

🔹 **Used in:** NLP pipelines and datasets like CoNLL-2003.

***

#### **3. Hugging Face Dataset Format**

Hugging Face uses a structured **JSON format** where tokens and labels are stored in lists.

**Example**

```json
{
  "tokens": ["I", "want", "an", "MBA", "candidate", "with", "5", "to", "7", "years", "of", "experience", "in", "sales"],
  "ner_tags": [0, 0, 0, 1, 0, 0, 2, 3, 3, 3, 0, 0, 0, 4]
}
```

* `"tokens"` holds the **actual words** in the sentence.
* `"ner_tags"` holds **numeric labels** for each token.
  * **0** → `O` (Outside)
  * **1** → `B-Education`
  * **2** → `B-Experience`
  * **3** → `I-Experience`
  * **4** → `B-Domain`

🔹 **Used in:** Hugging Face's `datasets` library for fine-tuning transformer models.

***

#### **Comparison Summary**

| Format           | Level             | Example                             | Pros                       | Cons                              |
| ---------------- | ----------------- | ----------------------------------- | -------------------------- | --------------------------------- |
| **Doccano**      | Character-level   | JSON with start-end positions       | Easy annotation            | Needs conversion to BIO           |
| **BIO**          | Token-level       | Word + Label per line               | Standard for NER           | Not directly used in Hugging Face |
| **Hugging Face** | Token-list format | JSON with `"tokens"` & `"ner_tags"` | Directly used for training | Needs mapping from BIO            |

***

#### **Next Steps**

1. **Convert Doccano → BIO**
   * You need a script to convert span-based annotations to token-level BIO format.
2. **Convert BIO → Hugging Face JSON**
   * Map BIO tags to numeric values for model training.

Would you like scripts for these conversions?
