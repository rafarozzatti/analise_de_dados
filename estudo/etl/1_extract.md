## 1. CSV

```python
# 1. Importar a biblioteca
import pandas as pd

# 2. Ler (extrair) o arquivo CSV
df = pd.read_csv("dados.csv")

# Mostrar informações do DataFrame original (antes do filtro)
df.info()
print(df.head())

# 3. Filtrar os dados (ex: só vendas com valor_total > 100)
df_filtrado = df.query("valor_total > 100")

# Mostrar informações do DataFrame filtrado
df_filtrado.info()
print(df_filtrado.head())

# 4. Salvar o novo DataFrame filtrado em um novo arquivo CSV
df_filtrado.to_csv("dados_filtrados_csv.csv", index=False)
```

**O que mudar:**

* `"dados.csv"` → arquivo CSV que você quer ler.
* A condição dentro do `query()` → filtro desejado para os dados.
* `"dados_filtrados_csv.csv"` → nome do arquivo CSV de saída.

---

## 2. Excel

```python
# 1. Importar a biblioteca
import pandas as pd

# 2. Ler (extrair) o arquivo Excel
df = pd.read_excel("dados.xlsx")

# Mostrar informações do DataFrame original (antes do filtro)
df.info()
print(df.head())

# 3. Filtrar os dados (ex: só vendas com valor_total > 100)
df_filtrado = df.query("valor_total > 100")

# Mostrar informações do DataFrame filtrado
df_filtrado.info()
print(df_filtrado.head())

# 4. Salvar o novo DataFrame filtrado em um arquivo Excel
df_filtrado.to_excel("dados_filtrados_excel.xlsx", index=False)
```

**O que mudar:**

* `"dados.xlsx"` → arquivo Excel de entrada.
* Condição do `query()`.
* `"dados_filtrados_excel.xlsx"` → arquivo Excel de saída.

---

## 3. JSON (local)

```python
# 1. Importar a biblioteca
import pandas as pd

# 2. Ler (extrair) o arquivo JSON local
df = pd.read_json("dados.json")

# Mostrar informações do DataFrame original (antes do filtro)
df.info()
print(df.head())

# 3. Filtrar os dados (ex: só vendas com valor_total > 100)
df_filtrado = df.query("valor_total > 100")

# Mostrar informações do DataFrame filtrado
df_filtrado.info()
print(df_filtrado.head())

# 4. Salvar o novo DataFrame filtrado em arquivo JSON
df_filtrado.to_json("dados_filtrados_json.json", orient="records")
```

**O que mudar:**

* `"dados.json"` → arquivo JSON de entrada.
* Condição do `query()`.
* `"dados_filtrados_json.json"` → arquivo JSON de saída.

---

## 4. CSV da internet (exemplo API com CSV)

```python
# 1. Importar a biblioteca
import pandas as pd

# 2. Ler (extrair) arquivo CSV diretamente da URL
url = "https://exemplo.com/dados.csv"
df = pd.read_csv(url)

# Mostrar informações do DataFrame original (antes do filtro)
df.info()
print(df.head())

# 3. Filtrar os dados (ex: só vendas com valor_total > 100)
df_filtrado = df.query("valor_total > 100")

# Mostrar informações do DataFrame filtrado
df_filtrado.info()
print(df_filtrado.head())

# 4. Salvar o novo DataFrame filtrado em CSV localmente
df_filtrado.to_csv("dados_filtrados_api.csv", index=False)
```

**O que mudar:**

* `url` → URL real do arquivo CSV.
* Condição do `query()`.
* `"dados_filtrados_api.csv"` → arquivo CSV de saída.

---

## 5. MySQL

```python
# 1. Importar bibliotecas
import pandas as pd
import pymysql

# 2. Criar conexão com o banco MySQL
con = pymysql.connect(
    host='localhost',
    user='usuario',
    password='senha',
    database='meu_banco'
)

# 3. Escrever consulta SQL (query)
consulta = """
SELECT * FROM vendas
WHERE valor_total > 100
"""

# 4. Extrair dados com pandas usando a conexão e a query
df = pd.read_sql(consulta, con)

# Mostrar informações do DataFrame
df.info()

# Mostrar as primeiras linhas para inspeção rápida
print(df.head())

# 5. Salvar resultado em CSV
df.to_csv("mysql_filtrado.csv", index=False)
```

**O que mudar:**

* `'localhost'`, `'usuario'`, `'senha'`, `'meu_banco'` → dados da sua conexão MySQL.
* `consulta` → SQL que você quer executar (nome da tabela, colunas e filtro).
* `"mysql_filtrado.csv"` → nome do arquivo CSV para salvar os dados extraídos.

---

## 6. PostgreSQL

```python
# 1. Importar bibliotecas
import pandas as pd
import psycopg2

# 2. Criar conexão com PostgreSQL
con = psycopg2.connect(
    host='localhost',
    user='usuario',
    password='senha',
    dbname='meu_banco'
)

# 3. Escrever consulta SQL
consulta = """
SELECT * FROM vendas
WHERE valor_total > 100
"""

# 4. Extrair dados com pandas usando a conexão e a query
df = pd.read_sql(consulta, con)

# Mostrar informações do DataFrame
df.info()

# Mostrar as primeiras linhas para inspeção rápida
print(df.head())

# 5. Salvar resultado em CSV
df.to_csv("postgres_filtrado.csv", index=False)
```

**O que mudar:**

* `'localhost'`, `'usuario'`, `'senha'`, `'meu_banco'` → dados da conexão PostgreSQL.
* `consulta` → SQL que você quer executar.
* `"postgres_filtrado.csv"` → nome do arquivo CSV para salvar.

---

## 7. SQLite

```python
# 1. Importar bibliotecas
import pandas as pd
import sqlite3

# 2. Criar conexão com SQLite
con = sqlite3.connect("meubanco.db")

# 3. Escrever consulta SQL
consulta = """
SELECT * FROM vendas
WHERE valor_total > 100
"""

# 4. Extrair dados com pandas usando a conexão e a query
df = pd.read_sql(consulta, con)

# Mostrar informações do DataFrame
df.info()

# Mostrar as primeiras linhas para inspeção rápida
print(df.head())

# 5. Salvar resultado em CSV
df.to_csv("sqlite_filtrado.csv", index=False)
```

**O que mudar:**

* `"meubanco.db"` → caminho do arquivo do banco SQLite.
* `consulta` → SQL que deseja executar.
* `"sqlite_filtrado.csv"` → nome do arquivo CSV para salvar.

---

## 8. SQL Server

```python
# 1. Importar bibliotecas
import pandas as pd
import pyodbc

# 2. Criar conexão com SQL Server
con = pyodbc.connect(
    'DRIVER={SQL Server};SERVER=localhost;DATABASE=meu_banco;UID=usuario;PWD=senha'
)

# 3. Escrever consulta SQL
consulta = """
SELECT * FROM vendas
WHERE valor_total > 100
"""

# 4. Extrair dados com pandas usando a conexão e a query
df = pd.read_sql(consulta, con)

# Mostrar informações do DataFrame
df.info()

# Mostrar as primeiras linhas para inspeção rápida
print(df.head())

# 5. Salvar resultado em CSV
df.to_csv("sqlserver_filtrado.csv", index=False)
```

**O que mudar:**

* String de conexão `'DRIVER=...;SERVER=...;DATABASE=...;UID=...;PWD=...'` com seus dados.
* `consulta` → SQL a ser executada.
* `"sqlserver_filtrado.csv"` → nome do arquivo CSV para salvar.

---

## 9. Oracle

```python
# 1. Importar bibliotecas
import pandas as pd
import cx_Oracle

# 2. Criar conexão com Oracle
con = cx_Oracle.connect("usuario/senha@localhost:1521/XE")

# 3. Escrever consulta SQL
consulta = """
SELECT * FROM vendas
WHERE valor_total > 100
"""

# 4. Extrair dados com pandas usando a conexão e a query
df = pd.read_sql(consulta, con)

# Mostrar informações do DataFrame
df.info()

# Mostrar as primeiras linhas para inspeção rápida
print(df.head())

# 5. Salvar resultado em CSV
df.to_csv("oracle_filtrado.csv", index=False)
```

**O que mudar:**

* `"usuario/senha@localhost:1521/XE"` → string de conexão Oracle com seus dados.
* `consulta` → SQL desejada.
* `"oracle_filtrado.csv"` → nome do arquivo CSV para salvar.

---

## 10. MongoDB (local)

```python
# 1. Importar bibliotecas
import pandas as pd
from pymongo import MongoClient

# 2. Criar conexão com MongoDB local
client = MongoClient("mongodb://localhost:27017/")
db = client["meu_banco"]
colecao = db["vendas"]

# 3. Buscar dados filtrando com query MongoDB
dados = list(colecao.find({ "valor_total": { "$gt": 100 } }))

# 4. Criar DataFrame a partir dos dados
df = pd.DataFrame(dados)

# Mostrar informações do DataFrame
df.info()

# Mostrar as primeiras linhas para inspeção rápida
print(df.head())

# 5. Salvar resultado em JSON
df.to_json("mongodb_local.json", orient="records")
```

**O que mudar:**

* `"mongodb://localhost:27017/"` → string de conexão do MongoDB local.
* `"meu_banco"` e `"vendas"` → banco e coleção.
* Query MongoDB no `find()` para filtrar os dados.
* `"mongodb_local.json"` → nome do arquivo JSON para salvar.

---

## 11. MongoDB (remoto)

```python
# 1. Importar bibliotecas
import pandas as pd
from pymongo import MongoClient

# 2. Criar conexão com MongoDB remoto
client = MongoClient("mongodb+srv://usuario:senha@cluster.mongodb.net/?retryWrites=true&w=majority")
db = client["meu_banco"]
colecao = db["vendas"]

# 3. Buscar dados filtrando com query MongoDB
dados = list(colecao.find({ "valor_total": { "$gt": 100 } }))

# 4. Criar DataFrame a partir dos dados
df = pd.DataFrame(dados)

# Mostrar informações do DataFrame
df.info()

# Mostrar as primeiras linhas para inspeção rápida
print(df.head())

# 5. Salvar resultado em JSON
df.to_json("mongodb_remoto.json", orient="records")
```

**O que mudar:**

* `"mongodb+srv://usuario:senha@cluster.mongodb.net/..."` → string de conexão do MongoDB remoto.
* `"meu_banco"` e `"vendas"` → banco e coleção.
* Query MongoDB no `find()`.
* `"mongodb_remoto.json"` → nome do arquivo JSON para salvar.
