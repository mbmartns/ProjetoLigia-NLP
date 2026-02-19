# 🧠 Fake News Detection – Desafio NLP

Este repositório contém a solução desenvolvida para o desafio de classificação de fake news (Trilha NLP). O objetivo é construir um modelo capaz de distinguir notícias falsas de verdadeiras, com foco em **generalização** e **interpretabilidade**.

## 📌 Sobre o desafio

- **Problema:** Classificação binária de textos (fake × real).
- **Métrica principal:** F1-Score (macro average) – adequada para dados desbalanceados.
- **Dados:** Dataset com ~22 mil notícias, contendo título, texto, assunto, data e rótulo.
- **Exigência extra:** Relatório técnico com análise de erros, métricas de negócio e explicabilidade (XAI).

## 🧩 Abordagem

### 1. Análise Exploratória (EDA)
- Identificação de **duplicatas** (649 textos, 741 títulos) e possíveis inconsistências.
- Descoberta de **vieses fortes**:  

### 2. Modelagem
- Modelo base: **RoBERTa-base** (pré-treinado em inglês), escolhido por capturar relações semânticas profundas.
- Fine-tuning com `transformers.Trainer`:

### 3. Explicabilidade (XAI)
- Utilização do **LIME** para entender as decisões do modelo em exemplos específicos.

## 📊 Resultados

- **F1 Macro na validação:** 0,9994 (apenas 1 erro em 2291 amostras).
- **Matriz de confusão:**

|                | Previsto Fake | Previsto Real |
|----------------|---------------|---------------|
| **Real (0)**   | 1744          | 0             |
| **Fake (1)**   | 1             | 547           |

- **Relatório de classificação:**

| Classe | Precision | Recall | F1-score |
|--------|-----------|--------|----------|
| 0      | 1.00      | 1.00   | 1.00     |
| 1      | 1.00      | 1.00   | 1.00     |

## 🗂️ Estrutura do repositório

├── notebooks/
│ ├── 01_eda.ipynb # Análise exploratória completa
│ ├── 02_treinamento.ipynb # Treinamento do modelo RoBERTa
│ └── 03_explicabilidade.ipynb # Interpretabilidade com LIME
├── data/ #amostra dos dados ou instruções para download
├── models/ # modelo salvo
├── submission.csv # arquivo gerado para o Kaggle
└── README.md


