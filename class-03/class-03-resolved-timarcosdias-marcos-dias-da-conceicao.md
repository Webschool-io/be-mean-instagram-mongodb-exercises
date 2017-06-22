# MongoDB - Aula 03 - Exercício
autor: Marcos Dias da Conceição

## Liste todos Pokemons com a altura **menor que** 0.5;
```
db.pokemons.find({height: {$lt : 0.5}})
{
  "_id": ObjectId("5681f2bfd8e520cdf2071617"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("5681f2bfd8e520cdf207161a"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 50
}
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
db.pokemons.find({height: {$gte : 0.5}})
{
  "_id": ObjectId("56819e1f8e301f18c67d3414"),
  "name": "Charizard",
  "description": "Dragão de fogo badass",
  "type": "fogo",
  "attack": 84,
  "height": 1.7
}
{
  "_id": ObjectId("56819e1f8e301f18c67d3415"),
  "name": "Gengar",
  "description": "Fantasminha não camarada",
  "type": "fantasma",
  "attack": 65,
  "height": 1.5
}
{
  "_id": ObjectId("56819e1f8e301f18c67d3416"),
  "name": "Pidgeotto",
  "description": "Pombo nervoso",
  "type": "normal",
  "attack": 60,
  "height": 1.09
}
{
  "_id": ObjectId("56819e1f8e301f18c67d3417"),
  "name": "Raichu",
  "description": "Rato chocante nível 2",
  "type": "elétrico",
  "attack": 90,
  "height": 0.79
}
{
  "_id": ObjectId("56819e1f8e301f18c67d3418"),
  "name": "Parasect",
  "description": "Cogumelo, paz e amor",
  "type": "grama",
  "attack": 95,
  "height": 0.99
}
{
  "_id": ObjectId("5681f2bfd8e520cdf2071618"),
  "name": "Charmander",
  "description": "Dragão cospidor de fogo",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("5681f2bfd8e520cdf2071619"),
  "name": "Squirtle",
  "description": "Tartaruga ejetora de água",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 7 record(s) in 3ms
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```
db.pokemons.find({ $and : [ {height: {$lte : 0.5}}, {type: 'grama'} ] })
{
  "_id": ObjectId("5681f2bfd8e520cdf2071617"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 0ms
```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```
db.pokemons.find({ $or: [{name: 'Pikachu'}, {attack : {$lte : 0.5}}] })
{
  "_id": ObjectId("5681f404d8e520cdf207161b"),
  "name": "Pikachu",
  "description": "Rato elétrico chocante",
  "type": "elétrico",
  "attack": 100,
  "height": 0.4
}
Fetched 1 record(s) in 0ms
```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```
db.pokemons.find({ $and : [{attack : {$gte : 48}}, {height : {$lte : 0.5}}]})
{
  "_id": ObjectId("5681f2bfd8e520cdf2071617"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("5681f2bfd8e520cdf2071619"),
  "name": "Squirtle",
  "description": "Tartaruga ejetora de água",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("5681f404d8e520cdf207161b"),
  "name": "Pikachu",
  "description": "Rato elétrico chocante",
  "type": "elétrico",
  "attack": 100,
  "height": 0.4
}
Fetched 3 record(s) in 1ms
```
