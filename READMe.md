# plant-disease-predictor
# Plant Disease Predictor

A small, text-based Python utility that performs simple rule-based predictions of common plant problems from a user's description of symptoms. The project matches words from a symptom description against a built-in keyword dictionary for a few conditions and prints a probable diagnosis, cause, and suggested treatment.

This tool is intended as an educational/demo script — not a substitute for a professional diagnosis.

---

## Table of contents
- Overview
- Features
- Technologies / Tools used
- How it works
- Installation
- Run the project
- Testing
- Text "screenshots" (sample terminal runs)
  

---

## Overview

The Plant Disease Predictor is a tiny command-line program implemented in pure Python. It contains a small `diseases` dictionary where each disease has:
- a list of keywords,
- a short cause description,
- simple treatment advice.

When a user types a symptom description, the script:
1. tokenizes the input (lowercase + split on whitespace),
2. counts keyword matches per disease,
3. returns the disease with the highest match count (or a general suggestion if no matches).

Included example dictionary (from the script):
- powdery mildew
- leaf blight
- root rot
- nutient deficiency

---

## Features

- Zero-dependency, pure-Python script.
- Keyword-based symptom matching.
- Prints predicted disease, cause and treatment.
- Easy to extend: add or modify diseases and keywords directly in the script.
- Can be refactored to be importable for unit tests or to power a small web UI.

---

## Technologies / Tools used

- Python 3 (3.6+ recommended)
- Optional: pytest for automated tests
- No external libraries required for the core script

---

## How it works (brief)

- The `diseases` dictionary maps disease names → metadata (keywords, cause, treatment).
- `predict_disease(text)` lowercases and splits the input text into tokens, then counts matches of those tokens against each disease's keyword list.
- The disease with the highest match count is returned. If the top score is zero, the script prints a general suggestion instead.

The current script is exact-word based (no stemming, punctuation removal, or fuzzy matching).

---

## Installation

1. Clone the repository:
```bash
git clone https://github.com/harshirathore2007-crypto/plant-disease-predictor.git
cd plant-disease-predictor
```

2. (Optional) Create and activate a virtual environment:
```bash
python3 -m venv .venv
# macOS / Linux
source .venv/bin/activate
# Windows (PowerShell)
.venv\Scripts\Activate.ps1
```

3. No packages are required for the basic script. If you intend to run tests install pytest:
```bash
pip install pytest
```

---

## Run the project

1. Save the provided script to a file (for example `predict.py`). Example content (already in your repository) — ensure it is guarded by a main check if you want to import it for tests


 2. At the prompt, type a plain-English description of symptoms:
Example:
describe the plant symtoms : leaves are white with a powdery coating

---

## Testing

Manual testing:
- Run the script and type different symptom descriptions to verify expected outputs.

Automated testing:
- To write simple unit tests, import `predict_disease` from `predict.py`. Make sure the script uses `if __name__ == "__main__":` guard so import doesn't trigger the input prompt.

Example test file: `tests/test_predict.py`
```python
# tests/test_predict.py
from predict import predict_disease

def test_powdery_mildew():
    assert predict_disease("white powder on leaves") == "powdery mildew"

def test_leaf_blight():
    assert predict_disease("brown edges and dry leaves") == "leaf blight"

def test_root_rot():
    assert predict_disease("roots are wet and black and soft") == "root rot"

def test_no_match():
    assert predict_disease("plant is growing well and green") is None
```

Run tests:
```bash
pytest -q
```

---



