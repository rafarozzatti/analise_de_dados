# Fatiamento de Strings em Python

Fatiar (ou **slice**) uma string significa **acessar partes dela** usando colchetes `[]` e índices. A sintaxe básica é:

```python
string[início:fim:passo]
```

---

## Exemplo base

```python
nome = 'Rafael Pires'
```

---

## `nome[0]` – Caractere no índice 0

```python
print(nome[0])
```

**Saída:**

```
R
```

---

## `nome[:6]` – Do início até o índice 5

```python
print(nome[:6])
```

**Saída:**

```
Rafael
```

> Vai do índice `0` até o `5` (o `6` não é incluído).

---

## `nome[8:]` – Do índice 8 até o fim

```python
print(nome[8:])
```

**Saída:**

```
ires
```

---

## `nome[2:6]` – Do índice 2 até o 5

```python
print(nome[2:6])
```

**Saída:**

```
fael
```

---

## `nome[2:6:2]` – Do índice 2 ao 5, pulando de 2 em 2

```python
print(nome[2:6:2])
```

**Saída:**

```
fl
```

> Pega o índice `2` e `4`, pulando um a cada passo.

---

## `nome[:]` – Cópia completa da string

```python
print(nome[:])
```

**Saída:**

```
Rafael Pires
```

---

## `nome[::-1]` – String invertida

```python
print(nome[::-1])
```

**Saída:**

```
seriP leafaR
```

> O passo `-1` inverte a ordem dos caracteres.
