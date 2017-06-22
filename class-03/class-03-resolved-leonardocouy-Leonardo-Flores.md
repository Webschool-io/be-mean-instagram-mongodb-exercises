# MongoDB - Aula 03 - Exercício
autor: **Leonardo Flores**

## Liste todos Pokemons com a altura **menor que** 0.5

```
MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean-pokemons> var query = {height: {$lt: 0.5}}
MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean-pokemons> db.pokedex.find(query)
{
  "_id": ObjectId("56e84dac791235930bbfa219"),
  "name": "Pikachu",
  "height": 0.4,
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge.",
  "attack": 4,
  "defense": 2,
  "type": "Electric"
}
Fetched 1 record(s) in 1ms
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

```
MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean-pokemons> db.pokedex.find(query)
{
  "_id": ObjectId("56e84d86791235930bbfa214"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "attack": 3,
  "defense": 2,
  "height": 0.7,
  "type": "Grass"
}
{
  "_id": ObjectId("56e84d86791235930bbfa215"),
  "name": "Ivysaur",
  "description": "There is a bud on this Pokémon's back. To support its weight, Ivysaur's legs and trunk grow thick and strong. If it starts spending more time lying in the sunlight, it's a sign that the bud will bloom into a large flower soon.",
  "attack": 3,
  "defense": 3,
  "height": 1,
  "type": "Grass"
}
{
  "_id": ObjectId("56e84d86791235930bbfa216"),
  "name": "Venusaur",
  "description": "There is a large flower on Venusaur's back. The flower is said to take on vivid colors if it gets plenty of nutrition and sunlight. The flower's aroma soothes the emotions of people.",
  "attack": 4,
  "defense": 4,
  "height": 2,
  "type": "Grass"
}
{
  "_id": ObjectId("56e84d86791235930bbfa217"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
  "attack": 3,
  "defense": 2,
  "height": 0.6,
  "type": "Fire"
}
{
  "_id": ObjectId("56e84d86791235930bbfa218"),
  "name": "Charmeleon",
  "description": "Charmeleon mercilessly destroys its foes using its sharp claws. If it encounters a strong foe, it turns aggressive. In this excited state, the flame at the tip of its tail flares with a bluish white color.",
  "attack": 3,
  "defense": 3,
  "height": 1.1,
  "type": "Fire"
}
Fetched 5 record(s) in 2ms
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama

```
MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean-pokemons> var query = {$and: [{height: {$lte: 0.5}}, {type: /grass/i}]}

MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean-pokemons> query
{
  "$and": [
    {
      "height": {
        "$lte": 0.5
      }
    },
    {
      "type": /grass/i
    }
  ]
}

MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean-pokemons> db.pokedex.find(query)
Fetched 0 record(s) in 1ms
```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

```
MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean-pokemons> var query = {$or: [{attack: {$lte: 0.5}}, {name: /pikachu/i}]}
MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean-pokemons> query
{
  "$or": [
    {
      "attack": {
        "$lte": 0.5
      }
    },
    {
      "name": /pikachu/i
    }
  ]
}
MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean-pokemons> db.pokedex.find(query)
{
  "_id": ObjectId("56e84dac791235930bbfa219"),
  "name": "Pikachu",
  "height": 0.4,
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge.",
  "attack": 4,
  "defense": 2,
  "type": "Electric"
}
Fetched 1 record(s) in 2ms
```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

```
MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean-pokemons> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean-pokemons> query
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
MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean-pokemons> db.pokedex.find(query)
Fetched 0 record(s) in 0ms
```
