# Arabic Fake News Dataset | مجموعة بيانات الأخبار العربية المضللة

> A dataset of Arabic news claims collected from three Arabic fact-checking platforms, labelled by each platform's verdict. Built for research on Arabic fake-news detection and NLP.
> مجموعة بيانات لأخبار وادعاءات عربية جُمعت من ثلاث منصات عربية لتدقيق الحقائق، مصنّفة حسب حكم كل منصة، لأغراض البحث في كشف الأخبار المضللة ومعالجة اللغة العربية.

## Sources / المصادر

| Platform | Country | Labels | Raw files |
|---|---|---|---|
| [Akeed](https://akeed.jo) — أكيد | Jordan | (single set of fact-checked claims) | 176 JSON |
| [Fatabyyano](https://fatabyyano.net) — فتبيّنوا | Regional | deceptive, fake, misleading-title, not-qualified, partially-fake, sarcastic | 1,154 JSON |
| [Misbar](https://misbar.com) — مسبار | Regional | commotion, false, misleading, myth, satire, selective, true, unclear | 2,726 JSON |

## Structure

```
Akeed/                      # one JSON file per article: url, title, text, img
Fatabayanoo/
├── RawData/<label>/*.json  # raw articles grouped by label
├── csvfiles/<label>.csv    # one CSV per label
└── fake_fatabayanoo_main.xlsx
Misbar/
├── RawData/<label>/*.json
├── XlsxData/
├── csvfiles/<label>.csv
└── fake_misbar_main.xlsx
```

Each record contains the article **URL**, **title**, **full text** and, where available, the **image URL**.

## Example

```python
import pandas as pd

fake = pd.read_csv("Fatabayanoo/csvfiles/fake.csv")
print(fake.head())
```

## Possible uses / الاستخدامات

- Training and evaluating Arabic fake-news / misinformation classifiers
- Multi-class claim classification using the platforms' verdict labels
- Arabic NLP research: text classification, stance detection, summarisation

## Data rights / حقوق البيانات

The articles belong to their original publishers (Akeed, Fatabyyano, Misbar). This dataset is shared **for research and educational purposes only**; please cite the original platforms and respect their terms of use. No licence is granted over the third-party content.

المحتوى ملك لمنصاته الأصلية، ويُشارك هنا لأغراض البحث والتعليم فقط، مع ضرورة الإشارة إلى المصادر واحترام شروط استخدامها.
