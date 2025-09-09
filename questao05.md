## Questão 05

**Enunciado:**
Consulta com $gte e $lte: Liste todos os produtos cujo preço esteja entre 200 e 400 reais (inclusive).

**Resposta:**
```js
db.produtos.find({
  preco: { $gte: 200, $lte: 400 }
})
```

**Output:**
```json
{
  "_id": 101,
  "nome": "Mouse Gamer",
  "categoria": "Periféricos",
  "preco": 250
}
{
  "_id": 102,
  "nome": "Teclado Mecânico",
  "categoria": "Periféricos",
  "preco": 400
}
{
  "_id": 104,
  "nome": "Headset Pro",
  "categoria": "Periféricos",
  "preco": 350
}
{
  "_id": 105,
  "nome": "FIFA 25",
  "categoria": "Jogos",
  "preco": 300
}
```
