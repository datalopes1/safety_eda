
# 👷EDA - Industrial Safety and Health Analytics Dabase

Neste projeto será realizado o processo de EDA (Exploratory Data Analysis) a partir do dataset Industrial Safety and Health Analytics Dabase, que pode ser encontrado no [Kaggle](https://www.kaggle.com/datasets/ihmstefanini/industrial-safety-and-health-analytics-database/), com licensa CC0: Public Domain e enviado por [Eduardo Magalhães Oliveira](https://www.kaggle.com/edumagalhaes).  

### 🛠️ Ferramentas utilizadas
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54) ![Jupyter Notebook](https://img.shields.io/badge/jupyter-%23FA0F00.svg?style=for-the-badge&logo=jupyter&logoColor=white)

## 1.1. Os dados, o problema e os objetivos

Não é fácil encontrar datasets de plantas industriais do mundo real, com o intuito de alertar sobre a urgência da necessidade das industrias buscarem entender as razões por trás de acidentes e lesões com seus colaboradores, Eduado Magalhães Oliveira compartilhou este dataset para serem extraídos insights e análises que possam ajudar nessa conscientização. 

Os dados foram colhidos a partir de registros de acidentes em 12 cidades de 3 países diferentes e anomizados por solicitação da empresa que cedeu os dados, de forma que cada linha é uma ocorrência. Sendo as colunas:

- **Data**: timestamp ou date/time da informação
- **Countries**: país onde ocorreu o registro (anomizado).
- **Local**: cidade onde ocorreu o registro (anomizado).
- **Industry sector**: setor industrial ao qual pertence a fábrica.
- **Accident level**: de I à V, registra o quão severo foi o acidente (I significando pouco severo, progredino até V que significa muito severo).
- **Potential Accident Level**: Dependendo do nível do acidente, o banco de dados também registra o quão grave o acidente poderia ter sido (de acordo com outros fatores envolvidos no acidente).
- **Genre**: Genêro do colaborador.
- **Employee or Third Party**: Se a pessoa machucada é empregado ou terceirizado.
- **Critical Risk**: Alguma descrição do tipo de risco envolvido no acidente.happened.

### Objetivos

Portando o objetivo dessa análise será:

- Explorar os dados para verificar se precisam de alguma transformação.
- Entender quais fatores elevam os riscos de acidente.
- Entender a gravidade dos acidentes, e quem está mais sujeito a eles (genêro e setores).
- Descobrir quais são os níveis e níveis críticos de acidentes mais recorrentes.

## 1.2. Importação das bibliotecas e carregamento dos dados
A bibliotecas utilizadas foram o pandas, numpy, datetime, matplotlib, seaborn, plotly e warnings.

# 🧱2. Entendendo os dados 
##  2.1. Estrutura do dataframe
Aqui busquei através do métodos shape, head(), tail(), e info() para entender a estrutura dos dados. 
## 2.2. Breves conclusões antes de partir para os próximos passos

- O dataset não possui dados nulos.
- O dataset não possui nenhuma coluna numérica
- A coluna "Potential Accident Level", tem graduação de I à VI.
- Algumas colunas estão com nomenclatura em português, por questão de organização vou por os nomes em inglês.
- Na coluna "Industry Sector" observamos somente industrias de mineração, metalurgia uma classificação de outros.
- Funcionários tercerizados também leva em conta funcionários que trabalham de forma remota, é um ponto interessante.
- Existe um pequeno erro de preenchimento em alguns dados como "\nNot applicable" que seriam "Not applicable", isso será corrigido.
- A coluna "Data" deve ser colocada no dtype datetime.

# 🧹3. Limpeza e manipulação dos dados
## 3.1. Verificação de nulos e duplicados
Verificação através dos métodos isna() e duplicated(). 
## 3.2. Manipulação dos dados e colunas
Foram feitos os processos de renomeação das colunas, conversão do tipo da coluna Date e conserto de erros de preenchimento.

# 🔍4. EDA ou Análise Exploratória de dados
### A quantidade de acidentes tem diminuidos ao longo do tempo?
![Gráfico1](https://github.com/datalopes1/safety_eda/blob/main/scr/img/p_1.png?raw=true)
Começamos com uma boa noticia para o período, existe uma tendência de queda da quantidade de acidentes registrados. A diferença é considerável sendo 46,82% de queda (De 299 em 2016 para 140 em 2017).
### Em que país ocorrem mais acidentes?
![Gráfico2](https://github.com/datalopes1/safety_eda/blob/main/scr/img/p_2.png?raw=true)
### Em que cidades ocorrem mais acidentes?
![Gráfico3](https://github.com/datalopes1/safety_eda/blob/main/scr/img/p_3.png?raw=true)
### Quais os setores onde são registrados mais acidentes?
![Gráfico4](https://github.com/datalopes1/safety_eda/blob/main/scr/img/p_4.png?raw=true)
O setor de mineração é onde encontramos o maior número de acidentes (241), é uma ára que envolve alto risco de acidentes em toda sua cadeia produtiva. Desde riscos de acidente mecânicos até acidentes químicos. De acordo com dados do Ministério da Economia no ano de 2020 ocorreram no Brasil 1400 acidentes neste setor, sendo 24 deles fatais como visto em artigo da [AMJ Consultoria](https://amjmineracao.com.br/acidente-de-trabalho-em-area-de-mineracao/#:~:text=Infelizmente%2C%20acidente%20de%20Trabalho%20na,em%202020%2C%20sendo%2042%20fatais.). 
### Qual a distribuição dos níveis de acidente?
![Gráfico5](https://github.com/datalopes1/safety_eda/blob/main/scr/img/p_5.png?raw=true)
Maioria dos acidentes estão no nível I, ou seja de pouca severidade, é um bom indicativo. Mas precisamos a frente, fazer um olhar mais profundo nessa distribuição dentro de cada setor industrial.
### Qual a distribuição por nível potencial de acidente?
![Gráfico6](https://github.com/datalopes1/safety_eda/blob/main/scr/img/p_6.png?raw=true)
Este é um ponto interessante, os acidentes nessas industrias tem potencial altíssimo de severidade, o que pode resultar em mortes ou invalidez. Os acidentes acabarem com baixo nível lesivo é positivo, mas deve se buscar eliminar os riscos em locais com esse potencial de danos ao colaborador.
### Qual a distribuição por sexo dentro da industria?
![Gráfico7](https://github.com/datalopes1/safety_eda/blob/main/scr/img/p_7.png?raw=true)
Como esperado a maioria dos colaboradores são homens, boa parte do volume de empregos dentro das industrias é braçal o que tradicionalmente é função dos homens. Nestes setores tradicionalmente mulheres estão em posições administrativas e de comando, como nas áreas de Engenharia, Administração e Recursos Humanos, posições envolvidas em menos riscos diretos de acidente.
### Qual a distribuição por tipo de contratação?
![Gráfico8](https://github.com/datalopes1/safety_eda/blob/main/scr/img/p_8.png?raw=true)
Existe um alto volume de acidentes envolvendo funcionários terceirizados, sendo eles para trabalho presencial ou remoto. Os dados não são claros com as funções, então fica a dúvida sobre quais os empregos remotos dentro dessas indústrias e porque eles fornecem riscos.
### Qual a distribuição dos riscos críticos?
![Gráfico9](https://github.com/datalopes1/safety_eda/blob/main/scr/img/p_9.png?raw=true)
A classificação Others, deixa a análise um pouco inconclusiva. Mas olhando para outros riscos críticos, é importante observar que Pressed (pressionado), Manual Tools (equipamentos manuais) e Chemical substances (substâncias químicas), são as outras três mais frequentes. O que pode estar ligado a alguns fatores como treinamento dos colaboradores, uso de EPI e falhas humanas.
### Qual a distribuição dos níveis de acidente em cada setor?
![Gráfico10](https://github.com/datalopes1/safety_eda/blob/main/scr/img/p_10.png?raw=true)
### Qual a distribuição por níveis de potencial de acidente em cada setor?
![Gráfico11](https://github.com/datalopes1/safety_eda/blob/main/scr/img/p_11.png?raw=true)
Mineração e Metalúrgia são setores que envolvem altos riscos em potencial, ambientes de alta temperatura, exposição a agentes químicos, choques e equipamentos de díficil manuseio. Apesar disso, maioria dos acidentes registrados acabaram sendo pouco severos, o que é positivo na contenção de danos.
### Tipos de contratação por setor
![Gráfico12](https://github.com/datalopes1/safety_eda/blob/main/scr/img/p_12.png?raw=true)
Somente setor de metalúrgia os acidentados em sua maioria são empregados pela empresa (mas por uma margem muito pequena, só de 1). É necessário investigar meios de diminuir acidentes ocorrendo com colaboradores tercerizados, fornecer treinamentos junto a suas empreas ou treiná-los juntos dos funcionários empregados pela empresa em caso de contratos mais longos.
### Qual a severidade dos acidentes que cada tipo de contratado está envolvido?
![Gráfico13](https://github.com/datalopes1/safety_eda/blob/main/scr/img/p_13.png?raw=true)

# ✅5. Conclusões
![Cap](https://github.com/datalopes1/safety_eda/blob/main/scr/img/cap_1.jpg?raw=true)
O Brasil é um dos países com maiores número de casos de acidentes de trabalho, no ano de 2022 foram registrados 612,9 mil acidentes com 2.538 casos fatais, um estudo da [OIT (Organização Internacional do Trabalho)](https://congressoemfoco.uol.com.br/area/pais/brasil-registra-um-acidente-de-trabalho-a-cada-51-segundos/) aponta que a cada 51 segundos acontece um acidente de trabalho no país. Ainda em outro estudo da OIT, o país foi rankeado em 4º lugar em fatalidades no período de [2002 à 2020](https://prev-one.com.br/artigo/brasil-ocupa-4a-posicao-no-ranking-mundial-de-acidentes-de-trabalho#:~:text=No%20mundo%2C%20o%20Brasil%20ocupa,emprego%20entre%202002%20e%202020.), ficando atrás somente de Índia, China e Indonésia, os setores observados nessa análise tem alto potencial tanto de acidentes de alta severidade quanto óbitos portando é necessário tomar medidas que mudem a cultura de Segurança e Saúde no Trabalho dentro da organizações. 

### Alguns insights 

- Pela baixíssima quantidade de mulheres registradas nos dados, não foi possível fazer uma análise mais aprofundada do recorte de sexo.
- O alto número de acidentes com tercerizados, evoca a necessidade das organizações e das empresas de terceirização reforçarem o treinamento, independente de rotatividade de colaboradores, para evitar acidentes.
- Existe uma necessidade de reforço da cultura de Segurança e Saúde no Trabaho, e constante aprendizado dos colaboradores e gestores.
- Apesar de um pouco inconclusivo, os Riscos Críticos com alto número de ocorrências indicam necessidade de maior treinamento dos colaboradores, ou de rotinas de trabalho menos repetitivas.
- Os potenciais de serveridade dos acidentes nestes setores é muito alta, e maioria dos envolvidos nos acidentes mais graves são os terceirizados, então novamente, é necessária maior conscientização e treinamento destes colaboradores junto as organizações. 
