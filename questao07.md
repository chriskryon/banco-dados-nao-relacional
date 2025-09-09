## Questão 07

**Enunciado:**
Consulta com $exists e $type: Verifique se há clientes com o campo clienteVip. Depois, liste apenas os documentos em que o campo idade seja do tipo number.

**Resposta:**
```js
db.clientes.find({ clienteVip: { $exists: true } })
db.clientes.find({ idade: { $type: "number" } })
```

**Output:**
```json
{
  "_id": 1,
  "nome": "Marcos",
  "idade": 25,
  "cidade": "Fortaleza"
}
{
  "_id": 2,
  "nome": "Julia",
  "idade": 30,
  "cidade": "São Paulo"
}
{
  "_id": 3,
  "nome": "Lucas",
  "idade": 19,
  "cidade": "Recife"
}
{
  "_id": 4,
  "nome": "Ana",
  "idade": 27,
  "cidade": "Fortaleza"
}
```
