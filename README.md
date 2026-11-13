# Arabic Fake News Dataset | مجموعة بيانات الأخبار العربية المضللة

> A dataset of Arabic news claims collected from three Arabic fact-checking platforms, labelled by each platform's verdict. Built for research on Arabic fake-news detection and NLP.
> مجموعة بيانات لأخبار وادعاءات عربية جُمعت من ثلاث منصات عربية لتدقيق الحقائق، مصنّفة حسب حكم كل منصة، لأغراض البحث في كشف الأخبار المضللة ومعالجة اللغة العربية.

## Research / البحث

This dataset was collected and curated by **Israa Khalil Alnabrisi** for her master's research at the Islamic University of Gaza, published as:

> Alnabrisi, I. K., & Saad, M. K. (2024). *Detect Arabic fake news through deep learning models and Transformers*. **Expert Systems with Applications**, 251, 123997. [https://doi.org/10.1016/j.eswa.2024.123997](https://doi.org/10.1016/j.eswa.2024.123997)

- About 4,000 labelled claims were scraped from the three platforms below, then cleaned, de-duplicated and curated into the 2,000-article **ArabicFakeNews** corpus used in the paper.
- Three versions of the corpus were tested: **title**, **description** and **full text**, to study how text length affects the models.
- Models compared: BiLSTM and BiGRU, Arabic Transformers (AraBERT, AraELECTRA, QARiB, ARBERT/MARBERT, ArGPT2) and zero-shot learning.
- Transformers outperformed the deep learning models on all three versions. The best result was **AraBERTv2 on the description version**:

| Model | Version | Accuracy | F1 | Precision | Recall |
|:--|:--|:--:|:--:|:--:|:--:|
| AraBERTv2 | Description | 0.97 | 0.97 | 0.97 | 0.966 |

Scrapers, notebooks and models: [motazsaad/Arabic-Fakenews](https://github.com/motazsaad/Arabic-Fakenews) (main contributor: Israa Khalil Alnabrisi).

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

## Citation / الاستشهاد

If you use this dataset, please cite:

```bibtex
@article{alnabrisi2024arabic,
  title   = {Detect Arabic fake news through deep learning models and Transformers},
  author  = {Alnabrisi, Israa Kh. and Saad, Motaz Kh.},
  journal = {Expert Systems with Applications},
  volume  = {251},
  pages   = {123997},
  year    = {2024},
  doi     = {10.1016/j.eswa.2024.123997}
}
```

## Data rights / حقوق البيانات

The articles belong to their original publishers (Akeed, Fatabyyano, Misbar). This dataset is shared **for research and educational purposes only**; please cite the original platforms and respect their terms of use. No licence is granted over the third-party content.

المحتوى ملك لمنصاته الأصلية، ويُشارك هنا لأغراض البحث والتعليم فقط، مع ضرورة الإشارة إلى المصادر واحترام شروط استخدامها.
