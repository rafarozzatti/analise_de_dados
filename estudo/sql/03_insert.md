**Comandos INSERT e SELECT em SQL**

O SQL (Structured Query Language) é a linguagem padrão para gerenciamento de bancos de dados relacionais. Dois dos comandos mais fundamentais em SQL são o `INSERT`, que insere dados em uma tabela, e o `SELECT`, que realiza consultas nesses dados.

Este documento explora ambos os comandos com explicações claras e exemplos usando operadores comuns como `=`, `<>`, `>`, `<`, `>=`, `<=`, `LIKE`, `IN`, `BETWEEN`, `AND` e `OR`.

---

### **1. Comando INSERT**

O comando `INSERT` é usado para adicionar novas linhas a uma tabela.

#### **Sintaxe Básica:**
```sql
INSERT INTO nome_tabela (coluna1, coluna2, ...)
VALUES (valor1, valor2, ...);
```

#### **Exemplo:**
```sql
INSERT INTO clientes (id, nome, idade)
VALUES (1, 'Ana', 25);
```
Esse comando insere um novo cliente com `id` 1, nome "Ana" e idade 25.

---

### **2. Comando SELECT**

O comando `SELECT` é usado para buscar dados de uma tabela.

#### **Sintaxe Básica:**
```sql
SELECT coluna1, coluna2
FROM nome_tabela
WHERE condição;
```

#### **Exemplo Simples:**
```sql
SELECT nome, idade
FROM clientes;
```
Retorna todos os nomes e idades dos clientes.

---

### **3. Filtros com WHERE e Operadores**

#### **= (igual)**
```sql
SELECT * FROM clientes WHERE idade = 25;
```
Retorna todos os clientes com 25 anos.

#### **<> (diferente)**
```sql
SELECT * FROM clientes WHERE idade <> 30;
```
Retorna todos os clientes que não têm 30 anos.

#### **> (maior que)**
```sql
SELECT * FROM clientes WHERE idade > 18;
```

#### **< (menor que)**
```sql
SELECT * FROM clientes WHERE idade < 60;
```

#### **>= (maior ou igual)**
```sql
SELECT * FROM clientes WHERE idade >= 40;
```

#### **<= (menor ou igual)**
```sql
SELECT * FROM clientes WHERE idade <= 21;
```

#### **LIKE (comparação textual com padrões)**
```sql
SELECT * FROM clientes WHERE nome LIKE 'A%';
```
Retorna todos os clientes cujo nome começa com "A".

#### **IN (valores específicos)**
```sql
SELECT * FROM clientes WHERE idade IN (18, 25, 30);
```
Retorna todos os clientes com idade 18, 25 ou 30.

#### **BETWEEN (intervalo inclusivo)**
```sql
SELECT * FROM clientes WHERE idade BETWEEN 20 AND 30;
```
Retorna todos os clientes com idade entre 20 e 30 (inclusive).

#### **AND (todas as condições devem ser verdadeiras)**
```sql
SELECT * FROM clientes WHERE idade > 18 AND nome LIKE 'M%';
```
Retorna clientes maiores de 18 cujo nome começa com "M".

#### **OR (pelo menos uma condição deve ser verdadeira)**
```sql
SELECT * FROM clientes WHERE idade < 18 OR idade > 60;
```
Retorna clientes menores de 18 ou maiores de 60 anos.

---

### **Considerações Finais**

O domínio dos comandos `INSERT` e `SELECT` é essencial para trabalhar com bancos de dados. Saber aplicar corretamente filtros e operadores permite consultar dados com precisão e eficiência. Praticar com diferentes condições e combinações vai aprimorar suas habilidades em SQL.
