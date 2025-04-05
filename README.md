# Projeto Prático - Previsão de Aluguel de Bicicletas com Azure Machine Learning

Este repositório contém o projeto prático desenvolvido como parte do curso de Fundamentos de Inteligência Artificial com Azure Machine Learning. Utilizamos o Azure ML Studio para criar, treinar e publicar um modelo de regressão para prever a demanda por bicicletas com base em dados históricos.

---

## 📌 Objetivo

Criar um modelo preditivo para estimar o número de bicicletas alugadas por hora, com base em variáveis como temperatura, umidade, estação do ano e outros fatores ambientais e temporais.

---

## 🔧 Etapas do Projeto

### 1. Criação do Workspace
- Acesse o portal do [Azure Machine Learning Studio](https://ml.azure.com).
- Crie um novo workspace com as configurações padrão.

### 2. Carregamento do Dataset
- Dataset utilizado: **Bike Rental UCI**.
- Origem: Open Datasets do Azure ML Studio.
- O dataset foi registrado no workspace para uso em experimentos de AutoML.

### 3. Execução do AutoML
- Acesse a seção **Automated ML > + New automated ML run**.
- Selecione o dataset carregado.
- Configurações utilizadas:
  - Nome do experimento: `bike-rental-automl`
  - Coluna de destino: `Rental Count` (número de aluguéis)
  - Tipo de tarefa: Regressão
  - Compute target: Cluster `Standard_DS11_v2`
- Iniciamos a execução do AutoML e aguardamos a avaliação dos modelos.

### 4. Avaliação do Modelo
- O AutoML testou diversos algoritmos de regressão (como Random Forest, ElasticNet, etc.).
- O modelo com menor erro RMSE foi selecionado automaticamente.
- Modelo final implantado via botão **Deploy model > Real-time endpoint**.

### 5. Publicação do Ponto de Extremidade
- O modelo foi implantado como um serviço REST com endpoint de inferência em tempo real.
- O endpoint foi testado via requisições POST com dados no formato JSON.
- As configurações do endpoint foram exportadas como `endpoint.json`.

---

## 📁 Arquivos neste repositório

- `README.md`: Instruções detalhadas de como o modelo foi criado.
- `endpoint.json`: Arquivo com informações do endpoint REST publicado pelo Azure.

---
