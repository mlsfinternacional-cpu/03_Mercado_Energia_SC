# 001 — Primeiros passos no laboratório

**Data:** 30/07/2026

## Objetivo

Iniciar o desenvolvimento do projeto **Energy Market of Santa Catarina**, preparando o ambiente de trabalho e realizando a primeira exploração do conjunto de dados da CELESC.

---

# Preparação do ambiente

Antes de iniciar a análise dos dados, organizei a estrutura do projeto no VS Code.

A estrutura criada foi:

```
03_Mercado_Energia_SC/

├── data/
│   ├── raw/
│   └── processed/
├── docs/
│   └── caderno_de_laboratorio/
├── images/
├── notebooks/
├── src/
└── README.md
```

Também selecionei o ambiente virtual (.venv) como Kernel do notebook.

---

# Instalação das bibliotecas

As primeiras bibliotecas utilizadas no projeto foram:

```python
import pandas as pd
import numpy as np

import matplotlib.pyplot as plt
import seaborn as sns
```

Na primeira execução apareceu o erro:

```
ModuleNotFoundError:
No module named 'pandas'
```

Percebi que o ambiente virtual havia sido criado, porém ainda não possuía as dependências instaladas.

Após instalar as bibliotecas necessárias, o notebook passou a executar normalmente.

---

# Primeiro contato com o VS Code

Este foi o primeiro projeto desenvolvido integralmente no VS Code.

Durante a configuração compreendi melhor alguns conceitos importantes:

- ambiente virtual;
- Kernel do Jupyter;
- instalação de bibliotecas;
- estrutura de pastas;
- notebooks;
- organização do projeto.

Também iniciei a criação deste Caderno de Laboratório para registrar decisões, descobertas e aprendizados durante a pesquisa.

---

# Primeiro contato com os dados

O primeiro arquivo analisado foi:

```
Municipio_Mensal_1T_2026.xlsx
```

Inicialmente tentei carregá-lo diretamente utilizando:

```python
pd.read_excel(arquivo)
```

A leitura ficou executando por vários minutos.

Ao invés de insistir na execução, decidi investigar a estrutura do arquivo.

---

# Conhecendo o arquivo antes de analisar

Utilizei:

```python
excel = pd.ExcelFile(arquivo)

excel.sheet_names
```

Descobri que o arquivo possui duas planilhas:

- Número de UC
- Consumo MWh

Essa etapa mostrou que conhecer a estrutura do arquivo antes de carregá-lo facilita muito a exploração dos dados.

Depois carreguei especificamente a aba:

```python
sheet_name="Consumo MWh"
```

A leitura ocorreu normalmente.

---

# Primeira exploração do DataFrame

Com os dados carregados iniciei a exploração utilizando algumas funções fundamentais do Pandas.

### Visualização inicial

```python
df.head()
```

Observei apenas as cinco primeiras linhas.

Nesse momento percebi que Florianópolis aparecia no início da tabela, mas compreendi que isso não significava que o conjunto de dados continha apenas esse município.

Era apenas o início do DataFrame.

Também utilizei:

```python
df.tail()
```

para visualizar as últimas linhas da tabela.

---

# Dimensão do conjunto de dados

Utilizando:

```python
df.shape
```

obtive:

- 7.716 linhas
- 395 colunas

Foi meu primeiro contato com um conjunto de dados dessa dimensão utilizando Pandas.

---

# Estrutura do DataFrame

Com:

```python
df.info()
```

identifiquei:

- predominância de colunas numéricas;
- poucas colunas descritivas;
- aproximadamente 23 MB em memória.

---

# Estrutura das colunas

Utilizando:

```python
df.columns
```

identifiquei uma organização muito interessante.

As oito primeiras colunas descrevem cada registro:

- tipo
- cod_muni
- agência
- núcleo
- unidade
- município
- cod_classe
- classe

A partir da nona coluna inicia-se uma série histórica mensal.

O primeiro mês registrado é:

1994-01

e o último:

2026-03

Percebi que o conjunto de dados reúne três dimensões importantes:

- espacial (municípios);
- econômica (classe de consumo);
- temporal (mais de trinta anos de histórico).

Essa estrutura torna o dataset muito mais rico do que eu imaginava quando escrevi o README inicial.

---

# Investigando os municípios

Perguntei diretamente ao conjunto de dados:

```python
df["município"].nunique()
```

Resultado:

```
290
```

Depois utilizei:

```python
df["município"].unique()
```

para visualizar todos os municípios distintos presentes no banco de dados.

Essa etapa mostrou que fazer perguntas diretamente ao DataFrame é muito mais eficiente do que procurar respostas visualmente em uma planilha.

---

# Hipóteses levantadas

Ao longo da exploração surgiram várias perguntas que orientarão as próximas análises:

- Por que existem 290 municípios no dataset?
- Qual é exatamente a unidade de observação de cada linha?
- Por que alguns registros apresentam valores ausentes (NaN)?
- Como a CELESC organiza esses registros?

Essas perguntas passam a fazer parte da própria pesquisa.

---

# Principal aprendizado do dia

Hoje compreendi que a Exploração Inicial dos Dados (EDA) não consiste em produzir gráficos imediatamente.

Antes disso é necessário conhecer profundamente o conjunto de dados.

Também percebi que aprender Pandas não significa decorar funções.

Cada função utilizada respondeu uma pergunta específica sobre o banco de dados.

O mais importante não foi aprender comandos.

Foi aprender a formular boas perguntas para os dados.

O notebook deixou de ser apenas um lugar para escrever código.

Hoje ele começou a se transformar em um laboratório de pesquisa.
