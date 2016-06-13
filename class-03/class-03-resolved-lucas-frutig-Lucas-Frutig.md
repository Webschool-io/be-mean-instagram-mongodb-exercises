# MongoDB - Aula 03 - Exercício
autor: Lucas Futig

## Liste todos os Pokemons com a altura menor que 0.5

```
vahalla(mongod-3.2.7) be-mean-pokemons> var query = {height: {$lt:0.5}}
vahalla(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("575eac71d750c75617a38e4f"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge. ",
  "type": "electric",
  "attack": 300,
  "defense": 200,
  "height": 0.4
}
Fetched 1 record(s) in 1ms

```

## Liste todos Pokemons com a altura maior ou igual que 0.5

```
vahalla(mongod-3.2.7) be-mean-pokemons> var query = {height: {$gte:0.5}}
vahalla(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("575eac71d750c75617a38e4b"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "type": "grass, poision",
  "attack": 300,
  "defense": 200,
  "height": 0.7
}
{
  "_id": ObjectId("575eac71d750c75617a38e4c"),
  "name": "Ivysaur",
  "description": "There is a bud on this Pokémon's back. To support its weight, Ivysaur's legs and trunk grow thick and strong. If it starts spending more time lying in the sunlight, it's a sign that the bud will bloom into a large flower soon. ",
  "type": "grass, poison",
  "attack": 300,
  "defense": 300,
  "height": 1
}
{
  "_id": ObjectId("575eac71d750c75617a38e4d"),
  "name": "Charmeleon",
  "description": "Charmeleon mercilessly destroys its foes using its sharp claws. If it encounters a strong foe, it turns aggressive. In this excited state, the flame at the tip of its tail flares with a bluish white color. ",
  "type": "fire",
  "attack": 300,
  "defense": 300,
  "height": 1.1
}
{
  "_id": ObjectId("575eac71d750c75617a38e4e"),
  "name": "Blastoise",
  "description": "Aloha aaaa",
  "type": "water",
  "attack": 400,
  "defense": 400,
  "height": 1.6
}
Fetched 4 record(s) in 1ms

```

## Liste todos os Pokemons com a altura menor ou igual que 0.5 e tipo grama

```
vahalla(mongod-3.2.7) be-mean-pokemons> var query = {$and: [{height: {$lte:0.5}},{type:/grass/}]}
vahalla(mongod-3.2.7) be-mean-pokemons> query
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

vahalla(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 31ms

```

## Liste todos os Pokemons com o name 'Pikachu' Ou com o attack menor ou igual que 0.5

```
vahalla(mongod-3.2.7) be-mean-pokemons> var query = {$or: [{attack: {$lte:0.5}},{name:/pikachu/i}]}
vahalla(mongod-3.2.7) be-mean-pokemons> query
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

vahalla(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("575eac71d750c75617a38e4f"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge. ",
  "type": "electric",
  "attack": 300,
  "defense": 200,
  "height": 0.4
}
Fetched 1 record(s) in 12ms


```

## Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com height menor ou igual que 0.5

```
vahalla(mongod-3.2.7) be-mean-pokemons> var query = {$and: [{attack: {$gte:48}},{height: {$lte:0.5}}]}
vahalla(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("575eac71d750c75617a38e4f"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge. ",
  "type": "electric",
  "attack": 300,
  "defense": 200,
  "height": 0.4
}
Fetched 1 record(s) in 1ms

```

