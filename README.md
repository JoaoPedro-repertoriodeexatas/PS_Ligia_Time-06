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

src/: Código fonte modularizado (pré-processamento e funções de inferência).


models/: Pesos dos modelos treinados (.json/.pkl) prontos para uso.


