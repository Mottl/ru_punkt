# ru_punkt
Russian language support for NLTK's PunktSentenceTokenizer

![Python 2.7](https://img.shields.io/badge/python-2.7-blue.svg)
![Python 3x](https://img.shields.io/badge/python-3.x-blue.svg)

## Instalation
1. Install NLTK python package:
```bash
pip install nltk
```

2. Download _punkt_ data:
```python
import nltk
nltk.download('punkt')
```

3. Download _ru_punkt_:
```bash
git clone https://github.com/Mottl/ru_punkt.git
```

4. Copy Russian tokenizer into `nltk_data` folder (ensure the appropriate location for your OS):
```bash
cp -r ru_punkt/nltk_data ~/nltk_data
```

## Usage
```python
import nltk

text = "Ай да А.С. Пушкин! Ай да сукин сын!"
print("Before:", nltk.sent_tokenize(text))
print("After:", nltk.sent_tokenize(text, language="russian"))
```
or 
```python
import nltk
tokenizer = nltk.data.load('tokenizers/punkt/russian.pickle')
text = "Ай да А.С. Пушкин! Ай да сукин сын!"
print("Before:", nltk.sent_tokenize(text))
print("After:", tokenizer.tokenize(text))
```

Output:
```
Before: ['Ай да А.С.', 'Пушкин!', 'Ай да сукин сын!']
After: ['Ай да А.С. Пушкин!', 'Ай да сукин сын!']
```

## Training data
Data for sentence tokenization was taken from 3 sources:  
– Articles from Russian Wikipedia (about 1 million sentences);  
– Common Russian abbreviations from Russian orthographic dictionary, edited by V. V. Lopatin;  
– Generated names initials.

## Implementation notes
After some research it was found that the single `params.abbrev_types` performs better than together with `params.collocations` and `params.ortho_content`, so the latter were removed from the trained tokenizer.
