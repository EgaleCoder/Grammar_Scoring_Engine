# voice2grammar-explainable-grammar-scoring-system

This project implements a **rule-based Grammar Scoring Engine** that evaluates spoken English by converting audio into text and analyzing grammatical quality using explainable linguistic features.

The system is designed to be **transparent, offline-capable, and reproducible**, making it suitable for automated evaluation scenarios such as assessments and screenings.

---

## Key Capabilities

- Converts speech to text using OpenAI Whisper
- Cleans and normalizes transcribed text
- Extracts grammar-related linguistic features
- Computes an explainable grammar score (0–10)
- Stores results in a structured CSV output

---

## Grammar Features Used

- **Error Ratio** – frequency of grammar-like mistakes
- **Sentence Length Analysis** – average sentence complexity
- **POS Consistency** – part-of-speech distribution stability
- **Repetition Detection** – word-level redundancy

---

## End-to-End Pipeline

Audio Input(.mp3,.wav)
   ↓
Whisper Transcription
   ↓
Text Cleaning
   ↓
Grammar Feature Extraction
   ↓
Rule-Based Grammar Score (0–10)

---

## How to Run on Kaggle

1. Upload audio samples as a **Kaggle Dataset**
2. Attach the dataset to the notebook
3. Run all notebook cells from top to bottom
4. Output CSV is generated at:



---

## Output Format

The generated CSV contains:

- Audio filename
- Transcribed text
- Extracted grammar features
- Final grammar score

This format is designed for easy inspection, validation, and downstream analysis.

---

## Function-Level Explanation

### `clean_text(text)`

**Purpose:**  
Normalizes raw transcribed text for reliable grammar analysis.

**What it does:**
- Converts text to lowercase
- Removes special characters and extra whitespace
- Normalizes repeated punctuation
- Ensures consistent formatting for downstream processing

**Why needed:**  
Speech-to-text output often contains noise; cleaning ensures fair and consistent feature extraction.

---

### `extract_grammar_features(text)`

**Purpose:**  
Extracts linguistic signals that correlate with grammatical quality.

**Features extracted:**
- **Error Ratio:** Approximate ratio of incorrect constructions
- **Average Sentence Length:** Measures sentence complexity
- **POS Consistency:** Variance in part-of-speech distribution
- **Repetition Score:** Detects excessive word repetition

**Why needed:**  
These features provide **interpretable signals** instead of black-box predictions.

---

### `grammar_score(features)`

**Purpose:**  
Computes a final grammar score using rule-based weighting.

**How it works:**
- Penalizes high error ratio
- Penalizes excessive repetition
- Rewards balanced sentence length
- Rewards stable POS distribution

**Output:**
- Final score scaled between **0 and 10**

**Why rule-based:**  
Ensures explainability, reproducibility, and compliance with offline constraints.

---

## Explanation of Imports

## Import Explanations

### `os`
Used for file and directory operations such as reading audio paths and creating output folders.

### `numpy (np)`
Supports numerical computations like averages, ratios, and feature normalization.

### `pandas (pd)`
Used to store extracted features and grammar scores in a tabular format and export them as CSV.

### `warnings`
Suppresses unnecessary runtime warnings to keep execution logs clean and readable.

### `whisper`
OpenAI Whisper model used for converting speech audio into text (speech-to-text).

### `re` (Regular Expressions)
Used for text cleaning tasks such as removing unwanted characters and normalizing whitespace.

### `nltk`
Natural Language Toolkit used for tokenization and Part-of-Speech (POS) tagging.
