# Pashto Sentiment Analysis Corpus

A sentence-level sentiment analysis dataset for Pashto — **10,234 sentences labeled positive, neutral, or negative**, drawn from published Pashto news text.

Pashto remains severely under-resourced in NLP, and sentiment analysis is one of the tasks where that gap hurts most: there is simply very little labeled Pashto text to train on. This corpus was built to give researchers a clean, balanced starting point.

## What's inside

| File | Description |
|---|---|
| `Pashto_Corpus_for_Sentiment_Analysis.csv` | `sentence`, `sentiment` — 10,234 rows |

## Class balance

| sentiment | rows |
|---|---|
| positive | 3,548 |
| neutral | 3,355 |
| negative | 3,331 |

The three classes are close to evenly balanced, so accuracy and macro-F1 track each other well.

## Text and orthography

The sentences come from published Pashto news writing and are kept **exactly as their authors wrote them** — no letter normalization (ي/ی, ك/ک distinctions preserved), because Pashto orthography genuinely varies and models should learn the text people actually write. Labels were assigned per sentence and passed through filtering and manual review before release.

## How to use it

```python
import pandas as pd
from sklearn.model_selection import train_test_split

df = pd.read_csv("Pashto_Corpus_for_Sentiment_Analysis.csv")

train, test = train_test_split(df, test_size=0.2, stratify=df["sentiment"], random_state=42)
```

## Related work

A companion dataset by the same author: the **Pashto Topic Classification Dataset** — 27,437 news paragraphs across 12 topics. The two datasets share no text, so they can be combined in multi-task setups.

## License and citation

Released for research and educational use.

```
Khairullah. Pashto Sentiment Analysis Corpus: 10K labeled sentences
for three-class sentiment classification. 2026.
```
