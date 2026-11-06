---
title: 'DocInsights @ EMNLP 2026 (Budapest): Calibrated Confidence for Document STP, and a Dr.DocBench Shared Task Paper'
date: 2026-10-29
permalink: /posts/2026/10/docinsights-emnlp-2026/
categories:
  - Blog Posts
tags:
  - EMNLP
  - Workshop
  - Document AI
  - VLM
location: "Budapest, Hungary"
---
<!-- PHOTO(cover): workshop room or Budapest skyline -> /images/emnlp2026/cover.jpg
<div align = 'center'>
<img src='/images/emnlp2026/cover.jpg' width = "600" >
</div>
-->

The **DocInsights 2026** workshop (Workshop on Document Intelligence and Understanding), co-located with EMNLP 2026, was held on **October 29, 2026 in Budapest**, Hungary. We had two papers there.

## 1. Calibrated confidence for straight-through processing

**Perception, Layout, and Validation: Calibrated Confidence for Reliable Straight-Through Processing of Financial Documents.** [ACL Anthology](https://aclanthology.org/2026.docinsights-1.17/), pp. 232-243.

Straight-through processing (STP) means key-value fields extracted from financial documents are accepted without human review. That requires a calibrated probability for each field and a bounded error rate among the auto-approved ones. VLMs can extract the fields, but their *verbalized* confidence is unreliable.

We build a **decomposed confidence score from three channels: perception, layout and validation**, and combine it with **conformal risk control**. On three public datasets (real invoices, synthetic invoices and ad-buy forms), with two VLM families (Qwen3.6-27B and Gemini-3.1-Flash-Lite):

- AUROC rises from **0.54-0.74** for the VLMs' native confidence signals to **0.90-0.99**.
- At a target error of 10% or less, native VLM confidence auto-approved only **0.1%-7.0%** of fields, while our method auto-approved **49-72%** and kept the error of accepted fields at or below the target.

## 2. Dr.DocBench shared task paper

**Image Fidelity and VLM Ensemble for Expert-Level Single-Page Document Parsing on Dr.DocBench.** This is the system description for our entry in the Dr.DocBench Challenge, which ended up in third place. The technical write-up is in a [separate post](/posts/2026/10/drdocbench-third-place/).

## At the workshop

<!-- TODO(Yushuo): your impressions: the room (Room F3), who presented (Yuxuan Han presented both papers), questions from the audience, favourite talks/posters, the Dr.DocBench winners announcement. -->

<!-- PHOTO: presentation / slides -> /images/emnlp2026/talk.jpg -->
<!-- PHOTO: workshop room -> /images/emnlp2026/room.jpg -->
<!-- PHOTO: team photo -> /images/emnlp2026/team.jpg -->
<!-- PHOTO: Budapest -> /images/emnlp2026/budapest.jpg -->

Proceedings are on the ACL Anthology as [2026.docinsights-1](https://aclanthology.org/volumes/2026.docinsights-1/). After the workshop I stayed on for some sightseeing; see [Vienna & Budapest](/posts/2026/11/vienna-budapest/).
