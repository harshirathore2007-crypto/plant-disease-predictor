# Project Statement — Plant Disease Predictor 

## Problem statement
Home gardeners, hobbyists, and small-scale growers often notice symptoms on their plants (discolored leaves, spots, wilting, soggy soil) but lack an easy, immediate way to map those natural-language observations to likely causes and simple next steps. Professional diagnosis can take time and may not be readily accessible. This project provides a small, offline, text-based utility that takes a plain-English description of plant symptoms and returns a likely condition along with a short cause and basic treatment guidance.

## Scope of the project
In-scope:
- A pure-Python, zero-dependency command-line program that accepts a short plain-English symptom description and returns a rule-based prediction (disease/condition).
- A simple, editable disease dictionary mapping condition names to keywords, short causes, and treatments.
- Clear behavior for no-match results (general suggestions).
- Unit-testability (script guarded by `if __name__ == "__main__":` so functions can be imported).
- Documentation (README and this statement file).

Out-of-scope:
- Professional medical or agricultural-grade diagnoses.
- Image-based diagnosis, machine learning models, or integration with cloud APIs.
- Advanced natural language processing (stemming, punctuation removal, fuzzy matching, synonyms) in the initial version.
- A web UI, mobile app, or real-time monitoring features (may be considered later).

Assumptions and limitations:
- The predictor is keyword-based and relies on exact token matches; it may miss matches due to punctuation, pluralization, or alternate phrasing.
- The disease dictionary is small and illustrative — results are educational, not definitive.
- Users should consider the suggestions as starting points and consult experts for serious or widespread plant problems.

## Target users
- Home gardeners who want a quick hint about common plant problems.
- Hobbyist growers and students learning basic plant pathology concepts.
- Educators demonstrating simple rule-based text matching in Python.
- Developers who want a minimal baseline to extend into tests, a web UI, or a more advanced NLP/ML system.

## High-level features
- Command-line interaction: prompt the user for a symptom description and print a predicted condition with cause and treatment.
- Keyword-based matching: a small dictionary of conditions with associated keyword lists is searched against the user's input.
- No external dependencies: runs with Python 3.6+ without additional packages.
- Importable prediction function: `predict_disease(text)` can be imported and unit tested.
- Clear fallback: when no condition matches, provide a general, actionable suggestion (sunlight, watering, fertilization).
- Easy extensibility: adding or updating conditions, keywords, and guidance is a simple change to the dictionary.

## Success criteria
- The script runs locally and returns a plausible predicted condition for simple test phrases included in the repository.
- Unit tests cover the main prediction cases and pass with pytest.
- The disease dictionary is easy to read and modify.

## Future enhancements (non-mandatory)
- Improve text preprocessing (punctuation removal, stemming, stopword handling).
- Add fuzzy matching, synonyms, or a synonym map to increase recall.
- Replace or augment rule-based matching with a lightweight ML model trained on symptom descriptions.
- Add an optional image upload flow or integration with an image-based diagnosis service.
- Build a simple web UI for broader accessibility.
