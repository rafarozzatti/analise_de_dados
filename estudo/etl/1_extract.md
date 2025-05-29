### 1. MySQL

**O que você deve alterar:**

* `host`: endereço do servidor MySQL (normalmente `"localhost"` para local).
* `user`: seu usuário do MySQL.
* `password`: sua senha do MySQL.
* `database`: nome do banco de dados onde está sua tabela (exemplo: `"pizzaria_db"`).
* `consulta`: a query SQL que deseja executar.

**Como usar:**

* Tenha o MySQL rodando e com as credenciais corretas.
* Instale o pacote `mysql-connector-python` (`pip install mysql-connector-python`).
* Execute o script para extrair os dados em CSV.

```python
import mysql.connector
import pandas as pd

conexao = mysql.connector.connect(
    host="localhost",        # Altere para o IP/hostname do seu servidor
    user="seu_usuario",      # Seu usuário MySQL
    password="sua_senha",    # Sua senha MySQL
    database="pizzaria_db"   # Banco de dados onde estão os dados
)

consulta = "SELECT * FROM pedidos_pizzaria LIMIT 100;"  # Query SQL para extrair dados

df = pd.read_sql(consulta, conexao)  # Executa query e carrega no DataFrame

df.to_csv("dados_mysql.csv", index=False)  # Salva os dados em CSV

conexao.close()  # Fecha a conexão

print("Dados exportados do MySQL com sucesso!")
```

---

### 2. PostgreSQL

**O que mudar:**

* `host`, `database`, `user`, `password`: credenciais do seu PostgreSQL.
* `consulta`: query para extrair dados.

**Como usar:**

* PostgreSQL deve estar instalado e rodando.
* Instale `psycopg2` com `pip install psycopg2-binary`.

```python
import psycopg2
import pandas as pd

conexao = psycopg2.connect(
    host="localhost",
    database="pizzaria_db",
    user="seu_usuario",
    password="sua_senha"
)

consulta = "SELECT * FROM pedidos_pizzaria LIMIT 100;"
df = pd.read_sql(consulta, conexao)
df.to_csv("dados_postgres.csv", index=False)

conexao.close()
print("Dados exportados do PostgreSQL com sucesso!")
```

---

### 3. SQLite

**O que mudar:**

* `sqlite3.connect`: caminho para o arquivo `.sqlite` do banco local.
* `consulta`: query para extrair dados.

**Como usar:**

* SQLite é um arquivo local, não precisa de servidor.
* Instalação extra geralmente não é necessária (vem com Python).

```python
import sqlite3
import pandas as pd

conexao = sqlite3.connect('pizzaria_db.sqlite')  # Altere para seu arquivo .sqlite

consulta = "SELECT * FROM pedidos_pizzaria LIMIT 100;"
df = pd.read_sql(consulta, conexao)
df.to_csv("dados_sqlite.csv", index=False)

conexao.close()
print("Dados exportados do SQLite com sucesso!")
```

---

### 4. SQL Server

**O que mudar:**

* Na string de conexão, ajuste `SERVER`, `DATABASE`, `UID` (usuário) e `PWD` (senha).
* Instale o driver ODBC adequado para seu sistema.
* `consulta`: query SQL que deseja executar.

**Como usar:**

* Tenha o SQL Server instalado.
* Instale pacote pyodbc (`pip install pyodbc`).
* Instale o ODBC Driver 17 (ou versão compatível).

```python
import pyodbc
import pandas as pd

conexao = pyodbc.connect(
    'DRIVER={ODBC Driver 17 for SQL Server};'
    'SERVER=localhost;'
    'DATABASE=pizzaria_db;'
    'UID=seu_usuario;'
    'PWD=sua_senha'
)

consulta = "SELECT * FROM pedidos_pizzaria"
df = pd.read_sql(consulta, conexao)
df.to_csv("dados_sqlserver.csv", index=False)

conexao.close()
print("Dados exportados do SQL Server com sucesso!")
```

---

### 5. Oracle

**O que mudar:**

* Substitua `'seu_usuario/sua_senha@localhost:1521/xe'` pelo seu usuário, senha e string de conexão Oracle.
* Ajuste a query conforme seu banco Oracle (exemplo usa `ROWNUM` para limitar resultados).

**Como usar:**

* Instale o Oracle Instant Client e `cx_Oracle` (`pip install cx_Oracle`).
* Garanta que o Oracle esteja acessível.

```python
import cx_Oracle
import pandas as pd

conexao = cx_Oracle.connect('seu_usuario/sua_senha@localhost:1521/xe')

consulta = "SELECT * FROM pedidos_pizzaria WHERE ROWNUM <= 100"
df = pd.read_sql(consulta, conexao)
df.to_csv("dados_oracle.csv", index=False)

conexao.close()
print("Dados exportados do Oracle com sucesso!")
```

---

### 6. MongoDB

**O que mudar:**

* String de conexão MongoDB no `MongoClient`.
* `db` e `colecao`: o nome do seu banco e da coleção.

**Como usar:**

* MongoDB deve estar rodando.
* Instale `pymongo` (`pip install pymongo`).

```python
from pymongo import MongoClient
import pandas as pd

cliente = MongoClient("mongodb://localhost:27017/")
db = cliente["pizzaria_db"]          # Seu banco MongoDB
colecao = db["pedidos_pizzaria"]     # Sua coleção

dados = list(colecao.find().limit(100))  # Pega os primeiros 100 documentos
df = pd.json_normalize(dados)            # Transforma para DataFrame Pandas
df.to_csv("dados_mongodb.csv", index=False)

cliente.close()
print("Dados exportados do MongoDB com sucesso!")
```

---

### 7. Excel com filtro

**O que mudar:**

* `caminho_arquivo`: caminho do seu arquivo Excel.
* `nome_aba`: nome ou índice da planilha.
* A query de filtro em `.query(...)` pode ser ajustada conforme quiser.

**Como usar:**

* Instale `pandas` e `openpyxl` (`pip install pandas openpyxl`).
* Execute para filtrar dados e salvar CSV.

```python
import pandas as pd

caminho_arquivo = 'vendas.xlsx'  # Caminho do arquivo Excel
nome_aba = 'Planilha1'           # Nome ou índice da planilha

df = pd.read_excel(caminho_arquivo, sheet_name=nome_aba)

print("Prévia dos dados:")
print(df.head())

print("\nInformações dos dados:")
print(df.info())

# Exemplo: filtro por valor_total maior que 100
df_filtrado = df.query("valor_total > 100")

print("\nDados filtrados (valor_total > 100):")
print(df_filtrado.head())

df_filtrado.to_csv("dados_filtrados.csv", index=False)
print("Arquivo CSV filtrado exportado com sucesso!")
```
---

## 8. Extração de **CSV**

```python
import pandas as pd

caminho_arquivo = 'dados.csv'  # Caminho do arquivo CSV

df = pd.read_csv(caminho_arquivo)

print("Prévia dos dados:")
print(df.head())

print("\nInformações dos dados:")
print(df.info())

# Exemplo: filtro por valor_total maior que 100
df_filtrado = df.query("valor_total > 100")

print("\nDados filtrados (valor_total > 100):")
print(df_filtrado.head())

df_filtrado.to_csv("dados_filtrados_csv.csv", index=False)
print("Arquivo CSV filtrado exportado com sucesso!")
```

**Explicações:**

* `pd.read_csv(...)`: carrega o arquivo CSV para o DataFrame.
* `df.head()`: mostra as primeiras linhas para pré-visualizar os dados.
* `df.info()`: exibe o resumo da estrutura dos dados (colunas, tipos, nulos).
* `df.query(...)`: filtra o DataFrame (nesse caso, apenas onde o valor\_total > 100).
* `df.to_csv(...)`: exporta os dados filtrados para um novo CSV.

---

## 9. Extração de **JSON Local**

```python
import pandas as pd

caminho_arquivo = 'dados.json'  # Caminho do arquivo JSON

df = pd.read_json(caminho_arquivo)

print("Prévia dos dados:")
print(df.head())

print("\nInformações dos dados:")
print(df.info())

# Exemplo: filtro por valor_total maior que 100
df_filtrado = df.query("valor_total > 100")

print("\nDados filtrados (valor_total > 100):")
print(df_filtrado.head())

df_filtrado.to_csv("dados_filtrados_json.csv", index=False)
print("Arquivo CSV filtrado exportado com sucesso!")
```

**Explicações:**

* `pd.read_json(...)`: carrega arquivos JSON locais, assumindo que estejam no formato "flat" (sem estrutura aninhada).
* Ideal para dados exportados de APIs ou sistemas.
* O processo de limpeza e exportação segue o mesmo padrão.

---

## 10. Extração de **API (JSON da Internet)**

```python
import pandas as pd
import requests

url = 'https://jsonplaceholder.typicode.com/posts'  # API de teste

resposta = requests.get(url)

if resposta.status_code == 200:
    dados = resposta.json()
    df = pd.DataFrame(dados)

    print("Prévia dos dados:")
    print(df.head())

    print("\nInformações dos dados:")
    print(df.info())

    # Exemplo: filtro por userId igual a 1
    df_filtrado = df.query("userId == 1")

    print("\nDados filtrados (userId == 1):")
    print(df_filtrado.head())

    df_filtrado.to_csv("dados_filtrados_api.csv", index=False)
    print("Arquivo CSV filtrado exportado com sucesso!")

else:
    print("Erro ao acessar a API:", resposta.status_code)
```

**Explicações:**

* `requests.get(...)`: envia uma requisição HTTP para a URL da API.
* `resposta.json()`: extrai os dados no formato JSON.
* `pd.DataFrame(dados)`: transforma os dados JSON em DataFrame.
* `query(...)`: aplica o filtro diretamente como uma consulta.
* `to_csv(...)`: exporta os dados para uso em Power BI ou Excel.

---

# Conexão com MongoDB e extração de dados em Python (local e remoto)

---

## 1. MongoDB Local

```python
from pymongo import MongoClient
import pandas as pd

# Conecta ao MongoDB rodando localmente na porta padrão 27017
cliente = MongoClient("mongodb://localhost:27017/")

# Seleciona o banco de dados
db = cliente["nome_do_banco"]

# Seleciona a coleção (equivalente à tabela)
colecao = db["nome_da_colecao"]

# Busca até 100 documentos da coleção
dados = list(colecao.find().limit(100))

# Converte os documentos JSON para DataFrame do pandas
df = pd.json_normalize(dados)

# Mostra as primeiras linhas
print(df.head())

# Salva em CSV para análise ou importação no Power BI
df.to_csv("dados_mongodb_local.csv", index=False)

print("Exportação local finalizada!")

# Fecha a conexão
cliente.close()
```

### O que mudar para usar:

* **`localhost`** na string de conexão indica que o MongoDB está na sua máquina local.
* **`nome_do_banco`**: substitua pelo nome do seu banco de dados MongoDB.
* **`nome_da_colecao`**: substitua pela coleção (tabela) que deseja extrair os dados.
* O `limit(100)` é só para trazer poucos dados de exemplo — ajuste ou remova conforme quiser.

---

## 2. MongoDB Remoto (na internet)

```python
from pymongo import MongoClient
import pandas as pd

# Exemplo de string de conexão com usuário e senha para um MongoDB remoto
uri = "mongodb+srv://usuario:senha@cluster0.mongodb.net/nome_do_banco?retryWrites=true&w=majority"

cliente = MongoClient(uri)

db = cliente["nome_do_banco"]
colecao = db["nome_da_colecao"]

dados = list(colecao.find().limit(100))
df = pd.json_normalize(dados)

print(df.head())

df.to_csv("dados_mongodb_remoto.csv", index=False)

print("Exportação remota finalizada!")

cliente.close()
```

### O que mudar para usar:

* **`usuario` e `senha`**: coloque seu usuário e senha do MongoDB Atlas (ou outro serviço remoto).
* **`cluster0.mongodb.net`**: substitua pelo endereço do seu cluster remoto (normalmente fornecido no dashboard do serviço).
* **`nome_do_banco` e `nome_da_colecao`**: igual ao local, escolha seu banco e coleção.
* A string de conexão `mongodb+srv://` é o padrão para conexões seguras em nuvem.

---

### Dicas importantes:

* Antes de rodar, **instale as dependências:**

```bash
pip install pymongo pandas
```

* Para o MongoDB remoto, garanta que seu IP está autorizado no dashboard do serviço (ex: MongoDB Atlas).
* Se a coleção tiver muitos dados, considere paginar ou filtrar os dados na consulta para não sobrecarregar a memória.
