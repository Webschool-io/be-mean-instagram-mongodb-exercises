# MongoDB - Aula 03 - Exercício
autor: **SERGIO DINIZ CORREIA**

## Liste todos Pokemons com a altura menor que 0.5;
``` javascript
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> var query = {height:{$lt:0.5}}
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> query
{
  "height": {
    "$lt": 0.5
  }
}
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564b2cc2de86e4e06dfe93b3"),
  "name": "Krabby",
  "description": "Krabby live on beaches, burrowed inside holes dug into the sand. On sandy beaches with little in the way of food, these Pokémon can be seen squabbling with each other over territory.",
  "type": "Water",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("564b2d8cde86e4e06dfe93b7"),
  "name": "Exeggcute",
  "description": "This Pokémon consists of six eggs that form a closely knit cluster. The six eggs attract each other and spin around. When cracks increasingly appear on the eggs, Exeggcute is close to evolution.",
  "type": "Water",
  "attack": 55,
  "height": 0.4
}
Fetched 2 record(s) in 9ms
```

## Liste todos Pokemons com a altura maior ou igual que 0.5;
``` javascript
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> var query = {height :{$gte: 0.5}}
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564b2d18de86e4e06dfe93b4"),
  "name": "Kingler",
  "description": "Kingler has an enormous, oversized claw. It waves this huge claw in the air to communicate with others. However, because the claw is so heavy, the Pokémon quickly tires.",
  "type": "Water",
  "attack": 55,
  "height": 1.3
}
{
  "_id": ObjectId("564b2d42de86e4e06dfe93b5"),
  "name": "Voltorb",
  "description": "nova descricao :)",
  "type": "Water",
  "attack": 55,
  "height": 0.5
}
{
  "_id": ObjectId("564b2d66de86e4e06dfe93b6"),
  "name": "Electrode",
  "description": "Electrode eats electricity in the atmosphere. On days when lightning strikes, you can see this Pokémon exploding all over the place from eating too much electricity.",
  "type": "Water",
  "attack": 55,
  "height": 1.2
}
Fetched 3 record(s) in 2ms
``` 

## Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama
``` javascript
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> var query = {$and:[{height:{$lte:0.5}},{type: "grama"}]}
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> query
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
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
```

## Liste todos Pokemons com o name Pikachu OU com attack menor ou igual que 0.5
``` javascript
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> var query = {$or : [{name: "Pikachu"},{attack: {$lte: 0.5}}]}
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> query
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
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 3ms
```

## Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com height menor ou igual que 0.5
``` javascript
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> query
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
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564b2cc2de86e4e06dfe93b3"),
  "name": "Krabby",
  "description": "Krabby live on beaches, burrowed inside holes dug into the sand. On sandy beaches with little in the way of food, these Pokémon can be seen squabbling with each other over territory.",
  "type": "Water",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("564b2d42de86e4e06dfe93b5"),
  "name": "Voltorb",
  "description": "nova descricao :)",
  "type": "Water",
  "attack": 55,
  "height": 0.5
}
{
  "_id": ObjectId("564b2d8cde86e4e06dfe93b7"),
  "name": "Exeggcute",
  "description": "This Pokémon consists of six eggs that form a closely knit cluster. The six eggs attract each other and spin around. When cracks increasingly appear on the eggs, Exeggcute is close to evolution.",
  "type": "Water",
  "attack": 55,
  "height": 0.4
}
Fetched 3 record(s) in 2ms
```



