# MongoDB - Aula 03 - Exercícios
autor: Leandro Carlos Pereira

1. Liste todos Pokemons com a altura **menor que** 0.5;
2. Liste todos Pokemons com a altura **maior ou igual que** 0.5;
3. Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama;
4. Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5;
5. Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5;


## Liste todos Pokemons com a altura **menor que** 0.5

```
> var query = {height: {$lt: 0.5}}
> db.pokemons.find(query)
{
  "_id": ObjectId("5642769b4041dcbeb60c77de"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("564278aa4041dcbeb60c77df"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("564279b54041dcbeb60c77e2"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

```
> var query = {height: {$gte: 0.5}}
> db.pokemons.find(query)
{
  "_id": ObjectId("564278de4041dcbeb60c77e0"),
  "name": "Charmander",
  "description": "Esse é o cão chupando mando de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("5642790c4041dcbeb60c77e1"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama

```
> var query = {$and: [{height: {$lte: 0.5}}, {type: /grama/}]}
> db.pokemons.find(query)
{
  "_id": ObjectId("564278aa4041dcbeb60c77df"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}

```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

```
> var query = {$or: [{height: {$lte: 0.5}}, {name: /pikachu/i}]}
> db.pokemons.find(query)
{
  "_id": ObjectId("5642769b4041dcbeb60c77de"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("564278aa4041dcbeb60c77df"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("5642790c4041dcbeb60c77e1"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("564279b54041dcbeb60c77e2"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

```
> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
> db.pokemons.find(query)
{
  "_id": ObjectId("5642769b4041dcbeb60c77de"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("564278aa4041dcbeb60c77df"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("5642790c4041dcbeb60c77e1"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
```