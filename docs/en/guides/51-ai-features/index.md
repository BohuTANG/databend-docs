---
title: 'Databend AI and ML(2024)'
sidebar_label: 'Databend AI & ML'
---


# Databend AI and Machine Learning

This article provides an overview of Databend's AI Functions, which are built-in SQL functions that enable direct application of AI to your data. Databend leverages advanced large language models (LLMs) hosted on Hugging Face, designed for enterprise-grade performance.

## Key Features

- **No Setup Required**: Seamlessly integrate AI capabilities into your SQL queries.
- **Open-Source Models**: Utilizes transparent and community-driven models from Hugging Face.
- **Data Security**: Your data remains within Databend's secure environment and is used exclusively by you.
- **Enterprise-Grade Performance**: Designed to handle large-scale data operations efficiently.

## Availability


| Function (Model)                   | AWS US East 2(Ohio) | AWS US East 1(N. Virginia) | AWS US West 2(Oregon) | AWS Asia Pacific (Singapore) | AWS Europe (Frankfurt) |   |
|------------------------------------|---------------------|----------------------------|-----------------------|------------------------------|------------------------|---|
| embed_text_768        (e5-base-v2) | ✔                   |                            |                       |                              |                        |   |
| ai_vector_similarity  (e5-base-v2) | ✔                   |                            |                       |                              |                        |   |
| ai_text_similarity    (e5-base-v2) | ✔                   |                            |                       |                              |                        |   |
| ai_sentiment           (qwen-7b)   | ✔                   |                            |                       |                              |                        |   |
| ai_extract             (qwen-7b)   | ✔                   |                            |                       |                              |                        |   |
| ai_classify            (qwen-7b)   | ✔                   |                            |                       |                              |                        |   |
| ai_translate           (qwen-7b)   | ✔                   |                            |                       |                              |                        |   |
| ai_generate            (qwen-7b)   | ✔                   |                            |                       |                              |                        |   |

