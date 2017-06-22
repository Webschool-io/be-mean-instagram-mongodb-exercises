# MongoDb - Aula 03 - Exercício

1. Liste todos Pokemons com a altura **menor que** 0.5;
2. Liste todos Pokemons com a altura **maior ou igual que** 0.5;
3. Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama;
4. Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5;
5. Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5;

## Estrutura

```md
# MongoDB - Aula 03 - Exercício
autor: **Welder Marcos**

## Liste todos Pokemons com a altura **menor que** 0.5

Welder-Mint(mongod-3.2.0) be-mean-pokemons> d
be-mean-pokemons.pokemons
Welder-Mint(mongod-3.2.0) be-mean-pokemons> var alturaMenor = {"height": {$lt: 0.5}}
Welder-Mint(mongod-3.2.0) be-mean-pokemons> d.find(alturaMenor)
{
  "_id": ObjectId("566c8ed640bc20c0ea5f5924"),
  "name": "Mew",
  "description": "Legendary",
  "type": "Psychic",
  "attack": 150,
  "deffense": 100,
  "height": 0.4
}
Fetched 1 record(s) in 1ms

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

Welder-Mint(mongod-3.2.0) be-mean-pokemons> d
be-mean-pokemons.pokemons
Welder-Mint(mongod-3.2.0) be-mean-pokemons> var alturaMaior = {"height": {$gte: 0.5}}
Welder-Mint(mongod-3.2.0) be-mean-pokemons> alturaMaior
{
  "height": {
    "$gte": 0.5
  }
}
Welder-Mint(mongod-3.2.0) be-mean-pokemons> d.find(alturaMaior)
{
  "_id": ObjectId("566c8ed640bc20c0ea5f5920"),
  "name": "Arbok",
  "description": "Snake",
  "type": "Poison",
  "attack": 85,
  "deffense": 69,
  "height": 3.5,
  "poison": 20
}
{
  "_id": ObjectId("566c8ed640bc20c0ea5f5921"),
  "name": "Blastoise",
  "description": "Tortoise",
  "type": "Water",
  "attack": 90,
  "deffense": 150,
  "height": 1.6
}
{
  "_id": ObjectId("566c8ed640bc20c0ea5f5922"),
  "name": "Venusaur",
  "description": "Plant",
  "type": "Grass",
  "attack": 90,
  "deffense": 75,
  "height": 2
}
{
  "_id": ObjectId("566c8ed640bc20c0ea5f5923"),
  "name": "Charizard",
  "description": "Dragon",
  "type": "Fire",
  "attack": 90,
  "deffense": 100,
  "height": 1.7
}
{
  "_id": ObjectId("566c8ed640bc20c0ea5f5925"),
  "name": "Wobbuffet",
  "description": "Zueiro do Anime",
  "type": "Psychic",
  "attack": 50,
  "deffense": 20,
  "height": 1.3
}
Fetched 5 record(s) in 3ms

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama

Welder-Mint(mongod-3.2.0) be-mean-pokemons> d
be-mean-pokemons.pokemons
Welder-Mint(mongod-3.2.0) be-mean-pokemons> gramado
{
  "$and": [
    {
      "height": {
        "$lte": 0.5
      }
    },
    {
      "type": /grass/
    }
  ]
}
Welder-Mint(mongod-3.2.0) be-mean-pokemons> d.find(gramado)
Fetched 0 record(s) in 2ms
Welder-Mint(mongod-3.2.0) be-mean-pokemons> mew
{
  "$and": [
    {
      "height": {
        "$lte": 0.5
      }
    },
    {
      "type": "Psychic"
    }
  ]
}
Welder-Mint(mongod-3.2.0) be-mean-pokemons> d.find(mew)
{
  "_id": ObjectId("566c8ed640bc20c0ea5f5924"),
  "name": "Mew",
  "description": "Legendary",
  "type": "Psychic",
  "attack": 150,
  "deffense": 100,
  "height": 0.4
}
Fetched 1 record(s) in 2ms

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

Welder-Mint(mongod-3.2.0) be-mean-pokemons> att
{
  "attack": {
    "$lte": 0.5
  }
}
Welder-Mint(mongod-3.2.0) be-mean-pokemons> pika
{
  "name": /Pikachu/i
}
Welder-Mint(mongod-3.2.0) be-mean-pokemons> pikaFraco
{
  "$or": [
    {
      "name": /Pikachu/i
    },
    {
      "attack": {
        "$lte": 0.5
      }
    }
  ]
}
Welder-Mint(mongod-3.2.0) be-mean-pokemons> d.find(pikaFraco)
Fetched 0 record(s) in 1ms

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

Welder-Mint(mongod-3.2.0) be-mean-pokemons> d
be-mean-pokemons.pokemons
Welder-Mint(mongod-3.2.0) be-mean-pokemons> qry
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
Welder-Mint(mongod-3.2.0) be-mean-pokemons> d.find(qry)
{
  "_id": ObjectId("566c8ed640bc20c0ea5f5924"),
  "name": "Mew",
  "description": "Legendary",
  "type": "Psychic",
  "attack": 150,
  "deffense": 100,
  "height": 0.4
}
Fetched 1 record(s) in 1ms

```
