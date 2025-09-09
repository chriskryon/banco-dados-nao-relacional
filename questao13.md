## Questão 13

**Enunciado:**
Exclusão: Remova o produto FIFA 25 do catálogo.

**Resposta:**
```js
db.produtos.deleteOne({ nome: "FIFA 25" })
```

**Output:**
```json
{
  "acknowledged": true,
  "deletedCount": 1
}
```
