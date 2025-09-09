## Questão 17

**Enunciado:**
Agregação com $lookup e $group: Liste as vendas e calcule o total de produtos vendidos por categoria

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
  },
  { $unwind: "$produto" },
  {
    $group: {
      _id: "$produto.categoria",
      vendas: {
        $push: {
          clienteId: "$clienteId",
          produtoId: "$produtoId",
          quantidade: "$quantidade",
          data: "$data"
        }
      },
      totalVendidos: { $sum: "$quantidade" }
    }
  }
])
```

**Output:**
```json
{
  "_id": null,
  "vendas": [
    {
      "clienteId": 1,
      "produtoId": 101,
      "quantidade": 1,
      "data": "2024-05-01"
    },
    {
      "clienteId": 1,
      "produtoId": 103,
      "quantidade": 2,
      "data": "2024-05-03"
    },
    {
      "clienteId": 2,
      "produtoId": 102,
      "quantidade": 1,
      "data": "2024-05-02"
    },
    {
      "clienteId": 4,
      "produtoId": 104,
      "quantidade": 2,
      "data": "2024-05-05"
    }
  ],
  "totalVendidos": 6
}
```
