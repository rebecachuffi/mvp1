# Análise do World Happiness Report (2015-2022)

![GitHub language count](https://img.shields.io/github/languages/count/rebecachuffi/mvp1?style=for-the-badge)
![GitHub top language](https://img.shields.io/github/languages/top/rebecachuffi/mvp1?style=for-the-badge)
![GitHub last commit](https://img.shields.io/github/last-commit/rebecachuffi/mvp1?style=for-the-badge)

> Uma análise aprofundada sobre os fatores que compõem a felicidade em escala global, explorando dados de 2015 a 2022, com o objetivo de entender suas nuances, prever tendências e classificar os países em diferentes níveis de bem-estar.

---

## 📋 Índice

* [Sobre o Projeto](#-sobre-o-projeto)
* [🎯 Objetivos e Perguntas](#-objetivos-e-perguntas)
* [💡 Hipóteses](#-hipóteses)
* [🧩 Tipo de Problema](#-tipo-de-problema)
* [💾 Fontes de Dados e Atributos](#-fontes-de-dados-e-atributos)
* [❗ Desafio Metodológico](#-desafio-metodológico)
* [🚀 Tecnologias Sugeridas](#-tecnologias-sugeridas)
* [▶️ Como Executar](#️-como-executar)
* [⚖️ Licença](#️-licença)
* [📫 Contato](#-contato)

---

## 📖 Sobre o Projeto

Inspirado pelo TedTalk "Choice, happiness and spaghetti sauce" de Malcolm Gladwell, este projeto mergulha na complexidade da mensuração da felicidade. A felicidade não é um indicador simples, e sua dependência de múltiplos fatores torna sua análise um desafio fascinante.

Utilizando o "World Happiness Report" como base, este trabalho busca desvendar como diferentes indicadores socioeconômicos e de percepção influenciam o bem-estar das nações, analisando um período de 8 anos (2015-2022) em aproximadamente 150 países.

---

## 🎯 Objetivos e Perguntas

O objetivo principal é entender como os fatores que compõem o Score de Felicidade influenciam nesse processo. Buscamos responder a algumas perguntas-chave:

* Quais países ou regiões possuem as maiores pontuações de felicidade?
* O Top 10 mundial sofreu muita variação ao longo dos 8 anos?
* Como as pontuações e rankings mudaram ano a ano, especialmente entre 2015-2017?
* Houve algum país com um aumento ou queda significativa de felicidade?
* Regiões distintas apresentam tendências distintas?
* Como fatores externos, como a **temperatura média** e as **horas trabalhadas**, influenciam na felicidade?
* É possível agrupar países com características semelhantes para análise?

---

## 💡 Hipóteses

As seguintes hipóteses serão investigadas:

1.  **Relação com Horas de Trabalho:** Existe uma forte relação (negativa) entre o Score de Felicidade e a média de horas trabalhadas por semana?
2.  **Relação com a Temperatura:** Existe uma correlação significativa entre o Score de Felicidade e a temperatura média de cada país, considerando que climas extremos podem impactar o bem-estar?
3.  **Previsão Temporal:** É possível, através de técnicas de Séries Temporais, prever a tendência do Score de Felicidade para os países?
4.  **Classificação:** É viável criar classes (labels) que classifiquem os níveis de felicidade dos países de forma coesa e significativa?

---

## 🧩 Tipo de Problema

Este projeto aborda dois tipos de problemas de Machine Learning:

1.  **Classificação Supervisionada:** Os países serão classificados em três níveis de felicidade (Classe 1, 2 e 3) com base em seu `Happiness Score`.
2.  **Séries Temporais:** Análise e previsão da evolução do `Happiness Score` de um país ao longo dos anos, considerando os dados de períodos anteriores.

---

## 💾 Fontes de Dados e Atributos

Utilizaremos três fontes principais de dados para o período de 2015 a 2022:

1.  **World Happiness Report:** Dados principais retirados de surveys do Gallup World Poll (GWP), via Kaggle.
2.  **Temperatura Média:** Dados anuais de temperatura média por país.
3.  **Horas Semanais Trabalhadas:** Dados anuais da média de horas trabalhadas por país.

### Atributos Principais do Dataset de Felicidade

O `Happiness Score` de cada país é calculado com base nos seguintes fatores:

* **`Economy (GDP per Capita)`:** PIB per capita em Paridade de Poder de Compra (PPP), ajustado para dólares de 2021. É utilizado o log do PIB para capturar melhor a relação não-linear.
* **`Family (Social Support)`:** Percepção de apoio de amigos ou parentes em momentos de dificuldade.
* **`Health (Life Expectancy)`:** Expectativa de vida ao nascer, ajustada por anos vividos com saúde (dados da OMS).
* **`Freedom`:** Percepção de liberdade para fazer escolhas de vida.
* **`Trust (Government Corruption)`:** Percepção sobre a disseminação da corrupção no governo e nas empresas.
* **`Generosity`:** Medida da generosidade da população, ajustada pela riqueza do país.
* **`Dystopia Residual`:** O `Happiness Score` é explicado pela soma dos seis fatores acima mais um resíduo. Esse resíduo representa o que sobra e é comparado a um país hipotético chamado **Dystopia**, que possui os piores valores do mundo para cada um dos seis indicadores, servindo como um ponto de referência.

---

## ❗ Desafio Metodológico

**Observação Crucial:** Os valores absolutos do `Happiness Score` **não são diretamente comparáveis entre anos diferentes**. Isso ocorre porque o ponto de referência (o score de `Dystopia`) muda anualmente. Para resolver esse problema e permitir uma análise temporal justa, técnicas de normalização ou outras abordagens metodológicas serão aplicadas para tornar os dados comparáveis ao longo do tempo.

---

## 🚀 Tecnologias Sugeridas

A análise será desenvolvida utilizando o ecossistema Python, com as seguintes bibliotecas:

* **Pandas & NumPy:** Para manipulação e processamento dos dados.
* **Matplotlib & Seaborn:** Para visualização de dados e insights.
* **Scikit-learn:** Para os modelos de classificação e métricas de avaliação.
* **Statsmodels / Prophet:** Para a análise e previsão de séries temporais.

---

## ▶️ Como Executar

[Esta seção deve ser preenchida com as instruções do seu notebook final. Exemplo abaixo.]

```bash
# Clone este repositório
git clone [https://github.com/rebecachuffi/mvp1.git](https://github.com/rebecachuffi/mvp1.git)

# Navegue até a pasta do projeto
cd mvp1

# Instale as dependências (crie um arquivo requirements.txt)
pip install -r requirements.txt

# Abra o notebook em um ambiente como Jupyter Lab ou VS Code
```

---

## ⚖️ Licença

[Sugestão: Escolha uma licença. MIT é uma boa opção padrão.]
Este projeto está sob a licença MIT.

---

## 📫 Contato

**Rebeca Chuffi**

[![LinkedIn](https://img.shields.io/badge/linkedin-%230077B5.svg?style=for-the-badge&logo=linkedin&logoColor=white)]([SEU_LINK_DO_LINKEDIN])
[![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white)](https://github.com/rebecachuffi)
