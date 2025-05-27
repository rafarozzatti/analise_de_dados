# Tuplas em Python: Exemplos e Explicações

## Criação de Tuplas

```python
frutas = ('laranja', 'pera', 'uva',)
print(frutas)

letras = tuple('python')
print(letras)

numeros = tuple([1, 2, 3, 4])
print(numeros)

pais = ('Brasil',)
print(pais)
```

## Acesso a Elementos da Tupla

```python
frutas = ('maça', 'laranja', 'uva', 'pera',)
print(frutas[0])      # Primeiro elemento
print(frutas[2])      # Terceiro elemento
print(frutas[-1])     # Último elemento
print(frutas[-3])     # Terceiro elemento a partir do final
```

## Tuplas Aninhadas (Matriz)

```python
matriz = (
    (1, 'a', 2),
    ('b', 3, 4),
    (6, 5, 'c')
)

print(matriz[0])         # Primeira linha da matriz
print(matriz[0][0])      # Primeiro elemento da primeira linha
print(matriz[0][-1])     # Último elemento da primeira linha
print(matriz[-1][-1])    # Último elemento da última linha
```

## Fatiamento de Tuplas

```python
tupla = ('p', 'y', 't', 'h', 'o', 'n',)

print(tupla[2:])         # A partir do índice 2
print(tupla[:2])         # Do início até o índice 2 (exclusivo)
print(tupla[1:3])        # Entre os índices 1 e 2
print(tupla[0:3:2])      # Do índice 0 ao 2, pulando de 2 em 2
print(tupla[::])         # Todos os elementos
print(tupla[::-1])       # Ordem invertida
```

## Percorrendo Tuplas

```python
carros = ('gol', 'celta', 'palio',)

for carro in carros:
    print(carro)
```

## Percorrendo com Indice (enumerate)

```python
carros = ('gol', 'celta', 'palio',)

for indice, carro in enumerate(carros):
    print(f'{indice}: {carro}')
```

## Contando Ocorrências

```python
cores = ('vermelho', 'azul', 'verde', 'azul',)

print(cores.count('vermelho'))  # 1
print(cores.count('azul'))      # 2
print(cores.count('verde'))     # 1
```

## Encontrando o Índice de Elementos

```python
linguagens = ('python', 'js', 'java', 'csharp',)

print(linguagens.index('java'))     # 2
print(linguagens.index('python'))   # 0
```

## Comprimento da Tupla

```python
linguagens = ('python', 'js', 'java', 'csharp',)

print(len(linguagens))  # 4
```
