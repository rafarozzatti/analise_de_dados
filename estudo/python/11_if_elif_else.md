# Estrutura Condicional `if / elif / else` em Python

A estrutura `if / elif / else` permite executar **blocos de código diferentes**, dependendo de várias condições.

É útil quando temos **mais de duas possibilidades** a considerar.

---

## Exemplo com menu de opções

```python
opcao = int(input('Informe uma opção:\n[1] Sacar\n[2] Extrato: '))

# Se a opção for 1, executa o saque
if opcao == 1:
    valor = float(input('Informe a quantia para saque: '))
# Se a opção for 2, exibe o extrato
elif opcao == 2:
    print('Exibindo o extrato...')
# Se a opção não for 1 nem 2, mostra mensagem de erro
else:
    print('Opção inválida')
```

---

### Explicação:

* `input()` lê a entrada do usuário como string. Usamos `int()` para converter e comparar com números.
* `\n` dentro da string quebra a linha e deixa o menu mais organizado.
* `if`: executa se `opcao == 1`.
* `elif`: executa se `opcao == 2`.
* `else`: executa se a opção for diferente de 1 ou 2.

---

### Exemplo de entrada e saída 1:

**Entrada:**

```
Informe uma opção:
[1] Sacar
[2] Extrato: 1
Informe a quantia para saque: 300
```

**Saída:**

```
(nenhuma mensagem, mas o valor foi capturado)
```

---

### Exemplo de entrada e saída 2:

**Entrada:**

```
Informe uma opção:
[1] Sacar
[2] Extrato: 2
```

**Saída:**

```
Exibindo o extrato...
```

---

### Exemplo de entrada e saída 3:

**Entrada:**

```
Informe uma opção:
[1] Sacar
[2] Extrato: 9
```

**Saída:**

```
Opção inválida
```
