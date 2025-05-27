# 🧮 Conjuntos (Sets) em Python

Conjuntos são estruturas de dados que armazenam **valores únicos e não ordenados**. São ideais para eliminar duplicatas, verificar relações entre coleções e realizar operações matemáticas (união, interseção, etc.).

---

## ✅ Criando conjuntos

```python
numeros = set([1, 2, 3, 1, 3, 4])
print(numeros)
```

**Saída:**

```
{1, 2, 3, 4}
```

> Cria um conjunto a partir de uma lista, eliminando os valores repetidos automaticamente.

```python
letras = set('abacaxi')
print(letras)
```

**Saída (ordem pode variar):**

```
{'c', 'i', 'a', 'x', 'b'}
```

> Transforma a string em um conjunto de letras únicas (sem ordem).

```python
carros = set(('palio', 'gol', 'celta', 'palio'))
print(carros)
```

**Saída:**

```
{'gol', 'palio', 'celta'}
```

> Cria um conjunto a partir de uma tupla; valores duplicados são removidos.

```python
linguagens = {'python', 'java', 'python'}
print(linguagens)
```

**Saída:**

```
{'java', 'python'}
```

> Também é possível criar conjuntos diretamente com chaves `{}`. Elementos duplicados são ignorados.

---

## 🔍 Acessando elementos

```python
numeros = {1, 2, 3, 4}
numeros = list(numeros)
print(numeros[0])
```

**Saída (valor pode variar):**

```
1
```

> Conjuntos não são indexáveis diretamente. É necessário converter para lista para acessar por índice.

---

## 🔁 Percorrendo conjuntos

```python
carros = {'gol', 'celta', 'palio'}
for carro in carros:
    print(carro)
```

**Saída (ordem pode variar):**

```
gol
celta
palio
```

> A ordem dos elementos não é garantida. Mas é possível iterar normalmente com `for`.

```python
for indice, carro in enumerate(carros):
    print(f'{indice}: {carro}')
```

**Saída (ordem pode variar):**

```
0: gol
1: celta
2: palio
```

> `enumerate()` pode ser usado para numerar os itens mesmo sem ordem fixa.

---

## ⚙️ Operações com conjuntos

### União – `union()`

```python
conjunto_a = {1, 2}
conjunto_b = {3, 4}
print(conjunto_a.union(conjunto_b))
```

**Saída:**

```
{1, 2, 3, 4}
```

> Junta os elementos dos dois conjuntos (sem repetir).

---

### Interseção – `intersection()`

```python
conjunto_a = {1, 2, 3}
conjunto_b = {2, 3, 4}
print(conjunto_a.intersection(conjunto_b))
```

**Saída:**

```
{2, 3}
```

> Mostra os elementos que estão em ambos os conjuntos.

---

### Diferença – `difference()`

```python
print(conjunto_a.difference(conjunto_b))
print(conjunto_b.difference(conjunto_a))
```

**Saída:**

```
{1}
{4}
```

> Mostra os elementos que estão em um conjunto e **não** no outro.

---

### Diferença simétrica – `symmetric_difference()`

```python
print(conjunto_a.symmetric_difference(conjunto_b))
```

**Saída:**

```
{1, 4}
```

> Mostra os elementos que estão em **um ou outro**, mas **não nos dois**.

---

## 🔗 Subconjuntos e superconjuntos

```python
conjunto_a = {1, 2, 3}
conjunto_b = {4, 1, 2, 5, 6, 3}

print(conjunto_a.issubset(conjunto_b))     # True
print(conjunto_b.issubset(conjunto_a))     # False
print(conjunto_a.issuperset(conjunto_b))   # False
print(conjunto_b.issuperset(conjunto_a))   # True
```

> `issubset()` verifica se um conjunto está contido no outro.
> `issuperset()` verifica se um conjunto **contém** o outro.

---

## 🚫 Conjuntos disjuntos – `isdisjoint()`

```python
conjunto_a = {1, 2, 3, 4, 5}
conjunto_b = {6, 7, 8, 9}
conjunto_c = {1, 0}

print(conjunto_a.isdisjoint(conjunto_b))  # True
print(conjunto_a.isdisjoint(conjunto_c))  # False
```

> Retorna `True` se os conjuntos **não têm nenhum item em comum**.

---

## 🔧 Métodos úteis

### `add()` – Adicionar elementos

```python
sorteio = {1, 23}
sorteio.add(25)
sorteio.add(42)
sorteio.add(25)
print(sorteio)
```

**Saída (ordem pode variar):**

```
{1, 42, 23, 25}
```

> Adiciona um elemento ao conjunto, mas **não insere se já existir**.

---

### `clear()` – Limpar o conjunto

```python
sorteio.clear()
print(sorteio)
```

**Saída:**

```
set()
```

> Remove todos os elementos do conjunto.

---

### `copy()` – Copiar conjunto

```python
sorteio = {1, 23}
copia = sorteio.copy()
print(copia)
```

**Saída:**

```
{1, 23}
```

> Cria uma cópia independente do conjunto.

---

## 🗑️ Remoção de elementos

### `discard()` – Remove **sem erro**

```python
numeros = {1, 2, 3, 4, 5}
numeros.discard(1)
numeros.discard(45)
print(numeros)
```

**Saída:**

```
{2, 3, 4, 5}
```

> Remove o item se existir. Se não existir, **não dá erro**.

---

### `pop()` – Remove item aleatório

```python
numeros = {1, 2, 3, 4}
numeros.pop()
numeros.pop()
print(numeros)
```

**Saída (valores variam):**

```
{3, 4}
```

> Remove e retorna um elemento **aleatório** do conjunto.

---

### `remove()` – Remove item **com erro**

```python
numeros = {0, 1, 2, 3}
numeros.remove(0)
print(numeros)
numeros.remove(45)
```

**Saída:**

```
{1, 2, 3}
Traceback (most recent call last):
  ...
KeyError: 45
```

> Remove o item, mas se não existir, **gera erro** (`KeyError`).

---

## 📏 Outras operações

### `len()` – Tamanho do conjunto

```python
numeros = {1, 2, 3, 4}
print(len(numeros))
```

**Saída:**

```
4
```

> Conta quantos elementos há no conjunto.

---

### Verificar existência

```python
print(1 in numeros)
print(10 in numeros)
```

**Saída:**

```
True
False
```

> Verifica se um valor está presente no conjunto.
