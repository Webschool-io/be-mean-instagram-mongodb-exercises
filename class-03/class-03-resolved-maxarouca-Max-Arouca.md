# MongoDB - Aula 02 - Exercício
autor: Max Arouca

## Liste todos Pokemons com a altura **menor que** 0.5;

````javascript

var query = {height: {$lt : 0.5}}
MacMax(mongod-3.0.7) be-mean-pokemons> query
{
  "height": {
    "$lt": 0.5
  }
}
MacMax(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 137ms

````

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

````javascript

be-mean-pokemons> var query = {height: {$gte : 0.5}}
MacMax(mongod-3.0.7) be-mean-pokemons> query
{
  "height": {
    "$gte": 0.5
  }
}
MacMax(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56428bc409501b8c943c4a91"),
  "name": "Wigglytuff",
  "description": "Wigglytuff has large, saucerlike eyes",
  "type": "fairy",
  "attack": 40,
  "height": 1
}
{
  "_id": ObjectId("56428bef09501b8c943c4a92"),
  "name": "Zubat",
  "description": "Zubat remains quietly unmoving in a dark spot during the bright daylight hours.",
  "type": "poison",
  "attack": 20,
  "height": 0.8
}
{
  "_id": ObjectId("56428c2909501b8c943c4a93"),
  "name": "Oddish",
  "description": "Oddish buries itself in soil to absorb nutrients from the ground using its entire body",
  "type": "grass",
  "attack": 30,
  "height": 0.8
}
{
  "_id": ObjectId("56428c3a09501b8c943c4a94"),
  "name": "Gloom",
  "description": "Gloom releases a foul fragrance from the pistil of its flower",
  "type": "grass",
  "attack": 30,
  "height": 0.8
}
{
  "_id": ObjectId("56428c5109501b8c943c4a95"),
  "name": "Misdreavus",
  "description": "Misdreavus frightens people with a creepy, sobbing cry",
  "type": "ghost",
  "attack": 30,
  "height": 0.7
}
Fetched 5 record(s) in 4ms

````

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama

````javascript

var query = {$and: [{height: {$lte: 0.5}},{type: {$eq: 'grass'}}]}
MacMax(mongod-3.0.7) be-mean-pokemons> query
{
  "$and": [
    {
      "height": {
        "$lte": 0.5
      }
    },
    {
      "type": {
        "$eq": "grass"
      }
    }
  ]
}
MacMax(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms

````

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

````javascript

MacMax(mongod-3.0.7) be-mean-pokemons> var query = {$or: [{name: 'Pikachu'}, {attack: {$lte: 0.5}}]}
MacMax(mongod-3.0.7) be-mean-pokemons> query
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
MacMax(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms

````

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

````javascript

MacMax(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
MacMax(mongod-3.0.7) be-mean-pokemons> query
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
MacMax(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms

````
