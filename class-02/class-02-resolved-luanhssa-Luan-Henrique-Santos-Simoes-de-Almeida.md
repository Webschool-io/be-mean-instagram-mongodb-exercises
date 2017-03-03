# MongoDB - Aula 02 - Exercício
autor: Luan Henrique Santos Simões de Almeida

## Criando database be-mean-pokemons (passo 1)
```
inspiron(mongod-3.2.6) bemean> use be-mean-pokemons
switched to db be-mean-pokemons
```

## Listagem das databases (passo 2)
```
inspiron(mongod-3.2.6) be-mean-pokemons> show dbs
bemean → 0.005GB
local  → 0.000GB
test   → 0.000GB
```

## Listagem das coleções (passo 3)
```
inspiron(mongod-3.2.6) be-mean-pokemons> show collections
```

## Inserindo pokemons (passo 4)
```
var pokemons = [
    {name:"Bulbasaur", description:"Dragão de fogo.", attack:30, defense:20, height:0.7, type:"grass", no:1},
    {name:"Ivysaur", descrption:"There is a bud on this Pokémon's back. To support its weight, Ivysaur's legs and trunk grow thick and strong. If it starts spending more time lying in the sunlight, it's a sign that the bud will bloom into a large flower soon.", attack:30, defense:30, height:1, type:"grass", no:2},
    {name:"Venusaur", descritpion:"There is a large flower on Venusaur's back. The flower is said to take on vivid colors if it gets plenty of nutrition and sunlight. The flower's aroma soothes the emotions of people.", attack:40, defense:40, height:2, type:"grass", no:3},
    {name:"Charmander", description:"The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.", attack:30, defense:20, height:0.6, type:"fire", no:4},
    {name:"Charmeleon", description:"Charmeleon mercilessly destroys its foes using its sharp claws. If it encounters a strong foe, it turns aggressive. In this excited state, the flame at the tip of its tail flares with a bluish white color.", attack:30, defense:30, height:1.1, type:"fire", no:5},
    {name:"Charizard", description:"Charizard flies around the sky in search of powerful opponents. It breathes fire of such great heat that it melts anything. However, it never turns its fiery breath on any opponent weaker than itself.", attack:40, defense:30, height:1.7, type:"fire", no:6}
]
inspiron(mongod-3.2.6) be-mean-pokemons> db.pokemons.save(pokemons)
Inserted 1 record(s) in 205ms
BulkWriteResult({
  "writeErrors": [ ],
  "writeConcernErrors": [ ],
  "nInserted": 6,
  "nUpserted": 0,
  "nMatched": 0,
  "nModified": 0,
  "nRemoved": 0,
  "upserted": [ ]
})
```

## Listagem dos pokemons (passo 5)
```
inspiron(mongod-3.2.6) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("5740d9f4b5d3c29540fc4859"),
  "name": "Bulbasaur",
  "description": "Dragão de fogo.",
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

## Buscando um pokemon pelo nome e armazenando em uma variável 'poke' (passo 6)
```
inspiron(mongod-3.2.6) be-mean-pokemons> var poke = db.pokemons.findOne({name:"Bulbasaur"})
```

## Modificando a descrição do pokemon e salvando (passo 7)
```
inspiron(mongod-3.2.6) be-mean-pokemons> poke.description = "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger."
Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.
inspiron(mongod-3.2.6) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
inspiron(mongod-3.2.6) be-mean-pokemons> db.pokemons.findOne({name:"Bulbasaur"})
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
```
