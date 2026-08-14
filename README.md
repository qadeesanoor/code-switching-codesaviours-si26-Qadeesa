#  **Code Switching**
## Code Switching NLP | Code Saviours SI-26 | Qadeesanoor

## About This Project

Roman Urdu mixed with English — *"Aaj mera mood nahi hai for anything"* — is
how millions of Pakistanis actually write online, on WhatsApp, Twitter, and
in comments. Almost no existing NLP resource or model is built to handle
this kind of code-switching. This project builds a labeled dataset that
captures it: real Roman Urdu–English mixed sentences, broken down
word-by-word, with each word tagged as Urdu, English, or a nativized
mixed/loanword.
The goal is to make a starting resource for anyone trying to build models
that work on how Pakistanis actually text and talk online — sentiment
analysis, chatbots, OCR post-processing, or word-level language
identification — instead of models trained only on clean, single-language
text.
## Label Scheme
Each word in every sentence is tagged as one of:
- **URD** — Roman Urdu word
- **ENG** — English word
- **MIX** — English-origin word fully nativized into everyday Roman Urdu
  speech (e.g. `phone`, `office`, `meeting`)

## Dataset Stats
- 151 sentences
- 1,489 word-level entries
- Label distribution: URD 901, ENG 488, MIX 100

## Approach
- Base model: `xlm-roberta-base`, fine-tuned for token classification
- Task: 3-class per-token classification (URD / ENG / MIX)
- Split: 80/20 train-test on sentence level (train_test_split, random_state=42)
- Framework: HuggingFace Transformers + Trainer API

## Evaluation
Per-label F1 (URD, ENG, MIX) and overall weighted F1 were computed using
standard per-token classification metrics (scikit-learn), not span-based
NER metrics — the task labels every token independently rather than marking
entity spans, so BIO-style sequence-labeling metrics (e.g. seqeval) do not
apply here.

- Overall F1: 98%
- F1 URD: 99%
- F1 ENG: 98%
- F1 MIX: 89% — note: MIX has only 100 total instances in the dataset,
  so this score is based on a small test-split sample (~15–20 words) and
  should be read as provisional, not a stable estimate.

## Known Limitations
- Dataset size (151 sentences) is small for fine-tuning a 270M-parameter
  transformer; results should be interpreted with that in mind rather than
  reported as a definitive performance benchmark.
- Class imbalance (URD 901, ENG 488, MIX 100) means MIX-label performance
  is the least reliable of the three.
