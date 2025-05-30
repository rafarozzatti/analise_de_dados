## Conhecer o Framework de Agregação (Aggregation) no MongoDB

O **framework de agregação** é usado para processar dados e retornar resultados transformados. Ele permite fazer operações como somar, agrupar, filtrar e ordenar documentos.

O principal comando é `aggregate()`.

Todos os exemplos usam a coleção `livros`.

---

### 1. `$match`

Filtra documentos (como um `find`).

```js
db.livros.aggregate([
  { $match: { autor: "Machado de Assis" } }
])
```

---

### 2. `$group`

Agrupa documentos e calcula valores agregados.

```js
db.livros.aggregate([
  {
    $group: {
      _id: "$autor",
      totalLivros: { $sum: 1 }
    }
  }
])
```

---

### 3. `$sort`

Ordena os documentos.

```js
db.livros.aggregate([
  { $sort: { ano: -1 } } // -1 = decrescente, 1 = crescente
])
```

---

### 4. `$project`

Escolhe quais campos mostrar ou renomear.

```js
db.livros.aggregate([
  {
    $project: {
      titulo: 1,
      autor: 1,
      ano: 1,
      _id: 0
    }
  }
])
```

---

### 5. Pipeline completo (Exemplo)

```js
db.livros.aggregate([
  { $match: { ano: { $gte: 1900 } } },
  { $group: { _id: "$autor", total: { $sum: 1 } } },
  { $sort: { total: -1 } }
])
```
