# MongoDB - Aula 03 - Exercício
autor: Vinícius Galvão

## Liste todos Pokemons com a altura **menor que** 0.5

```
MBP-de-Vinicius(mongod-3.0.6) be-mean-instagram> var q = {height: {$lt: 0.5}}
MBP-de-Vinicius(mongod-3.0.6) be-mean-instagram> db.pokemons.find(q)
{
  "_id": ObjectId("5643583ac1a1390994ce24e5"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("564358d3c1a1390994ce24e6"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("56435fe1c1a1390994ce24e9"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 3 record(s) in 2ms
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

```
MBP-de-Vinicius(mongod-3.0.6) be-mean-instagram> var q = {height: {$gte: 0.5}}
MBP-de-Vinicius(mongod-3.0.6) be-mean-instagram> db.pokemons.find(q)
{
  "_id": ObjectId("56435900c1a1390994ce24e7"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("56435974c1a1390994ce24e8"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 2 record(s) in 3ms
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama

```
MBP-de-Vinicius(mongod-3.0.6) be-mean-instagram> var q = {$and: [{height:{$lte:0.5}}, {type: "grama"}]}
MBP-de-Vinicius(mongod-3.0.6) be-mean-instagram> db.pokemons.find(q)
{
  "_id": ObjectId("564358d3c1a1390994ce24e6"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 2ms
```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

```
MBP-de-Vinicius(mongod-3.0.6) be-mean-instagram> var q = {$or: [{name: "Pikachu"}, {attack:{$lte:0.5}}]}
MBP-de-Vinicius(mongod-3.0.6) be-mean-instagram> db.pokemons.find(q)
{
  "_id": ObjectId("5643583ac1a1390994ce24e5"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
Fetched 1 record(s) in 1ms
```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

```
MBP-de-Vinicius(mongod-3.0.6) be-mean-instagram> var q = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
MBP-de-Vinicius(mongod-3.0.6) be-mean-instagram> db.pokemons.find(q)
{
  "_id": ObjectId("5643583ac1a1390994ce24e5"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("564358d3c1a1390994ce24e6"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("56435974c1a1390994ce24e8"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 3 record(s) in 0ms
```
