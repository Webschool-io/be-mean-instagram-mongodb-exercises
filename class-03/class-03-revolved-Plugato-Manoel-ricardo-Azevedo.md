# MongoDB - Aula 03 - Exercício
autor: Manoel Ricardo De Azevedo

## Liste todos Pokemons com a altura **menor que** 0.5;
```
> var query = { height: {$lt: 0.5} }                                            
> db.pokemons.find(query)
{
    "_id": ObjectId("56bd150a97a021d13054f170"),
    "name": "Pikachu",
    "description": "Rato eletrico bem fofinho",
    "type": "electric",
    "attack": 55,
    "height": 0.4
}
{
    "_id": ObjectId("56bd16555b1107c4f6701893"),
    "name": "Bulbassauro",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 49,
    "height": 0.4
}
{
    "_id": ObjectId("56bd16f25b1107c4f6701896"),
    "name": "Caterpie",
    "description": "Larva lutadora",
    "type": "inseto",
    "attack": 30,
    "height": 0.3,
    "defense": 35
}
Fetched 3 record(s) in 12ms                                                     
```
## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
> var query = { height: {$gte: 0.5} }
> db.pokemons.find(query)
{
  "_id": ObjectId("5647b5669dd42619b4f09b75"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "attack": 40,
  "defense": 20,
  "height": 0.6
}
{
  "_id": ObjectId("5647b5899dd42619b4f09b76"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "attack": 60,
  "defense": 30,
  "height": 0.5
}
Fetched 2 record(s) in 8ms

```
## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** attack igual a 55
```
> var query = {$and: [ { height: {$lte: 0.5} }, { attack: 55 } ] }
> db.pokemons.find(query)
{
    "_id": ObjectId("56bd150a97a021d13054f170"),
    "name": "Pikachu",
    "description": "Rato eletrico bem fofinho",
    "type": "electric",
    "attack": 55,
    "defense": 30,
    "height": 0.4
}
Fetched 1 record(s) in 5ms
```
## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```
> var query = {$or: [ {name: "Pickachu" }, { height: {$lte: 0.5} } ] }
> db.pokemons.find(query)
{
  "_id": ObjectId("5647b5319dd42619b4f09b74"),
  "name": "Pikachu",
  "description": "Rato eletrico bem fofinho",
  "attack": 55,
  "defense": 30,
  "height": 0.5
}
{
  "_id": ObjectId("5647b5899dd42619b4f09b76"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "attack": 60,
  "defense": 30,
  "height": 0.5
}
{
    "_id": ObjectId("56bd16555b1107c4f6701893"),
    "name": "Bulbassauro",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 49,
    "height": 0.4
}
{
    "_id": ObjectId("56bd16f25b1107c4f6701896"),
    "name": "Caterpie",
    "description": "Larva lutadora",
    "type": "inseto",
    "attack": 30,
    "height": 0.3,
    "defense": 35
}
Fetched 4 record(s) in 15ms
```
## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```
var query = {$and: [ {attack: {$gte: 48 } }, { height: {$lte: 0.5 } } ] }
db.pokemons.find(query)
{
  "_id": ObjectId("5647b5319dd42619b4f09b74"),
  "name": "Pikachu",
  "description": "Rato eletrico bem fofinho",
  "attack": 55,
  "defense": 30,
  "height": 0.5
}
{
    "_id": ObjectId("56bd16555b1107c4f6701893"),
    "name": "Bulbassauro",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 49,
    "height": 0.4
}
{
  "_id": ObjectId("5647b5899dd42619b4f09b76"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "attack": 60,
  "defense": 30,
  "height": 0.5
} 
Fetched 3 record(s) in 5ms

```
