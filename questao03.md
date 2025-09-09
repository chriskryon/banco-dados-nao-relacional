## Questão 03

**Enunciado:**
Consulta com $and: Liste todos os clientes que moram em Fortaleza E possuem idade maior que 25 anos.

**Resposta:**
```js
db.clientes.find({
  $and: [
    { cidade: "Fortaleza" },
    { idade: { $gt: 25 } }
  ]
})
```

**Output:**
```json
{
  "_id": 4,
  "nome": "Ana",
  "idade": 27,
  "cidade": "Fortaleza"
}
```
