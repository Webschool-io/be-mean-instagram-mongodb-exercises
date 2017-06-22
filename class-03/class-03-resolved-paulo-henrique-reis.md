# MongoDB - Aula 03 - Exercício
Autor: Paulo Henrique Reis

## Listar todos pokemons com altura menor que 0.5

```
 var query = {height : {$lt: 0.5}}
 db.pokemons.find(query)

{
  "_id": ObjectId("5928d46e4130db184bba0a70"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("5928d5124130db184bba0a73"),
  "name": "Pikachu",
  "description": "Modificando descrição",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("5928d5cd4130db184bba0a74"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "denfese": 25
}
{
  "_id": ObjectId("5928d6254130db184bba0a75"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3
}
```

## Listar todos pokemons com altura maior ou igual que 0.5

```
 var query = {height : {$gte: 0.5}}
 db.pokemons.find(query)

{
  "_id": ObjectId("5928d4864130db184bba0a71"),
  "name": "Charmander",
  "description": "Calango de fogo",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("5928d4a64130db184bba0a72"),
  "name": "Squirtle",
  "description": "uma tartaruga que cospe agua",
  "type": "fogo",
  "attack": 48,
  "height": 0.5
}

```

## Listar todos pokemons com altura maior ou igual que 0.5

```
var query = {height : {$lte: 0.5}}
db.pokemons.find(query)
{
  "_id": ObjectId("5928d46e4130db184bba0a70"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("5928d4a64130db184bba0a72"),
  "name": "Squirtle",
  "description": "uma tartaruga que cospe agua",
  "type": "fogo",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("5928d5124130db184bba0a73"),
  "name": "Pikachu",
  "description": "Modificando descrição",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("5928d5cd4130db184bba0a74"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "denfese": 25
}
{
  "_id": ObjectId("5928d6254130db184bba0a75"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3
}

```


## Listar todos pokemons com o nome "Pikachu" ou attack menor igual que 0.5

```
var query = {$or: [{name: "Pikachu"}, {attack: {$lte : 0.5} }] }
db.pokemons.find(query)

{
  "_id": ObjectId("5928d5124130db184bba0a73"),
  "name": "Pikachu",
  "description": "Modificando descrição",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}

```

## Listar todos pokemons com o attack maior ou igual que 48 e height menor ou igual a 0.5

```

 var query = {$and: [{attack: {$gte: 48 }}, {height : {$lte: 0.5}}  ] }
 db.pokemons.find(query)

{
  "_id": ObjectId("5928d46e4130db184bba0a70"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
} "height": 0.3,
{ "denfese": 25
  "_id": ObjectId("5928d4a64130db184bba0a72"),
  "name": "Squirtle",
  "description": "uma tartaruga que cospe agua",
  "type": "fogo",ie",
  "attack": 48,: "Larva lutadora",
  "height": 0.5to",
} "attack": 30,
{ "height": 0.3
  "_id": ObjectId("5928d5124130db184bba0a73"),
  "name": "Pikachu",in 81ms
  "description": "Modificando descrição",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}

```




