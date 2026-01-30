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
git clone [https://github.com/](https://github.com/)[SEU-USUARIO]/[NOME-DO-REPO].git
cd [NOME-DO-REPO]

# Criação do ambiente virtual (opcional mas recomendado)
python -m venv venv
source venv/bin/activate  # No Windows: venv\Scripts\activate

# Instalação das bibliotecas
pip install -r requirements.txt

jupyter notebook notebooks/1_EDA_Analise_Exploratoria.ipynb
