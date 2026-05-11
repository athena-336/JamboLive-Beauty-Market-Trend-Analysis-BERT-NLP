# Beauty Market Trend Analysis with BERT & NLP

An end-to-end NLP pipeline that cleans, classifies, and analyzes 
beauty product sales data from a Taiwanese e-commerce platform, 
with brand-level sales forecasting for market trend insights.

國立政治大學 文字探勘課程 · NCCU Text Mining Final Project · 2023 · 第九組

---

## Objective

Analyze beauty market trends from a national perspective — 
identifying top-performing countries, seasonal patterns, 
hot brands, and predicting January 2023 top sellers.

---

## Data
Data provided by industry partner under NDA. 
Raw data is not included in this repository.

---

## Pipeline

```
Raw Product Data
    ↓
Data Filtering (beauty & health category only)
    ↓
Text Cleaning (regex noise removal)
    ↓
Country Extraction (keyword matching + city-to-country mapping)
    ↓
Brand Extraction (CKIP tokenization + manual brand list)
    ↓
BERT Classification (product category labeling)
    ↓
Sales Analysis + Forecasting
```

---

## Tech Stack

| Step | Technology |
|---|---|
| Text Preprocessing | Python, Regex, CKIP Tokenizer |
| Product Classification | BERT (`bert-base-chinese`), fine-tuning on 500 labeled samples |
| Training Environment | Google Colab (GPU) |
| Train/Val/Test Split | 8 : 1 : 1 |
| Sales Analysis | Pandas, Matplotlib |
| Forecasting | ARIMA, Exponential Smoothing |

---

## BERT Classification

- 500 samples labeled via GPT + manual correction
- Fine-tuned `BertForSequenceClassification` on product names
- Outputs: large category (大類) + small category (小類)
- Example: 胺基酸潔面乳 → 保養品 / 洗面乳

---

## Key Findings

**Top Markets by Sales**
Korea dominates beauty sales volume; France leads in average 
unit price (luxury brands); USA benefits from high brand 
familiarity among Taiwanese consumers.

**Seasonal Patterns**
- July spike: Korean sunscreen products
- November spike: gift sets ahead of Christmas and New Year

**Top Brand — Korea**
Whoo后 leads in sales volume, driven by anti-aging positioning 
and gift box bundles in November.

**2023 January Sales Forecast**
Both ARIMA and Exponential Smoothing models predict Whoo后 
as the top brand, followed by Estee Lauder / Sulwhasoo / LANCOME.

---

## Team

| Member | Role |
|---|---|
| 黃筠茜 (Athena) | Results Analysis |
| 楊鵑慈 | Results Analysis |
| 江翊瑄 | Data Preprocessing |
| 黃任謙 | Data Preprocessing |

---

## 中文簡介

針對台灣電商平台美妝保健類商品進行文字探勘與市場趨勢分析。
流程包含正規表達式清洗、CKIP 斷詞輔助品牌萃取、BERT 中文模型
商品分類（500 筆人工標記訓練集），以及 ARIMA 與指數平滑法進行
品牌銷售額預測。最終找出各國熱門品牌、季節性趨勢，並預測 2023 
年 1 月爆牌排名。
