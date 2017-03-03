
# MongoDB - Aula 02 - Exercício
autor: Leonardo Flores

## Listagem das databases (passo 2)

```
MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean-pokemons> use be-mean-pokemons
switched to db be-mean-pokemons

MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean-pokemons> show dbs
be-mean → 0.004GB
local   → 0.000GB
test    → 0.000GB
```

## Listagem das coleções (passo 3)

```
show collections
MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean-pokemons> 
```

## Cadastro dos pokemons (passo 4)

```
MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean-pokemons> var pokemons = [{name: "Bulbasaur", description: "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger." , attack: 3 , defense: 2, height: 0.7},{name: "Ivysaur", description: "There is a bud on this Pokémon's back. To support its weight, Ivysaur's legs and trunk grow thick and strong. If it starts spending more time lying in the sunlight, it's a sign that the bud will bloom into a large flower soon." , attack: 3 , defense: 3, height: 1.0},{name: "Venusaur", description: "There is a large flower on Venusaur's back. The flower is said to take on vivid colors if it gets plenty of nutrition and sunlight. The flower's aroma soothes the emotions of people." , attack: 4 , defense: 4, height: 2.0},{name: "Charmander", description: "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely." , attack: 3 , defense: 2, height: 0.6},{name: "Charmeleon", description: "Charmeleon mercilessly destroys its foes using its sharp claws. If it encounters a strong foe, it turns aggressive. In this excited state, the flame at the tip of its tail flares with a bluish white color." , attack: 3 , defense: 3, height: 1.1}]

MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean-pokemons> pokemons
[
  {
    "name": "Bulbasaur",
    "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
    "attack": 3,
    "defense": 2,
    "height": 0.7
  },
  {
    "name": "Ivysaur",
    "description": "There is a bud on this Pokémon's back. To support its weight, Ivysaur's legs and trunk grow thick and strong. If it starts spending more time lying in the sunlight, it's a sign that the bud will bloom into a large flower soon.",
    "attack": 3,
    "defense": 3,
    "height": 1
  },
  {
    "name": "Venusaur",
    "description": "There is a large flower on Venusaur's back. The flower is said to take on vivid colors if it gets plenty of nutrition and sunlight. The flower's aroma soothes the emotions of people.",
    "attack": 4,
    "defense": 4,
    "height": 2
  },
  {
    "name": "Charmander",
    "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
    "attack": 3,
    "defense": 2,
    "height": 0.6
  },
  {
    "name": "Charmeleon",
    "description": "Charmeleon mercilessly destroys its foes using its sharp claws. If it encounters a strong foe, it turns aggressive. In this excited state, the flame at the tip of its tail flares with a bluish white color.",
    "attack": 3,
    "defense": 3,
    "height": 1.1
  }
]

MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean-pokemons> db.pokedex.insert(pokemons)
Inserted 1 record(s) in 24ms
BulkWriteResult({
  "writeErrors": [ ],
  "writeConcernErrors": [ ],
  "nInserted": 5,
  "nUpserted": 0,
  "nMatched": 0,
  "nModified": 0,
  "nRemoved": 0,
  "upserted": [ ]
})
```

## Lista dos pokemons (passo 5)

```
MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean-pokemons> db.pokedex.find({})
{
  "_id": ObjectId("56e837e36afcf13f23fa81d0"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "attack": 3,
  "defense": 2,
  "height": 0.7
}
{
  "_id": ObjectId("56e837e36afcf13f23fa81d1"),
  "name": "Ivysaur",
  "description": "There is a bud on this Pokémon's back. To support its weight, Ivysaur's legs and trunk grow thick and strong. If it starts spending more time lying in the sunlight, it's a sign that the bud will bloom into a large flower soon.",
  "attack": 3,
  "defense": 3,
  "height": 1
}
{
  "_id": ObjectId("56e837e36afcf13f23fa81d2"),
  "name": "Venusaur",
  "description": "There is a large flower on Venusaur's back. The flower is said to take on vivid colors if it gets plenty of nutrition and sunlight. The flower's aroma soothes the emotions of people.",
  "attack": 4,
  "defense": 4,
  "height": 2
}
{
  "_id": ObjectId("56e837e36afcf13f23fa81d3"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
  "attack": 3,
  "defense": 2,
  "height": 0.6
}
{
  "_id": ObjectId("56e837e36afcf13f23fa81d4"),
  "name": "Charmeleon",
  "description": "Charmeleon mercilessly destroys its foes using its sharp claws. If it encounters a strong foe, it turns aggressive. In this excited state, the flame at the tip of its tail flares with a bluish white color.",
  "attack": 3,
  "defense": 3,
  "height": 1.1
}
Fetched 5 record(s) in 4ms

```

## Pokemon (passo 6)

```
MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean-pokemons> var poke = db.pokedex.findOne({name: 'Pikachu'})
MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean-pokemons> poke
{
  "_id": ObjectId("56e83c4a6afcf13f23fa81dd"),
  "name": "Pikachu",
  "height": 0.4,
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge.",
  "attack": 4,
  "defense": 2
}

```

## Atualização do Pokemon (passo 7)

```
MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean-pokemons> var poke = db.pokedex.findOne({name: 'Pikachu'})
MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean-pokemons> poke
{
  "_id": ObjectId("56e83c4a6afcf13f23fa81dd"),
  "name": "Pikachu",
  "height": 0.4,
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge.",
  "attack": 4,
  "defense": 2
} 
MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean-pokemons> poke.description
Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge.
MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean-pokemons> poke.description = 'Modifiquei'
Modifiquei
MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean-pokemons> db.pokedex.save(poke)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
MacBook-Pro-de-Leonardo(mongod-3.2.1) be-mean-pokemons> db.pokedex.findOne({name: 'Pikachu'})
{
  "_id": ObjectId("56e8389a6afcf13f23fa81d5"),
  "name": "Pikachu",
  "height": 0.4,
  "description": "Modifiquei",
  "attack": 4,
  "defense": 2
}

```