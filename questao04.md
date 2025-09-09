## Questão 04

**Enunciado:**
Projeção: Mostre apenas o nome e o preco dos produtos da categoria Periféricos.

**Resposta:**
```js
db.produtos.find(
  { categoria: "Periféricos" },
  { nome: 1, preco: 1, _id: 0 }
)
```

**Output:**
```json
{
  "nome": "Mouse Gamer",
  "preco": 250
}
{
  "nome": "Teclado Mecânico",
  "preco": 400
}
{
  "nome": "Headset Pro",
  "preco": 350
}
```
