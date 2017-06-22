# MongoDB - Aula 03- Exercício
Autor: Rodrigo A Valente

## Liste todos os pokémons com altura menor que 0.5
```
> var query = {height: {$lt: 0.5}}
> db.pokemons.find(query).pretty()
{
    "_id" : ObjectId("5682f71f2ebc7952c85ba8c1"),
    "name" : "Pikachu",
    "description" : "Rato elétrico bem fofinho",
    "type" : "electric",
    "attack" : 55,
    "height" : 0.4
}
{
    "_id" : ObjectId("5682f80e2ebc7952c85ba8c2"),
    "name" : "Bulbassauro",
    "description" : "Chicote de trepadeira",
    "type" : "grass",
    "attack" : 49,
    "height" : 0.4
}
{
    "_id" : ObjectId("5682f9052ebc7952c85ba8c5"),
    "name" : "Caterpie",
    "description" : "Larva lutadora",
    "type" : "insect",
    "attack" : 30,
    "height" : 0.3,
    "defense" : 35
}
```

## Liste todos os pokémons com altura maior ou igual a 0.5
```
> var query = {height: {$gte: 0.5}}
> db.pokemons.find(query).pretty()
{
    "_id" : ObjectId("5682f80e2ebc7952c85ba8c3"),
    "name" : "Charmander",
    "description" : "Esse é o cão chupando manga de fofinho",
    "type" : "fire",
    "attack" : 52,
    "height" : 0.6
}
{
    "_id" : ObjectId("5682f80e2ebc7952c85ba8c4"),
    "name" : "Squirtle",
    "description" : "Ejeta água que passarinho não bebe",
    "type" : "water",
    "attack" : 48,
    "height" : 0.5
}
```

## Liste todos pokémons com altura menor ou igual a 0.5 e do tipo grama
```
> var query = {$and: [{height: {$lte: 0.5}}, {type: 'grass'}]}
> db.pokemons.find(query).pretty()
{
    "_id" : ObjectId("5682f80e2ebc7952c85ba8c2"),
    "name" : "Bulbassauro",
    "description" : "Chicote de trepadeira",
    "type" : "grass",
    "attack" : 49,
    "height" : 0.4
}
```

## Liste todos os pokémons com o name Pikachu ou com attack menor ou igual a 0.5
```
> var query = {$or: [{name: 'Pikachu'}, {attack: {$lte: 0.5}}]}
> db.pokemons.find(query).pretty()
{
    "_id" : ObjectId("5682f71f2ebc7952c85ba8c1"),
    "name" : "Pikachu",
    "description" : "Rato elétrico bem fofinho",
    "type" : "electric",
    "attack" : 55,
    "height" : 0.4
}
```

## Liste todos os pokémons com o attack maior ou igual a 48 e com height menor ou igual a 0.5
```
> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
> db.pokemons.find(query).pretty()
{
    "_id" : ObjectId("5682f71f2ebc7952c85ba8c1"),
    "name" : "Pikachu",
    "description" : "Rato elétrico bem fofinho",
    "type" : "electric",
    "attack" : 55,
    "height" : 0.4
}
{
    "_id" : ObjectId("5682f80e2ebc7952c85ba8c2"),
    "name" : "Bulbassauro",
    "description" : "Chicote de trepadeira",
    "type" : "grass",
    "attack" : 49,
    "height" : 0.4
}
{
    "_id" : ObjectId("5682f80e2ebc7952c85ba8c4"),
    "name" : "Squirtle",
    "description" : "Ejeta água que passarinho não bebe",
    "type" : "water",
    "attack" : 48,
    "height" : 0.5
}
```