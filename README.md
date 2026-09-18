# POS & NER Tagging on BBC News Headlines

![Python](https://img.shields.io/badge/Python-3.9%2B-3776AB?logo=python&logoColor=white)
![spaCy](https://img.shields.io/badge/spaCy-en__core__web__sm-09A3D5)
![NLTK](https://img.shields.io/badge/NLTK-3.8%2B-154F5B)
![License](https://img.shields.io/badge/License-MIT-green)

Linguistic analysis of 1,000 BBC News headlines using **part-of-speech (POS) tagging** and **named-entity recognition (NER)**. The project builds a classic NLP preprocessing pipeline with NLTK, then uses spaCy to answer a simple question: *what is the news actually talking about?*

## Overview

News headlines are short, dense, and grammatically compressed, which makes them a great playground for token-level NLP. This notebook:

1. Loads 1,000 BBC News articles (headlines + metadata) from `bbc_news.csv`
2. Cleans the headline text — lowercasing, stop-word removal, punctuation stripping
3. Tokenizes with NLTK and lemmatizes with `WordNetLemmatizer`
4. Runs spaCy's `en_core_web_sm` model to assign POS tags to every token
5. Aggregates token frequencies by grammatical role (nouns, verbs, adjectives)
6. Extracts named entities and ranks them by mention count

## Key findings

The corpus is from the 2022 news cycle, and the tag frequencies show it clearly:

| Lens | Top tokens (count) |
|---|---|
| **Nouns** | war (35), record (15), police (14), year (14), win (14) |
| **Verbs** | says (30), found (13), win (12), wins (10) |
| **Adjectives** | new (28), Russian (21), final (16), first (12) |
| **Entities (GPE/NORP)** | Ukraine (47), UK (36), England (32), Russian (20), US |

The dominance of *war*, *Russian*, and *Ukraine* reflects the Russia–Ukraine war coverage, while *says* being the top verb is a nice illustration of how headline journalism attributes statements.

## Project structure

```
├── POS_NER_PRATICAL.ipynb   # Full pipeline: cleaning → POS tagging → NER
├── bbc_news.csv             # 1,000 BBC News headlines with metadata
├── requirements.txt         # Python dependencies
└── README.md
```

## Getting started

```bash
git clone https://github.com/adityashroff06-code/POS-NER-Tagging.git
cd POS-NER-Tagging

python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt

# one-time model/corpus downloads
python -m spacy download en_core_web_sm
python -c "import nltk; [nltk.download(p) for p in ('punkt', 'stopwords', 'wordnet')]"

jupyter notebook POS_NER_PRATICAL.ipynb
```

## Dataset

`bbc_news.csv` contains 1,000 BBC News RSS items with columns `title`, `pubDate`, `guid`, `link`, and `description`. Only the `title` column is used in this analysis. The data is included for reproducibility and is the property of the BBC; it is used here for educational purposes only.

## Tech stack

- **pandas** — data wrangling
- **NLTK** — tokenization, stop words, lemmatization
- **spaCy** (`en_core_web_sm`) — POS tagging and named-entity recognition
- **matplotlib** — visualization

## License

Released under the [MIT License](LICENSE).

## Author

**Aditya Shroff** — [GitHub](https://github.com/adityashroff06-code) · [LinkedIn](https://www.linkedin.com/in/aditya-shroff-8033a31b0)
