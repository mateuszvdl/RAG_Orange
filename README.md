# Reddit Data Analyzer & RAG Chatbot 🤖📊

Projekt łączący techniki NLP (Natural Language Processing) oraz LLM (Large Language Models) do analizy nastrojów i opinii użytkowników platformy Reddit. Składa się z dwóch głównych modułów: narzędzia do scrapowania danych oraz inteligentnego chatbota opartego na architekturze RAG (Retrieval-Augmented Generation).

## 🚀 Funkcjonalności

1. **Reddit Scraper (`01_reddit_scraper.ipynb`)**
   * Pobieranie komentarzy z wybranego wątku za pomocą API Reddit (PRAW).
   * Czyszczenie tekstu i wstępne przetwarzanie (NLP).
   * Automatyczna klasyfikacja perswazji wypowiedzi za pomocą reguł leksykalnych do trzech kategorii: `science`, `social_norm` oraz `fear`.
   * Eksport przetworzonych danych analitycznych do formatu `.csv`.

2. **RAG Pipeline (`02_rag_pipeline.ipynb`)**
   * Wczytywanie i podział (chunking) pobranych danych.
   * Generowanie wektorów (embeddings) przy użyciu modeli **Hugging Face** (`sentence-transformers`).
   * Przechowywanie danych w lokalnej bazie wektorowej **FAISS** w celu szybkiego wyszukiwania semantycznego.
   * Integracja z LLM (przez **Groq API** z wykorzystaniem **LangChain**) pozwalająca na zadawanie pytań w języku naturalnym o wyodrębniony kontekst z Reddita.

## 🛠️ Technologie
* **Język:** Python
* **LLM & NLP:** LangChain, Hugging Face, Groq API (Llama), NLTK / Regex
* **Baza Wektorowa:** FAISS
* **Analiza Danych:** Pandas, PRAW (Reddit API)
* **Środowisko:** Jupyter Notebook, środowisko wirtualne (venv), python-dotenv

## 📁 Struktura projektu

```text
├── data/                   # Przechowuje pobrane pliki CSV z Reddita
├── notebooks/              # Pliki z kodem Jupyter Notebook
│   ├── 01_reddit_scraper.ipynb
│   └── 02_rag_pipeline.ipynb
├── .env                    # Zmienne środowiskowe i klucze API (nieśledzone przez Git)
├── .gitignore              # Reguły ignorowania plików dla Gita
├── README.md               # Dokumentacja
└── requirements.txt        # Zależności projektu
```

## ⚙️ Uruchomienie lokalne

1. **Sklonuj repozytorium:**
```bash
git clone [https://github.com/mateuszvdl/RAG_Orange.git](https://github.com/mateuszvdl/RAG_Orange.git)
cd RAG_Orange
```

2. **Utwórz i aktywuj wirtualne środowisko:**
```bash
# Mac/Linux:
python3 -m venv venv
source venv/bin/activate

# Windows:
python -m venv venv
venv\Scripts\activate
```

3. **Zainstaluj wymagane pakiety:**
```bash
pip install -r requirements.txt
```

4. **Skonfiguruj zmienne środowiskowe:**
Utwórz plik `.env` w głównym katalogu projektu i dodaj swoje klucze API:
```env
REDDIT_CLIENT_ID=twoj_klucz_id
REDDIT_CLIENT_SECRET=twoj_klucz_secret
GROQ_API_KEY=twoj_klucz_groq
```

5. **Uruchomienie:**
Otwórz projekt w VS Code, wybierz jako kernel środowisko `venv` i uruchamiaj notatniki w kolejności (najpierw pobranie danych, potem chatbot).