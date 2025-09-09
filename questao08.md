## Questão 08

**Enunciado:**
Inserção de Novo Cliente: Adicione um novo cliente chamado Jorge, 22 anos, morador de Salvador.

**Resposta:**
```js
db.clientes.insertOne({
  _id: 5,
  nome: "Jorge",
  idade: 22,
  cidade: "Salvador"
})
```

**Output:**
```json
{
  "acknowledged": true,
  "insertedId": 5
}
```
