# Word Embedding Dimensionality Selection

This repo implements the dimensionality selection procedure for word embeddings. The procedure is proposed
in the following papers, based on the notion of Pairwise Inner Produce (PIP) loss. No longer pick 300 as your word embedding dimensionality!
```
@inproceedings{yin2018dimensionality,
 title={On the Dimensionality of Word Embedding},
 author={Yin, Zi and Shen, Yuanyuan},
 booktitle={Advances in Neural Information Processing Systems},
 year={2018}
}
```
and
```
@article{yin2018pairwise,  
  title={Understand Functionality and Dimensionality of Vector Embeddings: the Distributional Hypothesis, the Pairwise Inner Product Loss and Its Bias-Variance Trade-off},  
  author={Yin, Zi},  
  journal={arXiv preprint arXiv:1803.00502},  
  year={2018}  
}
```

Currently, we implement the dimensionality selection procedure for the following algorithms:
- Word2Vec (skip-gram)
- GloVe
- Latent Semantic Analysis (LSA)

## How to use
The tool provides an optimal dimensionality for an algorithm on a corpus. For example, you can use it to
obtain the dimensionality for your Word2Vec embedding on the Text8 corpus.
You need to have the following:
- A corpus (--file [path to corpus])
- A config file (yaml) for algorithm specific parameters (--config file [path to config file])
- Name of algorithm (--algorithm [algorithm_name])

Run from root directory as package, e.g.:
`python -m main --file data/text8.zip --config_file word2vec_sample_config.yml --algorithm word2vec`

testing:
`python -m unittest test.test_tokenizer`

## Implement your own
You can extend the implementation if you have another embedding algorithm that is based on matrix factorization.
The only thing to do is to implement your matrix estimator as a subclass of SignalMatrix
