# MongoDB - Aula 03 - Exercício
autor: Ivan Diniz

## Liste todos Pokemons com a altura **menor que** 0.5;
```
$ var query = {height: {$lt: .5}}
$ db.pokemons.find(query)

{
  "_id": ObjectId("5675fff4c095c1d582e7932c"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("567600cfc095c1d582e7932d"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("567609fac095c1d582e79330"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 3 record(s) in 197ms

```
## Liste todos Pokemons com a altura **maior ou igual que** 0.5

```
$ var query = {height: {$gte: .5}}
$ db.pokemons.find(query)

{
  "_id": ObjectId("5676012ac095c1d582e7932e"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("5676018bc095c1d582e7932f"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 2 record(s) in 15ms
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama

```
$ var query = {$and : [ { height: {$lte : .5} } , { type : "grama" } ] }
$ db.pokemons.find(query)

{
  "_id": ObjectId("567600cfc095c1d582e7932d"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 21ms
	
```
## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

```
$ var query = { $or : [ {name : "Pikachu"}, { attack : {$lte : .5} } ] }
$ db.pokemons.find(query)

{
  "_id": ObjectId("5675fff4c095c1d582e7932c"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
Fetched 5 record(s) in 8ms

```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

```
$ var query = { $and : [ { attack : {$gte: 48} }, {height: {$lte: .5}} ]}
$ db.pokemons.find(query)

{
  "_id": ObjectId("5675fff4c095c1d582e7932c"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("567600cfc095c1d582e7932d"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("5676018bc095c1d582e7932f"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 3 record(s) in 6ms

```