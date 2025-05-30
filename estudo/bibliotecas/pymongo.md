# 🐍 Integração de Python com MongoDB usando PyMongo

## ✅ Pré-requisitos

* Python instalado
* MongoDB instalado e em execução local
* VSCode (ou outro editor)
* Terminal funcional

---

## 📦 Passo 1: Instalar o PyMongo

```bash
pip install pymongo
```

---

## 🔌 Passo 2: Conectar ao MongoDB

```python
from pymongo import MongoClient

# Conectar ao servidor MongoDB local
client = pymongo.MongoClient("mongodb://localhost:27017/")

print("Conectado com sucesso!")
```

✅ **Saída esperada:**

```
Conectado com sucesso!
```

---

## 🗄️ Passo 3: Criar banco de dados e coleção

```python
# Criar ou acessar um banco de dados
db = client["meu_banco"]

# Criar ou acessar uma coleção (como uma tabela)
colecao = db["clientes"]

print("Banco de dados e coleção criados!")
```

✅ **Saída esperada:**

```
Banco de dados e coleção criados!
```

---

## 📥 Passo 4: Inserir documentos

### Inserir um único documento

```python
documento = {
    "nome": "João Silva",
    "idade": 28,
    "cidade": "São Paulo"
}

colecao.insert_one(documento)
print("Documento inserido com sucesso!")
```

✅ **Saída esperada:**

```
Documento inserido com sucesso!
```

### Inserir vários documentos

```python
documentos = [
    {"nome": "Maria Oliveira", "idade": 34, "cidade": "Rio de Janeiro"},
    {"nome": "Carlos Souza", "idade": 22, "cidade": "Belo Horizonte"},
    {"nome": "Ana Costa", "idade": 45, "cidade": "Curitiba"}
]

colecao.insert_many(documentos)
print("Vários documentos inseridos com sucesso!")
```

✅ **Saída esperada:**

```
Vários documentos inseridos com sucesso!
```

---

## 🔍 Passo 5: Consultar documentos

### Consultar um documento específico

```python
documento_encontrado = colecao.find_one({"nome": "João Silva"})
print("Documento encontrado:", documento_encontrado)
```

✅ **Saída esperada (exemplo):**

```
Documento encontrado: {'_id': ObjectId('...'), 'nome': 'João Silva', 'idade': 28, 'cidade': 'São Paulo'}
```

### Consultar todos os documentos

```python
for documento in colecao.find():
    print(documento)
```

✅ **Saída esperada (exemplo):**

```
{'_id': ObjectId('...'), 'nome': 'João Silva', 'idade': 28, 'cidade': 'São Paulo'}
{'_id': ObjectId('...'), 'nome': 'Maria Oliveira', 'idade': 34, 'cidade': 'Rio de Janeiro'}
{'_id': ObjectId('...'), 'nome': 'Carlos Souza', 'idade': 22, 'cidade': 'Belo Horizonte'}
{'_id': ObjectId('...'), 'nome': 'Ana Costa', 'idade': 45, 'cidade': 'Curitiba'}
```

---

## ✏️ Passo 6: Atualizar documentos

### Atualizar um único documento

```python
colecao.update_one(
    {"nome": "João Silva"},          
    {"$set": {"idade": 29}}          
)

documento_atualizado = colecao.find_one({"nome": "João Silva"})
print("Documento atualizado:", documento_atualizado)
```

✅ **Saída esperada:**

```
Documento atualizado: {'_id': ObjectId('...'), 'nome': 'João Silva', 'idade': 29, 'cidade': 'São Paulo'}
```

### Atualizar vários documentos

```python
colecao.update_many(
    {"cidade": "Rio de Janeiro"},
    {"$set": {"estado": "RJ"}}
)

print("Vários documentos atualizados com sucesso!")
```

✅ **Saída esperada:**

```
Vários documentos atualizados com sucesso!
```

---

## ❌ Passo 7: Deletar documentos

### Deletar um único documento

```python
colecao.delete_one({"nome": "João Silva"})

documento_deletado = colecao.find_one({"nome": "João Silva"})
print("Documento após deleção:", documento_deletado)
```

✅ **Saída esperada:**

```
Documento após deleção: None
```

### Deletar vários documentos

```python
colecao.delete_many({"idade": {"$lt": 30}})
print("Documentos com idade < 30 foram deletados.")
```

✅ **Saída esperada (exemplo):**

```
Documentos com idade < 30 foram deletados.
```

---

## 🧼 (Opcional) Limpar a coleção para testes

```python
colecao.delete_many({})
print("Coleção limpa!")
```

✅ **Saída esperada:**

```
Coleção limpa!
```

---

## 🧾 Código completo final (tudo junto):

```python
import pymongo

# Conexão
client = pymongo.MongoClient("mongodb://localhost:27017/")
print("Conectado com sucesso!")

# Banco e coleção
db = client["meu_banco"]
colecao = db["clientes"]
print("Banco de dados e coleção criados!")

# Inserir documentos
colecao.insert_one({"nome": "João Silva", "idade": 28, "cidade": "São Paulo"})
colecao.insert_many([
    {"nome": "Maria Oliveira", "idade": 34, "cidade": "Rio de Janeiro"},
    {"nome": "Carlos Souza", "idade": 22, "cidade": "Belo Horizonte"},
    {"nome": "Ana Costa", "idade": 45, "cidade": "Curitiba"}
])
print("Documentos inseridos com sucesso!")

# Consultas
print("Consulta por nome:")
print(colecao.find_one({"nome": "João Silva"}))

print("Todos os documentos:")
for doc in colecao.find():
    print(doc)

# Atualização
colecao.update_one({"nome": "João Silva"}, {"$set": {"idade": 29}})
print("Após atualizar João Silva:")
print(colecao.find_one({"nome": "João Silva"}))

colecao.update_many({"cidade": "Rio de Janeiro"}, {"$set": {"estado": "RJ"}})
print("Vários documentos atualizados com sucesso!")

# Deleções
colecao.delete_one({"nome": "João Silva"})
print("Após deletar João Silva:")
print(colecao.find_one({"nome": "João Silva"}))

colecao.delete_many({"idade": {"$lt": 30}})
print("Documentos com idade < 30 foram deletados.")

# Limpar tudo
colecao.delete_many({})
print("Coleção limpa!")
```
