# Estrutura Condicional `if/else` em Python

A estrutura `if/else` permite **escolher entre dois caminhos**: um será executado se a condição for verdadeira (`if`), e o outro se for falsa (`else`).

---

## Exemplo com saldo e saque

```python
saldo = 2000.0
saque = float(input('Informe o valor do saque: '))

# Se saldo for maior ou igual, imprime 'Realizando saque!'
if saldo >= saque:
    print('Realizando saque!')
# Se não, imprime 'Saldo insuficiente!'
else:
    print('Saldo insuficiente!')
```

---

### Explicação:

* `if condição:` → Bloco executado **se a condição for verdadeira**.
* `else:` → Bloco executado **se a condição for falsa**.
* Ambos os blocos precisam estar **indentados** corretamente.
* `input()` lê uma string, por isso usamos `float()` para converter para número.

---

### Exemplo de entrada e saída 1:

**Entrada:**

```
Informe o valor do saque: 1500
```

**Saída:**

```
Realizando saque!
```

---

### Exemplo de entrada e saída 2:

**Entrada:**

```
Informe o valor do saque: 2500
```

**Saída:**

```
Saldo insuficiente!
```
