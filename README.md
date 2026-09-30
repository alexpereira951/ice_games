# 🎮 Ice Games --- Análise de Vendas de Videogames

Projeto de análise exploratória de dados desenvolvido para a **Ice**,
uma loja online de videogames que atua em diferentes mercados. O
objetivo é identificar padrões associados ao desempenho comercial de
jogos e plataformas, utilizando dados históricos de vendas, avaliações,
gêneros, plataformas e classificações etárias.

A análise considera principalmente o período de **2011 a 2016**,
buscando gerar evidências para o planejamento de campanhas e decisões
comerciais para **2017**.

------------------------------------------------------------------------

## 📌 Objetivo do Projeto

A análise procura responder perguntas de negócio como:

-   Quais plataformas apresentam maior potencial comercial?
-   Como as vendas das plataformas evoluíram ao longo do tempo?
-   Quais gêneros concentram maior volume de vendas?
-   Existem diferenças relevantes entre os mercados da América do Norte,
    Europa e Japão?
-   Qual é a relação entre avaliações de críticos, avaliações de
    usuários e vendas?
-   As classificações etárias da ESRB apresentam padrões diferentes
    entre as regiões?
-   Existem diferenças estatisticamente significativas entre
    determinadas médias de avaliações dos usuários?

------------------------------------------------------------------------

## 🧠 Abordagem / Arquitetura Técnica

O projeto foi desenvolvido como um **pipeline analítico em Jupyter
Notebook**, seguindo as principais etapas:

### 1. Carregamento e inspeção

-   Leitura do arquivo `games.csv` com **Pandas**.
-   Inspeção da estrutura, tipos de dados e valores ausentes.
-   Verificação da existência de registros duplicados.

### 2. Preparação dos dados

Foram realizados os seguintes tratamentos:

-   Padronização dos nomes das colunas para minúsculas.
-   Conversão de `user_score` para tipo numérico.
-   Substituição de `tbd` por valores ausentes em `user_score`.
-   Substituição de `RP` por valores ausentes em `rating`.
-   Preenchimento de valores ausentes de `year_of_release` com `0`,
    representando ano desconhecido.
-   Conversão de `year_of_release` para inteiro.
-   Criação da variável `total_sales`, somando as vendas de todas as
    regiões disponíveis.

### 3. Análise temporal e de plataformas

A análise investiga:

-   Quantidade de jogos lançados por ano.
-   Evolução das vendas por plataforma.
-   Ciclo de vida das plataformas.
-   Comportamento das plataformas entre 2011 e 2016.
-   Seleção das plataformas consideradas relevantes para a análise de
    2017.

Foram utilizadas estatísticas como **média, mediana e distribuição das
vendas**, além de diagramas de caixa.

### 4. Análise de avaliações

Para a plataforma PS4, foi analisada a relação entre:

-   `user_score` × `total_sales`
-   `critic_score` × `total_sales`

A associação foi medida por meio da **correlação de Pearson**.

### 5. Perfil regional

Foram comparados os mercados de:

-   🇺🇸 América do Norte
-   🇪🇺 Europa
-   🇯🇵 Japão

A análise identifica as principais plataformas e gêneros em cada região,
além de observar a distribuição das vendas por classificação ESRB.

### 6. Testes de hipóteses

Foram realizados testes estatísticos com nível de significância de **5%
(`α = 0,05`)**:

-   **Xbox One × PC:** comparação das médias das avaliações dos
    usuários.
-   **Action × Sports:** comparação das médias das avaliações dos
    usuários.

Antes do teste t, foi utilizado o **teste de Levene** para avaliar a
igualdade das variâncias.

------------------------------------------------------------------------

## 🗂️ Estrutura do Repositório

``` text
ice_games/
│
├── datasets/
│   └── games.csv
│
├── notebooks/
│   └── notebook.ipynb
│
└── requirements.txt
```

### Diretórios e arquivos

  -----------------------------------------------------------------------
  Caminho                             Descrição
  ----------------------------------- -----------------------------------
  `datasets/`                         Armazena os dados utilizados na
                                      análise.

  `datasets/games.csv`                Dataset histórico de jogos, vendas,
                                      plataformas, gêneros, avaliações e
                                      classificação etária.

  `notebooks/`                        Contém os notebooks utilizados no
                                      desenvolvimento da análise.

  `notebooks/notebook.ipynb`          Notebook principal com preparação,
                                      exploração, visualizações e testes
                                      estatísticos.

  `requirements.txt`                  Lista de dependências necessárias
                                      para executar o projeto.
  -----------------------------------------------------------------------

------------------------------------------------------------------------

## ⚙️ Instalação e Execução

### 1. Clonar o repositório

``` bash
git clone https://github.com/alexpereira951/ice_games
cd ice_games
```

### 2. Criar e ativar um ambiente virtual

``` bash
python -m venv .venv
```

**Windows:**

``` bash
.venv\Scripts\activate
```

**Linux/macOS:**

``` bash
source .venv/bin/activate
```

### 3. Instalar as dependências

``` bash
pip install -r requirements.txt
```

### 4. Executar o Jupyter Notebook

``` bash
jupyter notebook
```

Depois, abra:

``` text
notebooks/notebook.ipynb
```

> O notebook utiliza um caminho relativo para o dataset
> (`../datasets/games.csv`). Portanto, a estrutura de diretórios
> apresentada acima deve ser preservada para a execução correta.

------------------------------------------------------------------------

## 🛠️ Stack Tecnológica

  Tecnologia                Utilização
  ------------------------- ----------------------------------------------
  🐍 **Python**             Linguagem utilizada no projeto
  🐼 **Pandas**             Manipulação, limpeza e agregação dos dados
  🔢 **NumPy**              Operações numéricas e tratamento de valores
  📊 **Plotly Express**     Criação de gráficos interativos
  📈 **Seaborn**            Visualização estatística, incluindo boxplots
  🧪 **SciPy**              Testes estatísticos e correlação
  📓 **Jupyter Notebook**   Desenvolvimento e documentação da análise

------------------------------------------------------------------------

## 📊 Resultados e Conclusões

### Tendência temporal

O dataset contém **16.715 jogos**. A análise temporal identificou o
maior volume de lançamentos em **2008**, com **1.427 jogos**, seguido
por uma tendência de redução no número de lançamentos até 2016.

Para as análises voltadas ao planejamento de 2017, foi adotado o
intervalo de **2011 a 2016**, considerado mais representativo do cenário
recente observado no projeto.

### Plataformas

Entre 2011 e 2016, a análise destacou **PS4, Xbox One, Xbox 360 e PS3**
entre as plataformas com maior volume de vendas no período. Para a
análise prospectiva de 2017, foram selecionadas:

-   PS4
-   Xbox One
-   PC
-   PS Vita
-   Wii U

Nos dados analisados, **PS4 apresentou a maior média de vendas por jogo
(0,80 milhão)**, seguida por **Xbox One (0,65 milhão)**.

A análise das distribuições também mostrou a presença de valores
extremos de vendas, principalmente em PS4 e Xbox One.

### Avaliações e vendas no PS4

A correlação de Pearson calculada no projeto apresentou:

-   **Avaliações dos usuários × vendas:** `-0,03`
-   **Avaliações dos críticos × vendas:** `0,41`

Os resultados indicam uma associação linear praticamente inexistente
entre avaliações dos usuários e vendas no recorte analisado, enquanto as
avaliações dos críticos apresentaram uma associação positiva moderada.

### Perfil regional

**América do Norte**

-   Principais plataformas: Xbox 360, PS3 e PS4.
-   Principais gêneros: Action, Shooter e Sports.

**Europa**

-   Principais plataformas: PS3, PS4 e Xbox 360.
-   Principais gêneros: Action, Shooter e Sports.

**Japão**

-   Principais plataformas: 3DS, PS3 e PSP.
-   Principal gênero: Role-Playing, seguido por Action.

Os resultados mostram diferenças relevantes entre o perfil japonês e os
mercados da América do Norte e Europa, especialmente em plataformas e
gêneros.

### Classificação ESRB

A análise regional das vendas por classificação indicou maior
participação dos títulos classificados como **M** na América do Norte e
Europa, enquanto títulos classificados como **E** apresentaram
participação mais distribuída entre as regiões analisadas.

O notebook também observa a ausência de vendas de títulos classificados
como **EC** a partir de 2011 no recorte utilizado.

### Testes de hipóteses

Com `α = 0,05`:

-   **Xbox One × PC:** o teste não rejeitou a hipótese nula, com
    `p-valor = 0,6131`, não sendo identificada diferença
    estatisticamente significativa entre as médias das avaliações dos
    usuários no recorte analisado.
-   **Action × Sports:** o teste indicou diferença estatisticamente
    significativa entre as médias das avaliações dos usuários.

------------------------------------------------------------------------

## 💼 Insights de Negócio

A análise fornece evidências para algumas frentes de planejamento:

### Estratégia de plataformas

Os dados analisados destacam **PS4 e Xbox One** pelo desempenho médio
observado no período recente, enquanto **PC, PS Vita e Wii U** aparecem
como plataformas complementares no recorte selecionado.

### Estratégia regional

Os resultados sugerem a necessidade de considerar o perfil de cada
mercado:

-   **América do Norte e Europa:** maior concentração em gêneros como
    Action e Shooter.
-   **Japão:** maior participação de Role-Playing e forte presença de
    plataformas Nintendo e PlayStation portáteis.

### Estratégia baseada em avaliações

A correlação observada entre avaliações de críticos e vendas de PS4 foi
superior à correlação entre avaliações de usuários e vendas. Esse
resultado pode ser utilizado como um indicador exploratório para avaliar
a relação entre percepção especializada e desempenho comercial.

> As conclusões acima representam interpretações dos dados históricos
> analisados e não devem ser tratadas como garantia de desempenho
> futuro.

------------------------------------------------------------------------

## ⚠️ Limitações

O projeto apresenta limitações que devem ser consideradas na
interpretação dos resultados:

1.  **Valores ausentes:** o dataset contém valores ausentes em variáveis
    como ano de lançamento, gênero, avaliações e classificação ESRB.
    Alguns valores foram preservados e outros tratados conforme as
    regras definidas no notebook.

2.  **Recorte temporal:** as análises prospectivas utilizam
    principalmente dados de **2011 a 2016** para apoiar o planejamento
    de 2017. Portanto, os resultados refletem um período histórico
    específico e não representam automaticamente o comportamento de
    mercados posteriores.

3.  **Correlação não implica causalidade:** as análises de correlação
    entre avaliações e vendas identificam associações lineares, mas não
    permitem concluir que uma variável seja a causa direta da outra.

4.  **Cobertura regional e de mercado:** o perfil regional concentra-se
    em **América do Norte, Europa e Japão**. Além disso, diferenças de
    disponibilidade de dados, plataformas, gêneros e distribuição das
    vendas podem influenciar as comparações realizadas.

------------------------------------------------------------------------

## 📁 Dados

O projeto utiliza o arquivo:

``` text
datasets/games.csv
```

O dataset reúne informações sobre títulos de videogames, incluindo:

-   Nome do jogo
-   Plataforma
-   Ano de lançamento
-   Gênero
-   Vendas por região
-   Avaliação de críticos
-   Avaliação de usuários
-   Classificação ESRB

------------------------------------------------------------------------

## 🚀 Próximos Passos

Como evolução do projeto, algumas possibilidades seriam:

-   Automatizar o pipeline de tratamento dos dados.
-   Criar uma etapa de validação de qualidade dos dados.
-   Transformar as análises em um dashboard interativo.
-   Incorporar novos períodos de dados para avaliar a estabilidade dos
    padrões encontrados.
-   Avaliar modelos preditivos de vendas com validação estatística e
    temporal.
-   Expandir a análise para outras regiões e métricas disponíveis.

------------------------------------------------------------------------

## 👤 Projeto

**Ice Games --- Análise de Dados de Vendas de Videogames**

Projeto desenvolvido em Python com foco em **Análise Exploratória de
Dados, Estatística, Visualização e geração de insights de negócio**.
