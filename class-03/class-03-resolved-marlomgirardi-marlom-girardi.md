#MongoDb - Aula 03 - Exercício

autor: Marlom Girardi

##Listagem de todos os Pokemons com a altura menor que 0.5
```
dell-marlom(mongod-3.0.9) be-mean-instagram> var query = {height: {$lt: 0.5}}

dell-marlom(mongod-3.0.9) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56c0aeb639a0da5118e29a72"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "ttype": "eletric",
  "attack": 100,
  "height": 0.4
}
{
  "_id": ObjectId("56c0afca39a0da5118e29a73"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("56c0b0d639a0da5118e29a76"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 3 record(s) in 8ms
```

##Listagem de todos os Pokemons com a altura maior ou igual que 0.5
```
dell-marlom(mongod-3.0.9) be-mean-instagram> var query = {height:{$gte:0.5}}

dell-marlom(mongod-3.0.9) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56c0aff239a0da5118e29a74"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("56c0b05439a0da5118e29a75"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 2 record(s) in 1ms
```

##Listagem de todos os Pokemons com a altura menor ou igual que 0.5 E do tipo grama
```
dell-marlom(mongod-3.0.9) be-mean-instagram> var query = {$and: [{height: {$lte: 0.5}}, {type: "grama"}]}

dell-marlom(mongod-3.0.9) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56c0afca39a0da5118e29a73"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 0ms
```

## Listagem de todos os Pokemons com o nome Pikachu ou com attack menor ou igual que 0.5
```
dell-marlom(mongod-3.0.9) be-mean-instagram> var query = {$or: [{attack: {$lte: 0.5}}, {name: "Pikachu"}]}

dell-marlom(mongod-3.0.9) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56c0aeb639a0da5118e29a72"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "ttype": "eletric",
  "attack": 100,
  "height": 0.4
}
Fetched 1 record(s) in 0ms
```

## Listagem de todos os Pokemons com o attack maior ou igual que 48 E com height menor ou igual que 0.5
```
dell-marlom(mongod-3.0.9) be-mean-instagram> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
dell-marlom(mongod-3.0.9) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56c0aeb639a0da5118e29a72"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "ttype": "eletric",
  "attack": 100,
  "height": 0.4
}
{
  "_id": ObjectId("56c0afca39a0da5118e29a73"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("56c0b05439a0da5118e29a75"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 3 record(s) in 0ms
```
