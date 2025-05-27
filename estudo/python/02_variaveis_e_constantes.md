# Variáveis

Em Python, variáveis são usadas para armazenar valores. O conteúdo de uma variável **pode ser alterado** durante a execução do programa.

```python
nome = 'Rafael'
idade = 26
print(nome, idade)
```

**Saída:**

```
Rafael 26
```

A variável `nome` pode ser alterada:

```python
nome = 'Enzo'
print(nome, idade)
```

**Saída:**

```
Enzo 26
```

---

# Constantes

Em Python, **não existem constantes reais**, mas por convenção, usamos **letras maiúsculas** para indicar que uma variável **não deve ser alterada**.

```python
STATES = ['SP', 'RJ', 'SC', 'RS']
print(STATES)
```

**Saída:**

```
['SP', 'RJ', 'SC', 'RS']
```

> ⚠️ Mesmo sendo uma "constante", ainda é possível alterar o conteúdo se quisermos, então o respeito à imutabilidade depende do programador.
