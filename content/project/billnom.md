---
title: "Bill Nom"
date: 2023-03-06T15:14:18-06:00
author: "Erik Heen"
tags: ["ai","ml","nlp"]
description: "A lightweight NLP model to summarize legislative documents." 
draft: false
canonicalURL: "https://heen.dev/project/billnom"
cover:
    image: "/img/BillNom.png"
    alt: "Bill Nom icon"
    caption: "Icon is from an open-source, royalty-free icon library"
    relative: false
    hidden: true
editPost:
    URL: "https://git.heen.dev/billnom"
    Text: "View Source on GitHub"
---

> *1st place submission at Minnehack 2023, an annual hackathon at the University of Minnesota.*

Bill Nom takes in a URL for a bill on the [Minnesota Revisor's Office website](https://www.revisor.mn.gov/), scrapes the bill's contents, digests it with a lightweight Natural Language Processing (NLP) model, and outputs a summary that's easier for laypeople to grasp than the full text. The NLP model powering Bill Nom is small compared to many language models, at 230 MB, it can easily run under the memory and processing power limitations of a consumer-grade laptop.

Just like any other machine learning model, Bill Nom should not be perceived as any sort of panacea for complex, real-world issues. However, my team and I believe that it serves as a valuable proof-of concept for a tool that can alleviate the task of digesting "legalese"; a task often quite daunting for the average citizen.

## Structure

- The model at the heart of it was produced with the [T5 model from Google](https://huggingface.co/google/flan-t5-small) imported from [Huggingface](https://huggingface.co/)
- Our training data was obtained by scraping around a thousand documents from the [MN Revisor's Office website](https://www.revisor.mn.gov/), using [Beautiful Soup 4 (BS4)](https://beautiful-soup-4.readthedocs.io/en/latest/#).
- We used Pandas dataframes to process the raw JSON files produced by BS4.
- It was trained in a Jupyter notebook with PyTorch, which took approximately three hours to complete running on an Nvidia 3060 12GB.
- Front-end built using [Dash by Plotly](https://dash.plotly.com/). 
- API to access the back-end is just Python.

## Why

People often struggle trying to parse common legal vernacular, often dubbed "legalese" as a result. As a written language, legalese occupies an odd niche of being both very formulaic and very lacking in any sort of natural flow. It can feel very reduntant to read, with only a few keywords changing between otherwise identical phrases. Sentences can stretch on for much longer than is normal for common english.

This ultimately leaves the reader confused, as they are attempting to digest something written in a format that was intended to be logistically robust when taken together as a single unit, not necessarily construct any sort of narrative for the reader's internal dialogue to latch onto. All of this to say, reading and understanding legal documents is a very different skill than just reading common english.

## Source code

[github.com/eaheen/billnom](https://git.heen.dev/billnom)
