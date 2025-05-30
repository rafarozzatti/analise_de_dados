## Estudar Filtros e Operadores de Consulta no MongoDB

Os filtros servem para encontrar dados específicos em uma coleção. Podemos usá-los com operadores para fazer comparações e combinar condições.

Todos os exemplos abaixo usam a coleção `livros`.

---

### 1. Filtros Simples

#### 🔹 Buscar por igualdade

```js
db.livros.find({ autor: "Machado de Assis" })
```

#### 🔹 Buscar por valor numérico

```js
db.livros.find({ ano: 1899 })
```

---

### 2. Operadores de Comparação

* `$eq`: igual (implícito, como vimos acima)
* `$gt`: maior que
* `$lt`: menor que
* `$gte`: maior ou igual
* `$lte`: menor ou igual
* `$ne`: diferente

#### 🔹 Exemplo: livros publicados após 1900

```js
db.livros.find({ ano: { $gt: 1900 } })
```

#### 🔹 Exemplo: livros diferentes de 1899

```js
db.livros.find({ ano: { $ne: 1899 } })
```

---

### 3. Operadores Lógicos

* `$and`: todas as condições devem ser verdadeiras
* `$or`: pelo menos uma condição deve ser verdadeira

#### 🔹 Exemplo: livros de Machado publicados antes de 1900

```js
db.livros.find({
  $and: [
    { autor: "Machado de Assis" },
    { ano: { $lt: 1900 } }
  ]
})
```

#### 🔹 Exemplo: livros de Machado ou publicados em 1890

```js
db.livros.find({
  $or: [
    { autor: "Machado de Assis" },
    { ano: 1890 }
  ]
})
```

---

### 4. Operador `$in`

Usado para buscar um valor dentro de uma lista.

#### 🔹 Exemplo: livros de autores específicos

```js
db.livros.find({ autor: { $in: ["Machado de Assis", "Drummond"] } })
```
