# Estrutura Condicional `if` Aninhado em Python

Um `if` aninhado é quando você **coloca uma estrutura `if` dentro de outra**. Isso permite fazer **verificações mais específicas**, conforme o fluxo da lógica.

---

## Exemplo com tipo de conta e saque

```python
conta_normal = True
conta_universitaria = False
saldo = 2000
saque = 500

# Se a conta for normal
if conta_normal:
    # Se o saldo for suficiente
    if saldo >= saque:
        print('Saque realizado com sucesso!')
    # Se o saldo não for suficiente
    else:
        print('Saque realizado com uso do cheque especial!')
# Se a conta for universitária
elif conta_universitaria:
    # Se o saldo for suficiente
    if saldo >= saque:
        print('Saque realizado com sucesso!')
    # Se o saldo não for suficiente
    else:
        print('Saldo insuficiente!')
```

---

### Explicação:

* O primeiro `if` verifica o **tipo da conta**.
* Dentro dele, há outro `if` para verificar o **saldo disponível**.
* Esse processo é chamado de **aninhamento**: uma verificação depende da anterior.
* Se a conta for **normal**, o saque pode ser feito mesmo sem saldo (com cheque especial).
* Se a conta for **universitária**, só pode sacar se tiver saldo suficiente.

---

### Exemplo de Saída 1:

**Configuração:**

```python
conta_normal = True
saldo = 2000
saque = 500
```

**Saída:**

```
Saque realizado com sucesso!
```

---

### Exemplo de Saída 2:

**Configuração:**

```python
conta_normal = True
saldo = 300
saque = 500
```

**Saída:**

```
Saque realizado com uso do cheque especial!
```

---

### Exemplo de Saída 3:

**Configuração:**

```python
conta_normal = False
conta_universitaria = True
saldo = 300
saque = 500
```

**Saída:**

```
Saldo insuficiente!
```
