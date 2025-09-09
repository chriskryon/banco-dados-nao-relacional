## Questão 10

**Enunciado:**
Atualização com $set e $inc: Atualize o cliente chamado Lucas para incluir o campo status: "ativo". Em seguida, incremente sua idade em +1 ano.

**Resposta:**
```js
db.clientes.updateOne(
  { nome: "Lucas" },
  { $set: { status: "ativo" } }
)
db.clientes.updateOne(
  { nome: "Lucas" },
  { $inc: { idade: 1 } }
)
```

**Output:**
```json
{
  "acknowledged": true,
  "insertedId": null,
  "matchedCount": 1,
  "modifiedCount": 0,
  "upsertedCount": 0
}
{
  "acknowledged": true,
  "insertedId": null,
  "matchedCount": 1,
  "modifiedCount": 1,
  "upsertedCount": 0
}
```
