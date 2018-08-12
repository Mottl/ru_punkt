# ru_punkt
Russian language support for NLTK's PunktSentenceTokenizer

## Instalation
1. Install NLTK python package:
```bash
pip install nltk
```

2. Download ru_punkt:
```bash
git clone https://github.com/Mottl/ru_punkt.git
```

3. Download 'punkt' data:
```python
import nltk
nltk.download('nltk')
```

4. Copy Russian tokenizer into `nltk_data` folder (ensure which one is appropriate for your OS):
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
tokenizer = nltk.load('tokenizers/punkt/russian.pickle')
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
