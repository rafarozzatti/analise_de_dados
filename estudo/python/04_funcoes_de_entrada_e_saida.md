# Funções de Entrada e Saída em Python

Python usa as funções `input()` para entrada de dados e `print()` para saída de dados. Vamos entender como cada uma funciona.

---

## Entrada com `input()`

A função `input()` **lê dados digitados pelo usuário** e sempre retorna uma `string`.

```python
nome = input('Digite o seu nome: ')
idade = input('Informe sua idade: ')
```

Se o usuário digitar:

```
Digite o seu nome: Rafael
Informe sua idade: 26
```

As variáveis ficarão assim:

* `nome` = `'Rafael'` (tipo: `str`)
* `idade` = `'26'` (tipo: `str`)

---

## Saída com `print()`

A função `print()` **exibe informações na tela**. Pode receber vários argumentos e personalizar a forma de exibição com `sep` e `end`.

### Exibindo nome e idade:

```python
print(nome, idade)
```

**Saída:**

```
Rafael 26
```

---

### Usando o argumento `end`

O `end` define **o que será impresso no final da linha**. Por padrão, é uma quebra de linha (`\n`).

```python
print(nome, idade, end='...\n')
```

**Saída:**

```
Rafael 26...
```

---

### Usando o argumento `sep`

O `sep` define o **separador entre os argumentos**. Por padrão, é um espaço (`' '`).

```python
print(nome, idade, sep='#')
```

**Saída:**

```
Rafael#26
```

---

### Combinando `sep` e `end`

É possível usar os dois juntos:

```python
print(nome, idade, sep='#', end='...\n')
```

**Saída:**

```
Rafael#26...
```
