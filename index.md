---
layout: default
---

In this project, we present T<span class="span-small">A</span>PE<span class="span-small">X</span> (for **Ta**ble **P**re-training via **Ex**ecution), a conceptually simple and empirically powerful pre-training approach to empower existing models with table reasoning skills.
T<span class="span-small">A</span>PE<span class="span-small">X</span> realizes table pre-training by **learning a neural SQL executor over a synthetic corpus**, which is obtained by automatically synthesizing executable SQL queries.

<figure style="text-align:center">
  <img src="/assets/tapex_overview.jpg" width="300">
  <figcaption>Fig 1. The schematic illustration of T<span class="span-small">A</span>PE<span class="span-small">X</span>. Tables not shown for brevity.</figcaption>
</figure>

The central point of T<span class="span-small">A</span>PE<span class="span-small">X</span> is to train a model to **mimic the SQL query execution process over a table**.
We believe that if a model can be trained to faithfully *execute* SQL queries, then it must have a deep understanding of table structures and possess an inductive bias towards table structures.

<div style="text-align:center">
<img src="/assets/model_pretrain.gif" width="600"></div>

Meanwhile, since the diversity of SQL queries can be guaranteed systemically, and thus a *diverse* and *high-quality* pre-training corpus can be automatically synthesized for T<span class="span-small">A</span>PE<span class="span-small">X</span>.

# 🏆 T<span class="span-small">A</span>PE<span class="span-small">X</span> = SOTA on Four Benchmarks

We evaluate T<span class="span-small">A</span>PE<span class="span-small">X</span> on two tasks 💬 Table Question Answering and 🔎 Table Fact Verficiation.

<figure style="text-align:center">
  <img src="/assets/tableqa_task.png" width="500">
  <figcaption>Fig 2. An example of Table Question Answering. Credits: <a href="https://nlp.stanford.edu/blog/wikitablequestions-a-complex-real-world-question-understanding-dataset">Link</a>.</figcaption>
</figure>

<figure style="text-align:center">
  <img src="/assets/tableft_task.png" width="500">
  <figcaption>Fig 3. An example of Table Fact Verification. Credits: <a href="https://tabfact.github.io/">Link</a>.</figcaption>
</figure>

Experimental results demonstrate that T<span class="span-small">A</span>PE<span class="span-small">X</span> outperforms previous table pre-training approaches by a large margin, and our model achieves new state-of-the-art results on four well-known datasets, including:
- improving the WikiSQL denotation accuracy to <span style="color: #159957;font-weight:700;">89.6</span> (📈+4.9).
- improving the WikiTableQuestions denotation accuracy to <span style="color: #159957;font-weight:700;">57.5</span> (📈+4.8).
- improving the SQA denotation accuracy to <span style="color: #159957;font-weight:700;">74.5</span> (📈+3.5).
- improving the TabFact accuracy to <span style="color: #159957;font-weight:700;">84.6</span> (📈+3.6).

<figure style="text-align:center">
  <img src="/assets/dataset.jpg" width="400">
  <figcaption>Tab 1. Dataset statistics</figcaption>
</figure>

More importantly, our backbone is a simple Transformer-based Encoder-Decoder model without any task-specific architecture, which can be extended to **any kind of** downstream task.

# ⚔️ T<span class="span-small">A</span>PE<span class="span-small">X</span> v.s. Previous Table Pre-training

Our T<span class="span-small">A</span>PE<span class="span-small">X</span> can achieve significantly better results compared to previous table pre-training techniques, with a much smaller synthesized pre-training corpus.

<figure style="text-align:center">
  <img src="/assets/efficiency_demo.jpg" width="300">
  <figcaption>Fig 4. The amount of our pre-training corpus v.s. WikiTQ dev set denotation accuracy.</figcaption>
</figure>

| Pre-training Model |  Pre-training Task    |  Pre-training Scale |  WikiTQ Acc |
|:-------------|:------------------|:------| :----: |
| [T<span class="span-small">A</span>P<span class="span-small">A</span>S (Herzig et al., 2020)](https://aclanthology.org/2020.acl-main.398/)     | Masked Language Model | 21.3 Million  | 48.8 |
| [TaBERT (Yin et al., 2020)](https://aclanthology.org/2020.acl-main.745/)    | Masked Column Prediction +<br>Cell Value Recovery   | 26.3 Million  | 53.0 |
| [GraPPa (Yu et al., 2020)](https://openreview.net/forum?id=kyaIeYj4zZ)     | Masked Language Model +<br>SQL Semantic Prediction  | 0.9 Million | 51.9 |
| T<span class="span-small">A</span>PE<span class="span-small">X</span> (Ours, 1 Million)        | SQL Execution | 1.0 Million  | **56.1** |
| T<span class="span-small">A</span>PE<span class="span-small">X</span> (Ours, 5 Million)        | SQL Execution | 5.0 Million  | **57.0** |

> WikiTQ refers to the challenging [WikiTableQuestions](https://github.com/ppasupat/WikiTableQuestions) dataset (Pasupat and Liang, 2015).

# 😉 Other Interesting Work

- [https://github.com/microsoft/IRNet](https://github.com/microsoft/IRNet)
- [https://github.com/microsoft/ContextualSP](https://github.com/microsoft/ContextualSP)
- [https://github.com/JasperGuo/Unimer](https://github.com/JasperGuo/Unimer)

# 📍 Citation

If you find our work useful to you, please kindly cite it by:

```bibtex
@article{liu2021tapex,
  title={TAPEX: Learning a Neural SQL Executor for Table Pre-training},
  author={Liu, Qian and Chen, Bei and Guo, Jiaqi and Lin, Zeqi and Lou, Jian-Guang},
  journal={arxiv},
  year={2021}
}
```
