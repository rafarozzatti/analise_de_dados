**Chaves Primárias e Estrangeiras em SQL**

No design de bancos de dados relacionais, as **chaves primárias** e **chaves estrangeiras** são fundamentais para garantir a integridade dos dados e estabelecer os relacionamentos entre tabelas. Neste documento, abordaremos a definição, a importância e os exemplos de uso de cada tipo de chave.

---

### **1. Chave Primária (Primary Key)**

A **chave primária** é um campo (ou conjunto de campos) em uma tabela que identifica exclusivamente cada registro dessa tabela. Nenhum valor em uma chave primária pode ser nulo, e cada valor deve ser único.

#### **Características:**
- **Única**: Cada valor da chave primária deve ser único.
- **Não Nula**: Não pode ter valores nulos.
- **Índice**: Normalmente, uma chave primária é indexada, o que melhora o desempenho de consultas.

#### **Sintaxe para Criar uma Tabela com Chave Primária:**
```sql
CREATE TABLE clientes (
    id_cliente INT NOT NULL,
    nome VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL,
    PRIMARY KEY (id_cliente)
);
```
Neste exemplo, `id_cliente` é a chave primária, o que significa que cada `id_cliente` será único e não poderá ser nulo.

#### **Exemplo de Inserção:**
```sql
INSERT INTO clientes (id_cliente, nome, email)
VALUES (1, 'João Silva', 'joao@email.com');
```
Aqui, `id_cliente` precisa ser único, e não pode haver dois registros com o mesmo valor.

---

### **2. Chave Estrangeira (Foreign Key)**

A **chave estrangeira** é um campo (ou conjunto de campos) em uma tabela que cria uma ligação com a chave primária de outra tabela. Ela é usada para garantir a integridade referencial, ou seja, para assegurar que os dados de uma tabela sejam consistentes com os dados de outra tabela.

#### **Características:**
- **Relacionamento**: Estabelece um relacionamento entre duas tabelas.
- **Integridade Referencial**: Garante que os valores na chave estrangeira correspondam a valores existentes na chave primária da tabela referenciada.
- **Pode ser Nula**: A chave estrangeira pode permitir valores nulos, o que significa que o relacionamento pode ser opcional.

#### **Sintaxe para Criar uma Tabela com Chave Estrangeira:**
```sql
CREATE TABLE pedidos (
    id_pedido INT NOT NULL,
    id_cliente INT,
    data_pedido DATE,
    PRIMARY KEY (id_pedido),
    FOREIGN KEY (id_cliente) REFERENCES clientes(id_cliente)
);
```
Neste exemplo:
- A tabela `pedidos` tem uma chave estrangeira (`id_cliente`) que faz referência à chave primária `id_cliente` da tabela `clientes`.

#### **Exemplo de Inserção com Chave Estrangeira:**
```sql
INSERT INTO pedidos (id_pedido, id_cliente, data_pedido)
VALUES (1, 1, '2025-04-10');
```
Aqui, a inserção no `pedidos` usa o `id_cliente = 1`, que deve existir na tabela `clientes` para que a inserção seja válida.

---

### **3. Relação entre Chave Primária e Chave Estrangeira**

- **Relacionamento 1:N (Um para Muitos)**: Uma chave primária em uma tabela pode estar relacionada a muitas entradas em outra tabela por meio de uma chave estrangeira.

**Exemplo de Relacionamento 1:N:**
```sql
CREATE TABLE produtos (
    id_produto INT NOT NULL,
    nome VARCHAR(100) NOT NULL,
    PRIMARY KEY (id_produto)
);

CREATE TABLE vendas (
    id_venda INT NOT NULL,
    id_produto INT,
    quantidade INT,
    PRIMARY KEY (id_venda),
    FOREIGN KEY (id_produto) REFERENCES produtos(id_produto)
);
```
Neste exemplo, a chave primária de `produtos` é referenciada como chave estrangeira em `vendas`, criando um relacionamento 1:N (um produto pode ser vendido várias vezes, mas cada venda é associada a um único produto).

---

### **4. Considerações Finais**

As **chaves primárias** e **chaves estrangeiras** são cruciais para o modelo de dados de um banco relacional. Elas ajudam a:
- **Garantir a unicidade** e a **integridade dos dados** dentro de cada tabela.
- **Estabelecer relacionamentos entre tabelas**, facilitando consultas e garantindo que dados inconsistentes não sejam inseridos.

Ao projetar um banco de dados, é importante planejar e aplicar corretamente essas chaves para manter a organização e a consistência do sistema.
