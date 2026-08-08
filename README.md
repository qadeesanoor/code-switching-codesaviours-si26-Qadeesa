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
