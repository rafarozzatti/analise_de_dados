**Comandos UPDATE e DELETE em SQL**

Os comandos `UPDATE` e `DELETE` são essenciais para a manutenção e manipulação de dados em tabelas de um banco de dados relacional. O `UPDATE` é usado para modificar registros existentes, enquanto o `DELETE` remove registros.

Este documento fornece explicações claras e exemplos práticos de ambos os comandos, incluindo o uso da cláusula `WHERE` para garantir alterações precisas.

---

### **1. Comando UPDATE**

O comando `UPDATE` modifica os valores de colunas específicas em uma ou mais linhas de uma tabela.

#### **Sintaxe Básica:**
```sql
UPDATE nome_tabela
SET coluna1 = valor1, coluna2 = valor2, ...
WHERE condição;
```
> ⚠️ Atenção: Sempre use `WHERE` para evitar atualizar todos os registros da tabela por engano.

#### **Exemplo:**
```sql
UPDATE clientes
SET idade = 26
WHERE nome = 'Ana';
```
Atualiza a idade da cliente chamada "Ana" para 26.

#### **Exemplo com múltiplas colunas:**
```sql
UPDATE produtos
SET preco = 19.99, estoque = estoque + 10
WHERE nome = 'Caneta Azul';
```
Atualiza o preço da "Caneta Azul" e adiciona 10 unidades ao estoque.

---

### **2. Comando DELETE**

O comando `DELETE` remove uma ou mais linhas de uma tabela.

#### **Sintaxe Básica:**
```sql
DELETE FROM nome_tabela
WHERE condição;
```
> ⚠️ Atenção: Sem a cláusula `WHERE`, **todos os registros** da tabela serão deletados.

#### **Exemplo:**
```sql
DELETE FROM clientes
WHERE idade < 18;
```
Remove todos os clientes com menos de 18 anos.

#### **Exemplo com múltiplas condições:**
```sql
DELETE FROM produtos
WHERE preco > 100 AND estoque = 0;
```
Remove produtos com preço acima de 100 e estoque zerado.

---

### **3. Sem WHERE (perigoso)**
#### **UPDATE sem WHERE:**
```sql
UPDATE clientes
SET idade = 30;
```
Todos os clientes terão a idade alterada para 30.

#### **DELETE sem WHERE:**
```sql
DELETE FROM clientes;
```
Todos os registros da tabela `clientes` serão apagados. Use com extremo cuidado.

---

### **Considerações Finais**

Os comandos `UPDATE` e `DELETE` são ferramentas poderosas para manipulação de dados, mas exigem atenção ao uso da cláusula `WHERE`. Sempre revise suas instruções antes de executá-las para evitar alterações ou perdas de dados não intencionais. Uma boa prática é testar consultas com `SELECT` antes de executar `UPDATE` ou `DELETE`.
