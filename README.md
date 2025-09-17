# JSCON-schema-task2
# JSON Schema Classification & Information Extraction (Task 2)

[![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)]()
[![Run on Colab](https://img.shields.io/badge/Run%20on-Colab-F9AB00?logo=googlecolab\&logoColor=white)]()
[![Groq API](https://img.shields.io/badge/Powered%20by-Groq%20API-ff69b4)]()
[![OpenAI Compatible](https://img.shields.io/badge/OpenAI-Compatible-green)]()

---

## Project Summary

This repository demonstrates **JSON Schema–based Information Extraction** using **Groq API with OpenAI‑style function calling**. The notebook defines a JSON schema to capture five key details from unstructured chat inputs:

* Name
* Email
* Phone
* Location
* Age

The implementation calls the Groq API with structured function definitions so that responses are returned directly in JSON format, then validates the results against the schema.

---

## Table of Contents

1. [Key Features](#key-features)
2. [Repository Structure](#repository-structure)
3. [Quick Demo](#quick-demo)
4. [Prerequisites](#prerequisites)
5. [Installation & Setup](#installation--setup)
6. [Configuration](#configuration)
7. [How to Run](#how-to-run)
8. [Implementation Notes](#implementation-notes)
9. [Examples & Expected Output](#examples)
10. [Evaluation Checklist](#evaluation-checklist)
11. [Security & Best Practices](#security--best-practices)
12. [Troubleshooting](#troubleshooting)
13. [Contributing & License](#contributing--license)

---

## Key Features

* ✅ Define a **JSON schema** with 5 fields (name, email, phone, location, age).
* ✅ **Function calling** style prompts to force structured outputs.
* ✅ Extracts structured data from multiple styles of chat inputs.
* ✅ **Schema validation** using Python (ensures fields match definitions).
* ✅ Notebook demonstrates at least **3 sample chats** with diverse input.
* ✅ Outputs are clean, JSON‑compliant, and ready for downstream use.

---

## Repository Structure

```
JSCON-schema-task2/
├─ JSCON_schema.ipynb       # Main notebook implementing extraction & validation
├─ Copy_of_JSCON_schema.ipynb # (optional) backup/notebook copy
├─ README.md                 # This file
├─ assets/                   # (optional) screenshots / sample outputs
└─ requirements.txt          # Minimal dependencies
```

---

## Quick Demo

**Input Chat:**

```
User: Hi, I am Ravi Kumar. My email is ravi.k@example.com, and my phone number is +91-9876543210. I live in Bangalore and I am 24 years old.
```

**Model Output:**

```json
{
  "name": "Ravi Kumar",
  "email": "ravi.k@example.com",
  "phone": "+91-9876543210",
  "location": "Bangalore, India",
  "age": 24
}
```

Schema validation confirms the JSON structure matches the specification.

---

## Prerequisites

* Python 3.8+ (or Google Colab runtime).
* Groq API key (OpenAI‑compatible).
* Libraries: `openai` (Groq SDK), `jsonschema` (optional, for validation).

---

## Installation & Setup

**Option A — Run in Google Colab:**

1. Open `JSCON_schema.ipynb` in Colab.
2. Set your API key in the first cell:

```python
import os
os.environ['OPENAI_API_KEY'] = 'YOUR_API_KEY'
```

3. Run all cells.

**Option B — Run locally:**

```bash
git clone https://github.com/Bhoomika685/JSCON-schema-task2.git
cd JSCON-schema-task2
pip install -r requirements.txt
export OPENAI_API_KEY="your_api_key_here"
```

Then run the notebook in Jupyter.

---

## Configuration

In the notebook, the schema is defined like this:

```python
schema = {
  "type": "object",
  "properties": {
    "name": {"type": "string"},
    "email": {"type": "string", "format": "email"},
    "phone": {"type": "string"},
    "location": {"type": "string"},
    "age": {"type": "integer"}
  },
  "required": ["name", "email", "phone", "location", "age"]
}
```

You can extend or modify this schema to add fields such as **date of birth, gender, or address**.

---

## How to Run

1. Open the notebook.
2. Set the API key.
3. Review the schema definition cell.
4. Run the function‑calling extraction cell with a chat input.
5. Inspect the JSON output.
6. Validate against the schema (the notebook shows validation success/failure).

---

## Implementation Notes

* Uses Groq API in OpenAI‑compatible mode.
* Defines a function `extract_user_info` with arguments mapping directly to schema fields.
* Calls `client.chat.completions.create()` with `functions=[schema_definition]` to enforce structured output.
* Applies validation via `jsonschema` library to check compliance.

---

## Examples & Expected Output

**Example 1:**

```
User: Hello, my name is Aarti. You can mail me at aarti123@gmail.com. My phone is 9876501234, I stay in Pune, and I am 22.
```

**Output:**

```json
{
  "name": "Aarti",
  "email": "aarti123@gmail.com",
  "phone": "9876501234",
  "location": "Pune, India",
  "age": 22
}
```

**Example 2:**

```
User: This is Karthik, 25 years, living in Hyderabad. Contact: karthik@email.com / +91 9123456789.
```

**Output:**

```json
{
  "name": "Karthik",
  "email": "karthik@email.com",
  "phone": "+91 9123456789",
  "location": "Hyderabad, India",
  "age": 25
}
```

---

## Evaluation Checklist

* [x] JSON schema with 5 fields defined ✅
* [x] Function calling with Groq/OpenAI client ✅
* [x] Parsing of at least 3 sample chats ✅
* [x] Validation of outputs against schema ✅
* [x] Notebook outputs visible & clear ✅

---

## Security & Best Practices

* Do **not** commit API keys into GitHub.
* For demonstration, leave a placeholder cell asking the grader to insert their key at runtime.
* Use `.gitignore` for local `.env` files.

---

## Troubleshooting

* **Empty output or wrong JSON** → Check function definition format.
* **Schema validation fails** → Ensure all required fields are present in the chat input.
* **API errors** → Verify `OPENAI_API_KEY` and your Groq account limits.

---

## Contributing & License

**Author:** Bhoomika Hemkar (GitHub: @Bhoomika685)

