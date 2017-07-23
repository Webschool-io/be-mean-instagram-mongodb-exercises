# MongoDB - Aula 03 - Exercício
autor: Thiago Nogueira

##Liste todos Pokemons com a altura menor que 0.5
```
  TNP-MacBook-Air(mongod-3.0.7) be-mean-instagram> var query = {height: {$lt: 0.5}}
  TNP-MacBook-Air(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
  {
  "_id": ObjectId("564512586d17278fd3fe8fb0"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
  }
  {
  "_id": ObjectId("564513026d17278fd3fe8fb1"),
  "name": "Buldassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
  }
  {
  "_id": ObjectId("564514956d17278fd3fe8fb4"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
  }
  Fetched 3 record(s) in 19ms
```

## Liste todos Pokemons com a altura maior ou igual que 0.5
```
  TNP-MacBook-Air(mongod-3.0.7) be-mean-instagram> var query = {height: {$gte: 0.5}}
  TNP-MacBook-Air(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
  {
  "_id": ObjectId("564513406d17278fd3fe8fb2"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
  }
  {
  "_id": ObjectId("564513706d17278fd3fe8fb3"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
  }
  Fetched 2 record(s) in 9ms
```

## Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama
```
  TNP-MacBook-Air(mongod-3.0.7) be-mean-instagram> var query = { $and:[{type: "grama"}, {height: {$lte: 0.5}}]}
  TNP-MacBook-Air(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
  {
  "_id": ObjectId("564513026d17278fd3fe8fb1"),
  "name": "Buldassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
  }
  Fetched 1 record(s) in 0ms
```

## Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5
```
  TNP-MacBook-Air(mongod-3.0.7) be-mean-instagram> var query = {$or:[{name: "Pikachu"},{attack: {$lte: 0.5}}]}
  TNP-MacBook-Air(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
  {
  "_id": ObjectId("564512586d17278fd3fe8fb0"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
  }
  Fetched 1 record(s) in 2ms
```

## Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5
```
  TNP-MacBook-Air(mongod-3.0.7) be-mean-instagram> var query = {$and:[{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
  TNP-MacBook-Air(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
  {
    "_id": ObjectId("564512586d17278fd3fe8fb0"),
    "name": "Pikachu",
    "description": "Rato elétrico bem fofinho",
    "type": "eletric",
    "attack": 55,
    "height": 0.4
  }
  {
    "_id": ObjectId("564513026d17278fd3fe8fb1"),
    "name": "Buldassauro",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 49,
    "height": 0.4
  }
  {
    "_id": ObjectId("564513706d17278fd3fe8fb3"),
    "name": "Squirtle",
    "description": "Ejeta água que passarinho não bebe",
    "type": "água",
    "attack": 48,
    "height": 0.5
  }
  Fetched 3 record(s) in 1ms
```
