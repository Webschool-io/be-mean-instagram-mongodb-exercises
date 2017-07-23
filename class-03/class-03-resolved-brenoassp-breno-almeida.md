MongoDB - Aula 03 - Exercício
autor: Breno Almeida dos Santos Rodrigues Machado

## Liste todos Pokemons com a altura **menor que** 0.5;

breno-Inspiron-3437(mongod-3.0.7) be-mean-pokemons> query = {height: {$lt: 0.5}}
{
  "height": {
    "$lt": 0.5
  }
}
breno-Inspiron-3437(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5647ef597c289526011c4741"),
  "name": "Raichu",
  "description": "evolução do pikachu",
  "type": "elétrico",
  "attack": 90,
  "height": 0.4,
  "defense": 55
}
Fetched 1 record(s) in 1ms


## Liste todos Pokemons com a altura **maior ou igual que** 0.5;

breno-Inspiron-3437(mongod-3.0.7) be-mean-pokemons> query = {height: {$gte: 0.5}}
{
  "height": {
    "$gte": 0.5
  }
}
breno-Inspiron-3437(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5647ed127c289526011c473e"),
  "name": "Butterfree",
  "description": "Butterfree has a superior ability to search for delicious honey from flowers. It can even search out, extract, and carry honey from flowers that are blooming over six miles from its nest.",
  "type": "bug/flying",
  "attack": 45,
  "height": 11,
  "defense": 50
}
{
  "_id": ObjectId("5647ee247c289526011c473f"),
  "name": "Spearow",
  "description": "Spearow has a very loud cry that can be heard over half a mile away. If its high, keening cry is heard echoing all around, it is a sign that they are warning each other of danger.",
  "type": "voador",
  "attack": 60,
  "height": 3,
  "defense": 30
}
{
  "_id": ObjectId("5647ee967c289526011c4740"),
  "name": "Ekans",
  "description": "Ekans curls itself up in a spiral while it rests. Assuming this position allows it to quickly respond to a threat from any direction with a glare from its upraised head.",
  "type": "venenoso",
  "attack": 60,
  "height": 20,
  "defense": 44
}
{
  "_id": ObjectId("5647f00d7c289526011c4742"),
  "name": "Nidoqueen",
  "description": "Nidoqueens body is encased in extremely hard scales. It is adept at sending foes flying with harsh tackles. This Pokémon is at its strongest when it is defending its young.",
  "type": "venenoso",
  "attack": 92,
  "height": 13,
  "defense": 87
}
Fetched 4 record(s) in 4ms


## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama;

breno-Inspiron-3437(mongod-3.0.7) be-mean-pokemons> query = {$and: [{height: {$lte: 0.5}}, {'type': 'grama'}]}
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
breno-Inspiron-3437(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5;

breno-Inspiron-3437(mongod-3.0.7) be-mean-pokemons> query = {$or: [{attack: {$lte: 0.5}}, {'name': 'Pikachu'}]}
{
  "$or": [
    {
      "attack": {
        "$lte": 0.5
      }
    },
    {
      "name": "Pikachu"
    }
  ]
}
breno-Inspiron-3437(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms


## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5;

breno-Inspiron-3437(mongod-3.0.7) be-mean-pokemons> query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
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
breno-Inspiron-3437(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5647ef597c289526011c4741"),
  "name": "Raichu",
  "description": "evolução do pikachu",
  "type": "elétrico",
  "attack": 90,
  "height": 0.4,
  "defense": 55
}
Fetched 1 record(s) in 1ms
