**Funções Agregadas e Agrupamento de Resultados em SQL**

Em SQL, **funções agregadas** permitem realizar cálculos em conjuntos de valores de uma coluna. Já o **agrupamento de resultados** com `GROUP BY` e a ordenação com `ORDER BY` são usados para organizar e interpretar esses dados de forma significativa.

---

### **1. Funções Agregadas**

#### **a) COUNT**
Conta o número de registros.
```sql
SELECT COUNT(*) FROM pedidos;
```
Retorna a quantidade total de pedidos.

#### **b) SUM**
Soma os valores de uma coluna numérica.
```sql
SELECT SUM(valor_total) FROM pedidos;
```
Soma o valor de todos os pedidos.

#### **c) AVG**
Calcula a média dos valores de uma coluna numérica.
```sql
SELECT AVG(valor_total) FROM pedidos;
```
Retorna o valor médio dos pedidos.

#### **d) MIN**
Retorna o menor valor de uma coluna.
```sql
SELECT MIN(valor_total) FROM pedidos;
```
Retorna o menor valor encontrado nos pedidos.

#### **e) MAX**
Retorna o maior valor de uma coluna.
```sql
SELECT MAX(valor_total) FROM pedidos;
```
Retorna o maior valor encontrado nos pedidos.

---

### **2. Agrupamento de Resultados: GROUP BY**
Usado para agrupar linhas com valores iguais em colunas específicas, geralmente utilizado com funções agregadas.

#### **Exemplo:**
```sql
SELECT id_cliente, COUNT(*) AS total_pedidos
FROM pedidos
GROUP BY id_cliente;
```
Agrupa os pedidos por cliente e conta quantos pedidos cada um fez.

---

### **3. Ordenação de Resultados: ORDER BY**
Organiza os resultados de uma consulta em ordem crescente (padrão) ou decrescente (`DESC`).

#### **Exemplo:**
```sql
SELECT nome, idade
FROM clientes
ORDER BY idade DESC;
```
Lista os clientes do mais velho para o mais novo.

---

### **4. GROUP BY com HAVING**
A cláusula `HAVING` é usada para filtrar os resultados após o agrupamento.

#### **Exemplo:**
```sql
SELECT id_cliente, COUNT(*) AS total_pedidos
FROM pedidos
GROUP BY id_cliente
HAVING COUNT(*) > 5;
```
Mostra apenas os clientes que fizeram mais de 5 pedidos.

---

### **Considerações Finais**
Funções agregadas e agrupamento de resultados são essenciais para análise de dados em SQL. Elas permitem resumir, comparar e ordenar grandes volumes de informação de maneira clara e eficiente. Combinar `GROUP BY`, `HAVING` e `ORDER BY` com funções como `COUNT`, `SUM`, `AVG`, `MIN` e `MAX` amplia significativamente a capacidade de extração de informações dos dados armazenados.
