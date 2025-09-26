# Cookie Cats A/B Test – Impact of Gate Position on Early Retention

[![Python](https://img.shields.io/badge/python-3.9%2B-blue)](https://www.python.org/) [![Jupyter](https://img.shields.io/badge/jupyter-notebook-orange)](https://jupyter.org/) [![Licence: MIT](https://img.shields.io/badge/license-MIT-green)](LICENSE)

## 1. Executive summary

A controlled experiment on **90 189** new players tested whether moving the first progression gate from level 30 to level 40 would boost early‑stage engagement. The change reduced **Day‑7 retention by 0.8 pp** (p < 0.001). With current acquisition volumes that equates to roughly **7 000 fewer retained users per month** and a measurable decline in lifetime value. I therefore recommend keeping the gate at **level 30**.

---

## 2. Business context

In Free‑to‑Play games, Day‑1 and Day‑7 retention are key drivers of monetisation. Product managers hypothesised that postponing the first gate would let players enjoy more content before encountering friction, thereby increasing retention.

> **Question** Will shifting the gate from level 30 → 40 improve Day‑1 and Day‑7 retention?

---

## 3. Data

| File                   | Rows   | Purpose                                   |
| ---------------------- | ------ | ----------------------------------------- |
| `data/cookie_cats.csv` | 90 189 | Anonymised event log used in the analysis |

Key columns: `userid`, `version` (control / treatment), `sum_gamerounds`, `retention_1`, `retention_7`.

---

## 4. Methodology

1. **Data validation** – confirm randomisation, remove bots/nulls.
2. **Exploratory analysis** – distributions of game rounds and retention funnels.
3. **Hypothesis testing** – bootstrap 10 000 samples of the mean retention difference; confirm with two‑sample t‑tests.
4. **Effect size** – absolute & relative lifts with 95 % CIs.
5. **Business translation** – convert retention change into user and LTV impact using the internal model.

---

## 5. Results

| Metric          | Control | Treatment | Δ (pp) | p‑value |
| --------------- | ------- | --------- | ------ | ------- |
| Day‑1 retention | 44.8 %  | 44.2 %    | –0.6   | 0.03    |
| Day‑7 retention | 19.0 %  | 18.2 %    | –0.8   | <0.001  |

The treatment group under‑performs the control on both KPIs; the Day‑7 difference is both statistically and practically significant.

---

## 6. Recommendation

Retain the gate at **level 30**. The tested change harms retention without showing any long‑term benefit.

---

## 7. Reproducing the analysis

```bash
# Clone repository
$ git clone https://github.com/AMVukojevic/product-analyst-ab-test.git
$ cd product-analyst-ab-test

# Create virtual environment (or use conda)
$ python -m venv venv && source venv/bin/activate    # Windows: venv\Scripts\activate

# Install dependencies
$ pip install -r requirements.txt

# Launch notebook
$ jupyter notebook notebooks/analysis.ipynb
```

---

## 8. Repository structure

```
project-analyst-ab-test/
├── data/
│   └── cookie_cats.csv
├── images/
│   └── retention_chart.png
├── notebooks/
│   └── analysis.ipynb
├── requirements.txt
└── README.md
```

---

## 9. Skills demonstrated

* Experiment design and evaluation (A/B testing, bootstrapping)
* Statistical inference and effect‑size interpretation
* Data wrangling and visualisation in Python (`pandas`, `numpy`, `matplotlib`, `seaborn`)
* Translating analytical results into clear product decisions

---

## 10. Next steps

* Segment results by acquisition channel, geography, and device.
* Measure impact on monetisation KPIs (IAP revenue, ad impressions).
* Test alternative gate positions (e.g., levels 25 or 35) with sequential testing.

---

## 11. Contact

Prepared by **Ante Vukojević** · [LinkedIn](https://www.linkedin.com/in/ante-mislav-vukojevi%C4%87-0a4ba2386/) · [a.m.vukojevic@gmail.com](mailto:a.m.vukojevic@gmail.com)

*This project illustrates my ability to connect rigorous statistical analysis with actionable business recommendations—skills directly applicable to Business Analyst, Data Analyst, and Product Analytics roles.*
