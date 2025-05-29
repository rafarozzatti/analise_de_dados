# Programação Orientada a Objetos (POO) em Python

## 1. Definição de Classe e Criação de Objetos

```python
# Definição da classe Bicicleta
class Bicicleta:
    # Método construtor que inicializa os atributos da bicicleta
    def __init__(self, cor, modelo, ano, valor):
        self.cor = cor       # Cor da bicicleta
        self.modelo = modelo # Modelo da bicicleta
        self.ano = ano       # Ano de fabricação
        self.valor = valor   # Preço da bicicleta

    # Método para simular o som da buzina da bicicleta
    def buzinar(self):
        print('Plin plin...')

    # Método para simular a parada da bicicleta
    def parar(self):
        print('''Parando bicicleta...
Bicicleta parada!''')
        
    # Método para simular a bicicleta em movimento
    def correr(self):
        print('Vrummmmmmm...')

    # Método especial que define a representação em string da bicicleta
    def __str__(self):
        # Retorna uma string formatada com os atributos da bicicleta
        return f'{self.__class__.__name__}: {", ".join([f"{chave}: {valor}" for chave, valor in self.__dict__.items()])}'

# Criando um objeto da classe Bicicleta com atributos específicos
b1 = Bicicleta('vermelha', 'caloi', 2025, 600)

# Chamando os métodos da bicicleta
b1.buzinar() # Exibe "Plin plin..."
b1.parar()   # Exibe "Parando bicicleta... Bicicleta parada!"
b1.correr()  # Exibe "Vrummmmmmm..."

# Exibindo as informações formatadas da bicicleta b1
print(f'\nModelo: {b1.modelo.title()}')  # Transforma o primeiro caractere em maiúsculo
print(f'Ano: {b1.ano}')
print(f'Cor: {b1.cor.title()}')           # Transforma o primeiro caractere em maiúsculo
print(f'Valor: R${b1.valor:.2f}')        # Exibe o valor com duas casas decimais

print() # Linha em branco para organização

# Criando outro objeto da classe Bicicleta
b2 = Bicicleta('verde', 'monark', 2000, 189)

# Chamando o método buzinar de duas formas diferentes:
Bicicleta.buzinar(b2) # Chamando diretamente pela classe e passando o objeto b2
b2.buzinar()          # Chamando pelo próprio objeto b2

# Exibindo a representação da bicicleta b2 (usa o método __str__)
print(b2)
```

### Saída:
```
Plin plin...
Parando bicicleta...
Bicicleta parada!
Vrummmmmmm...

Modelo: Caloi
Ano: 2025
Cor: Vermelha
Valor: R$600.00
Plin plin...
Plin plin...
Bicicleta: cor: verde, modelo: monark, ano: 2000, valor: 189
```

## 2. Construtor e Destrutor com Escopo

```python
# Definição da classe Cachorro
class Cachorro:
    # Método construtor, chamado ao criar uma instância da classe
    def __init__(self, nome, cor, acordado=True):
        print('Inicializando a classe...')  # Mensagem indicando que um objeto está sendo criado
        self.nome = nome      # Nome do cachorro
        self.cor = cor        # Cor do cachorro
        self.acordado = acordado  # Estado do cachorro (acordado por padrão)

    # Método destrutor, chamado automaticamente quando o objeto é removido da memória
    def __del__(self):
        print('Removendo a instância de classe.')  # Mensagem indicando que o objeto foi destruído

    # Método que simula o cachorro latindo
    def falar(self):
        print('auau')

# Função para criar um cachorro dentro de um escopo local
def criar_cachorro():
    c = Cachorro('Zeus', 'branco e preto', False)  # Criando um objeto dentro da função
    # Como a variável "c" é local, ao final da execução da função, o objeto será destruído automaticamente.

# Criando um objeto da classe Cachorro
c = Cachorro('Chapple', 'amarelo')  # Exibe "Inicializando a classe..."
c.falar()  # Exibe "auau"

# Chamando a função que cria um cachorro
criar_cachorro()
# O objeto "Zeus" criado dentro da função será destruído ao final da função, então o destrutor será chamado.

# O programa termina aqui, e o objeto "c" também será removido da memória, chamando novamente o destrutor.
```

### Saída:
```
Inicializando a classe...
auau
Inicializando a classe...
Removendo a instância de classe.
Removendo a instância de classe.
```

---

Esses exemplos ilustram como definir classes, instanciar objetos, usar métodos especiais como `__init__` e `__str__`, e entender o ciclo de vida de um objeto com `__del__`.
