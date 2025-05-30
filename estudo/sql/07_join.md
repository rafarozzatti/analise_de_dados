**Consultas com Junções e Subconsultas em SQL**

Em bancos de dados relacionais, é comum precisarmos buscar dados que estão distribuídos em várias tabelas. Para isso, utilizamos **junções (joins)** e **subconsultas (subqueries)**. Este documento explica cada uma dessas abordagens com exemplos práticos e didáticos.

---

### **1. JOIN (Junção Interna)**
A junção interna retorna apenas os registros que possuem correspondência em ambas as tabelas.

#### **Sintaxe:**
```sql
SELECT colunas
FROM tabela1
JOIN tabela2
ON tabela1.coluna = tabela2.coluna;
```

#### **Exemplo:**
```sql
SELECT clientes.nome, pedidos.valor_total
FROM clientes
JOIN pedidos
ON clientes.id = pedidos.id_cliente;
```
Esse exemplo retorna o nome dos clientes e o valor de seus pedidos, apenas onde há correspondência entre as tabelas.

---

### **2. LEFT JOIN (Junção à Esquerda)**
Retorna todos os registros da tabela à esquerda e os correspondentes da tabela à direita. Se não houver correspondência, retorna NULL.

#### **Exemplo:**
```sql
SELECT clientes.nome, pedidos.valor_total
FROM clientes
LEFT JOIN pedidos
ON clientes.id = pedidos.id_cliente;
```
Clientes sem pedidos ainda aparecerão no resultado, com `valor_total` sendo `NULL`.

---

### **3. RIGHT JOIN (Junção à Direita)**
Retorna todos os registros da tabela à direita e os correspondentes da tabela à esquerda. Se não houver correspondência, retorna NULL.

#### **Exemplo:**
```sql
SELECT clientes.nome, pedidos.valor_total
FROM clientes
RIGHT JOIN pedidos
ON clientes.id = pedidos.id_cliente;
```
Pedidos sem cliente correspondente (caso exista) ainda aparecerão, com o `nome` sendo `NULL`.

---

### **4. Subconsultas (Subqueries)**
Subconsultas são consultas dentro de outras consultas, utilizadas para retornar valores intermediários.

#### **a) Subconsulta com WHERE**
```sql
SELECT nome
FROM clientes
WHERE id IN (SELECT id_cliente FROM pedidos WHERE valor_total > 100);
```
Seleciona os nomes dos clientes que têm pedidos com valor acima de 100.

#### **b) Subconsulta como Coluna**
```sql
SELECT nome,
       (SELECT COUNT(*) FROM pedidos WHERE pedidos.id_cliente = clientes.id) AS total_pedidos
FROM clientes;
```
Retorna o nome de cada cliente e o número de pedidos que ele realizou.

#### **c) Subconsulta na cláusula FROM**
```sql
SELECT media.valor_medio
FROM (
    SELECT AVG(valor_total) AS valor_medio
    FROM pedidos
) AS media;
```
Calcula a média de valor dos pedidos usando uma subconsulta como tabela temporária.

---

### **Considerações Finais**
Junções e subconsultas são ferramentas poderosas que permitem trabalhar com dados distribuídos em múltiplas tabelas. Saber quando usar uma ou outra depende da necessidade do problema. Em geral:
- Use `JOIN` quando quiser combinar dados de múltiplas tabelas com correspondência direta.
- Use `LEFT` ou `RIGHT JOIN` quando quiser garantir todos os registros de uma das tabelas.
- Use `SUBQUERIES` para cálculos intermediários, filtragens baseadas em agregações ou quando a lógica exigir múltiplas etapas.
