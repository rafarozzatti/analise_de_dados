**Criação de Tabelas em SQL: NOT NULL, UNIQUE e DEFAULT**

Ao projetar um banco de dados relacional, uma das etapas fundamentais é a criação de tabelas. As tabelas armazenam os dados em linhas e colunas, e sua definição deve ser feita de maneira cuidadosa para garantir integridade, consistência e organização das informações.

Este documento tem como objetivo explicar detalhadamente a criação de tabelas em SQL, abordando os principais comandos e restrições como `NOT NULL`, `UNIQUE` e `DEFAULT`, com exemplos práticos.

---

### **1. Comando CREATE TABLE**

O comando `CREATE TABLE` é usado para criar uma nova tabela em um banco de dados.

#### **Sintaxe Básica:**
```sql
CREATE TABLE nome_tabela (
    nome_coluna1 tipo_dado restrição,
    nome_coluna2 tipo_dado restrição,
    ...
);
```

---

### **2. Restrições (Constraints)**
As restrições ajudam a definir regras para os dados nas tabelas. Três das mais utilizadas são:

#### **a) NOT NULL**
- Garante que a coluna não pode receber valores nulos.
- Útil para campos obrigatórios.

**Exemplo:**
```sql
CREATE TABLE clientes (
    id INT,
    nome VARCHAR(100) NOT NULL,
    idade INT
);
```
Neste exemplo, o campo `nome` é obrigatório, ou seja, não pode ser deixado em branco.

#### **b) UNIQUE**
- Garante que todos os valores de uma coluna sejam únicos.
- Pode ser usado para evitar duplicatas, como em e-mails ou CPFs.

**Exemplo:**
```sql
CREATE TABLE usuarios (
    id INT,
    email VARCHAR(100) UNIQUE,
    senha VARCHAR(50)
);
```
Neste caso, não é permitido que dois usuários tenham o mesmo e-mail.

#### **c) DEFAULT**
- Define um valor padrão para a coluna caso nenhum valor seja fornecido na inserção.

**Exemplo:**
```sql
CREATE TABLE pedidos (
    id INT,
    status VARCHAR(20) DEFAULT 'Pendente',
    valor_total DECIMAL(10,2)
);
```
Se um novo pedido for inserido sem especificar o status, ele automaticamente receberá o valor 'Pendente'.

---

### **3. Exemplo Completo**
```sql
CREATE TABLE produtos (
    id INT,
    nome VARCHAR(100) NOT NULL,
    preco DECIMAL(10,2) NOT NULL,
    estoque INT DEFAULT 0,
    codigo_barra VARCHAR(50) UNIQUE
);
```
**Explicação:**
- `id` é um identificador da linha, mas não foi definida nenhuma chave primária.
- `nome` e `preco` são obrigatórios (`NOT NULL`).
- `estoque` recebe 0 por padrão se não for informado (`DEFAULT`).
- `codigo_barra` deve ser único (`UNIQUE`).

---

### **4. Considerações Finais**

O uso adequado das restrições `NOT NULL`, `UNIQUE` e `DEFAULT` torna o banco de dados mais confiável, evitando dados inconsistentes e facilitando a manutenção. Sempre que criar tabelas, pense nas regras de negócio que os dados devem seguir e use as constraints para refletir isso na estrutura do banco de dados.
