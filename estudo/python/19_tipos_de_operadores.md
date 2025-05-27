# Tipos de Operadores em Python

Em Python, os operadores permitem realizar cálculos, comparações, verificar conteúdo, entre outras operações. Abaixo está uma organização com exemplos e explicações.

---

## 1. Ordem de Precedência dos Operadores

1. Parêntesis `()`
2. Expoentes `**`
3. Multiplicação e divisão `*`, `/`, `//`, `%`
4. Soma e subtração `+`, `-`

```python
print(10 - 5 * 2)         # 0
print((10 - 5) * 2)       # 10
print(10 ** 2 * 2)        # 200
print(10 ** (2 * 2))      # 10000
print(10 / 2 * 4)         # 20.0
```

---

## 2. Operadores Aritméticos

```python
print(1 + 1)       # Adição: 2
print(10 - 2)      # Subtração: 8
print(4 * 3)       # Multiplicação: 12
print(12 / 3)      # Divisão: 4.0
print(12 // 2)     # Divisão inteira: 6
print(10 % 3)      # Módulo (resto): 1
print(2 ** 3)      # Exponenciação: 8
```

---

## 3. Operadores de Atribuição

```python
saldo = 500
print(saldo)       # 500

saldo += 200
print(saldo)       # 700

saldo -= 100
print(saldo)       # 600

saldo *= 2
print(saldo)       # 1200

saldo /= 5
print(saldo)       # 240.0

saldo //= 5
print(saldo)       # 48.0

saldo %= 480
print(saldo)       # 48.0

saldo = 80
saldo **= 2
print(saldo)       # 6400
```

---

## 4. Operadores de Comparacao

```python
saldo = 450
saque = 200

print(saldo == saque)  # False
print(saldo != saque)  # True
print(saldo > saque)   # True
print(saldo >= saque)  # True
print(saldo < saque)   # False
print(saldo <= saque)  # False
```

---

## 5. Operadores de Pertencimento (`in`)

```python
curso = 'Curso de Python'
frutas = ['laranja', 'uva', 'limão']
saques = [1500, 100]

print('Python' in curso)    # True
print('maça' in frutas)     # False
print(200 in saques)        # False
```

---

## 6. Operadores de Identidade (`is`, `is not`)

```python
curso = 'Curso de Python'
nome_curso = curso
saldo, limite = 200, 200

print(curso is nome_curso)       # True
print(curso is not nome_curso)   # False
print(saldo is limite)           # True
```

---

## 7. Operador `not`

```python
print(1000 > 1500)        # False
print(not 1000 > 1500)    # True

contatos_emergencia = []
print(contatos_emergencia)        # []
print(not contatos_emergencia)    # True

print('saque 1500;')       # saque 1500;
print(not 'saque 1500;')   # False

print('')       # (vazio)
print(not '')   # True
```

---

## 8. Operadores Lógicos (`and`, `or`)

```python
saldo = 1000
saque = 200
limite = 100

print(saldo >= saque and saque <= limite)  # False
print(saldo >= saque or saque <= limite)   # True
```
