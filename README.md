# Reducing Token Waste in Academic LLM Usage: Implications for Sustainable AI Computing


An empirical study investigating token waste in academic LLM interactions. It evaluates how optimized prompting across tasks—like assignment writing, exam prep, and coding—reduces token consumption, latency, and environmental impact without loss of educational quality, offering user-focused Green AI solutions.

This repository contains the empirical dataset, prompt optimization framework, and token consumption analysis scripts for the paper **"Reducing Token Waste in Academic LLM Usage"**.

## 📌 Project Overview
While Large Language Models (LLMs) significantly enhance student productivity, redundant prompt instructions and unnecessarily long contexts lead to computational inefficiency and energy waste. This project investigates how prompt optimization preserves educational quality while cutting down token usage.

## 📊 Dataset Categories
The dataset includes pairs of **Baseline (Inefficient)** vs. **Optimized** prompts across 5 key academic domains:
1. Assignment Writing
2. Exam Preparation
3. Programming Assistance
4. Concept Learning
5. Research Paper Summarization






token-waste-academic-llm/
│
├── README.md                      # প্রজেক্টের সারসংক্ষেপ, পেপারের তথ্য এবং ব্যবহারের নিয়মাবলী
├── LICENSE                        # Open-source লাইসেন্স (যেমন: MIT)
├── .gitignore                     # অনাবশ্যক ফাইল (যেমন: __pycache__, .env, .DS_Store)
├── requirements.txt               # প্রজেক্টের প্রয়োজনীয় লাইব্রেরি (tiktoken, pandas, matplotlib ইত্যাদি)
│
├── dataset/                       # আপনার তৈরি করা ডাটাবেস
│   ├── dataset.csv                # মূল মাস্টার ডাটা (সবগুলো ক্যাটাগরি একসাথে)
│   ├── dataset.jsonl              # LLM ইভালুয়েশনের জন্য JSONL ফরম্যাট
│   └── categories/                # ৫টি ক্যাটাগরির আলাদা আলাদা মার্কডাউন ফাইল
│       ├── 01_assignment_writing.md
│       ├── 02_exam_preparation.md
│       ├── 03_programming_help.md
│       ├── 04_concept_learning.md
│       └── 05_research_summarization.md
│
├── src/                           # টোকেন গণনা ও অ্যানালাইসিসের পাইথন কোড
│   ├── token_counter.py           # tiktoken দিয়ে ইনপুট/আউটপুট টোকেন হিসেব করার কোড
│   ├── latency_analyzer.py        # রেসপন্স টাইমের তথ্য বিশ্লেষণের কোড
│   └── quality_evaluator.py       # ১-৫ স্কেলে হিউম্যান জাজমেন্ট স্কোরের স্ক্রিপ্ট
│
├── paper/                         # আপনার গবেষণাপত্রের ডকুমেন্টস
│   ├── main_paper.pdf             # চূড়ান্ত রিসার্চ পেপারের পিডিএফ
│   └── paper_draft.md             # পেপারের ড্রাফট বা টেক্সট ভার্সন
│
└── visualization/                 # গ্রাফ ও চার্ট (Matplotlib/Seaborn দিয়ে তৈরি)
    ├── token_reduction_bar_chart.png
    └── latency_vs_quality_plot.png
