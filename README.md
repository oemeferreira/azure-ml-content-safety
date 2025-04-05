# Projeto Prático - Azure Machine Learning

Este repositório contém o projeto prático desenvolvido como parte do curso de Fundamentos de Inteligência Artificial com Azure Machine Learning. O objetivo foi criar, treinar e publicar um modelo preditivo utilizando os recursos do Azure ML Studio.

---

## 📌 Objetivo

Criar um modelo de Machine Learning com previsão baseada em dados reais, utilizando a ferramenta Azure Machine Learning Studio, e publicar um ponto de extremidade (endpoint) para inferência via API.

---

## 🔧 Etapas do Projeto

### 1. Criação do Workspace
- Acesse o portal do [Azure Machine Learning Studio](https://ml.azure.com).
- Crie um novo workspace com os parâmetros padrão (nome, região, assinatura).

### 2. Carregamento do Dataset
- No menu lateral, vá até **Datasets > +Create dataset > From Open Datasets**.
- Utilizei o dataset **Diabetes**, já disponível na plataforma.
- O dataset foi registrado no workspace para uso posterior no experimento.

### 3. Configuração do Experimento com AutoML
- Vá até **Automated ML** e clique em **+ New automated ML run**.
- Selecione o dataset carregado.
- Configure o experimento:
  - Nome do experimento: `diabetes-automl`
  - Coluna de destino: `Diabetic` ou a variável dependente apropriada
  - Tipo de tarefa: Classificação (Classification)
  - Compute cluster: Criado um novo cluster do tipo `Standard_DS11_v2`
- Inicie o processo e aguarde o AutoML avaliar os melhores modelos.

### 4. Avaliação e Seleção do Modelo
- Após a execução, visualize a tabela de métricas dos modelos.
- O modelo com melhor desempenho foi selecionado automaticamente com base na métrica `Accuracy` ou `AUC_weighted`.
- Clique em **Best model > Deploy model**.

### 5. Publicação do Ponto de Extremidade
- Configure o nome do serviço de inferência.
- O modelo foi publicado como um **Web Service Endpoint**.
- A URL do endpoint e a chave de autenticação foram geradas.
- O arquivo `.json` com as configurações do endpoint foi exportado (presente neste repositório como `endpoint.json`).

---

## 📁 Arquivos neste repositório

- `README.md`: Este arquivo com o passo a passo completo do projeto.
- `endpoint.json`: Arquivo com os detalhes do ponto de extremidade do modelo treinado (inclui URL, chave, métodos de requisição etc.).

---
