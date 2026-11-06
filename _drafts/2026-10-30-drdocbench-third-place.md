---
title: '3rd Place on Dr.DocBench: Image Fidelity and VLM Ensemble for Expert-Level Document Parsing'
date: 2026-10-30
permalink: /posts/2026/10/drdocbench-third-place/
categories:
  - Blog Posts
tags:
  - Competition
  - EMNLP
  - Document Parsing
  - VLM
location: "Singapore"
---
<div align = 'center'>
<!-- PHOTO(cover): leaderboard screenshot or certificate -> /images/emnlp2026/drdocbench-leaderboard.png -->
</div>

Our team **OC** finished **3rd** in the [Dr.DocBench Challenge](https://drdocbench-challenge.abaka-pages.com/) at the EMNLP 2026 DocInsights workshop, with an **Overall score of 85.63**.

## The task

Dr.DocBench is a difficulty-aware benchmark for expert-level document parsing, developed by 2077AI and collaborators. The challenge, organized and sponsored by Abaka AI, asks participants to convert hard document images into structured Markdown. Each page gets one prediction (single-page setting, rather than the two-page window in the original benchmark), and the output has to preserve the original-language text, HTML tables, LaTeX formulas, reading order and document structure.

Scoring uses four component metrics: **Text Edit Distance** (lower is better), **Table TEDS**, **Formula CDM** and **Reading Order** (higher is better). The **Overall** score averages the available component scores per page and then across scorable pages, and it decides the ranking.

## Final leaderboard

| Rank | Team | Overall |
|---|---|---|
| 1 | ohmyyuan | 87.28 |
| 2 | AIKHEMIST | 85.83 |
| 3 | **OC** | **85.63** |

The gap from 3rd to 1st is 1.65 points.
Timeline: the competition opened on August 10, the submission deadline was October 10, final evaluation ran October 11-23, and the winners were announced at the workshop on October 29.

## Our approach: image fidelity and a VLM ensemble

The shared-task paper is *Image Fidelity and VLM Ensemble for Expert-Level Single-Page Document Parsing on Dr.DocBench*.

<!-- TODO(Yushuo): I only know the title of the method. Please answer these in a few lines each and I will turn them into prose:
 1. "Image fidelity": what did you do (resolution/upscaling, rendering, cropping, preprocessing)? Why did it matter?
 2. Which VLMs were in the ensemble (names, sizes)?
 3. How did you combine outputs (per-region routing, voting, selection by a metric, merging tables/formulas)?
 4. Per-metric scores (Text Edit Distance, Table TEDS, Formula CDM, Reading Order) and what you were strongest/weakest at.
 5. Ablations: what gave the biggest gain; anything that did not work.
 6. Compute / time budget and the 3-submissions-per-day constraint: how did you decide what to submit?
 Only public information, nothing from the company. -->

## Lessons

<!-- TODO(Yushuo): 3-4 takeaways, e.g. what you'd do with another month. -->

## Links

- Challenge page: [drdocbench-challenge.abaka-pages.com](https://drdocbench-challenge.abaka-pages.com/)
- Workshop write-up: [DocInsights @ EMNLP 2026](/posts/2026/10/docinsights-emnlp-2026/)
