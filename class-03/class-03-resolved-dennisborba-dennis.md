# MongoDB -Aula 03 - Exercicio
autor: Dennis Borba

# 1. Liste todos Pokemons com a altura menor que 0.5;

...
Ubuntu-pc(mongod-3.0.7) be-mean-pokemons> query = {height: {$lt: 0.5}}
{
  "height": {
    "$lt": 0.5
  }
}
Ubuntu-pc(mongod-3.0.7) be-mean-pokemons> db.pokemon.find(query)
{
  "_id": ObjectId("564558a761e81beac8b5bd78"),
  "name": "Pidgey",
  "description": "Pequeno pássaro com extremo senso de direção",
  "type": "voador",
  "attack": 45,
  "height": 0.3,
  "defense": 40
}
Fetched 1 record(s) in 43ms
...


# 2. Liste todos Pokemons com a altura maior ou igual que 0.5;

...
Ubuntu-pc(mongod-3.0.7) be-mean-pokemons> query = {height: {$gte: 0.5}}
{
  "height": {
    "$gte": 0.5
  }
}
Ubuntu-pc(mongod-3.0.7) be-mean-pokemons> db.pokemon.find(query)
{
  "_id": ObjectId("5645582261e81beac8b5bd75"),
  "name": "Metapod",
  "description": "Casulo",
  "type": "inseto",
  "attack": 20,
  "height": 0.7,
  "defense": 55
}
{
  "_id": ObjectId("5645584461e81beac8b5bd76"),
  "name": "Butterfree",
  "description": "Borboleta",
  "type": "inseto voador",
  "attack": 45,
  "height": 1.1,
  "defense": 50
}
{
  "_id": ObjectId("5645587161e81beac8b5bd77"),
  "name": "Kakuna",
  "description": "Inseto que permanece imóvel dentro do casulo",
  "type": "inseto venenoso",
  "attack": 25,
  "height": 0.6,
  "defense": 50
}
{
  "_id": ObjectId("564558c361e81beac8b5bd79"),
  "name": "Sandshrew",
  "description": "Roedor",
  "type": "subterrâneo",
  "attack": 75,
  "height": 0.6,
  "defense": 85
}
{
  "_id": ObjectId("564558d361e81beac8b5bd7a"),
  "name": "Nidoking",
  "description": "Broca",
  "type": "subterrâneo venenoso",
  "attack": 102,
  "height": 1.4,
  "defense": 77
}
Fetched 5 record(s) in 3ms
...


# 3. Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama;

...
Ubuntu-pc(mongod-3.0.7) be-mean-pokemons> query1 = {height: {$lte: 0.5}}
{
  "height": {
    "$lte": 0.5
  }
}
Ubuntu-pc(mongod-3.0.7) be-mean-pokemons> query2 = {type: 'grama'}
{
  "type": "grama"
}
Ubuntu-pc(mongod-3.0.7) be-mean-pokemons> query = {$and: [query1, query2]}
{
  "$and": [
    {
      "height": {
        "$lte": 0.5
      }
    },
    {
      "type": "grama"
    }
  ]
}
Ubuntu-pc(mongod-3.0.7) be-mean-pokemons> db.pokemon.find(query)
Fetched 0 record(s) in 1ms
...


# 4. Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5;

...
Ubuntu-pc(mongod-3.0.7) be-mean-pokemons> query1 = {name: 'Pikachu'}
{
  "name": "Pikachu"
}
Ubuntu-pc(mongod-3.0.7) be-mean-pokemons> query2 = {attack: {$lte: 0.5}}
{
  "attack": {
    "$lte": 0.5
  }
}
Ubuntu-pc(mongod-3.0.7) be-mean-pokemons> query = {$or: [query1, query2]}
{
  "$or": [
    {
      "name": "Pikachu"
    },
    {
      "attack": {
        "$lte": 0.5
      }
    }
  ]
}
Ubuntu-pc(mongod-3.0.7) be-mean-pokemons> db.pokemon.find(query)
Fetched 0 record(s) in 1ms
...


# 5. Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5;

...
Ubuntu-pc(mongod-3.0.7) be-mean-pokemons> query1 = {attack: {$gte: 48}}
{
  "attack": {
    "$gte": 48
  }
}
Ubuntu-pc(mongod-3.0.7) be-mean-pokemons> query2 = {height: {$lte: 0.5}}
{
  "height": {
    "$lte": 0.5
  }
}
Ubuntu-pc(mongod-3.0.7) be-mean-pokemons> query = {$and: [query1, query2]}
{
  "$and": [
    {
      "attack": {
        "$gte": 48
      }
    },
    {
      "height": {
        "$lte": 0.5
      }
    }
  ]
}
Ubuntu-pc(mongod-3.0.7) be-mean-pokemons> db.pokemon.find(query)
Fetched 0 record(s) in 0ms
...












