# DistilBERT Reproduction

This repository contains a reproduction of the [DistilBERT](https://arxiv.org/abs/1910.01108) paper, implementing the knowledge distillation process from BERT to a compact student transformer model. The objective is to validate the core findings: comparable performance with reduced size and inference cost.

## Features

- Distillation from a pre-trained BERT teacher to a 6-layer student.
- Loss components: Cross-Entropy, Masked Language Modeling, Cosine Similarity.
- Cosine similarity tracking between student and teacher intermediate representations.
- Evaluation on MLM loss, perplexity, accuracy, and inter-layer alignment.
- Inference latency benchmarking and throughput comparison.

## Results Summary

| Metric                    | Teacher       | Student       |
|---------------------------|---------------|---------------|
| MLM Accuracy              | 57.87%        | 13.76%        |
| Perplexity                | 11.53         | 604.23        |
| Cosine Sim (L5 vs L10)    | —             | 0.4079        |
| Latency (avg/batch, sec)  | 0.035145      | 0.022781      |
| Throughput (samples/sec)  | 1422.67       | 2194.84       |

## Training Details

- Dataset: WikiText or similar large-scale corpus
- Optimizer: AdamW
- Scheduler: Linear decay
- Epochs: 7
- Batch size: Configurable
- Framework: PyTorch + HuggingFace Transformers

## Citation

If you use this repository or its contents in your work, consider citing the original DistilBERT paper:
```text
@article{Sanh2019DistilBERTAD,
  title={DistilBERT, a distilled version of BERT: smaller, faster, cheaper and lighter},
  author={Victor Sanh and Lysandre Debut and Julien Chaumond and Thomas Wolf},
  journal={ArXiv},
  year={2019},
  volume={abs/1910.01108}
}

```