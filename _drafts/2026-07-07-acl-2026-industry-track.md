---
title: 'ACL 2026 (San Diego): A Multistage Extraction Pipeline for Long Scanned Financial Documents'
date: 2026-07-07
permalink: /posts/2026/7/acl-2026-industry-track/
categories:
  - Blog Posts
tags:
  - ACL
  - Conference
  - Document AI
  - VLM
location: "San Diego, U.S."
---
<!-- PHOTO(cover): ACL venue overall shot -> /images/acl2026/venue.jpg
<div align = 'center'>
<img src='/images/acl2026/venue.jpg' width = "600" >
</div>
-->

Our paper **A Multistage Extraction Pipeline for Long Scanned Financial Documents: An Empirical Study in Industrial KYC Workflows** appeared in the Industry Track of the 64th Annual Meeting of the Association for Computational Linguistics (ACL 2026, July 2-7, San Diego).
It is in *Proceedings of ACL 2026, Volume 6: Industry Track*, pp. 1419-1433. [Paper on ACL Anthology](https://aclanthology.org/2026.acl-industry.99/).

## The problem

KYC, anti-money-laundering and compliance teams need structured data from financial documents that are long, multilingual, scanned, noisy and visually inconsistent. A file can run to dozens of pages, yet only a few pages matter for any given field. Feeding the whole file to a vision-language model (VLM) end-to-end turns out to be unreliable. The paper's argument: **find the right pages first, then let a compact VLM read only those.**

## The pipeline

1. **Image preprocessing.** Edge/contour detection removes blank areas and borders; skew is fixed in two steps (PaddleOCR's orientation classifier for coarse rotation, a Hough transform for fine skew); then rescaling, CLAHE contrast normalization and light denoising.
2. **Multilingual OCR.** PaddleOCR (v3) and EasyOCR are compared.
3. **Hybrid page-level retrieval.** Each target field gets a query built from financial terms, document-type cues and language-specific keywords. BM25 catches exact keywords, sentence embeddings catch paraphrases, and the combined score ranks the pages.
4. **Compact VLM extraction.** A structured prompt (field keywords, document-type cues, output format) guides the model, which can also flag ambiguity in a remarks field.
5. **Human-in-the-loop review.** Analysts check every field, as KYC rules require, and their corrections are used to refine prompts and retrieval queries. The reported metrics are raw model outputs, before corrections.

## Results

The evaluation set is 120 production KYC documents (about 3,000 scanned pages): 81 financial statements and 39 payslips in English, Indonesian, Simplified Chinese and Traditional Chinese. The data cannot be released. Everything ran on a single NVIDIA A100 80GB.

Field-level accuracy:

| OCR | VLM | Full pipeline | Direct PDF to VLM |
|---|---|---|---|
| PaddleOCR | MiniCPM-o-2.6 | **87.27%** | 55.38% |
| PaddleOCR | Qwen3-VL-8B-Instruct | 85.30% | 55.91% |
| PaddleOCR | Gemma-3-27B-IT | 72.97% | 47.64% |
| EasyOCR | MiniCPM-o-2.6 | 75.20% | 54.20% |

- The best pair gains about **31.9 points** over feeding the document straight to the VLM.
- Page retrieval cut the pages sent to the VLM by roughly **70%**, with per-page inference time comparable to the baseline.
- **Ablations:** removing page-level retrieval hurt the most (about 16-24 points), image preprocessing came second (about 6-16), and structured prompting added under 5 points on average. Payslips are the exception: they are short, so prompting matters most and retrieval matters little.
- A smaller model with well-curated input beat a bigger one: MiniCPM-o-2.6 outperformed Gemma-3-27B-IT.

## Limitations

Terminology varies across documents (revenue, income, sales), which can break retrieval; low-quality scans and handwriting cause OCR errors; currency-unit ambiguity in multilingual text (IDR'000, ribuan, juta) causes magnitude mistakes; and prompts and queries are still written by hand per field.

## At the conference

<!-- TODO(Yushuo): 1-3 paragraphs in your own words: poster or oral? who you talked to, questions people asked, talks you liked, anything surprising. -->

<!-- PHOTO: poster / presentation -> /images/acl2026/poster.jpg -->
<!-- PHOTO: venue / sessions -> /images/acl2026/session.jpg -->
<!-- PHOTO: you at the conference -> /images/acl2026/me.jpg -->

The conference social event was held aboard the USS Midway, which gets its own [short post](/posts/2026/7/acl-2026-uss-midway/).
