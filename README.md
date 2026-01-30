# 🏥 Sistema Inteligente de Triagem - Protocolo Manchester

> **Desafio Liga de IA (LIGIA) - Processo Seletivo 2026**
> **Eixo Temático:** A - Saúde e Bem-Estar 
> **Equipe:** 6

## 📋 Sobre o Projeto

Este projeto consiste em uma **Prova de Conceito (PoC)**  de um sistema de Inteligência Artificial para auxílio à decisão clínica na triagem de pacientes. Utilizando dados clínicos simulados, o modelo classifica os pacientes em **5 níveis de prioridade** baseados no **Protocolo de Manchester** (Azul, Verde, Amarelo, Laranja, Vermelho).

O objetivo é reduzir erros de triagem e otimizar o fluxo de atendimento em emergências, garantindo que casos graves recebam prioridade imediata.

---

## 🛠️ Instalação e Configuração

Siga os passos abaixo para reproduzir o ambiente de desenvolvimento e executar o projeto (Requisito: **Reprodutibilidade** ).

### 1. Pré-requisitos
* Python 3.8 ou superior
* Git

### 2. Clonar o Repositório
```bash
git clone https://github.com/JoaoPedro-repertoriodeexatas/PS_Ligia_Time-06.git
cd PS_Ligia_Time-06

# Criação do ambiente virtual (opcional mas recomendado)
python -m venv venv
source venv/bin/activate  # No Windows: venv\Scripts\activate

# Instalação das bibliotecas
pip install -r requirements.txt

jupyter notebook notebooks/1_EDA_Analise_Exploratoria.ipynb
```
🧠 Metodologia e Modelagem
Adotamos uma abordagem comparativa para garantir a robustez da solução:

Baseline (Linha de Base): Utilizamos um algoritmo Random Forest para estabelecer uma métrica base de desempenho.

Modelo Avançado: Implementamos o XGBoost (Gradient Boosting), otimizando hiperparâmetros para superar o baseline.

Justificativa da Métrica
Dado o contexto crítico de saúde, a Acurácia isolada não é suficiente. Priorizamos a análise do Recall (Sensibilidade) e F1-Score, especialmente para as classes críticas (Laranja e Vermelho).


Justificativa: Um Falso Negativo (classificar um paciente grave como leve) apresenta risco de vida, sendo o erro que mais buscamos minimizar. 

Estrutura do Repositório 

data/: Contém os datasets (observando as regras da LGPD, dados anonimizados).

notebooks/: Análises exploratórias e pipelines de treinamento.

## 🔍 Análise Exploratória de Dados (EDA)

A etapa de exploração de dados foi fundamental para garantir a qualidade da modelagem. O dataset original utiliza o sistema **KTAS (Korean Triage and Acuity Scale)**, que classifica a urgência em 5 níveis (1 a 5), possuindo equivalência direta com o **Protocolo de Manchester** utilizado no SUS.

### ⚙️ Processamento e Ferramentas
Utilizamos **Pandas, Matplotlib e Seaborn** para o tratamento e visualização dos dados. O pipeline de engenharia de dados incluiu:
* **Tradução e Padronização:** Adaptação das features para o português para facilitar a interpretabilidade.
* **Limpeza:** Tratamento de valores nulos e inconsistentes.
* **Correlação:** Estudo da relação entre sintomas (sinais vitais, queixa principal) e a classificação final.

```bash
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
import math
import seaborn as sns
import scipy.stats as stat
from sklearn.model_selection import train_test_split
from sklearn.compose import ColumnTransformer
from sklearn.preprocessing import OneHotEncoder
from sklearn.model_selection import train_test_split
from sklearn.metrics import classification_report
from sklearn.metrics import confusion_matrix
from sklearn.preprocessing import LabelEncoder
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import (accuracy_score,f1_score,roc_auc_score,classification_report)
from sklearn.metrics import (confusion_matrix,ConfusionMatrixDisplay,roc_curve,auc)
import xgboost as xgb
from sklearn.model_selection import StratifiedKFold
from sklearn.metrics import classification_report, accuracy_score, f1_score
from sklearn.metrics import confusion_matrix, ConfusionMatrixDisplay
from xgboost import XGBClassifier
from google.colab import files
```

### 💡 Principais Insights: O Fenômeno "Mistriage"
Um dos focos centrais da nossa análise foi a comparação entre duas variáveis críticas:
1.  `KTAS_enfermeiro`: Classificação inicial realizada na triagem.
2.  `KTAS_especialista`: O "padrão-ouro" definido pelo médico após o atendimento.

> **Achado Relevante:** Observamos a existência de divergências classificadas como **"Mistriage"** (Subtriagem ou Sobretriagem). Nossa análise gráfica buscou entender quais sintomas levam os enfermeiros a classificar incorretamente em comparação ao especialista, justificando o uso de IA para apoiar essa decisão e reduzir erros.

src/: Código fonte modularizado (pré-processamento e funções de inferência).


models/: Pesos dos modelos treinados (.json/.pkl) prontos para uso.


