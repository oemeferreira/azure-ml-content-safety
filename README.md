# 🚲 Projeto Prático - Previsão de Aluguéis de Bicicletas com Azure AutoML

Este repositório contém o projeto prático desenvolvido como parte do curso de Fundamentos de Inteligência Artificial com Azure Machine Learning. O objetivo foi criar, treinar e publicar um modelo preditivo utilizando os recursos do Azure ML Studio, e também exportar o modelo treinado para uso em ambientes externos, como Google Colab, Kaggle ou Binder.

---

## 📌 Objetivo

Criar um modelo de Machine Learning com previsão baseada em dados reais de aluguéis de bicicletas, utilizando a ferramenta Azure Machine Learning Studio com AutoML, e publicar um ponto de extremidade ou exportar o modelo para uso externo.

---

## 🔧 Etapas do Projeto

### 1. Criação do Workspace
- Acesse o portal do [Azure Machine Learning Studio](https://ml.azure.com).
- Crie um novo workspace com os parâmetros padrão (nome, região, assinatura).

### 2. Carregamento do Dataset
- Foi utilizado o dataset **Bike Sharing Dataset**, disponível no [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Bike+Sharing+Dataset).
- O dataset foi carregado no Azure ML Studio no formato `.csv`, com as colunas listadas abaixo.

#### 🎯 Coluna alvo (target)
- `rentals`: quantidade de aluguéis

#### 📥 Atributos utilizados como entrada (features)
| Coluna        | Descrição                          |
|---------------|-------------------------------------|
| `day`         | Dia do mês                         |
| `mnth`        | Mês (numérico)                     |
| `year`        | Ano (ex: 2022)                     |
| `season`      | Estação (1=primavera, 4=inverno)   |
| `holiday`     | Feriado (0=não, 1=sim)             |
| `weekday`     | Dia da semana (0=domingo)          |
| `workingday`  | Dia útil                           |
| `weathersit`  | Condição climática                 |
| `temp`        | Temperatura normalizada            |
| `atemp`       | Sensação térmica normalizada       |
| `hum`         | Umidade normalizada                |
| `windspeed`   | Velocidade do vento normalizada    |

---

### 3. Treinamento com AutoML
- Acesse a aba **Automated ML > New automated ML run**
- Dataset: Bike Sharing Dataset
- Nome do experimento: `bike-rentals-automl`
- Coluna de destino: `rentals`
- Tipo de tarefa: Regressão
- Compute cluster: `Standard_E4s_v3` (ou similar, respeitando as cotas)
- Após a execução, o melhor modelo foi selecionado com base na métrica `Normalized Root Mean Squared Error (RMSE)`.

---

### 4. Exportação e uso externo do modelo
- O modelo foi exportado como `.pkl` e está disponível neste repositório.
- Para testar o modelo fora do Azure, utilizamos o ambiente **Binder**, que permite executar notebooks Python na nuvem gratuitamente.

---

## 🚀 Como Executar o Projeto

### ✅ Executar via Binder (100% online e gratuito)

Clique no botão abaixo para abrir o notebook no Binder:

[![Abrir no Binder](https://mybinder.org/badge_logo.svg)](https://notebooks.gesis.org/binder/jupyter/user/oemeferreira-mslearn-azure-ml-ywu74ne6/doc/tree/mslearn-bike-rentals.ipynb)

### 💻 Executar localmente (opcional)

```bash
# Clonar o repositório
git clone https://github.com/oemeferreira/mslearn-azure-ml.git
cd mslearn-azure-ml/mslearnbike

# Instalar dependências
pip install -r requirements.txt

# Executar o notebook
jupyter notebook mslearn-bike-rentals.ipynb
