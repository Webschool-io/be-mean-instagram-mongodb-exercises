# MongoDB - Aula 03 - Exercício
autor: Luan Henrique Santos Simões de Almeida


## Listagem dos pokemons com altura menor que 0.5 (passo 1)
```
inspiron(mongod-3.2.6) be-mean-pokemons> var query = {height:{$lt:0.5}}
inspiron(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```

## Listagem dos pokemons com altura maior ou igual que 0.5 (passo 2)
```
inspiron(mongod-3.2.6) be-mean-pokemons> var query = {height:{$gte:0.5}}
inspiron(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5740d9f4b5d3c29540fc4859"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "attack": 30,
  "defense": 20,
  "height": 0.7,
  "type": "grass",
  "no": 1
}
{
  "_id": ObjectId("5740d9f4b5d3c29540fc485a"),
  "name": "Ivysaur",
  "descrption": "There is a bud on this Pokémon's back. To support its weight, Ivysaur's legs and trunk grow thick and strong. If it starts spending more time lying in the sunlight, it's a sign that the bud will bloom into a large flower soon.",
  "attack": 30,
  "defense": 30,
  "height": 1,
  "type": "grass",
  "no": 2
}
{
  "_id": ObjectId("5740d9f4b5d3c29540fc485b"),
  "name": "Venusaur",
  "descritpion": "There is a large flower on Venusaur's back. The flower is said to take on vivid colors if it gets plenty of nutrition and sunlight. The flower's aroma soothes the emotions of people.",
  "attack": 40,
  "defense": 40,
  "height": 2,
  "type": "grass",
  "no": 3
}
{
  "_id": ObjectId("5740d9f4b5d3c29540fc485c"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
  "attack": 30,
  "defense": 20,
  "height": 0.6,
  "type": "fire",
  "no": 4
}
{
  "_id": ObjectId("5740d9f4b5d3c29540fc485d"),
  "name": "Charmeleon",
  "description": "Charmeleon mercilessly destroys its foes using its sharp claws. If it encounters a strong foe, it turns aggressive. In this excited state, the flame at the tip of its tail flares with a bluish white color.",
  "attack": 30,
  "defense": 30,
  "height": 1.1,
  "type": "fire",
  "no": 5
}
{
  "_id": ObjectId("5740d9f4b5d3c29540fc485e"),
  "name": "Charizard",
  "description": "Charizard flies around the sky in search of powerful opponents. It breathes fire of such great heat that it melts anything. However, it never turns its fiery breath on any opponent weaker than itself.",
  "attack": 40,
  "defense": 30,
  "height": 1.7,
  "type": "fire",
  "no": 6
}
Fetched 6 record(s) in 5ms
```

## Listagem dos pokemons com altura menor ou igual que 0.5 e do tipo grama (passo 3)
```
inspiron(mongod-3.2.6) be-mean-pokemons> var query = {$and: [{height:{$lte:0.5}, type:"grass"}]}
inspiron(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```

## Listagem dos pokemons com o nome 'Pikachu' ou ataque menor que 0.5
```
inspiron(mongod-3.2.6) be-mean-pokemons> var query = {$or:[{name:"Pikachu"}, {attack:{$lte:0.5}}]}
inspiron(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```

## Listagem dos pokemons com ataque maior ou igual que 48 e altura menor ou igual que 0.5
```
inspiron(mongod-3.2.6) be-mean-pokemons> var query = {$and:[{attack:{$gte:48}}, {height:{$lte:0.5}}]}
inspiron(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```
