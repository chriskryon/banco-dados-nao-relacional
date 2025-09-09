## Questão 02

**Enunciado:**
Consulta com Filtro: Liste todos os clientes que moram em Fortaleza.

**Resposta:**
```js
db.clientes.find({ cidade: "Fortaleza" })
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
  "_id": 4,
  "nome": "Ana",
  "idade": 27,
  "cidade": "Fortaleza"
}
```
