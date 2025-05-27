# Usando `range()` com `for` em Python

A função `range()` é muito usada em conjunto com o laço `for` para repetir ações um número definido de vezes ou para iterar sobre uma sequência de números.

---

## Exemplo: percorrendo números com `for` e `range()`

```python
# Percorre os números de 0 até 10 (inclusive)
for numero in range(0, 11):
    # Imprime os números na mesma linha, separados por espaço
    print(numero, end=' ')

print()  # Pula uma linha para separar as saídas

# Percorre os números de 0 até 50, pulando de 5 em 5
for numero in range(0, 51, 5):
    # Imprime os números na mesma linha, separados por espaço
    print(numero, end=' ')
```

---

### Explicação:

* `range(0, 11)` gera números de 0 até 10 (o último número é exclusivo).
* `range(0, 51, 5)` gera números de 0 até 50, pulando de 5 em 5 (0, 5, 10, ..., 50).
* O argumento `end=' '` no `print` evita pular linha e separa os números por espaço.
* `print()` é usado para pular linha entre os dois blocos.

---

### Saída:

```
0 1 2 3 4 5 6 7 8 9 10 
0 5 10 15 20 25 30 35 40 45 50 
```
