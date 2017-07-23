# MongoDB - Aula 03 - Exercício
Autor: Ubirajara Pelli

## Liste todos Pokemons com a altura **menor que** 0.5;
```
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> var query = {height: {$lt: 0.5}}
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5644bd4c3c7fe93746e4b470"),
  "name": "Pikachu",
  "description": "Eu prefiro cerveja",
  "type": "eletric",
  "attack": 55,
  "defense": 30,
  "height": 0.4
}
{
  "_id": ObjectId("5644bdae3c7fe93746e4b471"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "defense": 45,
  "height": 0.4
}
{
  "_id": ObjectId("5644be6d5af181c8ac5d1230"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "defense": 20,
  "height": 0.3
}
Fetched 3 record(s) in 62ms
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> var query = {height: {$gte: 0.5}}
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5644bdd73c7fe93746e4b472"),
  "name": "Charmander",
  "description": "Dragão de fogo",
  "type": "fogo",
  "attack": 52,
  "defense": 40,
  "height": 0.6
}
{
  "_id": ObjectId("5644be4b5af181c8ac5d122f"),
  "name": "Squirtle",
  "description": "Tartaruga que solta água",
  "type": "água",
  "attack": 48,
  "defense": 35,
  "height": 0.5
}
Fetched 2 record(s) in 2ms
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{height: {$lte: 0.5}}, {type:'grama'}]}
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5644bdae3c7fe93746e4b471"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "defense": 45,
  "height": 0.4
}
Fetched 1 record(s) in 0ms
```
## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> var query = {$or: [{name: 'Pikachu'},{attack:{$lte: 0.5}}]}
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5644bd4c3c7fe93746e4b470"),
  "name": "Pikachu",
  "description": "Eu prefiro cerveja",
  "type": "eletric",
  "attack": 55,
  "defense": 30,
  "height": 0.4
}
Fetched 1 record(s) in 1ms
```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> var query = {$and:[{attack:{$gte: 48}},{height:{$lte:0.5}}]}
Ubirajaras-Mac-mini(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5644bd4c3c7fe93746e4b470"),
  "name": "Pikachu",
  "description": "Eu prefiro cerveja",
  "type": "eletric",
  "attack": 55,
  "defense": 30,
  "height": 0.4
}
{
  "_id": ObjectId("5644bdae3c7fe93746e4b471"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "defense": 45,
  "height": 0.4
}
{
  "_id": ObjectId("5644be4b5af181c8ac5d122f"),
  "name": "Squirtle",
  "description": "Tartaruga que solta água",
  "type": "água",
  "attack": 48,
  "defense": 35,
  "height": 0.5
}
Fetched 3 record(s) in 2ms
```
