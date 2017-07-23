# MongoDB - Aula 03 - Exercício
autor: Rafael Taro Osako

## Liste todos Pokemons com a altura **menor que** 0.5;

Rafaels-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> var query =  {height: {$lt:0.5}}
Rafaels-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5668b84cd9bf505f036304d0"),
  "name": "Pidgey",
  "description": "Pássaro com super senso de direção",
  "attack": 20,
  "defense": 20,
  "height": 0.3
}
{
  "_id": ObjectId("5668ba12d9bf505f036304d3"),
  "name": "Pikachu",
  "description": "Rato elétrico",
  "attack": 30,
  "defense": 20,
  "height": 0.4
}
Fetched 2 record(s) in 8ms

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

Rafaels-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> var query =  {height: {$gte:0.5}}
Rafaels-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5668b7d5d9bf505f036304ce"),
  "name": "Blastoise",
  "description": "tartaruga tanque",
  "attack": 40,
  "defense": 40,
  "height": 1.6
}
{
  "_id": ObjectId("5668b82dd9bf505f036304cf"),
  "name": "Butterfree",
  "description": "Borboletinha",
  "attack": 20,
  "defense": 20,
  "height": 1.1
}
{
  "_id": ObjectId("5668b856d9bf505f036304d1"),
  "name": "Zubat",
  "description": "Morcego, se queima no sol",
  "attack": 20,
  "defense": 20,
  "height": 0.8
}
{
  "_id": ObjectId("5668b85dd9bf505f036304d2"),
  "name": "Bellsprout",
  "description": "Plants vs zombies",
  "attack": 40,
  "defense": 20,
  "height": 0.7
}
Fetched 4 record(s) in 5ms


## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama

Rafaels-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{height:{$lte:0.5}}, {type:'grama'}] }
Rafaels-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms


## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

Rafaels-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> var query = {$or: [{attack:{$lte:0.5}}, {name:'Pikachu'}] }
Rafaels-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5668ba12d9bf505f036304d3"),
  "name": "Pikachu",
  "description": "Rato elétrico",
  "attack": 30,
  "defense": 20,
  "height": 0.4
}
Fetched 1 record(s) in 1ms
Rafaels-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> 

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
Rafaels-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> var query = {$and:[ {attack:{$gte:48}}, {height:{$lte:0.5}}]}
Rafaels-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
Rafaels-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> 
