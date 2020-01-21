# Sense Embeddings for Syntactic and Semantic Analogy for Portuguese
Implementation of Sense Embeddings for Syntactic and Semantic Analogy for Portuguese

---

## About the paper

This repository contains the results obtained in a paper to be presented in <a href="http://comissoes.sbc.org.br/ce-pln/stil2019/">STIL 2019</a>.

```
Rodrigues, J. S. and Caseli, H. M. (2019). Generating Sense Embeddings for Syntactic and Semantic Analogy for Portuguese.
STIL - Symposium in Information and Human Language Technology. Salvador, Bahia.
```

<a href="https://drive.google.com/open?id=1_VL-UTNxg-dBPFUVgMqvifCQb_JDbTUk">Trained embeddings models</a>

### Abstract

Word embeddings are numerical vectors which can represent words or concepts in a low-dimensional continuous space. These vectors are able to capture useful syntactic and semantic information. The traditional approaches like Word2Vec, GloVe, Wang2Vec and FastText have a strict drawback: they produce a single vector representation per word ignoring the fact that ambiguous words can assume different meanings. In this paper we present the first experiments carried out for generating sense-specific word embeddings for Portuguese. Our experiments show that sense vectors outperform traditional word vectors in syntactic and semantic analogy tasks, proving that the language resource generated here can improve the performance of NLP tasks in Portuguese.

---

### Contents

* [Installation](#installation)
* [Usage](#usage)
  * [Preprocessing text file](#preprocessing-text-file)
  * [Syntactic and Semantic analogies evaluation](#syntactic-and-semantic-analogies-evaluation)

---

## Installation
```
virtualenv venv -p python3
source venv/bin/activate
pip install -r requirements.txt
python -m spacy download pt
```

## Usage

### Trained embeddings models

Download the pre-trained sense vectors and add them to the models folder.

### Preprocessing text file (in order to train embedding models)

Script used for cleaning corpus

All emails are mapped to a EMAIL token.
All numbers are mapped to 0 token.
All urls are mapped to URL token.
Different quotes are standardized.
Different hiphen are standardized.
HTML strings are removed.
All text between brackets are removed.
All sentences shorter than 5 tokens were removed.
```
python preprocessing.py <input_file.txt> <output_file.txt>
```

Annotate the corpus with PoS tags with the nlpnet tool
```
python postagging.py <input_folder.txt> <output_folder.txt>
```

### Syntactic and Semantic analogies evaluation

This method is similar to that one developed by [nlx-group](https://github.com/nlx-group/lx-dsemvectors)
```
python analogies.py -m <embedding_model.txt> -t <testset.txt> -r
```
#### Brazilian Portuguese testsets

Only syntactic analogies
```
python analogies.py -m <embedding_model.txt> -t datasets/analogies/testset/LX-4WAnalogiesBr_syntactic.txt -r
```
Only semantic analogies
```
python analogies.py -m <embedding_model.txt> -t datasets/analogies/testset/LX-4WAnalogiesBr_semantic.txt -r
```
All analogies
```
python analogies.py -m <embedding_model.txt> -t datasets/analogies/testset/LX-4WAnalogiesBr.txt -r
```
#### European Portuguese testsets

Only syntactic analogies
```
python analogies.py -m <embedding_model.txt> -t datasets/analogies/testset/LX-4WAnalogies_syntactic.txt -r
```
Only semantic analogies
```
python analogies.py -m <embedding_model.txt> -t datasets/analogies/testset/LX-4WAnalogies_semantic.txt -r
```
All analogies
```
python analogies.py -m <embedding_model.txt> -t datasets/analogies/testset/LX-4WAnalogies.txt -r
```

