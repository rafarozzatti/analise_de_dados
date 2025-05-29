# Encapsulamento em Python

Encapsulamento é o conceito da programação orientada a objetos que consiste em proteger os dados internos de uma classe, restringindo o acesso direto a eles. Isso é feito usando atributos privados ou protegidos e métodos para acessar ou modificar esses dados de forma controlada.

Em Python, por convenção:
- Um atributo com **1 sublinhado** (`_atributo`) é considerado **protegido**.
- Um atributo com **2 sublinhados** (`__atributo`) é considerado **privado**.

---

## Exemplo 1 – Encapsulamento com `@property`

```python
class Foo:
    def __init__(self, x=None):
        self._x = x  # Atributo protegido por convenção

    @property
    def x(self):
        # Getter: retorna o valor de _x, ou 0 se for None
        return self._x or 0

    @x.setter
    def x(self, value):
        # Setter: soma o valor recebido ao valor atual de _x
        self._x += value

    @x.deleter
    def x(self):
        # Deleter: reseta _x para 0
        self._x = 0

foo = Foo(10)
print(foo.x)     # Saída: 10
del foo.x        # Reseta _x para 0
print(foo.x)     # Saída: 0
foo.x = 10       # Soma 10 ao _x atual (0)
print(foo.x)     # Saída: 10
```

### Explicação:
- `@property` permite acessar um método como se fosse um atributo (`foo.x`).
- `@x.setter` define o que acontece ao atribuir um valor (`foo.x = 10`).
- `@x.deleter` permite deletar o atributo (`del foo.x`).
- O atributo `_x` é protegido e manipulado indiretamente, o que exemplifica bem o encapsulamento.

---

## Exemplo 2 – Encapsulamento com métodos públicos

```python
class Conta:
    def __init__(self, saldo):
        self._saldo = saldo  # Atributo protegido por convenção

    def depositar(self, valor):
        self._saldo += valor

    def sacar(self, valor):
        if valor > self._saldo:
            print(f'Erro: Saldo insuficiente para sacar R${valor:.2f}. Saldo disponível: R${self._saldo:.2f}')
        else:
            self._saldo -= valor

    def mostrar_saldo(self):
        return self._saldo

conta = Conta(100)
conta.depositar(100)   # Saldo: 200
conta.sacar(50)        # Saldo: 150
conta.sacar(300)       # Erro: saldo insuficiente
print(f'Saldo final: R${conta.mostrar_saldo():.2f}')
```

### Explicação:
- O atributo `_saldo` é protegido e não acessado diretamente de fora.
- O controle de acesso e validação acontece através de métodos públicos (`depositar`, `sacar`, `mostrar_saldo`).
- Esse modelo é comum em sistemas que precisam proteger dados sensíveis, como contas bancárias.
