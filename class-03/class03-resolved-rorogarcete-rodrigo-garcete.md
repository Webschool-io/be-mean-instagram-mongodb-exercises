# MongoDB - Aula 03 - Exercício
autor: Rodrigo Garcete

## Liste todos Pokemons com a altura **menor que** 0.5;
rodrigo-Satellite-L505(mongod-2.6.11) be-mean-testes> var query = {height: {$lt: 0.5}}
rodrigo-Satellite-L505(mongod-2.6.11) be-mean-testes> db.pokemons.find(query)
{
  "_id": ObjectId("564a51d972aa280c76049528"),
  "name": "Pikachu",
  "decription": "Rato eletrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "defense": 35
}
{
  "_id": ObjectId("564a535572aa280c76049529"),
  "name": "Bulbassouro",
  "description": "Chicote de trepaderia",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 2 record(s) in 3ms

## Liste todos Pokemons com a altura **maior ou igual que** 0.5
rodrigo-Satellite-L505(mongod-2.6.11) be-mean-testes> var query = {height: {$gte: 0.5}}
rodrigo-Satellite-L505(mongod-2.6.11) be-mean-testes> db.pokemons.find(query)
{
  "_id": ObjectId("564a535a72aa280c7604952a"),
  "name": "Charmander",
  "description": "Esse e o cao chupando manda de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("564a536272aa280c7604952b"),
  "name": "Squirtle",
  "description": "Ejeta agua que passarinho nao bebe",
  "type": "agua",
  "attack": 48,
  "height": 0.5
}
Fetched 2 record(s) in 1ms

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
rodrigo-Satellite-L505(mongod-2.6.11) be-mean-testes> var query = {$and :[{height: {$lte: 0.5}}, {type:'grama'}] }
rodrigo-Satellite-L505(mongod-2.6.11) be-mean-testes> db.pokemons.find(query)
{
  "_id": ObjectId("564a535572aa280c76049529"),
  "name": "Bulbassouro",
  "description": "Chicote de trepaderia",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 1ms

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
rodrigo-Satellite-L505(mongod-2.6.11) be-mean-testes> var query = {$or :[{attack: {$lte: 0.5}}, {name:'Pikachu'}] }
rodrigo-Satellite-L505(mongod-2.6.11) be-mean-testes> db.pokemons.find(query)
{
  "_id": ObjectId("564a51d972aa280c76049528"),
  "name": "Pikachu",
  "decription": "Rato eletrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "defense": 35
}
Fetched 1 record(s) in 1ms

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que**  0.5
rodrigo-Satellite-L505(mongod-2.6.11) be-mean-testes> var query = {$and :[{attack: {gte: 48}}, {height: {$lte: 0.5}}] }
rodrigo-Satellite-L505(mongod-2.6.11) be-mean-testes> db.pokemons.find(query)
Fetched 0 record(s) in 1ms


