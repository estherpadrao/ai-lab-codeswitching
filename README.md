# WhatsApp Code-Switching Analysis (EN–PT)

## Overview

This project analyzes code-switching behavior in multilingual WhatsApp conversations, focusing on English–Portuguese mixing.

Instead of training a model, the notebook uses a rule-based pipeline combined with language detection to label each word and analyze how languages are used within real conversations.

The goal is to understand:

* When and how speakers switch languages
* How much each language is used
* What roles different languages play in a sentence

---

## Dataset

* Raw WhatsApp chat exported as a `.txt` file
* Supports both Android and iOS formats
* Includes real conversational data with informal language, abbreviations, and mixed-language usage

Preprocessing includes:

* Parsing timestamps and senders
* Removing system messages and noise
* Tokenizing messages into words

---

## Problem Setup

* Input: raw chat messages
* Task:

  * Label each word as **English (EN), Portuguese (PT), or UNSURE**
  * Identify patterns of language mixing
* Output:

  * Token-level language labels
  * Aggregated statistics and visualizations

---

## Approach

### 1. Word-Level Language Detection

Each token is labeled using:

* Rule-based filters (short words, abbreviations → UNSURE)
* Lingua (language detection library) for probabilistic language detection

Only high-confidence predictions are used for EN/PT classification.

---

### 2. Code-Switching Analysis

The notebook computes:

* Language usage per message
* Language ratios (EN vs PT)
* Frequency of switching across messages

---

### 3. Per-Sender Analysis

Breaks down behavior by user:

* Number of messages
* Language distribution
* Degree of code-switching

This shows who mixes languages the most and how their usage differs.

---

### 4. Grammatical Role Analysis

Using spaCy:

* Words are tagged with part-of-speech (POS)
* English and Portuguese words are analyzed separately
* Distinguishes:

  * **Content words** (nouns, verbs, adjectives)
  * **Function words** (connectors, auxiliaries, etc.)

This reveals how each language is used structurally.

---

## Visualizations

The notebook includes multiple visualizations:

* Language distribution plots (EN vs PT usage)
* Per-sender comparisons
* English ratio per message
* POS breakdown of code-switched words
* Word clouds showing vocabulary in each language

These help connect raw text data to interpretable patterns.

---

## Key Insights

* The chat is Portuguese-dominant with English insertions
* Code-switching often occurs within sentences, not just between them
* English is frequently used for specific word types or expressions
* Informal text (abbreviations, slang) introduces ambiguity in language detection

---

## Tech Stack

* Python
* Pandas
* NumPy
* Matplotlib / Seaborn
* Lingua (language detection)
* spaCy
* WordCloud

---

## How to Run

1. Export a WhatsApp chat as `.txt`
2. Place it in the working directory
3. Open the notebook:

```bash
jupyter notebook
```

4. Run cells sequentially to parse, label, and analyze the chat
