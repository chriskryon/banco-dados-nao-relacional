# Revisão - Banco de Dados Não Relacional

Christopher Costa Silva

Questão 1

```sql
use rede_games
switched to db rede_games
```

---

Questão 2 – Consulta com Filtro Liste todos os clientes que moram em Fortaleza.

```sql
db.clientes.find({ cidade: "Fortaleza" })

{
  _id: 1,
  nome: 'Marcos',
  idade: 25,
  cidade: 'Fortaleza'
}
{
  _id: 4,
  nome: 'Ana',
  idade: 27,
  cidade: 'Fortaleza'
}
```

---

Questão 3 – Consulta com $and Liste todos os clientes que moram em Fortaleza E possuem idade maior que 25 anos.

```sql
db.clientes.find({
  $and: [
    { cidade: "Fortaleza" },
    { idade: { $gt: 25 } }
  ]
})

{
  _id: 4,
  nome: 'Ana',
  idade: 27,
  cidade: 'Fortaleza'
}
```

---

Questão 4 – Projeção Mostre apenas o nome e o preco dos produtos da categoria Periféricos.

```sql
db.produtos.find(
  { categoria: "Periféricos" },
  { nome: 1, preco: 1, _id: 0 }
)


{
  nome: 'Mouse Gamer',
  preco: 250
}
{
  nome: 'Teclado Mecânico',
  preco: 400
}
{
  nome: 'Headset Pro',
  preco: 350
}
```

---

Questão 5 – Consulta com $gte e $lte Liste todos os produtos cujo preço esteja entre 200 e 400 reais (inclusive).

```sql
db.produtos.find({
  preco: { $gte: 200, $lte: 400 }
})

{
  _id: 101,
  nome: 'Mouse Gamer',
  categoria: 'Periféricos',
  preco: 250
}
{
  _id: 102,
  nome: 'Teclado Mecânico',
  categoria: 'Periféricos',
  preco: 400
}
{
  _id: 104,
  nome: 'Headset Pro',
  categoria: 'Periféricos',
  preco: 350
}
{
  _id: 105,
  nome: 'FIFA 25',
  categoria: 'Jogos',
  preco: 300
}
```

---

Questão 6 – Consulta com $nor e $not Liste todos os clientes que não moram em Fortaleza e não possuem idade inferior a 20 anos.

```sql
db.clientes.find({
  $nor: [
    { cidade: "Fortaleza" },
    { idade: { $not: { $gte: 20 } } }
  ]
})

{
  _id: 2,
  nome: 'Julia',
  idade: 30,
  cidade: 'São Paulo'
}
```

---

Questão 7 – Consulta com $exists e $type Verifique se há clientes com o campo clienteVip. Depois, liste apenas os documentos em que o campo idade seja do tipo number.

```sql
db.clientes.find({ clienteVip: { $exists: true } })

db.clientes.find({ idade: { $type: "number" } })


{
  _id: 1,
  nome: 'Marcos',
  idade: 25,
  cidade: 'Fortaleza'
}
{
  _id: 2,
  nome: 'Julia',
  idade: 30,
  cidade: 'São Paulo'
}
{
  _id: 3,
  nome: 'Lucas',
  idade: 19,
  cidade: 'Recife'
}
{
  _id: 4,
  nome: 'Ana',
  idade: 27,
  cidade: 'Fortaleza'
}
```

---

Questão 8 – Inserção de Novo Cliente Adicione um novo cliente chamado Jorge, 22 anos, morador de Salvador.

```sql
db.clientes.insertOne({
  _id: 5,
  nome: "Jorge",
  idade: 22,
  cidade: "Salvador"
})

{
  acknowledged: true,
  insertedId: 5
}
```

---

Questão 9 – Atualização O cliente Marcos mudou-se para Natal. Atualize sua cidade.

```sql
db.clientes.updateOne(
  { nome: "Marcos" },
  { $set: { cidade: "Natal" } }
)

{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
```

---

Questão 10 – Atualização com $set e $inc Atualize o cliente chamado Lucas para incluir o campo status: "ativo". Em seguida, incremente sua idade em +1 ano.

```sql
db.clientes.updateOne(
  { nome: "Lucas" },
  { $set: { status: "ativo" } }
)

{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 0,
  upsertedCount: 0
}

db.clientes.updateOne(
  { nome: "Lucas" },
  { $inc: { idade: 1 } }
)

{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
```

---

Questão 11 – Atualização com replaceOne Substitua completamente o documento da cliente Julia por um novo documento: { nome: "Julia", idade: 31, cidade: "Rio de Janeiro", clienteVip: true }

```sql
db.clientes.replaceOne(
  { nome: "Julia" },
  { nome: "Julia", idade: 31, cidade: "Rio de Janeiro", clienteVip: true }
)

{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
```

---

Questão 12 – Atualização com $rename e $unset Renomeie o campo preco para valor em todos os produtos. Depois, remova o campo categoria dos documentos

```sql
db.produtos.updateMany(
  {},
  { $rename: { "preco": "valor" } }
)

{
  acknowledged: true,
  insertedId: null,
  matchedCount: 5,
  modifiedCount: 0,
  upsertedCount: 0
}

db.produtos.updateMany(
  {},
  { $unset: { categoria: "" } }
)

{
  acknowledged: true,
  insertedId: null,
  matchedCount: 5,
  modifiedCount: 0,
  upsertedCount: 0
}
```

---

Questão 13 – Exclusão Remova o produto FIFA 25 do catálogo.

```sql
db.produtos.deleteOne({ nome: "FIFA 25" })

{
  acknowledged: true,
  deletedCount: 1
}
```

---

Questão 14 – Operadores Lógicos Liste os clientes que são de São Paulo OU de Recife.

```sql
db.clientes.find({
  $or: [
    { cidade: "São Paulo" },
    { cidade: "Recife" }
  ]
})

{
  _id: 3,
  nome: 'Lucas',
  idade: 21,
  cidade: 'Recife',
  status: 'ativo'
}
```

---

Questão 15 – Agregação com $lookup Liste as vendas com os dados completos do produto comprado.

```sql
db.vendas.aggregate([
  {
    $lookup: {
      from: "produtos",
      localField: "produtoId",
      foreignField: "_id",
      as: "produto"
    }
  }
])
```

---

Questão 16 – Agrupamento Calcule o total de produtos vendidos por categoria.

```sql
db.produtos.aggregate([
  {
    $group: {
      _id: "$categoria",
      totalVendidos: { $sum: 1 } 
    }
  }
])

{
  _id: null,
  totalVendidos: 4
}
```

---

Questão 17 – Agregação com $lookup e $group Liste as vendas e calcule o total de produtos vendidos por categoria

```sql
db.vendas.aggregate([
  {
    $lookup: {
      from: "produtos",
      localField: "produtoId",
      foreignField: "_id",
      as: "produto"
    }
  },
  { $unwind: "$produto" },
  {
    $group: {
      _id: "$produto.categoria",
      vendas: {
        $push: {
          clienteId: "$clienteId",
          produtoId: "$produtoId",
          quantidade: "$quantidade",
          data: "$data"
        }
      },
      totalVendidos: { $sum: "$quantidade" }
    }
  }
])

{
  _id: null,
  vendas: [
    {
      clienteId: 1,
      produtoId: 101,
      quantidade: 1,
      data: '2024-05-01'
    },
    {
      clienteId: 1,
      produtoId: 103,
      quantidade: 2,
      data: '2024-05-03'
    },
    {
      clienteId: 2,
      produtoId: 102,
      quantidade: 1,
      data: '2024-05-02'
    },
    {
      clienteId: 4,
      produtoId: 104,
      quantidade: 2,
      data: '2024-05-05'
    }
  ],
  totalVendidos: 6
}
```

---

Questão 18 – Paginação Liste os produtos ordenados pelo preço em ordem decrescente, exibindo apenas os 2 produtos mais caros.

```sql
db.produtos.find().sort({ valor: -1 }).limit(2)

{
  _id: 102,
  nome: 'Teclado Mecânico',
  valor: 400
}
{
  _id: 104,
  nome: 'Headset Pro',
  valor: 350
}
```

---

Questão 19 – Paginação com skip Liste os produtos ordenados pelo valor (antes chamado de preco) em ordem decrescente, exibindo apenas do 3º ao 5º produto mais caro.

```sql
db.produtos.find().sort({ valor: -1 }).skip(2).limit(2)

{
  _id: 101,
  nome: 'Mouse Gamer',
  valor: 250
}
{
  _id: 103,
  nome: 'CS:GO Deluxe',
  valor: 120
}
```

---

