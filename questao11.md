## Questão 11

**Enunciado:**
Atualização com replaceOne: Substitua completamente o documento da cliente Julia por um novo documento: { nome: "Julia", idade: 31, cidade: "Rio de Janeiro", clienteVip: true }

**Resposta:**
```js
db.clientes.replaceOne(
  { nome: "Julia" },
  { nome: "Julia", idade: 31, cidade: "Rio de Janeiro", clienteVip: true }
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
