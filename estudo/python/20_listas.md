# Listas em Python

## Introdução

As listas são estruturas de dados que armazenam uma sequência de elementos. Elas podem conter qualquer tipo de dado (strings, inteiros, listas, etc.) e são mutáveis, ou seja, podem ser modificadas após a criação.

## Criação de Listas

```python
frutas = ['laranja', 'maça', 'uva']
print(frutas)

frutas = []
print(frutas)

letras = list('python')
print(letras)

numeros = list(range(10))
print(numeros)

carro = ['Ferrari', 'F8', 4200000, 2020, 2900, 'São Paulo', True]
print(carro)
```

## Acessando Itens por Índice

```python
frutas = ['maça', 'laranja', 'uva', 'pera']
print(frutas[0])      # maça
print(frutas[2])      # uva
print(frutas[-1])     # pera
print(frutas[-3])     # laranja
```

## Listas Aninhadas

```python
matriz = [
    [1, 'a', 2],
    ['b', 3, 4],
    [6, 5, 'c']
]

print(matriz[0])        # [1, 'a', 2]
print(matriz[0][0])     # 1
print(matriz[0][-1])    # 2
print(matriz[-1][-1])   # 'c'
```

## Fatiamento

```python
lista = ['p', 'y', 't', 'h', 'o', 'n']

print(lista[2:])     # ['t', 'h', 'o', 'n']
print(lista[:2])     # ['p', 'y']
print(lista[1:3])    # ['y', 't']
print(lista[0:3:2])  # ['p', 't']
print(lista[::])     # ['p', 'y', 't', 'h', 'o', 'n']
print(lista[::-1])   # ['n', 'o', 'h', 't', 'y', 'p']
```

## Percorrendo Listas

```python
carros = ['gol', 'celta', 'palio']
for carro in carros:
    print(carro)
```

### Com `enumerate()`

```python
for indice, carro in enumerate(carros):
    print(f'{indice}: {carro}')
```

## Compreensão de Listas

```python
# Forma tradicional
numeros = [1, 30, 21, 2, 9, 65, 34]
pares = []
for numero in numeros:
    if numero % 2 == 0:
        pares.append(numero)

# Com compreensão
pares = [numero for numero in numeros if numero % 2 == 0]
```

## Métodos de Manipulação

### `append()`

```python
lista = []
lista.append(1)
lista.append('Python')
lista.append([40, 30, 20])
print(lista)
```

### `clear()`

```python
lista.clear()
print(lista)
```

### `copy()`

```python
nova_lista = lista.copy()
print(nova_lista)
```

### `count()`

```python
cores = ['vermelho', 'azul', 'verde', 'azul']
print(cores.count('vermelho'))
print(cores.count('azul'))
print(cores.count('verde'))
```

### `extend()`

```python
linguagens = ['python', 'js', 'c']
linguagens.extend(['java', 'csharp'])
print(linguagens)
```

### `index()`

```python
print(linguagens.index('java'))
print(linguagens.index('python'))
```

### `pop()`

```python
linguagens.pop()     # Remove o último
linguagens.pop(0)    # Remove o primeiro
```

### `remove()`

```python
linguagens.remove('c')
print(linguagens)
```

### `reverse()`

```python
linguagens.reverse()
print(linguagens)
```

### `sort()`

```python
linguagens.sort()                        # Ordem alfabética crescente
linguagens.sort(reverse=True)           # Ordem alfabética decrescente
linguagens.sort(key=lambda x: len(x))   # Por tamanho crescente
linguagens.sort(key=lambda x: len(x), reverse=True)  # Por tamanho decrescente
```

### `len()`

```python
print(len(linguagens))
```

### `sorted()`

```python
print(sorted(linguagens, key=lambda x: len(x)))
print(sorted(linguagens, key=lambda x: len(x), reverse=True))
```
