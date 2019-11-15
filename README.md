# HanziGlyphLM
Replicating Dai 2017's language model and try to improve it using tricks in Meng 2019

## Reference

1. Dai, Falcon, and Zheng Cai. "Glyph-aware Embedding of Chinese Characters." Proceedings of the First Workshop on Subword and Character Level Models in NLP. 2017.

```
@inproceedings{dai2017glyph,
  title={Glyph-aware Embedding of Chinese Characters},
  author={Dai, Falcon and Cai, Zheng},
  booktitle={Proceedings of the First Workshop on Subword and Character Level Models in NLP},
  pages={64--69},
  year={2017}
}
```

2. Wu W, Meng Y, Han Q, et al. Glyce: Glyph-vectors for Chinese Character Representations[J]. arXiv preprint arXiv:1901.10125, 2019.

```
@article{meng2019glyce,
  title={Glyce: Glyph-vectors for Chinese Character Representations},
  author={Meng, Yuxian and Wu, Wei and Wang, Fei and Li, Xiaoya and Nie, Ping and Yin, Fan and Li, Muyu and Han, Qinghong and Sun, Xiaofei and Li, Jiwei},
  journal={arXiv preprint arXiv:1901.10125},
  year={2019}
}
```

## Objective

Dai et al. (2017) tried to combine CNN-encoded glyph images of characters and character embeddings as the input of a RNNLM. However, they reported that the CNN is ignored by the trained model, leading to no improvement.

Meng et al. (2019) combined a similar CNN and BERT and proposed some important tricks to train the model, including:

- A tailored CNN setting which improve +1% F1 scores in LCQMC sentence pair classification task.
- A training stratigy which improve +1% F1 scores (compared to vanilla joint learning)
- A auxiliary image-classification training objective which bring +0.8% F1 scores

Meng et al. evaluated their methods in tagging, sentence pair classification and single sentence classification. The results are amazing. However, not including RNNLM.

I wonder if Meng et al.'s tricks can help the RNNLM. Thus, I planned to do the following works:

1. First, replicate Dai et al.'s model.
2. Then, validate the tricks one by one for the model.
