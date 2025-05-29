# Polimorfismo em Python

O polimorfismo permite que objetos de diferentes classes respondam de forma diferente ao mesmo método, promovendo flexibilidade e reutilização de código. Em Python, isso é possível graças à **herança** e à **sobrescrita de métodos**.

---

## Exemplo – Polimorfismo com Pássaros

```python
# Define a classe base "Passaro"
class Passaro:
    # Método que representa a ação de voar
    def voar(self):
        print('Voando...')

# Define uma classe "Pardal" que herda de "Passaro"
class Pardal(Passaro):
    # Sobrescreve o método "voar"
    def voar(self):
        # Chama o método "voar" da classe pai (Passaro)
        super().voar()

# Define uma classe "Avestruz" que também herda de "Passaro"
class Avestruz(Passaro):
    # Sobrescreve o método "voar" com um comportamento diferente
    def voar(self):
        print('Avestruz não pode voar')

# Função que aceita um objeto e chama seu método "voar"
def plano_voo(obj):
    obj.voar()

# Cria uma instância de Pardal
p1 = Pardal()

# Cria uma instância de Avestruz
p2 = Avestruz()

# Chama a função "plano_voo" passando o pardal
plano_voo(p1)  # Saída esperada: "Voando..."

# Chama a função "plano_voo" passando o avestruz
plano_voo(p2)  # Saída esperada: "Avestruz não pode voar"
```

### Saída:
```
Voando...
Avestruz não pode voar
```

### Explicação Detalhada:
- A classe `Passaro` define um método `voar()` que imprime "Voando...".
- A classe `Pardal` herda de `Passaro` e sobrescreve o método `voar()`, mas ainda chama o método original da superclasse com `super().voar()`.
- A classe `Avestruz` também herda de `Passaro`, mas redefine o método `voar()` para dizer que não pode voar.
- A função `plano_voo(obj)` aceita qualquer objeto e chama seu método `voar()`, sem precisar saber a classe exata do objeto.

Esse é um exemplo clássico de **polimorfismo**, onde a mesma função (`plano_voo`) executa comportamentos diferentes dependendo do objeto que recebe.
