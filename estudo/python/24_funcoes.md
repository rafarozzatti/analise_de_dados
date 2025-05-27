# 📘 Funções em Python

Funções são blocos de código reutilizáveis. Permitem organizar o código em partes menores e mais legíveis. Em Python, funções são definidas com a palavra-chave `def`.

---

## ✅ Criando Funções Simples

```python
def exibir_mensagem():
    print('Olá mundo!')
```

> 📌 Essa função **não recebe argumentos** e apenas imprime uma mensagem.

```python
exibir_mensagem()
```

**Saída:**

```
Olá mundo!
```

---

## 📥 Funções com Argumentos

```python
def exibir_mensagem_2(nome):
    print(f'Seja bem vindo {nome}!')
```

> 📌 Essa função **recebe um argumento** chamado `nome`.

```python
exibir_mensagem_2(nome='Rafael')
```

**Saída:**

```
Seja bem vindo Rafael!
```

---

## 🧾 Argumentos Opcionais (com valor padrão)

```python
def exibir_mensagem_3(nome='Anônimo'):
    print(f'Seja bem vindo {nome}!')
```

> 📌 Se nenhum valor for passado, o padrão será `'Anônimo'`.

```python
exibir_mensagem_3()
exibir_mensagem_3(nome='Enzo')
```

**Saída:**

```
Seja bem vindo Anônimo!
Seja bem vindo Enzo!
```

---

## ➕ `return`: Retornando valores

```python
def calcular_total(numeros):
    return sum(numeros)
```

> 📌 Essa função retorna a soma de uma lista de números.

```python
print(calcular_total([10, 20, 34]))
```

**Saída:**

```
64
```

---

```python
def retorna_antecessor_sucessor(numero):
    antecessor = numero - 1
    sucessor = numero + 1
    return antecessor, sucessor
```

> 📌 Retorna uma **tupla** com o antecessor e o sucessor.

```python
print(retorna_antecessor_sucessor(10))
```

**Saída:**

```
(9, 11)
```

---

## 🌟 `*args` e `**kwargs`: Argumentos variáveis

```python
def exibir_poema(data_extenso, *args, **kwargs):
    texto = '\n'.join(args)
    meta_dados = '\n'.join([f'{chave.title()}: {valor}' for chave, valor in kwargs.items()])
    mensagem = f'{data_extenso}\n\n{texto}\n\n{meta_dados}'
    print(mensagem)
```

> 📌 `*args` recebe vários textos (linhas do poema), e `**kwargs` recebe metadados como `autor` e `ano`.

```python
exibir_poema(
    "Terça-feira, 01 de Abril de 2025",
    "The Zen of Python",
    "Beautiful is better than ugly.",
    "Explicit is better than implicit.",
    autor="Tim Peters",
    ano=1999,
)
```

**Saída:**

```
Terça-feira, 01 de Abril de 2025

The Zen of Python
Beautiful is better than ugly.
Explicit is better than implicit.

Autor: Tim Peters
Ano: 1999
```

---

## 🧭 Parâmetros posicionais obrigatórios com `/`

```python
def criar_carro(modelo, ano, placa, /, marca, motor, combustivel):
    print(modelo, ano, placa, marca, motor, combustivel)
```

> 📌 Os parâmetros antes da `/` (modelo, ano, placa) **devem ser passados por posição**.

```python
criar_carro('Palio', 1999, 'ABC-1234', marca='Fiat', motor='1.0', combustivel='Gasolina')
```

**Saída:**

```
Palio 1999 ABC-1234 Fiat 1.0 Gasolina
```

```python
# ERRO: modelo, ano e placa não podem ser passados por nome
criar_carro(modelo='Palio', ano=1999, placa='ABC-1234', marca='Fiat', motor='1.0', combustivel='Gasolina')
```

**Erro:**

```
TypeError: criar_carro() got some positional-only arguments passed as keyword arguments
```

---

## 🧭 Parâmetros nomeados obrigatórios com `*`

```python
def criar_carro(*, modelo, ano, placa, marca, motor, combustivel):
    print(modelo, ano, placa, marca, motor, combustivel)
```

> 📌 Os parâmetros após o `*` **devem ser passados com nome**.

```python
criar_carro(modelo='Palio', ano=1999, placa='ABC-1234', marca='Fiat', motor='1.0', combustivel='Gasolina')
```

**Saída:**

```
Palio 1999 ABC-1234 Fiat 1.0 Gasolina
```

```python
# ERRO: argumentos sem nome
criar_carro('Palio', 1999, 'ABC-1234', marca='Fiat', motor='1.0', combustivel='Gasolina')
```

**Erro:**

```
TypeError: criar_carro() takes 0 positional arguments but 3 were given
```

---

## 🌍 Usando `global` para alterar variáveis fora da função

```python
salario = 2000

def salario_bonus(bonus):
    global salario
    salario += bonus
    return salario
```

> 📌 A variável `salario` é global e pode ser modificada de dentro da função.

```python
print(salario_bonus(500))
```

**Saída:**

```
2500
```

---

## 📦 `**kwargs` com dicionário (desempacotamento)

```python
def salvar_carro(marca, modelo, ano, placa):
    print(f'Carro inserido com sucesso! {marca}/{modelo}/{ano}/{placa}')
```

```python
salvar_carro('Fiat', 'Palio', 1999, 'ABC-1234')
salvar_carro(marca='Fiat', modelo='Palio', ano=1999, placa='ABC-1234')
salvar_carro(**{'marca': 'Fiat', 'modelo': 'Palio', 'ano': 1999, 'placa': 'ABC-1234'})
```

**Saída:**

```
Carro inserido com sucesso! Fiat/Palio/1999/ABC-1234
Carro inserido com sucesso! Fiat/Palio/1999/ABC-1234
Carro inserido com sucesso! Fiat/Palio/1999/ABC-1234
```
