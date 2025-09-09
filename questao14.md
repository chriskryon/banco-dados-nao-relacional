## Questão 14

**Enunciado:**
Operadores Lógicos: Liste os clientes que são de São Paulo OU de Recife.

**Resposta:**
```js
db.clientes.find({
  $or: [
    { cidade: "São Paulo" },
    { cidade: "Recife" }
  ]
})
```

**Output:**
```json
{
  "_id": 3,
  "nome": "Lucas",
  "idade": 21,
  "cidade": "Recife",
  "status": "ativo"
}
```
