# Laço `while True` em Python

O laço `while True` cria um loop **infinito**, que só termina quando uma condição interna usa a palavra-chave `break` para sair do laço. Isso é útil quando você quer que o programa continue rodando até que uma condição específica seja satisfeita.

---

## Exemplo: ler números até digitar 10

```python
# Loop infinito
while True:
    numero = int(input('Informe um número: '))

    # Sai do laço se o número for 10
    if numero == 10:
        break

    print(numero)
```

---

### Explicação:

* `while True:` cria um laço que nunca para sozinho.
* Dentro do laço, o programa lê um número do usuário.
* Se o número for 10, o comando `break` interrompe o laço.
* Caso contrário, o número digitado é impresso.
* Assim, o programa fica pedindo números até que o usuário digite 10.

---

### Exemplo de entrada e saída:

**Entrada:**

```
Informe um número: 3
3
Informe um número: 7
7
Informe um número: 10
```

**Saída:**

```
3
7
```

(O programa termina após digitar 10.)
