# MongoDB - Aula 03 - Exercício
autor: Carlan Calazans

## Liste todos os pokemons com a altura **menor que** 0.5

```
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e509"),
  "name": "Pikachu",
  "description": "Descricao modificada",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "defense": 34
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50a"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defense": 45
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50b"),
  "name": "Charmander",
  "description": "Esse é o co chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "defense": 14
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50c"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho no bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "defense": 67
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50d"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 22
}
Fetched 5 record(s) in 1ms
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> var q = {height: {$lt: 0.5}}
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(q)
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e509"),
  "name": "Pikachu",
  "description": "Descricao modificada",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "defense": 34
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50a"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defense": 45
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50d"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 22
}
Fetched 3 record(s) in 4ms
```

## Liste todos os pokemons com a altura **maior ou igual a** 0.5

```
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> var q = {height: {$gte: 0.5}}
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(q)
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50b"),
  "name": "Charmander",
  "description": "Esse é o co chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "defense": 14
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50c"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho no bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "defense": 67
}
Fetched 2 record(s) in 49ms
```

## Liste todos os pokemons com a altura **menor ou igual a** 0.5 **e** do tipo grama

```
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> var q = {$and: [ {height: {$lte: 0.5}}, {type: {$eq: 'grama'}} ]}
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(q)
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50a"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defense": 45
}
Fetched 1 record(s) in 149ms

**OU**

bemeaninstagram(mongod-3.0.7) be-mean-pokemons> var q = {height: {$lte: 0.5}, type: {$eq: 'grama'}}
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(q)
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50a"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defense": 45
}
Fetched 1 record(s) in 2ms
```

## Liste todos os pokemons com o name `Pikachu` **ou** com attack **menor ou igual a** 0.5

```
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> var q = {$or: [{name: {$eq: 'Pikachu'}}, {attack: {$lte: 0.5}}]}
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(q)
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e509"),
  "name": "Pikachu",
  "description": "Descricao modificada",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "defense": 34
}
Fetched 1 record(s) in 2ms
```

## Liste todos os pokemons com o attack **maior ou igual a** 48 **e** com height **menor ou igual a** 0.5

```
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> var q = {$and: [ {attack: {$gte: 48}}, {height: {$lte: 0.5}} ]}
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(q)
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e509"),
  "name": "Pikachu",
  "description": "Descricao modificada",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "defense": 34
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50a"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defense": 45
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50c"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho no bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "defense": 67
}
Fetched 3 record(s) in 5ms

**OU**

bemeaninstagram(mongod-3.0.7) be-mean-pokemons> var q = {attack: {$gte: 48}, height: {$lte: 0.5}}
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(q)
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e509"),
  "name": "Pikachu",
  "description": "Descricao modificada",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "defense": 34
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50a"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defense": 45
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50c"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho no bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "defense": 67
}
Fetched 3 record(s) in 2ms
```