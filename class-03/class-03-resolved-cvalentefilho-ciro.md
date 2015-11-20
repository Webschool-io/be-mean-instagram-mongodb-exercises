#MongoDB - Aula 03 - Exercício
autor: Ciro Valente Filho

## Liste todos Pokemons com a altura menor que 0.5; (passo 1)
```
be-mean-pokemons> var query = { height: {$lt: 0.5}  }

be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564a7844d6905d59d846bf10"),
  "name": "Mew",
  "description": "pokemon rosa do mal",
  "type": "Psiquico",
  "attack": 90,
  "height": 0.4
}
Fetched 1 record(s) in 34ms

```
## Liste todos Pokemons com a altura maior ou igual que 0.5; (passo 2)

```

 be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564a7826d6905d59d846bf0f"),
  "name": "Totodile",
  "description": "jacare Azul",
  "type": "Agua",
  "attack": 30,
  "height": 0.9
}
{
  "_id": ObjectId("564a7877d6905d59d846bf11"),
  "name": "Charizard ",
  "description": "pokemon fodao",
  "type": "Fogo",
  "attack": 20,
  "height": 90
}
{
  "_id": ObjectId("564a787cd6905d59d846bf12"),
  "name": "Jigglypuff ",
  "description": "pokemon chato pacas",
  "type": "Normal",
  "attack": 20,
  "height": 0.5
}
{
  "_id": ObjectId("564a79603931d0f16891c3dc"),
  "name": "Snorlax",
  "description": "Gato Grande",
  "type": "Normal",
  "attack": 100,
  "height": 1000
}

Fetched 4 record(s) in 7ms

```
## Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama; (passo 3)
```

var query = {$and: [{ height:{ $gte:0.5 } } , { type: "grama" } ]}

be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms

```
## Alterado a query anterior para ocorrer retorno de dados

```
var query = { $or : [{heigth: {$gte: 0.5}}, {type: 'grama'}]  }
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564f10d8117ee24336fbeeb7"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}

```

## Liste todos Pokemons com name 'Pikachu' OU com attack menor ou igual que 0.5 (passo 4)

```
be-mean-pokemons> var query = {$or: [{ name: 'Pikachu' } , { attack: {$lte: 0.5}} ]}
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564f1081117ee24336fbeeb6"),
  "name": "Pikachu",
  "description": "Rato eletrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4
}
Fetched 1 record(s) in 3ms

```


## Liste todos Pokemons com attack maior ou igual que 48 E com height menor ou igual que 0.5 (passo 5)

```
be-mean-pokemons> var query = { $and : [{heigth: {$gte: 48}}, {heigth: {$lte: 0.5}}]  }
be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms

```