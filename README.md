# 🧬 Cancer Clinical Data Warehouse with TCGA, SQL & Python

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python&logoColor=white)](https://www.python.org/)
[![SQLite](https://img.shields.io/badge/SQLite-Database-003B57?logo=sqlite&logoColor=white)](https://www.sqlite.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)](https://jupyter.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Data: TCGA via GDC](https://img.shields.io/badge/Data-TCGA%20GDC%20API-red)](https://portal.gdc.cancer.gov/)

> A fully self-contained, beginner-friendly SQL project that downloads real cancer patient data from the **NIH Genomic Data Commons (GDC)**, builds a relational SQLite warehouse, and runs 9 meaningful SQL analyses. Complete with survival plots and a Kaplan-Meier curve.

---

## 📖 What This Project Is

This project builds a **miniature clinical data warehouse** using publicly available data from [The Cancer Genome Atlas (TCGA)](https://www.cancer.gov/tcga) program.

The project covers 5 TCGA cancer types:

| Project ID | Cancer Type |
|---|---|
| TCGA-BRCA | Breast Invasive Carcinoma |
| TCGA-LUAD | Lung Adenocarcinoma |
| TCGA-COAD | Colon Adenocarcinoma |
| TCGA-GBM | Glioblastoma Multiforme |
| TCGA-PRAD | Prostate Adenocarcinoma |

---

## 🛠️ SQL Skills Demonstrated

| SQL Concept | Where It Is Used |
|---|---|
| `CREATE TABLE` with primary & foreign keys | Database schema design |
| `INSERT INTO` / `to_sql()` | Loading cleaned DataFrames into SQLite |
| `SELECT`, `FROM`, `WHERE` | All 9 queries |
| `JOIN` / `LEFT JOIN` | Queries 1, 2, 6, 7, 8, 9 |
| `GROUP BY` + `ORDER BY` | All aggregation queries |
| `COUNT`, `AVG`, `MIN`, `MAX`, `SUM` | Demographic, survival, and mutation queries |
| `CASE WHEN ... THEN ... ELSE ... END` | Stage normalisation, smoking status labels |
| `COALESCE(a, b)` | Survival duration — prefer death date, fall back to last follow-up |
| Common Table Expressions (`WITH ... AS`) | Multi-step survival and mutation burden queries |
| `ROW_NUMBER() OVER (PARTITION BY ...)` | Top-5 diagnosis patterns per cancer type |
| Subqueries | Above-average age at diagnosis filter |

---

## 📊 Analyses & Visualisations

1. **Patient count per cancer type** — bar chart
2. **Average age at diagnosis by cancer type and gender** — grouped bar chart
3. **Tumour stage distribution** — stacked bar chart
4. **Observed death percentage per cancer type** — bar chart
5. **Kaplan-Meier survival curves** — one curve per cancer type
6. **Mutation burden proxy distribution** — box plot (log scale)
7. **Mutation burden vs. observed survival** — multi-table JOIN analysis
8. **Treatment patterns** — treatment type counts per cancer type
9. **Tobacco smoking exposure trends** — grouped bar chart by project

---

## 🗄️ Database Schema

The SQLite warehouse (`tcga_warehouse.db`) contains five relational tables connected by `case_id`:
