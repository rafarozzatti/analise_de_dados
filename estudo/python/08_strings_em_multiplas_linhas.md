# Strings em Múltiplas Linhas em Python

Em Python, é possível criar strings com várias linhas usando **três aspas simples (`'''`) ou três aspas duplas (`"""`)**. Isso é útil para textos longos, mensagens formatadas ou textos com quebras de linha.

---

## Exemplo com f-string e múltiplas linhas

```python
nome = 'Rafael'

print(f'''Olá, meu nome é {nome}.
Eu estou aprendendo Python''')
```

### Explicação:

* `f'''...'''`: permite usar **f-string** com múltiplas linhas.
* As quebras de linha no texto são **mantidas automaticamente**.
* O valor da variável `nome` é **interpolado normalmente**.

---

### Saída:

```
Olá, meu nome é Rafael.
Eu estou aprendendo Python
```
