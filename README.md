# NLP-from-scratch

**From Python to RAG in 13 hands-on notebooks.** A learning path I built to understand NLP and LLMs by writing the core pieces myself first (BPE, logistic regression, attention, LoRA, DPO) and then comparing with the real libraries and models.

Every code line has an **Arabic comment** above it. The examples use football data where possible.

## The notebooks

| # | Notebook | What it covers |
| --- | --- | --- |
| 1 | [nb01-pandas-numpy-football](nb01-pandas-numpy-football.ipynb) | Pandas and NumPy on football data |
| 2 | [nb02-python-for-ai-chatbot](nb02-python-for-ai-chatbot.ipynb) | The Python you need for AI |
| 2b | [nb02b-python-data-structures](nb02b-python-data-structures.ipynb) | Python data structures for AI |
| 3 | [nb03-sklearn-text-intent-bot](nb03-sklearn-text-intent-bot.ipynb) | scikit-learn for text: an intent classifier |
| 4 | [nb04-ml-concepts-football](nb04-ml-concepts-football.ipynb) | Machine learning concepts on football data |
| 5 | [nb05-deep-learning-keras](nb05-deep-learning-keras.ipynb) | Deep learning with TensorFlow / Keras |
| 6 | [nb06-tokenization](nb06-tokenization.ipynb) | Tokenization: BPE from scratch, WordPiece, GPT-2 BPE, Arabic vs English token cost |
| 7 | [nb07-text-classification](nb07-text-classification.ipynb) | Text classification: logistic regression in NumPy, checked against scikit-learn |
| 8 | [nb08-embeddings](nb08-embeddings.ipynb) | Embeddings: co-occurrence vectors, Word2Vec (gensim), sentence embeddings |
| 9 | [nb09-transformers-gpt2](nb09-transformers-gpt2.ipynb) | Self-attention from scratch, then real GPT-2: sampling, top-k/top-p, perplexity |
| 10 | [nb10-post-training](nb10-post-training.ipynb) | Instruction tuning, LoRA in Keras, DPO on GPT-2 log-probabilities |
| 11 | [nb11-bert-masked-lm](nb11-bert-masked-lm.ipynb) | BERT: fill-mask, contextual vectors, feature extraction, NER |
| 12 | [nb12-retrieval-rag](nb12-retrieval-rag.ipynb) | Retrieval and RAG: TF-IDF vs dense retrieval, prompt assembly, generation |

## Run them

```bash
pip install pandas numpy matplotlib scikit-learn tensorflow transformers torch gensim
jupyter notebook
```

The football notebooks read a local `fpl.json`. Download it once next to the notebooks from the public Fantasy Premier League API:

```bash
curl -o fpl.json https://fantasy.premierleague.com/api/bootstrap-static/
```

The Hugging Face models (bert-base-uncased, GPT-2, MiniLM, dslim/bert-base-NER) download automatically on first run.

## Honest notes

- **Small, self-written data.** Several notebooks use small datasets I wrote myself (for example 60 intent sentences), so scores such as 0.87 accuracy on 15 test sentences are only illustrative.
- **Not football data everywhere.** The text classification and Word2Vec notebooks use real labeled newsgroup sports articles (baseball vs hockey), not football.
- **Frameworks.** My own deep learning code (notebook 5, LoRA in notebook 10) is Keras / TensorFlow. Hugging Face models run on a PyTorch backend, because current `transformers` no longer ships TensorFlow models.
- **Lighter than production.** Full BERT fine-tuning and a full DPO run were replaced by lighter versions (feature extraction, a 6-step DPO demo on one pair) because of limited RAM. They show the mechanism, not a real training run.
- **Weak spots are left in.** For example GPT-2 small is a weak generator in the RAG notebook, and NER mislabels some clubs. I kept the real outputs.
- Notebooks are saved without outputs. Run them to reproduce the results.

## Author

Mostafa Elesely, [GitHub](https://github.com/mostafaelesely) | [LinkedIn](https://www.linkedin.com/in/mostafa-elesely-4b86ab318/)
