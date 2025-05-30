## 📘 O que é NoSQL e MongoDB?

### 🔹 O que é NoSQL?

**NoSQL** é um tipo de banco de dados que não usa o modelo tradicional de tabelas como os bancos relacionais (como o MySQL ou o PostgreSQL). Ele é mais flexível e funciona bem com grandes volumes de dados e aplicações modernas, como redes sociais, jogos, aplicativos e sistemas em tempo real.

Em vez de armazenar os dados em linhas e colunas, o NoSQL usa diferentes formatos. Um dos principais formatos é o de **documentos**, como o **MongoDB**.

---

### 🔹 O que é o MongoDB?

O **MongoDB** é um banco de dados NoSQL que armazena os dados em **documentos parecidos com arquivos JSON** (formato de texto usado para representar dados). Cada documento pode ter diferentes campos, sem a necessidade de um modelo fixo como nas tabelas tradicionais.

---

### 📦 Como o MongoDB organiza os dados:

* **Banco de Dados** → como um diretório principal.
* **Coleção** → como uma pasta com vários arquivos.
* **Documento** → como um arquivo JSON, onde os dados realmente ficam guardados.

Exemplo de um documento no MongoDB:

```json
{
  "titulo": "Dom Casmurro",
  "autor": "Machado de Assis",
  "ano": 1899
}
```

---

### ✅ Vantagens do MongoDB:

* Não precisa de estrutura fixa (você pode mudar os campos dos dados a qualquer momento).
* Fácil de entender por parecer com JSON.
* Muito usado em aplicações web modernas.
* Funciona bem com grandes quantidades de dados.
