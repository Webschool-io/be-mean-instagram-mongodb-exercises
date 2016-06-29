# MongoDB - Aula 03 - Exercício
autor: Cristiano Mesquita

## Listando Pokemons com altura menor que 0.5

ubuntu(mongod-2.6.10) be-mean-pokemons> var query = {height:{$lt:0.5}}
ubuntu(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("574c79c0748f0b8a396f30c7"),
  "name": "Pokebola",
  "description": "boiolão",
  "attack": 5,
  "defense": 0.1,
  "type": "grama",
  "height": 0.2
}
Fetched 1 record(s) in 0ms

## Listando todos os pokemons com altura maior ou igual a 0.5
ubuntu(mongod-2.6.10) be-mean-pokemons> var query = {height:{$gte:0.5}}
ubuntu(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("574c79c0748f0b8a396f30c7"),
  "name": "Pokebola",
  "description": "boiolão",
  "attack": 5,
  "defense": 0.1,
  "type": "grama",
  "height": 0.2
}
Fetched 1 record(s) in 0ms

## Listando todos os Pokemons com altura menor ou igual a 0.5 e tipo grama
ubuntu(mongod-2.6.10) be-mean-pokemons> var query = {$and:[{height:{$lte:0.5}},{type:"grama"}]}
ubuntu(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("574c79c0748f0b8a396f30c7"),
  "name": "Pokebola",
  "description": "boiolão",
  "attack": 5,
  "defense": 0.1,
  "type": "grama",
  "height": 0.2
}
Fetched 1 record(s) in 66ms


## Listando todos os Pokemons com o nome Pikachu ou attack menor ou igual a 0.5
ubuntu(mongod-2.6.10) be-mean-instagram> var query = {$or:[{name:"Pikachu"},{attack:{$lte:0.5}}]}
ubuntu(mongod-2.6.10) be-mean-instagram> db.pokemons.find(query);
{
  "_id": ObjectId("574a6ff751f10f8cd6c8d5b8"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
Fetched 1 record(s) in 1ms





## Listando todos os pokemons com attack maior ou igual a 48 e altura menor ou igual a 0.5

ubuntu(mongod-2.6.10) be-mean-pokemons> var query = {$and:[{attack:{$gte:48}},{height:{$lte:0.5}}]}
ubuntu(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("574c82c61740fbd12911c175"),
  "name": "Thunderbird",
  "description": "O Fodão",
  "attack": 48,
  "defense": 45,
  "type": "Rosca Froxa",
  "height": 0.4
}
Fetched 1 record(s) in 1ms

