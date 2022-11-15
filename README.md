# Membradas de Sílica
<p align="justify">Este repositório contém uma análise exploratória de dados de membranas de sílica utilizadas em processos de separação de gás carbônico por meio de permeação gasosa.</p>
<p align="justify">O projeto conta com uma introdução descrevendo o processo de separação gasosa por membranas e vantagens da utilização de membranas de sílica para este processo.</p>

<p align="justify">O objetivo deste estudo dirigido é apresentar uma análise exploratória de um conjunto de dados de permeação gasosa utilizando membranas de sílica obtidas no website da Sociedade da Membrana da Australásia. Este notebook contém um planejamento detalhado da solução, que é apresentada com um texto introdutório, gráficos e tabelas representando os dados e discussões dos resultados obtidos.</p>

## Planejamento da solução: Método SAPE (Saída - Processo - Entrada)

### Saída (Produto Final):
- Arquivo tipo .xlsx com a base de dados após processo de limpeza;
- Notebook intitulado "membranas_de_sílica" contendo:
    - Introdução em texto acerca do processo de permeação de gases por membranas, especialmente do tipo sílica;
    - Gráficos 3D correlacionando os dados, utilizando a biblioteca Matplotlib;
    - Gráfico de pares de todo o conjunto de dados, utilizando a biblioteca Seaborn;
    - Tabelas com informações das correlações das colunas do conjunto de dados;
    - Modelo de regressão linear múltipla correlacionando a permeabilidade de H<sub>2</sub> com as permeabilidades de CO<sub>2</sub> e N<sub>2</sub>.

### Processo (Passos de realização):
#### Etapa A - Importação e limpeza dos dados
- **A.1.** Importação dos dados para o notebook, a partir de um arquivo do tipo .xlsx;<br/>
- **A.2.** Criação de um dataframe utilizando a biblioteca Pandas;<br/>
- **A.3.** Análise e limpeza do dataframe, a partir da observação de nome e tipo das colunas, para então proceder à remoção de  colunas irrelevantes e renomeação das colunas relevantes;<br/>
- **A.4.** Verificação de dados faltantes (NaN - Not a Number; "-") através da biblioteca missingno utilizando visualização do   tipo Matrix;<br/>
- **A.6** Remoção de linhas contendo dados faltantes;<br/>
- **A.7** Visualização dos dados presentes no através da biblioteca missingno utilizando visualização do tipo Barras;<br/>
- **A.8** Criação de um arquivo .xlsx com o conjunto de dados após sua limpeza.<br/>
   
#### Etapa B - Criação de gráficos
- **B.1.** Criação de gráficos 3D com a biblioteca Matplotlib e discussão dos resultados obtidos;
- **B.2.** Criação de um gráfico de pares com a biblioteca Seaborn relacionando todas as colunas do dataframe, com discussão dos resultados;
- **B.3.** Aplicação da função describe() da biblioteca Pandas no dataframe.

#### Etapa C - Correlação e Regressão Linear
- **C.1.** Aplicação da função corr() da biblioteca Pandas no dataframe e discussão dos resultados obtidos;
- **C.2.** Análise de viabilidade e aplicação de métodos de regressão linear múltipla correlacionando a permeabilidade de H<sub>2</sub> com as permeabilidades de CO<sub>2</sub> e N<sub>2</sub>, fazendo uso da biblioteca scikit-learn.
     
### Entrada (Fontes das bases de dados):
- Arquivo tipo .xlsx nomeado "MSA Membrane Database.xlsx" disponível no website da Sociedade da Membrana da Australásia.


## Resultados
As etapas A, B e C foram desenvolvidas com sucesso.

Ao fim da etapa A, após processos de importação, análise e limpeza de dados, foi criado um arquivo .xlsx com o conjunto de dados tratados a partir de uma base bruta original.
Foram utilizadas nesta etapa as bibliotecas <strong>Pandas</strong>, <strong>Missingno</strong> e <strong>Matplotlib</strong>.

Na etapa B foram desenvolvidos gráficos 2D e 3D utilizando as bibliotecas <strong>Matplotlib</strong> e <strong>Seaborn</strong> para avaliar as relações entre as pressões e temperaturas de hidrogênio, nitrogênio e gás carbônicos e as permeabilidades destes gases.

A etapa C conta com a correlação das variáveis dependente e independentes do conjunto de dados, assim como a regressão linear para avaliar a influência de cada variável do modelo.
A biblioteca <strong>sklearn.linear</strong> foi utilizada para gerar uma equação do tipo

<p align="center"><strong>P<sup>prev</sup><sub>H<sub>2</sub></sub> = b<sub>1</sub>P<sub>CO<sub>2</sub></sub> + b<sub>2</sub>N<sub>CO<sub>2</sub></sub> + A</strong></p>

onde<br/>
P<sup>prev</sup><sub>H<sub>2</sub></sub> é a permeabilidade de H<sub>2</sub> prevista pelo modelo,<br/>
P<sub>CO<sub>2</sub></sub> é a permeabilidade de CO<sub>2</sub>,<br/>
P<sub>N<sub>2</sub></sub> é a permeabilidade de N<sub>2</sub>.

## Conclusão

<p align="justify">No modelo de regressão linear múltipla, a equação resultante é P<sup>prev</sup><sub>H<sub>2</sub></sub> = 2,917240P<sub>CO<sub>2</sub></sub> + 0,571883P<sub>N<sub>2</sub></sub> + 2,476253.10<sup>-7</sup> — significando que a permeabilidade de H<sub>2</sub> é prevista para aumentar 2,917240 mol/(m².s.Pa) e 0.571883 mol/(m².s.Pa) quando as permeabilidades de CO<sub>2</sub> e N<sub>2</sub> aumentarem em 1 mol/(m².s.Pa), respectivamente, e que a permeabilidade de H<sub>2</sub> é 2.476253e-07 mol/(m².s.Pa) quando as permeabilidades de CO<sub>2</sub> e N<sub>2</sub> forem ambas iguais a zero.</p>

### Coeficiente de determinação - R²
<p align="justify">Um artifício para avaliar a performance de um modelo de regressão linear é o <strong>coeficiente de determinação</strong>, representado como R². Este parâmetro representa a proporção da variabilidade na variável dependente explicada pelas variáveis independentes, dando a ideia de quão bem pode-se prever a variável dependente a partir das variáveis independentes.</p>

<p align="justify">O resultado de R² = 0,9111 significa que o modelo de regressão linear múltipla explica cerca de <strong>91,11%</strong> da variância da permeabilidade de H<sub>2</sub> a partir das permeabilidades de CO<sub>2</sub> e N<sub>2</sub>.</p>
