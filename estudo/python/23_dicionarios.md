# 📘 Dicionários em Python

Dicionários armazenam **pares chave\:valor**, permitindo acesso rápido a informações associadas a uma chave. São mutáveis, dinâmicos e ideais para representar registros (como uma ficha de pessoa, produto, etc.).

---

## ✅ Criando Dicionários

```python
# Primeira forma de criar um dicionário
pessoa = {'nome': 'Rafael', 'idade': 26}
print(pessoa)
```

**Saída:**

```
{'nome': 'Rafael', 'idade': 26}
```

> Utiliza chaves `{}` para definir pares chave\:valor diretamente.

```python
# Outra forma de criar um dicionário
pessoa = dict(nome='Rafael', idade=26)
print(pessoa)
```

**Saída:**

```
{'nome': 'Rafael', 'idade': 26}
```

> Usa a função `dict()` com parâmetros nomeados — mesmo efeito da forma anterior.

---

## ➕ Adicionando/Alterando valores

```python
pessoa['telefone'] = '3333-1234'
print(pessoa)
```

**Saída:**

```
{'nome': 'Rafael', 'idade': 26, 'telefone': '3333-1234'}
```

> Atribuir um valor a uma nova chave **adiciona** ao dicionário. Se a chave já existir, o valor será **atualizado**.

---

## 📂 Dicionários Aninhados

```python
contatos = {
    'rafael@gmail.com': {'nome': 'Rafael', 'idade': 26, 'telefone': '3333-2221'},
    'enzo@gmail.com': {'nome': 'Enzo', 'idade': 16, 'telefone': '3443-2121'},
    ...
}

print(contatos['enzo@gmail.com']['telefone'])
```

**Saída:**

```
3443-2121
```

> Dicionários podem conter outros dicionários como valor. É possível acessar as informações aninhadas usando colchetes múltiplos.

---

## 🔁 Iterando sobre Dicionários

```python
for chave in contatos:
    print(f'{chave}: {contatos[chave]}')
```

> Percorre as **chaves** e imprime os valores correspondentes.

```python
for chave, valor in contatos.items():
    print(f'{chave}: {valor}')
```

> `items()` retorna **pares chave-valor** diretamente, ideal para laços `for`.

---

## 🧹 Limpar Dicionário

```python
contatos.clear()
print(contatos)
```

**Saída:**

```
{}
```

> Remove **todos os pares** do dicionário.

---

## 🧪 Cópia de Dicionário

```python
copia = contatos.copy()
```

> Cria uma cópia **independente**. Alterações na cópia não afetam o original.

---

## 🧰 `fromkeys`

```python
exemplo1 = dict.fromkeys(['nome', 'telefone'])
```

**Saída:**

```
{'nome': None, 'telefone': None}
```

```python
exemplo2 = dict.fromkeys(['nome', 'telefone'], 'vazio')
```

**Saída:**

```
{'nome': 'vazio', 'telefone': 'vazio'}
```

> Cria um novo dicionário com as chaves informadas. O valor padrão pode ser `None` ou definido pelo usuário.

---

## 🔍 `get`

```python
print(contatos.get('chave'))        # Chave inexistente
print(contatos.get('chave', {}))    # Valor padrão
print(contatos.get('rafael@gmail.com', {}))  # Chave existente
```

**Saída:**

```
None
{}
{'nome': 'Rafael', 'idade': 26, 'telefone': '3333-2221'}
```

> Evita erro ao acessar chaves inexistentes e permite definir um valor padrão para retornar.

---

## 📦 `items`, `keys`, `values`

```python
print(contatos.items())   # Pares chave-valor
print(contatos.keys())    # Apenas chaves
print(contatos.values())  # Apenas valores
```

**Saídas:**

```
dict_items([...])
dict_keys([...])
dict_values([...])
```

> Essas funções facilitam a iteração ou verificação das partes do dicionário.

---

## ❌ `pop` e `popitem`

```python
print(contatos.pop('rafael@gmail.com'))
```

> Remove e **retorna** o valor da chave.

```python
print(contatos.pop('rafael@gmail.com', {}))
```

> Retorna `{}` se a chave não existir (sem erro).

```python
print(contatos.popitem())
```

> Remove o **último item inserido** no dicionário (em versões recentes do Python).

---

## 🔧 `setdefault`

```python
print(contatos.setdefault('nome', 'Enzo'))   # já existe
print(contatos.setdefault('idade', 26))      # não existe
```

**Saída:**

```
Rafael
26
```

> Retorna o valor da chave. Se a chave **não existir**, ela será criada com o valor informado.

---

## 🔄 `update`

```python
contatos.update({'rafael@gmail.com': {'nome': 'Rafa'}})
```

> Atualiza ou adiciona um novo par chave\:valor ao dicionário.

```python
contatos.update({'enzo@gmail.com': {'nome': 'Enzo'}})
```

> Pode adicionar múltiplos pares com um único comando.

---

## ❓ Verificar se Chave Existe

```python
print('rafael@gmail.com' in contatos)
print('maria@gmail.com' in contatos)
```

**Saída:**

```
True
False
```

> Usa o operador `in` para verificar se uma chave existe no dicionário.

---

## 🗑️ Deletando com `del`

```python
del contatos['rafael@gmail.com']['telefone']
del contatos['enzo@gmail.com']
```

> Remove uma **chave específica** ou um campo interno dentro de um dicionário aninhado.
