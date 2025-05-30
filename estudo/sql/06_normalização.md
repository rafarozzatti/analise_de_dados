**Normalização em Banco de Dados: 1FN, 2FN e 3FN**

A normalização é um processo utilizado no projeto de bancos de dados relacionais para organizar os dados e eliminar redundâncias. Seu objetivo é dividir os dados em tabelas relacionadas de forma que seja evitada a repetição desnecessária de informações e sejam prevenidos problemas de atualização, inserção e exclusão.

As formas normais (FNs) são as etapas desse processo. As três primeiras formas normais são as mais utilizadas: **Primeira Forma Normal (1FN)**, **Segunda Forma Normal (2FN)** e **Terceira Forma Normal (3FN)**.

---

### **1. Primeira Forma Normal (1FN)**

**Regra:** Eliminar grupos repetitivos e garantir que cada campo contenha apenas um valor (valores atômicos).

**Exemplo de tabela não normalizada:**
| Cliente_ID | Nome       | Telefones         |
|------------|------------|-------------------|
| 1          | Ana Souza  | 9999-0001, 9999-0002 |

**Problema:** A coluna "Telefones" possui mais de um valor.

**Tabela em 1FN:**
| Cliente_ID | Nome       | Telefone   |
|------------|------------|------------|
| 1          | Ana Souza  | 9999-0001  |
| 1          | Ana Souza  | 9999-0002  |

Agora cada campo possui apenas um valor, e o grupo repetitivo foi eliminado.

---

### **2. Segunda Forma Normal (2FN)**

**Requisitos:**
- Estar na 1FN;
- Eliminar dependências parciais, ou seja, todos os atributos não-chave devem depender da tabela inteira (chave primária completa).

**Exemplo de tabela em 1FN:**
| Pedido_ID | Produto_ID | Nome_Produto | Quantidade |
|-----------|-------------|--------------|------------|
| 101       | 1           | Teclado      | 2          |
| 101       | 2           | Mouse        | 1          |

**Problema:** "Nome_Produto" depende apenas de "Produto_ID", e não da chave composta (Pedido_ID + Produto_ID).

**Tabelas em 2FN:**

**Pedidos_Produtos:**
| Pedido_ID | Produto_ID | Quantidade |
|-----------|-------------|------------|
| 101       | 1           | 2          |
| 101       | 2           | 1          |

**Produtos:**
| Produto_ID | Nome_Produto |
|------------|---------------|
| 1          | Teclado       |
| 2          | Mouse         |

Agora, os dados estão organizados de forma que cada atributo depende da chave primária completa da sua respectiva tabela.

---

### **3. Terceira Forma Normal (3FN)**

**Requisitos:**
- Estar na 2FN;
- Eliminar dependências transitivas, ou seja, nenhum campo não-chave deve depender de outro campo não-chave.

**Exemplo de tabela em 2FN:**
| Aluno_ID | Nome_Aluno | Curso_ID | Nome_Curso |
|----------|-------------|----------|------------|
| 1        | João Silva  | 10       | Engenharia |

**Problema:** "Nome_Curso" depende de "Curso_ID", que é um campo não-chave.

**Tabelas em 3FN:**

**Alunos:**
| Aluno_ID | Nome_Aluno | Curso_ID |
|----------|-------------|----------|
| 1        | João Silva  | 10       |

**Cursos:**
| Curso_ID | Nome_Curso  |
|----------|-------------|
| 10       | Engenharia  |

Agora todas as dependências estão diretamente ligadas à chave primária, e o modelo está devidamente normalizado até a 3FN.

---

### **Considerações Finais**

A normalização é essencial para um projeto de banco de dados eficiente e organizado. Apesar de existirem formas normais mais avançadas (como 4FN e 5FN), a maioria dos sistemas relacionais funciona muito bem até a 3FN. Seguindo esses princípios, é possível garantir integridade, reduzir redundância e melhorar a manutenção do banco de dados.
