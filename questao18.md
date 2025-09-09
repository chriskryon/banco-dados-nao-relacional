## Questão 18

**Enunciado:**
Paginação: Liste os produtos ordenados pelo preço em ordem decrescente, exibindo apenas os 2 produtos mais caros.

**Resposta:**
```js
db.produtos.find().sort({ valor: -1 }).limit(2)
```

**Output:**
```json
{
  "_id": 102,
  "nome": "Teclado Mecânico",
  "valor": 400
}
{
  "_id": 104,
  "nome": "Headset Pro",
  "valor": 350
}
```
