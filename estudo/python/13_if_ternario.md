# Condicional Ternária em Python (`if` ternário)

A expressão **condicional ternária** em Python é uma forma **resumida** de escrever um `if/else` simples.
Ela é usada quando queremos **atribuir um valor a uma variável com base em uma condição**.

---

## Exemplo com saque e saldo

```python
saldo = 2000
saque = 500

# Se saldo for maior ou igual ao saque, status = 'Sucesso', senão = 'Falha'
status = 'Sucesso' if saldo >= saque else 'Falha'

print(f'{status} ao realizar o saque!')
```

---

### Explicação:

A sintaxe do if ternário é:

```python
<variável> = <valor_se_verdadeiro> if <condição> else <valor_se_falso>
```

No exemplo:

* Se `saldo >= saque`, então `status` recebe `'Sucesso'`
* Caso contrário, `status` recebe `'Falha'`

Essa forma é **mais compacta** que um `if/else` tradicional, e muito útil para **atribuições simples**.

---

### Exemplo de saída 1:

**Configuração:**

```python
saldo = 2000
saque = 500
```

**Saída:**

```
Sucesso ao realizar o saque!
```

---

### Exemplo de saída 2:

**Configuração:**

```python
saldo = 400
saque = 500
```

**Saída:**

```
Falha ao realizar o saque!
```
