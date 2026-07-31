# Dia 002 — Primeiras análises

**Data:** 31/07/2026

## Objetivo
Compreender a estrutura da base de dados antes de iniciar as análises estatísticas e visuais.

## O que foi feito
- Exploração das colunas da planilha "Consumo MWh".
- Verificação da estrutura do DataFrame (`df.info()` e `df.columns`).
- Identificação dos 290 municípios presentes na base.
- Levantamento das categorias da variável `classe`.
- Levantamento dos tipos de consumidor (`Livre` e `Cativo`).
- Investigação das colunas de identificação:
  - município
  - agência
  - núcleo
  - unidade
- Comparação entre municípios com maior e menor quantidade de registros.
- Primeiros testes utilizando `groupby()` para compreender a granularidade dos dados.

## Descobertas
- A base possui 395 colunas, sendo:
  - 8 colunas cadastrais;
  - 387 colunas correspondentes às séries mensais de consumo.
- Existem 290 municípios registrados.
- As classes de consumo incluem:
  - Residencial
  - Industrial
  - Comercial
  - Rural
  - Poder Público
  - Serviço Público
  - Iluminação Pública
  - Próprio
  - Revenda
- O mercado está dividido entre consumidores **Cativos** e **Livres**.
- Municípios apresentam quantidades muito diferentes de registros, indicando diferentes níveis de detalhamento na base.

## Hipóteses investigadas
Durante a exploração surgiram algumas hipóteses para explicar a quantidade de registros por município.

Foram testadas as seguintes possibilidades:

- Agência responsável.
- Núcleo regional.
- Unidade administrativa.
- Classe de consumo.
- Tipo de consumidor (Livre/Cativo).

Os testes mostraram que essas variáveis, isoladamente, não explicam completamente a quantidade de registros observada para alguns municípios.

## Reflexões
Antes de produzir gráficos ou estatísticas descritivas, tornou-se evidente a necessidade de compreender a lógica de construção da base.

Nesta etapa, o foco deixou de ser apenas utilizar comandos do Pandas e passou a ser responder uma pergunta fundamental:

> **O que representa cada linha deste conjunto de dados?**

Essa investigação será essencial para garantir interpretações corretas nas próximas análises.

## Próximos passos
- Investigar a granularidade dos registros.
- Consultar a documentação e o contexto do Boletim de Mercado da CELESC.
- Identificar a unidade de observação da base.
- Iniciar as primeiras estatísticas descritivas do consumo de energia.