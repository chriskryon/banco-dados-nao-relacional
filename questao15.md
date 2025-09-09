## Questão 15

**Enunciado:**
Agregação com $lookup: Liste as vendas com os dados completos do produto comprado.

**Resposta:**
```js
db.vendas.aggregate([
  {
    $lookup: {
      from: "produtos",
      localField: "produtoId",
      foreignField: "_id",
      as: "produto"
    }
  }
])
```
