## Questão 16

**Enunciado:**
Agrupamento: Calcule o total de produtos vendidos por categoria.

**Resposta:**
```js
db.produtos.aggregate([
  {
    $group: {
      _id: "$categoria",
      totalVendidos: { $sum: 1 }
    }
  }
])
```

**Output:**
```json
{
  "_id": null,
  "totalVendidos": 4
}
```
