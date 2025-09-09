## Questão 09

**Enunciado:**
Atualização: O cliente Marcos mudou-se para Natal. Atualize sua cidade.

**Resposta:**
```js
db.clientes.updateOne(
  { nome: "Marcos" },
  { $set: { cidade: "Natal" } }
)
```

**Output:**
```json
{
  "acknowledged": true,
  "insertedId": null,
  "matchedCount": 1,
  "modifiedCount": 1,
  "upsertedCount": 0
}
```
