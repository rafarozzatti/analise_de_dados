# Interfaces e Classes Abstratas em Python

Interfaces e classes abstratas são estruturas que nos ajudam a definir um "contrato" de métodos que devem ser implementados nas classes filhas. Isso é muito útil para garantir que diferentes classes compartilhem a mesma interface, mesmo que a implementação interna seja diferente.

Em Python, usamos a biblioteca `abc` (Abstract Base Class) para criar classes abstratas e métodos abstratos.

---

## Exemplo 1 – Classe Abstrata com Métodos Obrigatórios

```python
from abc import ABC, abstractmethod

# Classe abstrata base
class ControleRemoto(ABC):
    @abstractmethod
    def ligar(self):
        pass

    @abstractmethod
    def desligar(self):
        pass

# Classe concreta que herda da classe abstrata
class ControleTV(ControleRemoto):
    def ligar(self):
        print('Ligando a TV...')
        print('Ligada!')

    def desligar(self):
        print('Desligando a TV...')
        print('Desligada!')

# Outra classe concreta que herda da classe abstrata
class ControleArCondicionado(ControleRemoto):
    def ligar(self):
        print('Ligando o Ar Condicionado...')
        print('Ligado!')

    def desligar(self):
        print('Desligando o Ar Condicionado...')
        print('Desligado!')

# Usando as classes
controle = ControleTV()
controle.ligar()
controle.desligar()

controle = ControleArCondicionado()
controle.ligar()
controle.desligar()
```

### Explicação:
- `ControleRemoto` é uma **classe abstrata**.
- `ligar` e `desligar` são **métodos abstratos**, obrigatórios nas subclasses.
- `ControleTV` e `ControleArCondicionado` implementam esses métodos.
- Você **não pode instanciar** uma classe abstrata diretamente.

---

## Exemplo 2 – Métodos de Classe e Métodos Estáticos

```python
class Pessoa:
    def __init__(self, nome=None, idade=None):
        self.nome = nome
        self.idade = idade

    @classmethod
    def criar_de_date_nascimento(cls, ano, mes, dia, nome):
        idade = 2025 - ano  # Simplificação, não considera mês e dia
        return cls(nome, idade)

    @staticmethod
    def e_maior_idade(idade):
        return idade >= 18

# Criando uma pessoa a partir do ano de nascimento
p = Pessoa.criar_de_date_nascimento(1994, 3, 21, 'Guilherme')
print(p.nome, p.idade)

# Usando método estático
print(Pessoa.e_maior_idade(18))  # True
print(Pessoa.e_maior_idade(8))   # False
```

### Explicação:
- `@classmethod` permite criar objetos de formas alternativas, recebendo a própria classe como argumento (`cls`).
- `@staticmethod` cria funções utilitárias relacionadas à classe, mas que não dependem da instância nem da classe.

---

## Exemplo 3 – Atributos de Classe vs. Atributos de Instância

```python
class Estudante:
    escola = 'DIO'  # Atributo de classe

    def __init__(self, nome, matricula):
        self.nome = nome
        self.matricula = matricula

    def __str__(self):
        return f'{self.nome} - {self.matricula} - {self.escola}'

# Função auxiliar para mostrar os dados
def mostrar_valores(*objs):
    for obj in objs:
        print(obj)

# Criando estudantes
aluno_1 = Estudante('Guilherme', 1)
aluno_2 = Estudante('Giovanna', 2)
mostrar_valores(aluno_1, aluno_2)

# Alterando o atributo de classe
Estudante.escola = 'Python'
aluno_3 = Estudante('Chappin', 3)
mostrar_valores(aluno_1, aluno_2, aluno_3)
```

### Explicação:
- `escola` é um **atributo de classe**, compartilhado entre todas as instâncias.
- `nome` e `matricula` são **atributos de instância**, exclusivos para cada objeto.
- Quando o valor do atributo de classe muda, ele reflete em todas as instâncias que não tenham sobrescrito esse atributo.
