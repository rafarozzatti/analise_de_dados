# Conversão de Tipos em Python

A **conversão de tipos** (type casting) é usada para transformar valores de um tipo para outro, como de `str` para `int`, ou de `int` para `float`.

---

## Float para Int

Converte um número decimal (`float`) para inteiro (`int`), **descartando a parte decimal**.

```python
print(int(1.0))
print(type(int(1.0)))
```

**Saída:**

```
1
<class 'int'>
```

---

## String para Int

Converte uma string que representa um número inteiro para o tipo `int`.
A string **precisa conter apenas dígitos válidos**, senão ocorre erro.

```python
print(int('10'))
print(type(int('10')))
```

**Saída:**

```
10
<class 'int'>
```

---

## Float para String

Converte um número decimal (`float`) para texto (`str`).
O valor passa a ser tratado como uma cadeia de caracteres.

```python
print(str(10.10))
print(type(str(10.10)))
```

**Saída:**

```
10.1
<class 'str'>
```

---

## Int para String

Converte um número inteiro para texto (`str`).
Muito útil para concatenar números com outras strings.

```python
print(str(10))
print(type(str(10)))
```

**Saída:**

```
10
<class 'str'>
```

---

## String para Float

Converte uma string com número decimal para tipo `float`.
A string **deve estar no formato correto**, com ponto (`.`) e não vírgula.

```python
print(float('10.10'))
print(type(float('10.10')))
```

**Saída:**

```
10.1
<class 'float'>
```

---

## Int para Float

Converte um número inteiro (`int`) para decimal (`float`), **adicionando `.0`**.

```python
print(float(10))
print(type(float(10)))
```

**Saída:**

```
10.0
<class 'float'>
```
