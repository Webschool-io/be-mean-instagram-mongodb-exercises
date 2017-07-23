# MongoDB - Aula 03 - Exercício
autor: Diêgo Bolina

#1 - Liste todos os Pokemons com a altura menor que 0.5;

Diegos-MacBook-Pro(mongod-3.2.0) be-mean-pokemons> var query = {height: {$lt: 0.5}}
Diegos-MacBook-Pro(mongod-3.2.0) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("566f7a8eabd4340bccd4c61d"),
  "name": "Pikachu",
  "description": "Rato Elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("566f7a8eabd4340bccd4c621"),
  "name": "Spearow",
  "description": "Changing description of Spearow",
  "type": "Tinybird",
  "attack": 60,
  "height": 0.3
}
Fetched 2 record(s) in 7ms


#2 - Liste todos os Pokemons com a altura maior ou igual que 0.5;

Diegos-MacBook-Pro(mongod-3.2.0) be-mean-pokemons> var query = {height: {$gte: 0.5}}
Diegos-MacBook-Pro(mongod-3.2.0) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("566f7a8eabd4340bccd4c61e"),
  "name": "Diglett",
  "description": "Diglett are raised in most farms",
  "type": "ground",
  "attack": 55,
  "height": 2
}
{
  "_id": ObjectId("566f7a8eabd4340bccd4c61f"),
  "name": "Mewtwo",
  "description": "Mewtwo is a Pokémon that was created by genetic manipulation",
  "type": "Physic",
  "attack": 110,
  "height": 2
}
{
  "_id": ObjectId("566f7a8eabd4340bccd4c620"),
  "name": "Abra",
  "description": "Abra sleeps for eighteen hours a day",
  "type": "Physic",
  "attack": 20,
  "height": 0.9
}
Fetched 3 record(s) in 2ms


#3 - Liste todos os Pokemons com a altura menor ou igual que 0.5 E do tipo Electric;

Diegos-MacBook-Pro(mongod-3.2.0) be-mean-pokemons> var query = { $and: [{height: {$lte: 0.5}},{type: 'electric'}]}
Diegos-MacBook-Pro(mongod-3.2.0) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("566f7a8eabd4340bccd4c61d"),
  "name": "Pikachu",
  "description": "Rato Elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
Fetched 1 record(s) in 1ms

#4 - Liste todos os Pokemons com o name 'Pikachu' OU com attack menor ou igual que 0.5;

Diegos-MacBook-Pro(mongod-3.2.0) be-mean-pokemons> var query = { $or: [{attack: {$lte: 0.5}},{name: 'Pikachu'}]}
Diegos-MacBook-Pro(mongod-3.2.0) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("566f7a8eabd4340bccd4c61d"),
  "name": "Pikachu",
  "description": "Rato Elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
Fetched 1 record(s) in 1ms

#5 - Liste todos os pokemons com attack MAIOR OU IGUAL QUE 48 E com height MENOR OU IGUAL QUE 0.5;

Diegos-MacBook-Pro(mongod-3.2.0) be-mean-pokemons> var query = { $and: [{attack: {$gte: 48}},{height: {$lte: 0.5}}]}
Diegos-MacBook-Pro(mongod-3.2.0) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("566f7a8eabd4340bccd4c61d"),
  "name": "Pikachu",
  "description": "Rato Elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("566f7a8eabd4340bccd4c621"),
  "name": "Spearow",
  "description": "Changing description of Spearow",
  "type": "Tinybird",
  "attack": 60,
  "height": 0.3
}
Fetched 2 record(s) in 2ms