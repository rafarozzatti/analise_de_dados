# 📃 Decoradores, Iteradores e Geradores em Python

---

## ✨ Decoradores

Decoradores são funções que **recebem outra função como argumento** e retornam uma nova função com funcionalidades adicionais.

### ✏️ Decorador básico

```python
def meu_decorador(funcao):
    def envelope():
        print('Faz algo antes de executar')
        funcao()
        print('Faz algo depois de executar')
    return envelope

@meu_decorador
def ola_mundo():
    print('Olá mundo!')

ola_mundo()
```

**Saída:**

```
Faz algo antes de executar
Olá mundo!
Faz algo depois de executar
```

### 📂 Decorador com argumentos

```python
def meu_decorador(funcao):
    def envelope(*args, **kwargs):
        print('Faz algo antes de executar')
        funcao(*args, **kwargs)
        print('Faz algo depois de executar')
    return envelope

@meu_decorador
def ola_mundo(nome):
    print(f'Olá mundo {nome}!')

ola_mundo('Rafael')
```

**Saída:**

```
Faz algo antes de executar
Olá mundo Rafael!
Faz algo depois de executar
```

### ↩️ Decorador que retorna valor

```python
def meu_decorador(funcao):
    def envelope(*args, **kwargs):
        print('Faz algo antes de executar')
        resultado = funcao(*args, **kwargs)
        print('Faz algo depois de executar')
        return resultado
    return envelope

@meu_decorador
def ola_mundo(nome, outr_argumento):
    print(f'Olá mundo {nome}!')
    return nome.upper()

resultado = ola_mundo('João', 1000)
print(resultado)
```

**Saída:**

```
Faz algo antes de executar
Olá mundo João!
Faz algo depois de executar
JOÃO
```

### 📲 Usando `functools.wraps`

Preserva o nome e docstring da função original:

```python
import functools

def meu_decorador(funcao):
    @functools.wraps(funcao)
    def envelope(*args, **kwargs):
        funcao(*args, **kwargs)
    return envelope

@meu_decorador
def ola_mundo(nome, outr_argumento):
    print(f'Olá mundo {nome}!')

print(ola_mundo.__name__)
```

**Saída:**

```
ola_mundo
```

---

## ⟳ Iteradores

Um **iterador** é um objeto que implementa os métodos `__iter__()` e `__next__()`.

### 🔄 Exemplo de iterador personalizado

```python
class MeuIterador:
    def __init__(self, numeros: list[int]):
        self.numeros = numeros
        self.cont = 0

    def __iter__(self):
        return self

    def __next__(self):
        try:
            numero = self.numeros[self.cont]
            self.cont += 1
            return numero * 2
        except IndexError:
            raise StopIteration

for i in MeuIterador(numeros=[1, 2, 3]):
    print(i)
```

**Saída:**

```
2
4
6
```

---

## ✨ Geradores

Geradores permitem criar iteradores de forma mais simples com `yield`.

### ⚛️ Exemplo de gerador

```python
def meu_gerador(numeros: list[int]):
    for numero in numeros:
        yield numero * 2

for i in meu_gerador(numeros=[1, 2, 3]):
    print(i)
```

**Saída:**

```
2
4
6
```

---

## 📊 Função retornando função

Python permite retornar uma função de dentro de outra.

```python
def calcular(operacao):
    def somar(a, b):
        return a + b
    
    def subtrair(a, b):
        return a - b

    if operacao == '+':
        return somar
    else:
        return subtrair

resultado = calcular('+')(1, 3)
print(resultado)
```

**Saída:**

```
4
```
