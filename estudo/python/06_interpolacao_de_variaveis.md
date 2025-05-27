# Interpolação de Variáveis em Python

Interpolação é o processo de **inserir variáveis dentro de uma string**. Em Python, a forma mais moderna e recomendada de fazer isso é usando **f-strings** (`f''`), disponíveis a partir do Python 3.6.

---

## Exemplo com f-string

```python
nome = 'Rafael'
idade = 26
profissao = 'Programador'
linguagem = 'Python'
saldo = 45.475

print(f'Nome: {nome}\nIdade: {idade}\nSaldo: {saldo:.2f}')
```

### Explicação:

* `f'...'`: ativa a interpolação.
* `{nome}`: insere o valor da variável `nome`.
* `\n`: quebra de linha.
* `{saldo:.2f}`: formata o número com **duas casas decimais**.

---

### Saída:

```
Nome: Rafael
Idade: 26
Saldo: 45.48
```

> 🔎 O valor `45.475` é **arredondado** para `45.48` ao ser formatado com `.2f`.
