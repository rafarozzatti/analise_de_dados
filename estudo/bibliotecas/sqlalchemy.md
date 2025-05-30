A biblioteca **SQLAlchemy** é uma poderosa ferramenta para trabalhar com **bancos de dados relacionais** em Python. Ela permite interagir com bancos como **SQLite, MySQL, PostgreSQL, SQL Server, Oracle** e outros, de forma mais **estruturada, segura e orientada a objetos**, usando uma camada de **abstração** sobre SQL puro.

---

### 📌 O que é o SQLAlchemy?

É uma biblioteca de **ORM (Object Relational Mapper)** que também fornece uma **Core SQL Expression Language**.
Ou seja, o SQLAlchemy tem **duas formas principais de uso**:

1. **SQLAlchemy Core** (baixo nível): você escreve comandos SQL com Python.
2. **SQLAlchemy ORM** (alto nível): você trabalha com **classes Python que representam tabelas**.

---

### 🔧 Instalação

```bash
pip install sqlalchemy
```

---

### 🧠 Conceitos Básicos

* **Engine**: conecta ao banco.
* **Connection**: uma conexão ativa.
* **MetaData**: guarda informações sobre tabelas.
* **Table**: representa uma tabela.
* **Column**: representa uma coluna.
* **Session**: no ORM, é usada para consultar e salvar objetos no banco.

---

## ✅ Parte 1: SQLAlchemy Core (baixo nível)

### 📌 Criação de Engine (conexão com banco)

```python
from sqlalchemy import create_engine

# Cria a conexão com o banco de dados SQLite (arquivo chamado 'meubanco.db')
engine = create_engine("sqlite:///meubanco.db")

# Exemplo comentado para conexão com MySQL (você precisaria instalar 'pymysql')
# engine = create_engine("mysql+pymysql://usuario:senha@localhost:3306/nomedobanco")
```

### 📌 Criando Tabela

```python
from sqlalchemy import MetaData, Table, Column, Integer, String

# Objeto que armazena o "esquema" do banco de dados (as tabelas, colunas etc.)
metadata = MetaData()

# Cria a tabela 'usuarios' com colunas: id, nome e idade
usuarios = Table(
    "usuarios", metadata,
    Column("id", Integer, primary_key=True),  # Coluna 'id' do tipo inteiro e chave primária
    Column("nome", String),                   # Coluna 'nome' do tipo string
    Column("idade", Integer)                  # Coluna 'idade' do tipo inteiro
)

# Cria fisicamente as tabelas no banco de dados (caso ainda não existam)
metadata.create_all(engine)
```

### 📌 Inserindo Dados

```python
# Insere um novo registro usando o SQLAlchemy Core
with engine.connect() as conn:
    # Cria um comando INSERT para a tabela 'usuarios'
    ins = usuarios.insert().values(nome="João", idade=30)

    # Executa o comando
    conn.execute(ins)
```

### 📌 Consultando Dados

```python
from sqlalchemy import select

# Faz uma consulta SELECT usando SQLAlchemy Core
with engine.connect() as conn:
    # Cria a instrução SELECT * FROM usuarios
    sel = select(usuarios)

    # Executa a consulta
    result = conn.execute(sel)

    # Itera sobre os resultados e imprime cada linha
    for row in result:
        print(row)  # Exemplo de saída: (1, 'João', 30)
```

---

## ✅ Parte 2: SQLAlchemy ORM (alto nível)

### 📌 Base do ORM

```python
from sqlalchemy.orm import declarative_base

# Cria a classe base do ORM (usada para definir modelos como classes Python)
Base = declarative_base()
```

### 📌 Criando Classe-Tabela

```python
from sqlalchemy import Column, Integer, String

# Define a classe 'Usuario' que representa a tabela 'usuarios' no banco
class Usuario(Base):
    __tablename__ = 'usuarios'  # Nome da tabela no banco

    # Define as colunas como atributos da classe
    id = Column(Integer, primary_key=True)  # Coluna 'id' como chave primária
    nome = Column(String)                   # Coluna 'nome'
    idade = Column(Integer)                 # Coluna 'idade'
```

### 📌 Criando Banco e Tabela

```python
# Cria a tabela 'usuarios' no banco de dados (se não existir)
Base.metadata.create_all(engine)
```

### 📌 Criando Sessão

```python
from sqlalchemy.orm import sessionmaker

# Cria uma fábrica de sessões conectada ao banco
Session = sessionmaker(bind=engine)

# Cria uma instância de sessão (conexão com o banco)
session = Session()
```

### 📌 Inserindo com ORM

```python
# Cria um novo objeto 'Usuario' (registro na tabela)
novo = Usuario(nome="Maria", idade=25)

# Adiciona o objeto à sessão (ainda não salva no banco)
session.add(novo)

# Salva (confirma) as alterações no banco
session.commit()

```

### 📌 Consultando com ORM

```python
# Consulta todos os registros da tabela 'usuarios'
usuarios = session.query(Usuario).all()

# Itera e imprime nome e idade de cada usuário
for u in usuarios:
    print(u.nome, u.idade)
    # Exemplo de saída: Maria 25
```

### 📌 Atualizando

```python
# Busca o primeiro usuário com nome "Maria"
u = session.query(Usuario).filter_by(nome="Maria").first()

# Altera a idade para 26
u.idade = 26

# Salva a alteração no banco
session.commit()
```

### 📌 Deletando

```python
# Remove o objeto 'u' da sessão (registro será excluído)
session.delete(u)

# Confirma a exclusão no banco
session.commit()
```

---

## 🧰 Lista de Funções / Componentes Importantes

### 📦 SQLAlchemy Core

| Função/Classe                                  | Descrição                   |
| ---------------------------------------------- | --------------------------- |
| `create_engine()`                              | Cria conexão com o banco    |
| `MetaData()`                                   | Armazena esquema de tabelas |
| `Table()`                                      | Define uma tabela           |
| `Column()`                                     | Define uma coluna           |
| `Integer`, `String`, etc.                      | Tipos de dados              |
| `select()`, `insert()`, `update()`, `delete()` | Comandos SQL                |
| `text()`                                       | Escreve SQL puro            |
| `bindparam()`                                  | Cria parâmetros SQL seguros |
| `and_()`, `or_()`                              | Composição de filtros       |
| `between()`, `like()`                          | Filtros avançados           |

---

### 🧠 SQLAlchemy ORM

| Função/Classe                | Descrição                                     |
| ---------------------------- | --------------------------------------------- |
| `declarative_base()`         | Cria a base para as classes ORM               |
| `Base.metadata.create_all()` | Cria tabelas no banco                         |
| `sessionmaker()`             | Cria sessões de banco                         |
| `Session()`                  | Permite adicionar, consultar e salvar objetos |
| `query()`                    | Consulta objetos                              |
| `filter()`, `filter_by()`    | Aplica filtros nas consultas                  |
| `add()`, `add_all()`         | Adiciona objetos                              |
| `commit()`                   | Salva as mudanças                             |
| `rollback()`                 | Desfaz mudanças pendentes                     |
| `delete()`                   | Remove um objeto                              |
| `first()`, `all()`           | Retorna resultados da query                   |

---

### 🧪 Recursos Avançados

| Recurso                     | Descrição                                  |
| --------------------------- | ------------------------------------------ |
| `relationship()`            | Relacionamentos entre tabelas (1\:N, N\:M) |
| `backref`, `back_populates` | Cria links bidirecionais                   |
| `ForeignKey()`              | Define chaves estrangeiras                 |
| `joinedload()`              | Carregamento de relacionamentos            |
| `hybrid_property`           | Propriedades calculadas                    |
| `mapeamento com herança`    | ORM com herança entre classes              |

---

## ✅ Exemplo Completo (ORM com SQLite)

```python
from sqlalchemy import create_engine, Column, Integer, String
from sqlalchemy.orm import declarative_base, sessionmaker

# Cria a base do ORM
Base = declarative_base()

# Define a classe que representa a tabela 'usuarios'
class Usuario(Base):
    __tablename__ = 'usuarios'
    id = Column(Integer, primary_key=True)  # Coluna 'id'
    nome = Column(String)                   # Coluna 'nome'
    idade = Column(Integer)                 # Coluna 'idade'

# Cria a engine de conexão com o SQLite
engine = create_engine("sqlite:///meubanco.db")

# Cria a tabela no banco (se necessário)
Base.metadata.create_all(engine)

# Cria uma fábrica de sessões
Session = sessionmaker(bind=engine)
session = Session()

# ---------- INSERIR ----------
# Cria um novo usuário e insere no banco
novo = Usuario(nome="João", idade=28)
session.add(novo)
session.commit()

# ---------- CONSULTAR ----------
# Busca todos os usuários
usuarios = session.query(Usuario).all()

# Exibe os resultados
for u in usuarios:
    print(u.id, u.nome, u.idade)
    # Exemplo de saída: 1 João 28
```
