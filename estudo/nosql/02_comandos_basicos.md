## Aprender os Comandos Básicos em MongoDB (CRUD)

Neste documento, vamos aprender os comandos básicos do MongoDB, conhecidos como **CRUD**, que são:

* **C**reate: Criar dados (inserir documentos);
* **R**ead: Ler dados (consultar documentos);
* **U**pdate: Atualizar dados (modificar documentos);
* **D**elete: Excluir dados (remover documentos).

Todos os comandos abaixo usam uma coleção chamada `livros`.

---

### 1. Criar dados

#### 🔹 Inserir um único documento

```js
db.livros.insertOne({ titulo: "Dom Casmurro", autor: "Machado de Assis", ano: 1899 })
```

#### 🔹 Inserir vários documentos

```js
db.livros.insertMany([
  { titulo: "O Cortiço", autor: "Aluísio Azevedo", ano: 1890 },
  { titulo: "Memórias Póstumas", autor: "Machado de Assis", ano: 1881 }
])
```

---

### 2. Ler dados

#### 🔹 Mostrar todos os documentos

```js
db.livros.find()
```

#### 🔹 Mostrar um único documento

```js
db.livros.findOne({ autor: "Machado de Assis" })
```

---

### 3. Atualizar dados

#### 🔹 Atualizar o primeiro documento que encontrar

```js
db.livros.updateOne(
  { titulo: "Dom Casmurro" },
  { $set: { ano: 1900 } }
)
```

#### 🔹 Atualizar vários documentos

```js
db.livros.updateMany(
  { autor: "Machado de Assis" },
  { $set: { classico: true } }
)
```

---

### 4. Excluir dados

#### 🔹 Excluir um único documento

```js
db.livros.deleteOne({ titulo: "O Cortiço" })
```

#### 🔹 Excluir vários documentos

```js
db.livros.deleteMany({ autor: "Desconhecido" })
```
