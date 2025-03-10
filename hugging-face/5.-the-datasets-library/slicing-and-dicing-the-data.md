# Slicing and dicing the data

* Similar to pandas we can manipulate dataset
* Looking at same records

```python
drug_sample = drug_dataset["train"].shuffle(seed=42).select(range(1000))
# Peek at the first few examples
drug_sample[:3]
#{'Unnamed: 0': [87571, 178045, 80482],
# 'drugName': ['Naproxen', 'Duloxetine', 'Mobic'],
# 'condition': ['Gout, Acute', 'ibromyalgia', 'Inflammatory Conditions'],
# 'review': ['"like the previous person mention, I&#039;m a strong believer of aleve, it works faster for my gout than the prescription meds I take. No more going to the doctor for refills.....Aleve works!"',
#  '"I have taken Cymbalta for about a year and a half for fibromyalgia pain. It is great\r\nas a pain reducer and an anti-depressant, however, the side effects outweighed \r\nany benefit I got from it. I had trouble with restlessness, being tired constantly,\r\ndizziness, dry mouth, numbness and tingling in my feet, and horrible sweating. I am\r\nbeing weaned off of it now. Went from 60 mg to 30mg and now to 15 mg. I will be\r\noff completely in about a week. The fibro pain is coming back, but I would rather deal with it than the side effects."',
#  '"I have been taking Mobic for over a year with no side effects other than an elevated blood pressure.  I had severe knee and ankle pain which completely went away after taking Mobic.  I attempted to stop the medication however pain returned after a few days."'],
# 'rating': [9.0, 3.0, 10.0],
# 'date': ['September 2, 2015', 'November 7, 2011', 'June 5, 2013'],
# 'usefulCount': [36, 13, 128]}
```

* Rename column

```python
drug_dataset = drug_dataset.rename_column(
    original_column_name="Unnamed: 0", new_column_name="patient_id"
)
drug_dataset
# DatasetDict({
#     train: Dataset({
#         features: ['patient_id', 'drugName', 'condition', 'review', 'rating', 'date', 'usefulCount'],
#         num_rows: 161297
#     })
#     test: Dataset({
#         features: ['patient_id', 'drugName', 'condition', 'review', 'rating', 'date', 'usefulCount'],
#         num_rows: 53766
#     })
# })
```

* Remove null records

```python
drug_dataset = drug_dataset.filter(lambda x: x["condition"] is not None)
```

* Lowecase the records

```python
def lowercase_condition(example):
    return {"condition": example["condition"].lower()}


drug_dataset.map(lowercase_condition)
```
