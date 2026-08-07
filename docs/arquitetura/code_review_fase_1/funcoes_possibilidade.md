# Funções Candidatas — Primeira Auditoria

**Origem:** Auditoria Arquitetural dos Notebooks 01–04

Este documento registra as funções identificadas como candidatas à modularização durante a primeira fase da pesquisa.

---

# 1. Leitura dos Dados

```python
import pandas as pd

def carregar_dados(caminho: str) -> pd.DataFrame:
    """
    Lê a base de dados e retorna um DataFrame.
    """
    return pd.read_excel(caminho)
```

---

# 2. Limpeza dos Dados

```python
def limpar_dados(df):
    """
    Executa operações básicas de limpeza.
    """
    df = df.drop_duplicates()
    df = df.dropna(how="all")
    return df
```

---

# 3. Padronização de Colunas

```python
def padronizar_colunas(df):
    """
    Padroniza nomes das colunas.
    """
    df.columns = (
        df.columns
        .str.strip()
        .str.lower()
        .str.replace(" ", "_")
    )
    return df
```

---

# 4. Padronização de Municípios

```python
def padronizar_municipios(df, coluna):
    """
    Padroniza nomes de municípios.
    """
    df[coluna] = (
        df[coluna]
        .str.upper()
        .str.strip()
    )
    return df
```

---

# 5. Conversão de Datas

```python
def converter_datas(df, coluna):
    """
    Converte uma coluna para datetime.
    """
    df[coluna] = pd.to_datetime(df[coluna])
    return df
```

---

# 6. Agregações

```python
def agrupar_consumo(df, grupo, valor):
    """
    Agrupa dados por uma ou mais colunas.
    """
    return (
        df
        .groupby(grupo)[valor]
        .sum()
        .reset_index()
    )
```

---

# 7. Configuração dos Gráficos

```python
import matplotlib.pyplot as plt

def configurar_grafico():
    """
    Aplica configurações padrão aos gráficos.
    """
    plt.style.use("default")
    plt.grid(alpha=0.3)
```

---

# 8. Gráfico de Barras

```python
def grafico_barras(df, x, y, titulo):
    """
    Gera gráfico de barras.
    """
    plt.figure(figsize=(10, 6))
    plt.bar(df[x], df[y])
    plt.title(titulo)
    plt.xticks(rotation=45)
    plt.show()
```

---

# 9. Gráfico de Linhas

```python
def grafico_linhas(df, x, y, titulo):
    """
    Gera gráfico de linhas.
    """
    plt.figure(figsize=(10, 6))
    plt.plot(df[x], df[y])
    plt.title(titulo)
    plt.grid(True)
    plt.show()
```

---

# Evolução

Estas funções ainda permanecem distribuídas pelos notebooks.

A implementação em `src/` ocorrerá somente quando a reutilização justificar sua extração, preservando a natureza exploratória da primeira fase do projeto.