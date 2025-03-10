# Creating new columns

* Function to count no. of words in each review

```python
def compute_review_length(example):
    return {"review_length": len(example["review"].split())}
    
drug_dataset = drug_dataset.map(compute_review_length)
# Inspect the first training example
drug_dataset["train"][0]
# {'patient_id': 206461,
#  'drugName': 'Valsartan',
#  'condition': 'left ventricular dysfunction',
#  'review': '"It has no side effect, I take it in combination of Bystolic 5 Mg and Fish Oil"',
#  'rating': 9.0,
#  'date': 'May 20, 2012',
#  'usefulCount': 27,
#  'review_length': 17}

drug_dataset["train"].sort("review_length")[:3]
```

* Filter

```python
drug_dataset = drug_dataset.filter(lambda x: x["review_length"] > 30)
print(drug_dataset.num_rows)

drug_dataset = drug_dataset.map(lambda x: {"review": html.unescape(x["review"])})
```
