# Métodos da Classe String em Python

Strings (`str`) possuem diversos métodos úteis para manipulação de texto.

---

## Método `.upper()`

Transforma todas as letras em **maiúsculas**.

```python
nome = 'raFAel'
print(nome.upper())
```

**Saída:**

```
RAFAEL
```

---

## Método `.lower()`

Transforma todas as letras em **minúsculas**.

```python
print(nome.lower())
```

**Saída:**

```
rafael
```

---

## Método `.title()`

Deixa **apenas a primeira letra de cada palavra em maiúscula**.

```python
print(nome.title())
```

**Saída:**

```
Rafael
```

---

## Remoção de espaços em branco

Dado o texto:

```python
texto = ' Olá, mundo! '
print(texto + '.')
```

**Saída:**

```
 Olá, mundo! .
```

---

### Método `.strip()`

Remove os espaços em branco **do começo e do fim**.

```python
print(texto.strip() + '.')
```

**Saída:**

```
Olá, mundo!.
```

---

### Método `.rstrip()`

Remove espaços em branco **do lado direito (final)**.

```python
print(texto.rstrip() + '.')
```

**Saída:**

```
 Olá, mundo!.
```

---

### Método `.lstrip()`

Remove espaços em branco **do lado esquerdo (início)**.

```python
print(texto.lstrip() + '.')
```

**Saída:**

```
Olá, mundo! .
```

---

## Centralização de texto com `.center()`

Dado:

```python
menu = 'Python'
```

Centraliza a string em um espaço de 14 caracteres, preenchendo os lados com espaços:

```python
print(menu.center(14))
```

**Saída:**

```
    Python    
```

---

Centraliza e usa o caractere `#` para preencher os espaços:

```python
print(menu.center(14, '#'))
```

**Saída:**

```
####Python####
```

---

## Método `.join()`

Une cada caractere da string com o separador especificado:

```python
print('.'.join(menu))
```

**Saída:**

```
P.y.t.h.o.n
```
