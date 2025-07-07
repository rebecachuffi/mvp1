# **Projeto MVP - Happiness Score**
Análise de Dados e Boas Práticas


Nome: Rebeca Chuffi Saccochi


Duração: 60 horas 

[Notebook](https://github.com/rebecachuffi/mvp1/blob/main/MVP1_RebecaChuffi.ipynb) | [Repositório](https://github.com/rebecachuffi/mvp1/tree/main)

## **Contexto**
Este projeto é o primeiro feito na área de Ciência de Dados da minha vida! Escolhi o dataset por gostar do tema, mas não tinha ideia do quão desafiadora seria a etapa de limpeza e tratamento de dados. Minha área é Matemática e nunca tive contato com programação, então é possível que alguns métodos não sejam os mais comuns, visto que fui aprendendo enquanto tentava solucionar os problemas que apareciam.  

## **Descrição do Problema**
O conjunto de dados **"World Happiness Report"** é um conjunto que apresenta uma maneira de mensurar felicidade através de alguns índices que serão definidos em breve. O *dataset* em questão é formado por 8 subconjuntos referentes aos anos de 2015 a 2022, considerando em média 150 países em cada um. A motivação para analisar esse dataset veio de um TedTalk chamado [Choice, happiness and spaghetti sauce](https://www.ted.com/talks/malcolm_gladwell_choice_happiness_and_spaghetti_sauce) - Malcolm Gladwell, que analisou um aspecto curioso da natureza das escolhas e da felicidade. Assisti  esse *Tedtalk* em 2016 e o fato da felicidade não ser um indicador simples de ser mensurado e de, potencialmente, depender de vários outros possíveis fatores, me chamou a atenção fez com que esse *dataset* particular sobre felicidade se destacasse em meio a tantos outras possibilidades.

O objetivo inicial deste projeto é entender como os fatores que "formam" o Score de Felicidade influenciam nesse processo - Economy (GDP per Capita), Family, Health (Life Expectancy), Freedom, Trust (Government Corruption) e Generosity,  se podemos identificar diferenças entre as regiões/continentes, além de entender como a Felicidade se relaciona com outros fatores (Temperatura e Horas Trabalhadas) e quais modelos podemos usar para prever a tendência de felicidade dos países em anos futuros. 

*  Análise Temporal: entender a evolução da felicidade ao longos dos anos e os possíveis impactos de eventos globais nas métricas. Além disso, escolher alguns países para analisar individualmente as mudanças no nível de felicidade.

*  Problemas de Classificação: classificar os países como Classe 1, Classe 2, Classe 3 (de acordo com o score de felicidade)

*  Padrões ocultos: Países com alto PIB, mas baixa felicidade? - (Essa parte deixaremos para uma segunda versão do trabalho )

*  Agrupar países com características semelhantes para fazer as análises. 


------------
**Algumas perguntas potencialmente interessantes:**

Quais países ou regiões possuem as maiores pontuações de felicidade? 

O Top 10 do mundo teve muita variação em 8 anos? 

Como as classificações ou pontuações dos países mudaram entre os relatórios de 2015 e 2016, bem como entre 2016 e 2017?

Algum país apresentou um aumento ou uma queda significativa na felicidade durante esses anos?

Regiões distintas apresentam tendências distintas? 

Como a temperatura e as horas trabalhadas influenciam na felicidade? 



## Hipóteses do Problema

- Considerando que excesso de trabalho é um fator atual e preocupante, existe relação forte entre o Score de Felicidade e as Horas Trabalhadas por Semana? 

- Sabemos que locais com baixas temperaturas costumam ter mais problemas com saúde mental. Por outro lado, países com maiores temperaturas tem uma grande interseção com países mais pobres. Existe relação entre o Score de Felicidade e a Temepratura média de cada país?

- Considerando um contexto de séries temporais, é possível prever a tendência de cada país em termos do Score de Felicidade? De que maneira conseguimos fazer isso?

- Considerando um contexto Classificação, é possível criar labels que façam sentido para classificar a Felicidade? 



## Seleção de Dados

Utilizaremos mais de uma fonte de dados:

*   Happiness Score (Score de Felicidade): esse é nosso atributo principal. Os dados foram retirados do survey do Gallup World Poll (GWP) dos anos de 2015 até 2022. Muitos datasets foram retirados do Kaggle, porém não achei uma fonte com todos os anos necessários, logo há uma homogeneidade de estruturas que precisaremos resolver. 

*  Temperatura Média por país dos anos de 2015 a 2022.  

*  Horas Semanais trabalhadas por país dos anos de 2015 a 2022. 


## Atributos do Dataset

Nosso principal dataset, que aqui chamaremos apenas de **Happiness**, é formado por 8 subconjuntos referentes aos anos de 2015 a 2022. Ele possui os seguintes atributos:

━━━━━━━━━━━━━━━━━━━━

**Atributos e como foram coletados:**


- ***Happiness Score*** (Score de Felicidade): esse é nosso atributo principal. Os dados foram retirados do *survey* do Gallup World Poll (GWP) dos anos de 2005 até 2020. O domínio do *Happiness Score* varia de 0 (pior vida que você pode imaginar) até 10 (melhor dia que você pode imaginar). Além disso, o *Happiness Score* de cada país representa a **média** nacional.

- ***Happiness Rank*** (Rank de felicidade considerando os 158 países)

Para calcular o *Happiness Score*, compusemos os dados de outros atributos específicos que serão detalhados a seguir:

As colunas que aparecem após a pontuação de felicidade estimam o quanto cada um dos seis fatores abaixo contribuem para que a avaliação da vida em cada país seja mais alta do que seria em um país hipotético chamado Dystopia (piores valores médios do mundo para cada um desses seis indicadores).

- ***Economy (GDP per Capita)*** (PIB per capita): O PIB per capita está expresso em Paridade de Poder de Compra (PPP), ajustado para dólares internacionais constantes de 2021, obtido dos World Development Indicators (WDI) do Banco Mundial. Não é o valor nominal do PIB, mas sim ajustado pelo custo de vida de cada país. Além disso, é utilizado o log do PIB per capita, pois ele captura melhor a relação não-linear. Por exemplo, um aumento de USD $1.000$ no PIB per capita impacta muito mais um país pobre (ex: USD $500$ → USD $1.500$) que um país rico (ex: USD $50.000$ → USD $51.000$).

- ***Family or Social Support*** (Família ou Suporte Social): mede a disponibilidade de apoio emocional ou material em tempos de dificuldade a partir da seguinte pergunta: "Se você estivesse em apuros, há parentes ou amigos que poderiam ajudar?"

- ***Health (Life Expectancy)*** (Saúde - expectativa de vida): calculada através dos dois fatores:expectativa de vida ao nascer (dados da OMS) e ajustado pela fração de anos vividos com saúde (usando dados de morbidade e incapacidade). Padronização: Os valores são normalizados para uma escala comparável entre países.

- ***Freedom*** (Liberdade): média das respostas binárias à pergunta "Você está satisfeito ou insatisfeito com a sua liberdade de escolher o que fazer com sua própria vida?".

- ***Trust (Government Corruption)*** (Corrupção): média das respostas binárias das duas perguntas: "A corrupção está disseminada no governo ou não?" e "A corrupção está disseminada nas empresas ou não?". Essas duas perguntas avaliam a percepção das pessoas sobre a corrupção no setor público e privado.

- ***Generosity*** (Generosidade): primeiro é calculado quanto de doação seria esperado para cada país baseado apenas na sua riqueza (PIB per capita). A "generosidade" é definida como a diferença entre o quanto o país realmente doa e o quanto seria esperado que ele doasse por causa da sua riqueza.


- ***Dystopia*** (Distopia): **Dystopia** é um país imaginário que representa uma sociedade hipotética caótica, opressiva e indesejável, onde prevalecem sofrimento, injustiça e ausência de liberdade. A criação da **Dystopia** fornece um ponto de referência em que todos os países podem ser favoravelmente comparados (nenhum país tem desempenho pior do que Dystopia) em relação aos seis principais indicadores que compoem o *Happiness Score*.

***Dystopia Residual***: o que sobra quando subtraímos todos os fatores mensurados do Happiness Score. O modelo possui algumas variáveis explicativas, mas nem tudo que influencia na felicidade está nela. O Residual captura diferenças culturais, políticas, emocionais ou subjetivas não mensuradas diretamente. O valor da Dystopia nos ajuda a criar uma "régua" de onde partir em cada ano.  


**OBSERVAÇÃO IMPORTANTE:**
Os menores valores observados para os seis indicadores caracterizam **Dystopia** e, portanto, esse valor muda anualmente. Por conta disso, observamos algo **IMPORTANTE**: não é possível comparar os valores absolutos de felicidade durante anos diferentes, pois o valor da felicidade para **Dystopia** muda, e assim a percepção de uma felicidade com score de 5.5 em 2015 pode ser diferente da mesma nota em 2016. Para resolver esse problema metodológico, usaremos algumas técnicas que tornarão os dados comparáveis.


**Cálculo do Hapiness Score:**
O Hapiness Score de cada país foi calculado por uma **regressão de mínimos quadrados ordinários (MQO)** com 6 variáveis explicativas (aquelas que citamos acima) + Dystopia Residual.

## **Tecnologias Utilizadas**

- **Python**: Para análise de dados e visualização.
- **Pandas**: Manipulação e análise de dados.
- **Matplotlib / Seaborn**: Visualização de dados.
- **Scikit-learn**: Construção e avaliação de modelos preditivos.
- **Pycountry**: Para normalização dos nomes dos países.

## **Instalação**

Para executar este projeto localmente, basta abrir com Colab: [Notebook](https://github.com/rebecachuffi/mvp1/blob/main/MVP1_RebecaChuffi.ipynb) 

## **Bibliotecas**
```
!pip install pycountry
!pip install rich
!pip install iso3166
!pip install diptest
```
```
#Manipulação de data frames
import pandas as pd
import missingno as ms # para tratamento de missings

#manipulação numérica
import numpy as np

#construção de gráficos
import matplotlib.pyplot as plt

#biblioteca de países
import pycountry

#exibição de dados no jupyter notebook
from IPython.display import display

#graficos
import seaborn as sns

#estatística
import diptest
from scipy import stats


#pré-processamento e modelos
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler, MinMaxScaler, OneHotEncoder
from sklearn.decomposition import PCA
from sklearn.compose import ColumnTransformer
from sklearn.pipeline import Pipeline
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import classification_report, confusion_matrix


from rich.console import Console
from rich.panel import Panel
console = Console()

from iso3166 import countries
```

## **Datasets**

*   [Hapiness Score 2015](https://www.kaggle.com/datasets/unsdsn/world-happiness)
*   [Hapiness Score 2016](https://www.kaggle.com/datasets/unsdsn/world-happiness)
*   [Hapiness Score 2017](https://www.kaggle.com/datasets/unsdsn/world-happiness)
*   [Hapiness Score 2018](https://www.kaggle.com/datasets/unsdsn/world-happiness)
*   [Hapiness Score 2019](https://www.kaggle.com/datasets/unsdsn/world-happiness)
*  [Hapiness Score 2020](https://www.kaggle.com/datasets/londeen/world-happiness-report-2020)
*   [Hapiness Score 2021](https://www.kaggle.com/datasets/ajaypalsinghlo/world-happiness-report-2021/data)
*   [Hapiness Score 2022](https://www.kaggle.com/datasets/mathurinache/world-happiness-report)
*   [Hapiness Score 2023](https://www.kaggle.com/datasets/ajaypalsinghlo/world-happiness-report-2023)

OUTROS DADOS

Além dos *datasets* principais (Happiness Scores 2015- 2023) selecionei alguns outros dados que podem fazer sentido serem comparados com Score de Felicidade. Não necessariamente usaremos todos num primeiro momento, mas serve como possíveis sugestões para trabalhos futuros com Happiness Score:


*   [Rate of deaths and missing persons due to natural disasters, 2005 to 2022](https://ourworldindata.org/grapher/deaths-and-missing-persons-due-to-natural-disasters?tab=table#explore-the-datas)

*   [Mean temperature for countries by year 1901-2022](https://www.kaggle.com/datasets/palinatx/mean-temperature-for-countries-by-year-2014-2022)

*   [Horas semanais trabalhadas em média por país](https://rshiny.ilo.org/dataexplorer46/?lang=en&segment=indicator&id=HOW_TEMP_SEX_AGE_ECO_NB_A)

*   [Cause of death of injury by mental problems](https://vizhub.healthdata.org/gbd-results?params=gbd-api-2021-public/2aed16e64a46bf57257dfc6ac4f86862)
*   **Radiação solar média anual** (kWh/m²/dia) (baixamos esse conjunto de dados via API pelo site da NASA)


*   **Temperatura (do ar até 2 metros de altura)** em graus Celsius (baixamos esse conjunto de dados via API pelo site da NASA)


## **Modelos**

Grande parte da etapa de limpeza e Tranformação de dados foi feita de maneira exaustiva nas etapas anteriores (inclusive, passei 30 horas só fazendo isso, jesus nos ajude).

A ideia é usar algum **modelo de Machine Learning** para previsão com séries temporais. Nos próximos cursos, descobrirei quais dos modelos fazem mais sentido no nosso contexto. Algumas possibilidades são:

*   Modelos baseados em regressão: Como a regressão linear ou regressão polinomial.

*   Modelos de aprendizado supervisionado: Como Random Forest, Support Vector Machines (SVM) ou Gradient Boosting Machines (GBM), que são úteis para séries temporais também.

*   Modelos de séries temporais (como ARIMA, LSTM, RNN)


## **Conclusão**

Além das hipóteses propostas inicialmente, tivemos vários insights ao longo do caminho. A parte de limpeza e tratamento de dados me fez chorar lágrimas de sangue, mas foi muito bom, proque aprendi e entendi coisas que até então eram bem teóricas. Mas vamos às hipóteses:


**- Considerando que excesso de trabalho é um fator atual e preocupante, existe relação forte entre o Score de Felicidade e as Horas Trabalhadas por Semana?**

Existe uma relação inversamente proporcional entre horas trabalhadas e felicidade, mas essa não é forte (como podemos ver no seção de correlação). 

**- Sabemos que locais com baixas temperaturas costumam ter mais problemas com saúde mental. Por outro lado, países com maiores temperaturas tem uma grande interseção com países mais pobres. Existe relação entre o Score de Felicidade e a Temepratura média de cada país?**

Temperaturas médias pequenas tendem a ter alto Happiness Score - o que é o oposto do que imaginada inicialmente. Imagino que há vários fatores que influenciem a Felicidade e temperatura baixas estão ligadas a países com índices econômicos maiores, por exemplo, existe uma grande interseção. Portanto, concluímos que não é um fator relevante para essa discussão.

**- Considerando um contexto de séries temporais, é possível prever a tendência de cada país em termos do Score de Felicidade? De que maneira conseguimos fazer isso?**

É possível treinar o conjunto de dados com anos anteriores e usar o último ano em que se tem dados para testar o modelo. Escolhemos países que estavam presentes no maior número de anos possível para essa análise. 

**- Considerando um contexto Classificação, é possível criar labels que façam sentido para classificar a Felicidade?** 

É possível sim! Ainda não usei nenhum modelo específico, então como essas Classes serão criadas ainda é algo que descobrirei posteriormente, apesar de ter deixado uma sugestão de label ao avaliar anualmente os scores dos países. 
