## Aprender Atualizações e Operadores de Modificação no MongoDB

Você pode atualizar documentos existentes no MongoDB usando comandos como `updateOne`, `updateMany` e operadores de modificação como `$set`, `$inc`, `$rename` e outros.

Todos os exemplos utilizam a coleção `livros`.

---

### 1. Operador `$set`

Usado para definir ou atualizar um valor de campo.

```js
db.livros.updateOne(
  { titulo: "Dom Casmurro" },
  { $set: { editora: "Editora Brasil" } }
)
```

---

### 2. Operador `$inc`

Incrementa (ou decrementa) um valor numérico.

```js
db.livros.updateOne(
  { titulo: "Dom Casmurro" },
  { $inc: { edicao: 1 } }
)
```

---

### 3. Operador `$rename`

Renomeia um campo existente.

```js
db.livros.updateMany(
  {},
  { $rename: { "ano": "ano_publicacao" } }
)
```

---

### 4. Operador `$unset`

Remove um campo de um documento.

```js
db.livros.updateMany(
  {},
  { $unset: { edicao: "" } }
)
```

---

### 5. Atualizar Múltiplos Documentos

```js
db.livros.updateMany(
  { autor: "Machado de Assis" },
  { $set: { classico: true } }
)
```
