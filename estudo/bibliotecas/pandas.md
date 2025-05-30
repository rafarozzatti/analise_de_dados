A biblioteca **Pandas** é uma das mais importantes ferramentas da linguagem **Python** para **ciência de dados**, **análise de dados**, **engenharia de dados** e **manipulação de dados tabulares** (estruturados).

---

### 📦 O que é o Pandas?

**Pandas** é uma biblioteca de código aberto que fornece estruturas de dados rápidas, flexíveis e expressivas. As duas principais estruturas são:

* **Series**: uma lista de uma dimensão com índice.
* **DataFrame**: uma tabela de duas dimensões (como uma planilha do Excel ou uma tabela SQL), com linhas e colunas nomeadas.

---

### 🚀 Por que usar o Pandas?

* Leitura e escrita de arquivos: CSV, Excel, JSON, SQL, Parquet, etc.
* Filtragem, ordenação, agrupamento e agregação de dados.
* Limpeza, tratamento de valores ausentes, remoção de duplicatas.
* Cálculos estatísticos e operações vetorizadas.
* Integração com outras bibliotecas como NumPy, Matplotlib, Seaborn, Scikit-learn.

---

### 🧠 Estruturas de Dados do Pandas

1. **Series** – estrutura de 1 dimensão (como um array)
2. **DataFrame** – estrutura de 2 dimensões (como uma planilha)

```python
# Importa a biblioteca pandas, usada para manipulação e análise de dados em estruturas como Series e DataFrames
import pandas as pd

# Cria uma Series: uma estrutura unidimensional do pandas, como um vetor com índice
# Neste exemplo, temos os valores 10, 20 e 30 associados aos índices 'a', 'b' e 'c'
s = pd.Series([10, 20, 30], index=['a', 'b', 'c'])

# Cria um DataFrame: estrutura bidimensional do pandas, semelhante a uma tabela
# Aqui, o DataFrame tem duas colunas:
# - 'nome': com três nomes
# - 'idade': com a idade correspondente de cada pessoa
df = pd.DataFrame({
    'nome': ['Ana', 'Bruno', 'Carlos'],
    'idade': [23, 35, 30]
})
```

---

### 🔧 Principais Categorias de Funções do Pandas

Organizarei TODAS as principais funcionalidades em categorias. Se quiser uma explicação mais profunda de cada uma com exemplos, posso detalhar depois.

---

## 1. **Leitura e Escrita de Arquivos**

```python
pd.read_csv('dados.csv')              # Lê CSV
pd.read_excel('planilha.xlsx')       # Lê Excel
pd.read_json('arquivo.json')         # Lê JSON
pd.read_sql(query, conexão)          # Lê de banco de dados
pd.read_parquet('arquivo.parquet')   # Lê Parquet
```

E o oposto:

```python
df.to_csv('saida.csv')
df.to_excel('saida.xlsx')
df.to_json('saida.json')
df.to_sql('tabela', conexão)
df.to_parquet('saida.parquet')
```

---

## 2. **Criação de DataFrames e Series**

```python
pd.DataFrame(dados)               # De dicionário, lista de listas, etc.
pd.Series([1, 2, 3])              # Cria uma Series
```

---

## 3. **Visualização Inicial de Dados**

```python
df.head()                         # Primeiras 5 linhas
df.tail()                         # Últimas 5 linhas
df.shape                         # (linhas, colunas)
df.info()                         # Informações do DataFrame
df.describe()                     # Estatísticas resumidas
df.columns                        # Lista de colunas
df.index                          # Índice
```

---

## 4. **Seleção e Filtro de Dados**

```python
df['coluna']                      # Seleciona uma coluna
df[['col1', 'col2']]              # Seleciona múltiplas colunas
df.iloc[0]                        # Seleção por posição (linha)
df.loc[0]                         # Seleção por rótulo (linha)
df[df['coluna'] > 10]             # Filtra linhas com condição
```

---

## 5. **Modificação e Manipulação de Dados**

```python
df['nova_col'] = df['col1'] + df['col2']  # Nova coluna
df.rename(columns={'velho': 'novo'})      # Renomear colunas
df.drop('coluna', axis=1)                 # Remover coluna
df.drop(0, axis=0)                        # Remover linha
df.sort_values('coluna')                  # Ordenar por coluna
df.sort_index()                           # Ordenar por índice
df.reset_index()                          # Resetar índice
df.set_index('coluna')                    # Definir índice
```

---

## 6. **Tratamento de Dados Faltantes**

```python
df.isnull()                        # Verifica nulos
df.notnull()                      # Verifica não nulos
df.dropna()                       # Remove linhas com nulos
df.fillna(0)                      # Preenche nulos com valor
df.fillna(method='ffill')         # Preenche com valor anterior
```

---

## 7. **Operações Estatísticas e Matemáticas**

```python
df.mean()                         # Média
df.median()                       # Mediana
df.std()                          # Desvio padrão
df.sum()                          # Soma
df.min(), df.max()                # Mínimo e Máximo
df.corr()                         # Correlação
df.count()                        # Contagem de não nulos
```

---

## 8. **Agrupamento e Agregação**

```python
df.groupby('coluna')              # Agrupa por coluna
df.groupby('coluna').sum()        # Soma por grupo
df.agg(['mean', 'max'])           # Agregações múltiplas
df.pivot_table(values='col', index='A', columns='B')  # Tabela dinâmica
```

---

## 9. **Combinação de DataFrames**

```python
pd.concat([df1, df2])             # Concatenação
pd.merge(df1, df2, on='id')       # Junção por coluna comum
df.join(outra_df)                 # Junção pelo índice
```

---

## 10. **Aplicação de Funções**

```python
df.apply(funcao)                  # Aplica função em colunas ou linhas
df['coluna'].map(lambda x: x*2)   # Transforma valores de uma coluna
df.applymap(lambda x: x*2)        # Aplica em todo o DataFrame
```

---

## 11. **Datas e Horários**

```python
pd.to_datetime(df['data'])        # Converte para datetime
df['data'].dt.year                # Extrai o ano
df['data'].dt.month               # Extrai o mês
df['data'].dt.weekday             # Dia da semana
```

---

## 12. **Strings**

```python
df['coluna'].str.lower()          # Minúsculas
df['coluna'].str.contains('abc')  # Contém string
df['coluna'].str.replace('a', 'b')# Substituição
```

---

## 13. **Outras utilidades úteis**

```python
df.duplicated()                   # Verifica duplicatas
df.drop_duplicates()             # Remove duplicatas
df.sample(5)                      # Amostra aleatória
df.memory_usage()                # Memória ocupada
```

---

## ⚠️ Observação

A biblioteca **Pandas tem centenas de funções**. Acima está um **guia completo com as principais funções de uso prático e profissional**, organizadas por categoria. Muitas delas possuem variações e argumentos adicionais.
