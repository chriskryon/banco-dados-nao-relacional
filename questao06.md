## Questão 06

**Enunciado:**
Consulta com $nor e $not: Liste todos os clientes que não moram em Fortaleza e não possuem idade inferior a 20 anos.

**Resposta:**
```js
db.clientes.find({
  $nor: [
    { cidade: "Fortaleza" },
    { idade: { $not: { $gte: 20 } } }
  ]
})
```

**Output:**
```json
{
  "_id": 2,
  "nome": "Julia",
  "idade": 30,
  "cidade": "São Paulo"
}
```
