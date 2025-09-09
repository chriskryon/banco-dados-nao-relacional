## Questão 12

**Enunciado:**
Atualização com $rename e $unset: Renomeie o campo preco para valor em todos os produtos. Depois, remova o campo categoria dos documentos.

**Resposta:**
```js
db.produtos.updateMany(
  {},
  { $rename: { "preco": "valor" } }
)
db.produtos.updateMany(
  {},
  { $unset: { categoria: "" } }
)
```

**Output:**
```json
{
  "acknowledged": true,
  "insertedId": null,
  "matchedCount": 5,
  "modifiedCount": 0,
  "upsertedCount": 0
}
{
  "acknowledged": true,
  "insertedId": null,
  "matchedCount": 5,
  "modifiedCount": 0,
  "upsertedCount": 0
}
```
