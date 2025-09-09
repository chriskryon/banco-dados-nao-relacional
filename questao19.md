## Questão 19

**Enunciado:**
Paginação com skip: Liste os produtos ordenados pelo valor (antes chamado de preco) em ordem decrescente, exibindo apenas do 3º ao 5º produto mais caro.

**Resposta:**
```js
db.produtos.find().sort({ valor: -1 }).skip(2).limit(2)
```

**Output:**
```json
{
  "_id": 101,
  "nome": "Mouse Gamer",
  "valor": 250
}
{
  "_id": 103,
  "nome": "CS:GO Deluxe",
  "valor": 120
}
```
