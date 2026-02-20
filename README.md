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

- **F1 Macro na validação:** 1,0000 (nenhum erro em 2291 amostras).
- **Matriz de confusão:**

|                | Previsto Fake | Previsto Real |
|----------------|---------------|---------------|
| **Real (0)**   | 1744          | 0             |
| **Fake (1)**   | 0             | 547           |

- **Relatório de classificação:**

| Classe | Precision | Recall | F1-score |
|--------|-----------|--------|----------|
| 0      | 1.00      | 1.00   | 1.00     |
| 1      | 1.00      | 1.00   | 1.00     |

## 🗂️ Estrutura do repositório
<img width="510" height="191" alt="image" src="https://github.com/user-attachments/assets/d7c530e2-6a76-4863-8119-fe27a7e5786f" />

## 🚀 Como reproduzir

Para reproduzir os resultados e executar os notebooks, siga os passos abaixo:

## 1. Clonar o repositório

```bash
git clone [https://github.com/seu-usuario/fake-news-detection.git](https://github.com/mbmartns/ProjetoLigia-NLP.git)
```

## 2. Instalar as dependências

É recomendado usar um ambiente virtual (conda ou venv).
### Usando pip
```bash
pip install torch transformers datasets accelerate peft scikit-learn matplotlib seaborn lime pandas numpy
```
### Usando conda
```bash
conda create -n fake-news python=3.9
conda activate fake-news
conda install pytorch transformers datasets accelerate scikit-learn matplotlib seaborn pandas numpy -c pytorch -c huggingface -c conda-forge
pip install peft lime
```

## 3. Executar os notebooks

Abra os notebooks na seguinte ordem (recomendado usar Jupyter ou Google Colab):

1. `notebooks/EDA-nlp.ipynb` — análise exploratória
2. `notebooks/Training-nlp.ipynb` — fine-tuning do modelo

## 4. Resultados

* O modelo treinado será salvo em:

```
./modelo_final_lora
```

* O arquivo `submission.csv` será gerado para submissão no Kaggle

---

