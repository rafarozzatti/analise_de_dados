# Laço `while` em Python

O laço `while` executa repetidamente um bloco de código **enquanto uma condição for verdadeira**. É útil quando você não sabe exatamente quantas vezes o código deve rodar, mas sabe a condição para continuar.

---

## Exemplo: menu de opções com `while`

```python
opcao = 1

# Enquanto a opção for diferente de 0, o laço continua
while opcao != 0:
    opcao = int(input('[1] Sacar \n[2] Extrato \n[0] Sair \nOpção: '))

    if opcao == 1:
        print('Sacando...')
    elif opcao == 2:
        print('Exibindo o extrato...')

print('Obrigado por usar nosso sistema bancário, até logo!')
```

---

### Explicação:

* `while opcao != 0:` significa que o código dentro do laço vai repetir **enquanto a opção for diferente de 0**.
* O programa lê a opção do usuário a cada ciclo.
* Dependendo da opção, executa uma ação:

  * `1` imprime “Sacando...”
  * `2` imprime “Exibindo o extrato...”
* Quando o usuário digita `0`, o laço termina e o programa imprime a mensagem de despedida.

---

### Exemplo de entrada e saída:

**Entrada:**

```
[1] Sacar 
[2] Extrato 
[0] Sair 
Opção: 1
Sacando...
[1] Sacar 
[2] Extrato 
[0] Sair 
Opção: 2
Exibindo o extrato...
[1] Sacar 
[2] Extrato 
[0] Sair 
Opção: 0
Obrigado por usar nosso sistema bancário, até logo!
```
