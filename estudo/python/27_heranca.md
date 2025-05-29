# Herança em Python

A **herança** é um dos pilares da Programação Orientada a Objetos (POO). Ela permite que uma classe reutilize atributos e comportamentos (métodos) de outra classe, promovendo o **reuso de código**, a **organização** e a **especialização**.

Imagine que você tem uma classe chamada `Veiculo` com algumas características básicas, como cor, placa e número de rodas. Em vez de repetir essas características em outras classes como `Carro`, `Moto` ou `Caminhao`, você pode **herdar** essas características da classe `Veiculo`.

---

## Exemplo 1 – Herança Simples com Veículos

```python
class Veiculo:
    def __init__(self, cor, placa, numero_rodas):
        self.cor = cor
        self.placa = placa
        self.numero_rodas = numero_rodas

    def ligar_motor(self):
        print('Ligando o motor')

    def __str__(self):
        return f'{self.__class__.__name__}: {", ".join([f"{chave}: {valor}" for chave, valor in self.__dict__.items()])}'

class Motocicleta(Veiculo):
    pass  # Herda tudo da classe Veiculo

class Carro(Veiculo):
    pass  # Também herda tudo da classe Veiculo

class Caminhao(Veiculo):
    def __init__(self, cor, placa, numero_rodas, carregado):
        super().__init__(cor, placa, numero_rodas)  # Chama o construtor da classe pai
        self.carregado = carregado  # Novo atributo específico do caminhão

    def esta_carregado(self):
        print(f'{"Sim" if self.carregado else "Não"} estou carregado')

moto = Motocicleta('preta', 'abc-1234', 2)
carro = Carro('branco', 'xde-0098', 4)
caminhao = Caminhao('roxo', 'gfd-8712', 8, True)

print(moto)
print(carro)
print(caminhao)
caminhao.esta_carregado()
```

### Saída esperada:
```
Motocicleta: cor: preta, placa: abc-1234, numero_rodas: 2
Carro: cor: branco, placa: xde-0098, numero_rodas: 4
Caminhao: cor: roxo, placa: gfd-8712, numero_rodas: 8, carregado: True
Sim estou carregado
```

### Explicação:
- A classe `Veiculo` possui atributos comuns e um método `ligar_motor`.
- `Motocicleta` e `Carro` **herdam** diretamente da classe `Veiculo` e não precisam repetir o código do construtor.
- `Caminhao` também herda de `Veiculo`, mas **adiciona um novo atributo** (`carregado`) e um novo método `esta_carregado()`.
- O `super()` é usado para acessar o construtor da classe pai e reutilizar a inicialização.

---

## Exemplo 2 – Herança Múltipla com Animais

Agora vamos ver herança múltipla, onde uma classe pode herdar de **mais de uma classe**.

```python
class Animal:
    def __init__(self, nro_patas):
        self.nro_patas = nro_patas

    def __str__(self):
        return f'{self.__class__.__name__}: {", ".join([f"{chave}: {valor}" for chave, valor in self.__dict__.items()])}'

class Mamifero(Animal):
    def __init__(self, cor_pelo, **kwargs):
        super().__init__(**kwargs)
        self.cor_pelo = cor_pelo

class Ave(Animal):
    def __init__(self, cor_bico, **kwargs):  # Corrigido 'kwars' para 'kwargs'
        super().__init__(**kwargs)
        self.cor_bico = cor_bico

class Gato(Mamifero):
    pass  # Herda tudo de Mamifero

class Ornitorinco(Mamifero, Ave):
    pass  # Herda de Mamifero e Ave

gato = Gato(nro_patas=4, cor_pelo='Preto')
print(gato)

ornitorinco = Ornitorinco(nro_patas=2, cor_pelo='Vermelho', cor_bico='Laranja')
print(ornitorinco)
```

### Saída esperada:
```
Gato: nro_patas: 4, cor_pelo: Preto
Ornitorinco: nro_patas: 2, cor_pelo: Vermelho, cor_bico: Laranja
```

### Explicação:
- `Animal` é a classe mais genérica, com um atributo `nro_patas`.
- `Mamifero` e `Ave` **herdam de Animal** e acrescentam seus próprios atributos (`cor_pelo` e `cor_bico`).
- A palavra-chave `**kwargs` permite repassar argumentos para a classe base sem precisar listar todos explicitamente.
- `Gato` herda de `Mamifero`, então tem `nro_patas` e `cor_pelo`.
- `Ornitorinco` herda de `Mamifero` **e** `Ave`, tendo os atributos das duas classes. Isso é possível graças à **herança múltipla**.
- O método `__str__` é chamado automaticamente ao usar `print()`, e exibe todos os atributos do objeto.
