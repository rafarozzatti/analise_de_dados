# Laço `for` em Python

O laço `for` é usado para **percorrer uma sequência** (como uma string, lista, tupla, etc.) e executar um bloco de código para cada elemento dessa sequência.

---

## Exemplo: imprimir as vogais de um texto

```python
texto = input('Informe um texto: ')
vogais = 'AEIOU'

# Percorre cada letra do texto
for letra in texto:
    # Se a letra (em maiúscula) estiver em vogais, imprime a letra
    if letra.upper() in vogais:
        print(letra, end='')
```

---

### Explicação:

* `for letra in texto:` percorre cada caractere da string `texto`.
* `letra.upper()` transforma a letra em maiúscula para facilitar a comparação.
* `if letra.upper() in vogais:` verifica se a letra é uma vogal.
* `print(letra, end='')` imprime a letra na mesma linha, sem pular para a próxima.

---

### Exemplo de entrada e saída:

**Entrada:**

```
Informe um texto: Rafael Pires
```

**Saída:**

```
aaeie
```
