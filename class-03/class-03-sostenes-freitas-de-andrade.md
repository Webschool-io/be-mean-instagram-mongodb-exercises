# MongoDB - Aula 03 - Exercicio
Autor: Sóstenes Freitas de Andrade usuario:(sostenesfreitas)


## Liste todos Pokemons com a altura menor que 0.5;
```
BlackArch(mongod-3.2.1) be-mean-pokemons> query = {"height":{$lt:0.5}}

BlackArch(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
      "_id": ObjectId("56cc5195935d3f5fe428cc50"),
      "name": "voltorb",
      "attack": 12,
      "defense": 11,
      "height": 0.3
}
{
      "_id": ObjectId("56cc5195935d3f5fe428cc51"),
      "name": "evee",
      "attack": 30,
      "defense": 20,
      "height": 0.4
}
{
      "_id": ObjectId("56cc5195935d3f5fe428cc52"),
      "name": "weezing",
      "attack": 33,
      "defense": 12,
      "height": 0.4
}
Fetched 3 record(s) in 3ms
```
## Liste todos Pokemons com a altura maior ou igual que 0.5
```
BlackArch(mongod-3.2.1) be-mean-pokemons> var query = {"height":{$gte:0.5}}
BlackArch(mongod-3.2.1) be-mean-pokemons> query

BlackArch(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
      "_id": ObjectId("56c64b4304e657a13e0cd708"),
      "name": "darkrai",
      "attack": 200,
      "defense": 120,
      "height": 10,
      "description": "Melhor pokemon ever"
}
{
      "_id": ObjectId("56c64b6904e657a13e0cd709"),
      "name": "charizard",
      "attack": 150,
      "defense": 50,
      "height": 89
}
{
      "_id": ObjectId("56c64baa04e657a13e0cd70c"),
      "name": "umbreon",
      "attack": 77,
      "defense": 55,
      "height": 44
}
{
      "_id": ObjectId("56c64bde04e657a13e0cd70d"),
      "name": "vaporeon",
      "attack": 87,
      "defense": 29,
      "height": 54
}
{
      "_id": ObjectId("56c64bf304e657a13e0cd70e"),
      "name": "mew",
      "attack": 200,
      "defense": 209,
      "height": 4
}
{
      "_id": ObjectId("56c64c0404e657a13e0cd70f"),
      "name": "mewtwo",
      "attack": 300,
      "defense": 290,
      "height": 40
}
{
      "_id": ObjectId("56c64c2904e657a13e0cd710"),
      "name": "arceus",
      "attack": 400,
      "defense": 390,
      "height": 400
}
Fetched 7 record(s) in 2ms
```
## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** attack maior ou igual a 55
```
BlackArch(mongod-3.2.1) be-mean-pokemons> query = {$and: [ { height: {$lte: 0.5} }, { attack: {$gte: 55 } } ] }

BlackArch(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
      "_id": ObjectId("56cc5195935d3f5fe428cc50"),
      "name": "Pikachu",
      "type": "electric",
      "attack": 55,
      "defense": 30,
      "height": 0.4
}

Fetched 1 record(s) in 2ms
```
## Liste todos Pokemons com o name `Pikachu` OU com altura menor ou igual que 0.5
```
BlackArch(mongod-3.2.1) be-mean-pokemons> var query = {$or:[{"name":"pikachu"},{"height":{$lte:0.5}}]}
BlackArch(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
      "_id": ObjectId("56cc5195935d3f5fe428cc50"),
      "name": "voltorb",
      "attack": 12,
      "defense": 11,
      "height": 0.3
}
{
      "_id": ObjectId("56cc5195935d3f5fe428cc51"),
      "name": "evee",
      "attack": 30,
      "defense": 20,
      "height": 0.4
}
{
      "_id": ObjectId("56cc5195935d3f5fe428cc52"),
      "name": "weezing",
      "attack": 33,
      "defense": 12,
      "height": 0.4
}
{
      "_id": ObjectId("56cc55ecc8b1a12ce58bb459"),
      "name": "pikachu",
      "attack": 22,
      "defense": 11,
      "height": 0.3
}
Fetched 4 record(s) in 2ms
```
## Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5
```

BlackArch(mongod-3.2.1) be-mean-pokemons> var query = {$and:[{"attack":{$gte:48}},{"height":{$lte:0.5}}]}
BlackArch(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
      "_id": ObjectId("56cc5763c8b1a12ce58bb45a"),
      "name": "ferrothorn",
      "attack": 50,
      "defense": 40,
      "height": 0.4
}
Fetched 1 record(s) in 1ms
```
