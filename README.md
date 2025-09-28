
# Q→A Retrieval System – Psychology-6k

*by [deliriodelluna](https://github.com/deliriodelluna)*

## 🌐 Introduzione

Questo progetto nasce a scopo didattico come esercizio di **Information Retrieval** applicato alla linguistica computazionale per Unict(LM-43)
L’obiettivo è realizzare un sistema capace di associare una **domanda** alla sua **risposta corretta** partendo dal dataset *Psychology-6k*.

---

## 🔄 Workflow del progetto

```text
      ┌───────────────────────┐
      │   1. Analisi Dataset  │
      └──────────┬────────────┘
                 │
      ┌──────────▼────────────┐
      │ 2. Pulizia & Normal.  │
      │  - Light              │
      │  - Lemma              │
      └──────────┬────────────┘
                 │
      ┌──────────▼────────────┐
      │ 3. Candidate Answers  │
      └──────────┬────────────┘
                 │
      ┌──────────▼────────────┐
      │ 4. Embeddings (GTE)   │
      └──────────┬────────────┘
                 │
      ┌──────────▼────────────┐
      │ 5. Retrieval + MRR    │
      └──────────┬────────────┘
                 │
      ┌──────────▼────────────┐
      │ 6. GUI con Gradio     │
      └───────────────────────┘
```

---

## 📂 Struttura del progetto

### 1. Analisi del dataset

* Caricamento di *Psychology-6k*.
* Verifica di valori mancanti.
* Ogni riga → **input** (domanda) + **output** (risposta gold).

### 2. Pulizia e normalizzazione

* Funzioni di preprocessing:

  * `clean_text_light`
  * `lemmatize_spacy`
* Gestione di maiuscole, caratteri speciali, stopword, POS.

### 3. Candidate Answers

* Generazione di 1 gold + k risposte negative.
* Creazione di un set bilanciato per ogni domanda.

### 4. Embeddings con SentenceTransformers

* Modello: `thenlper/gte-small`.
* Embeddings normalizzati (coseno).
* Salvataggio su `.pkl` per riuso.

### 5. Retrieval e valutazione

* Recupero tramite dot product.
* Metrica: **Mean Reciprocal Rank (MRR)**.
* Risultati:

  * Light → MRR = 0.975
  * Lemma → MRR = 0.958
* Analisi critica: la modalità *light* mantiene più informazione semantica.

### 6. Interfaccia GUI

* Implementata con **Gradio**.
* Demo interattiva: scelta modalità, inserimento query, top-k risposte con score.

---

## 📊 Riflessioni finali

* La pipeline mostra come il pre-processing influenzi la performance.
* Il dataset contiene domande duplicate/simili → questo può gonfiare i punteggi della MRR.
* Con altre metriche come **MAP (Mean Average Precision)** l’impatto dei duplicati sarebbe stato gestito diversamente.

---

## 🚀 Come eseguire

```bash
git clone https://github.com/deliriodelluna/qna-retrieval.git
cd qna-retrieval
pip install -r requirements.txt
```

Eseguire il notebook e lanciare la GUI con:

```python
demo.launch(share=True)
```

---

## 🛠️ Tecnologie usate

* Python 3.10+
* pandas, numpy
* spaCy
* SentenceTransformers
* Gradio

---

## 📖 Autore

Realizzato da **deliriodelluna**  come progetto didattico e portfolio di linguistica computazionale.


