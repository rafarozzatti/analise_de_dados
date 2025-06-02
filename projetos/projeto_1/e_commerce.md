## Projeto de Análise de Dados - E-commerce

### Objetivo do Projeto

Criar um banco de dados relacional completo para um sistema de e-commerce com os seguintes requisitos:

* Cadastro de clientes, produtos, pedidos, itens dos pedidos e pagamentos.
* Registro detalhado das transações de vendas.
* Possibilidade de extração e análise dos dados com Python (Pandas).

---

### Criação do Banco de Dados

```sql
CREATE DATABASE e_commerce;

USE e_commerce;
```

### Criação das Tabelas

#### Tabela clientes

```sql
CREATE TABLE clientes (
	id INT PRIMARY KEY,
    nome VARCHAR(100),
    email VARCHAR(50),
    data_cadastro DATE,
    cidade VARCHAR(100),
    estado VARCHAR(50)
);
```

#### Tabela produtos

```sql
CREATE TABLE produtos (
	id INT PRIMARY KEY,
    nome_produto VARCHAR(100),
    categoria VARCHAR(50),
    preco DECIMAL(10, 2)
);
```

#### Tabela pedidos

```sql
CREATE TABLE pedidos (
	id INT PRIMARY KEY,
    id_cliente INT,
    data_pedido DATE,
    valor_total DECIMAL(10, 2),
    FOREIGN KEY(id_cliente) REFERENCES clientes(id)
);
```

#### Tabela itens\_pedidos

```sql
CREATE TABLE itens_pedidos (
	id INT PRIMARY KEY,
    id_pedido INT,
    id_produto INT,
    quantidade INT,
    preco_unitario DECIMAL(10, 2),
    FOREIGN KEY(id_pedido) REFERENCES pedidos(id),
    FOREIGN KEY(id_produto) REFERENCES produtos(id)
);
```

#### Tabela pagamentos

```sql
CREATE TABLE pagamentos (
	id INT PRIMARY KEY,
    id_pedido INT,
    forma_pagamento VARCHAR(20),
    status_pagamento VARCHAR(20),
    data_pagamento DATE,
    FOREIGN KEY(id_pedido) REFERENCES pedidos(id)
);
```

### Inserção de Dados

#### Tabela clientes

```sql
INSERT INTO clientes (id, nome, email, data_cadastro, cidade, estado) VALUES
(1, 'Ana Silva', 'ana@gmail.com', '2023-01-10', 'São Paulo', 'SP'),
(2, 'Carlos Souza', 'carlos@gmail.com', '2023-02-15', 'Rio de Janeiro', 'RJ'),
(3, 'Mariana Lima', 'mariana@gmail.com', '2023-03-05', 'Belo Horizonte', 'MG'),
(4, 'Pedro Oliveira', 'pedro@gmail.com', '2023-03-20', 'Curitiba', 'PR'),
(5, 'Fernanda Costa', 'fernanda@gmail.com', '2023-04-01', 'Fortaleza', 'CE'),
(6, 'Lucas Almeida', 'lucas@gmail.com', '2023-04-10', 'Salvador', 'BA'),
(7, 'Juliana Martins', 'juliana@gmail.com', '2023-05-05', 'Porto Alegre', 'RS'),
(8, 'Ricardo Fernandes', 'ricardo@gmail.com', '2023-05-15', 'Recife', 'PE'),
(9, 'Amanda Rocha', 'amanda@gmail.com', '2023-06-01', 'Manaus', 'AM'),
(10, 'Bruno Pereira', 'bruno@gmail.com', '2023-06-20', 'Belém', 'PA'),
(11, 'Larissa Castro', 'larissa@gmail.com', '2023-07-10', 'Goiânia', 'GO'),
(12, 'Eduardo Gomes', 'eduardo@gmail.com', '2023-07-25', 'Campinas', 'SP'),
(13, 'Patrícia Dias', 'patricia@gmail.com', '2023-08-01', 'São Luís', 'MA'),
(14, 'Thiago Santos', 'thiago@gmail.com', '2023-08-15', 'Natal', 'RN'),
(15, 'Camila Moreira', 'camila@gmail.com', '2023-09-01', 'Maceió', 'AL');
```

#### Tabela produtos

```sql
INSERT INTO produtos (id, nome_produto, categoria, preco) VALUES
(1, 'Notebook Dell', 'Informática', 3500.00),
(2, 'Smartphone Samsung', 'Celulares', 2200.00),
(3, 'Fone Bluetooth JBL', 'Acessórios', 300.00),
(4, 'Monitor LG 24"', 'Informática', 900.00),
(5, 'Teclado Mecânico', 'Informática', 450.00),
(6, 'Cadeira Gamer', 'Móveis', 1200.00),
(7, 'Mouse Logitech', 'Informática', 150.00),
(8, 'Smartwatch Xiaomi', 'Wearables', 800.00),
(9, 'Caixa de Som JBL', 'Acessórios', 400.00),
(10, 'Tablet Samsung', 'Celulares', 1800.00),
(11, 'HD Externo 1TB', 'Informática', 350.00),
(12, 'Câmera GoPro', 'Eletrônicos', 2200.00),
(13, 'Microfone Blue', 'Acessórios', 500.00),
(14, 'Roteador TP-Link', 'Informática', 250.00),
(15, 'Webcam Logitech', 'Acessórios', 320.00);
```

#### Tabela pedidos

```sql
INSERT INTO pedidos (id, id_cliente, data_pedido, valor_total) VALUES
(1, 1, '2023-04-01', 3700.00),
(2, 2, '2023-04-02', 2500.00),
(3, 3, '2023-04-03', 300.00),
(4, 4, '2023-04-05', 1350.00),
(5, 5, '2023-04-06', 800.00),
(6, 6, '2023-04-10', 1500.00),
(7, 7, '2023-04-12', 1200.00),
(8, 8, '2023-04-15', 900.00),
(9, 9, '2023-04-20', 3500.00),
(10, 10, '2023-04-25', 1000.00),
(11, 11, '2023-05-01', 800.00),
(12, 12, '2023-05-05', 600.00),
(13, 13, '2023-05-10', 2200.00),
(14, 14, '2023-05-15', 1500.00),
(15, 15, '2023-05-20', 300.00),
(16, 1, '2023-06-01', 3200.00),
(17, 3, '2023-06-05', 400.00),
(18, 5, '2023-06-10', 1800.00),
(19, 7, '2023-06-15', 2200.00),
(20, 9, '2023-06-20', 900.00);
```

#### Tabela itens_pedidos

```sql
INSERT INTO itens_pedidos (id, id_pedido, id_produto, quantidade, preco_unitario) VALUES
(1, 1, 1, 1, 3500.00),
(2, 1, 3, 1, 200.00),
(3, 2, 2, 1, 2200.00),
(4, 2, 3, 1, 300.00),
(5, 3, 3, 1, 300.00),
(6, 4, 4, 1, 900.00),
(7, 4, 7, 3, 150.00),
(8, 5, 8, 1, 800.00),
(9, 6, 6, 1, 1200.00),
(10, 6, 15, 1, 300.00),
(11, 7, 6, 1, 1200.00),
(12, 8, 4, 1, 900.00),
(13, 9, 1, 1, 3500.00),
(14, 10, 5, 2, 450.00),
(15, 10, 7, 1, 150.00),
(16, 11, 8, 1, 800.00),
(17, 12, 14, 2, 250.00),
(18, 13, 2, 1, 2200.00),
(19, 13, 9, 1, 400.00),
(20, 14, 6, 1, 1200.00),
(21, 15, 3, 1, 300.00),
(22, 16, 1, 1, 3200.00),
(23, 16, 15, 1, 300.00),
(24, 17, 9, 1, 400.00),
(25, 18, 2, 1, 2200.00),
(26, 18, 13, 1, 500.00),
(27, 19, 2, 1, 2200.00),
(28, 19, 14, 1, 250.00),
(29, 20, 4, 1, 900.00),
(30, 20, 7, 1, 150.00),
(31, 5, 9, 1, 400.00),
(32, 7, 3, 1, 300.00),
(33, 8, 15, 2, 300.00),
(34, 11, 14, 1, 250.00),
(35, 12, 12, 1, 2200.00),
(36, 13, 10, 1, 1800.00),
(37, 14, 11, 1, 350.00),
(38, 15, 13, 1, 500.00),
(39, 16, 4, 1, 900.00),
(40, 17, 5, 1, 450.00);
```

#### Tabela pagamentos

```sql
INSERT INTO pagamentos (id, id_pedido, forma_pagamento, status_pagamento, data_pagamento) VALUES
(1, 1, 'Cartão de Crédito', 'Pago', '2023-04-02'),
(2, 2, 'Boleto', 'Pago', '2023-04-03'),
(3, 3, 'Pix', 'Pago', '2023-04-03'),
(4, 4, 'Cartão de Crédito', 'Pago', '2023-04-06'),
(5, 5, 'Boleto', 'Pendente', NULL),
(6, 6, 'Pix', 'Pago', '2023-04-11'),
(7, 7, 'Cartão de Crédito', 'Pago', '2023-04-13'),
(8, 8, 'Boleto', 'Pago', '2023-04-16'),
(9, 9, 'Pix', 'Pago', '2023-04-21'),
(10, 10, 'Cartão de Crédito', 'Pago', '2023-04-26'),
(11, 11, 'Boleto', 'Pago', '2023-05-02'),
(12, 12, 'Pix', 'Pago', '2023-05-06'),
(13, 13, 'Cartão de Crédito', 'Pago', '2023-05-11'),
(14, 14, 'Boleto', 'Pago', '2023-05-16'),
(15, 15, 'Pix', 'Pendente', NULL),
(16, 16, 'Cartão de Crédito', 'Pago', '2023-06-02'),
(17, 17, 'Boleto', 'Pago', '2023-06-06'),
(18, 18, 'Pix', 'Pago', '2023-06-11'),
(19, 19, 'Cartão de Crédito', 'Pago', '2023-06-16'),
(20, 20, 'Boleto', 'Pago', '2023-06-21');
```

---

### Querys de Análise

#### Faturamento Geral

```sql
SELECT COUNT(*) AS total_de_pedidos, SUM(valor_total) AS faturamento_geral 
FROM pedidos;
```

#### Faturamento Mensal

```sql
SELECT YEAR(data_pedido) AS ano, MONTH(data_pedido) AS mes, SUM(valor_total) AS faturamento_mensal 
FROM pedidos
GROUP BY ano, mes
ORDER BY ano, mes;
```

#### Produtos Mais Vendidos

```sql
SELECT p.nome_produto AS produto, SUM(ip.quantidade) AS quantidade 
FROM produtos p
INNER JOIN itens_pedidos ip ON p.id = ip.id_produto
GROUP BY p.nome_produto
ORDER BY quantidade DESC;
```

#### Total Gasto por Cliente

```sql
SELECT c.nome, SUM(p.valor_total) AS total_gasto 
FROM clientes c
INNER JOIN pedidos p ON c.id = p.id_cliente
GROUP BY c.nome
ORDER BY total_gasto DESC;
```

#### Pedidos por Estado e Status do Pagamento

```sql
SELECT c.estado AS estado, pg.status_pagamento, COUNT(*) AS total_pedidos 
FROM pedidos p
INNER JOIN clientes c ON p.id_cliente = c.id
INNER JOIN pagamentos pg ON p.id = pg.id_pedido
GROUP BY c.estado, pg.status_pagamento
ORDER BY c.estado, pg.status_pagamento;
```

---

### Extração de Dados com Python

```python
# 1. Importar bibliotecas
import pandas as pd
import pymysql

# 2. Criar conexão com o banco MySQL
conexao = pymysql.connect(
    host='localhost',
    user='root',
    password='Rafa17@2',
    database='e_commerce'
)

try:
    # 3. Consultas SQL (query)
    queries = {
        "total_pedidos_faturamento": """
        SELECT COUNT(*) AS total_de_pedidos, SUM(valor_total) AS faturamento_geral
        FROM pedidos;
        """,
        "faturamento_mensal": """
        SELECT YEAR(data_pedido) AS ano, MONTH(data_pedido) AS mes, SUM(valor_total) AS faturamento_mensal
        FROM pedidos
        GROUP BY ano, mes
        ORDER BY ano, mes;
        """,
        "produtos_mais_vendidos": """
        SELECT p.nome_produto AS produto, SUM(ip.quantidade) AS quantidade
        FROM produtos p
        INNER JOIN itens_pedidos ip ON p.id = ip.id_produto
        GROUP BY p.nome_produto
        ORDER BY quantidade DESC;
        """,
        "clientes_compras": """
        SELECT c.nome, SUM(p.valor_total) AS total_gasto
        FROM clientes c
        INNER JOIN pedidos p ON c.id = p.id_cliente
        GROUP BY c.nome
        ORDER BY total_gasto DESC;
        """,
        "qtd_pedidos_estado": """
        SELECT c.estado AS estado, pg.status_pagamento, COUNT(*) AS total_pedidos
        FROM pedidos p
        INNER JOIN clientes c ON p.id_cliente = c.id
        INNER JOIN pagamentos pg ON p.id = pg.id_pedido
        GROUP BY c.estado, pg.status_pagamento
        ORDER BY c.estado, pg.status_pagamento;
        """
    }

    for nome, sql in queries.items():
        df = pd.read_sql(sql, conexao)
        df.info()
        print(df.head())
        df.to_csv(f"{nome}.csv", index=False)
        print(f"{nome}.csv exportado com sucesso!")

except Exception as e:
    print(f"Ocorreu um erro: {e}")

finally:
    conexao.close()
```

---

### Exemplo de Arquivos Exportados (.CSV)

#### 📁 `total_pedidos_faturamento.csv`

total_de_pedidos,faturamento_geral
20,30650.0

#### 📁 `faturamento_mensal.csv`

ano,mes,faturamento_mensal
2023,4,16750.0
2023,5,5400.0
2023,6,8500.0

#### 📁 `produtos_mais_vendidos.csv`

produto,quantidade
Fone Bluetooth JBL,5.0
Mouse Logitech,5.0
Smartphone Samsung,4.0
"Monitor LG 24""",4.0
Roteador TP-Link,4.0
Webcam Logitech,4.0
Notebook Dell,3.0
Teclado Mecânico,3.0
Cadeira Gamer,3.0
Caixa de Som JBL,3.0
Smartwatch Xiaomi,2.0
Microfone Blue,2.0
Tablet Samsung,1.0
HD Externo 1TB,1.0
Câmera GoPro,1.0

#### 📁 `clientes_compras.csv`

nome,total_gasto
Ana Silva,6900.0
Amanda Rocha,4400.0
Juliana Martins,3400.0
Fernanda Costa,2600.0
Carlos Souza,2500.0
Patrícia Dias,2200.0
Lucas Almeida,1500.0
Thiago Santos,1500.0
Pedro Oliveira,1350.0
Bruno Pereira,1000.0
Ricardo Fernandes,900.0
Larissa Castro,800.0
Mariana Lima,700.0
Eduardo Gomes,600.0
Camila Moreira,300.0

#### 📁 `qtd_pedidos_estado.csv`

estado,status_pagamento,total_pedidos
AL,Pendente,1
AM,Pago,2
BA,Pago,1
CE,Pago,1
CE,Pendente,1
GO,Pago,1
MA,Pago,1
MG,Pago,2
PA,Pago,1
PE,Pago,1
PR,Pago,1
RJ,Pago,1
RN,Pago,1
RS,Pago,2
SP,Pago,3

---

### Parte dos Gráficos

*A ser desenvolvida.*
