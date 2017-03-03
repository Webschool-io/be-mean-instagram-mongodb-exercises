# MongoDB - Aula 02 - Exercício
autor: Jefferson da Silva

## 'Criando' o database (passo 1)
```
jefferson(mongod-3.2.1) test> use be-mean-pokemons
switched to db be-mean-pokemons
```

## Listagem das databases (passo 2)
```
jefferson(mongod-3.2.1) be-mean-pokemons> show dbs
be-mean           → 0.004GB
be-mean-instagram → 0.000GB
local             → 0.000GB
```

## Listagem das coleções (passo 3)
```
jefferson(mongod-3.2.1) be-mean-pokemons> show collections
```

## Cadastro dos pokemons (passo 4)
```
jefferson(mongod-3.2.1) be-mean-pokemons> var pokemonsArray = [
...   {
...     name: 'Fearow',
...     description: "Fearow is recognized by its long neck and elongated beak.",
...     attack: 5,
...     defense: 3,
...     height: 1.2
...   },
...   {
...     name: 'Sandshrew',
...     description: "Sandshrew's body is configured to absorb water without waste, enabling it to survive in an arid desert. ",
...     attack: 4,
...     defense: 4,
...     height: 0.6
...   },
...   {
...     name: 'Nidoqueen',
...     description: "Nidoqueen's body is encased in extremely hard scales.",
...     attack: 5,
...     defense: 4,
...     height: 1.3
...   },
...   {
...     name: 'Oddish',
...     description: "During the daytime, Oddish buries itself in soil to absorb nutrients from the ground using its entire body.",
...     attack: 3,
...     defense: 3,
...     height: 0.5
...   },
...   {
...     name: 'Parasect',
...     description: "Parasect is known to infest large trees en masse and drain nutrients from the lower trunk and roots.",
...     attack: 5,
...     defense: 4,
...     height: 1.0
...   }
... ]
```
```
jefferson(mongod-3.2.1) be-mean-pokemons> db.pokemons.insert(pokemonsArray)
Inserted 1 record(s) in 858ms
BulkWriteResult({
  "writeErrors": [ ],
  "writeConcernErrors": [ ],
  "nInserted": 5,
  "nUpserted": 0,
  "nMatched": 0,
  "nModified": 0,
  "nRemoved": 0,
  "upserted": [ ]
})
```


## Lista dos pokemons (passo 5)
```
jefferson(mongod-3.2.1) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("56bb0e84681eaca5d83a6912"),
  "name": "Fearow",
  "description": "Fearow is recognized by its long neck and elongated beak.",
  "attack": 5,
  "defense": 3,
  "height": 1.2
}
{
  "_id": ObjectId("56bb0e84681eaca5d83a6913"),
  "name": "Sandshrew",
  "description": "Sandshrew's body is configured to absorb water without waste, enabling it to survive in an arid desert. ",
  "attack": 4,
  "defense": 4,
  "height": 0.6
}
{
  "_id": ObjectId("56bb0e84681eaca5d83a6914"),
  "name": "Nidoqueen",
  "description": "Nidoqueen's body is encased in extremely hard scales.",
  "attack": 5,
  "defense": 4,
  "height": 1.3
}
{
  "_id": ObjectId("56bb0e84681eaca5d83a6915"),
  "name": "Oddish",
  "description": "During the daytime, Oddish buries itself in soil to absorb nutrients from the ground using its entire body.",
  "attack": 3,
  "defense": 3,
  "height": 0.5
}
{
  "_id": ObjectId("56bb0e84681eaca5d83a6916"),
  "name": "Parasect",
  "description": "Parasect is known to infest large trees en masse and drain nutrients from the lower trunk and roots.",
  "attack": 5,
  "defense": 4,
  "height": 1
}
Fetched 5 record(s) in 44ms
```

## Busca do pokemon (passo 6)
```
jefferson(mongod-3.2.1) be-mean-pokemons> var sandshrew = db.pokemons.findOne({ name: "Sandshrew" })
```

## Atualização do pokemon (passo 6)
```
jefferson(mongod-3.2.1) be-mean-pokemons> sandshrew.description = "Tatu do deserto"
Tatu do deserto
```
```
jefferson(mongod-3.2.1) be-mean-pokemons> db.pokemons.save(sandshrew)
Updated 1 existing record(s) in 14ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```
