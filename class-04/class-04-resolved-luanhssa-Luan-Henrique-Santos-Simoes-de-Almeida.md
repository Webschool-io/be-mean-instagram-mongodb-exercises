# MongoDB - Aula 04 - Exercício
autor: Luan Henrique Santos Simões de Almeida

## Adicionando dois ataques para Pikachu, Squirtle, Bulbassauro e Charmander (passo 1)
```
inspiron(mongod-3.2.6) be-mean-pokemons> var query = {name: {$in: [/pikachu/i, /squirtle/i, /bulbasaur/i, /charmander/i]}}
inspiron(mongod-3.2.6) be-mean-pokemons> var mod = {$pushAll: {moves: ['ataque rápido', 'cabeçada']}}
inspiron(mongod-3.2.6) be-mean-pokemons> var options = {multi: true}
inspiron(mongod-3.2.6) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 18ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
```

## Adicionando o movimento desvio em todos (passo 2)
```
inspiron(mongod-3.2.6) be-mean-pokemons> var query = {}
inspiron(mongod-3.2.6) be-mean-pokemons> var mod = {$push: { moves: 'desvio'}}
inspiron(mongod-3.2.6) be-mean-pokemons> var options = {multi: true}
inspiron(mongod-3.2.6) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 8 existing record(s) in 2ms
WriteResult({
  "nMatched": 8,
  "nUpserted": 0,
  "nModified": 8
})
```

## Adicionando o pokemon 'AindaNaoExisteMon' (passo 3)
```
inspiron(mongod-3.2.6) be-mean-pokemons> var query = {name: /aindanaoexistemon/i}
inspiron(mongod-3.2.6) be-mean-pokemons> var mod = {$set: {description: "Sem maiores informações."}, $setOnInsert: {name:"AindaNaoExisteMon", attack:null, defense:null, height:null, type:null}}
inspiron(mongod-3.2.6) be-mean-pokemons> var options = {upsert: true}
inspiron(mongod-3.2.6) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 1ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("5741be11b652f8b30414147f")
})
```

## Listagem dos pokemons que possuam 'investida' e 'ataque rápido' (passo 4)
```
inspiron(mongod-3.2.6) be-mean-pokemons> var query = {moves: {$all: [/ataque rápido/i, /investida/i]}}
inspiron(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5741baa39ed40ebd7b7383a2"),
  "name": "Pikachu",
  "description": "Rato elétrico fofinho.",
  "attack": 100,
  "height": 0.4,
  "type": "electric",
  "no": 25,
  "moves": [
    "ataque rápido",
    "cabeçada",
    "desvio",
    "investida"
  ]
}
Fetched 1 record(s) in 2ms
```

## Listagem dos pokemons que possuam 'ataque rapiddo' e 'cabeçada' (passo 5)
```
inspiron(mongod-3.2.6) be-mean-pokemons> var query = {moves: {$all: [/ataque rápido/i, /cabeçada/i]}}
inspiron(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5740d9f4b5d3c29540fc4859"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "attack": 30,
  "defense": 20,
  "height": 0.7,
  "type": "grass",
  "no": 1,
  "moves": [
    "ataque rápido",
    "cabeçada",
    "desvio"
  ]
}
{
  "_id": ObjectId("5740d9f4b5d3c29540fc485c"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
  "attack": 30,
  "defense": 20,
  "height": 0.6,
  "type": "fire",
  "no": 4,
  "moves": [
    "ataque rápido",
    "cabeçada",
    "desvio"
  ]
}
{
  "_id": ObjectId("5741baa39ed40ebd7b7383a2"),
  "name": "Pikachu",
  "description": "Rato elétrico fofinho.",
  "attack": 100,
  "height": 0.4,
  "type": "electric",
  "no": 25,
  "moves": [
    "ataque rápido",
    "cabeçada",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("5741baa39ed40ebd7b7383a3"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe.",
  "attack": 48,
  "height": 0.5,
  "type": "water",
  "no": 7,
  "moves": [
    "ataque rápido",
    "cabeçada",
    "desvio"
  ]
}
Fetched 4 record(s) in 2ms
```

## Listagem dos pokemons que não são do tipo 'elétrico' (passo 6)
```
inspiron(mongod-3.2.6) be-mean-pokemons> var query = {type: {$ne: "electric"}}
inspiron(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5740d9f4b5d3c29540fc4859"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "attack": 30,
  "defense": 20,
  "height": 0.7,
  "type": "grass",
  "no": 1,
  "moves": [
    "ataque rápido",
    "cabeçada",
    "desvio"
  ]
}
{
  "_id": ObjectId("5740d9f4b5d3c29540fc485a"),
  "name": "Ivysaur",
  "descrption": "There is a bud on this Pokémon's back. To support its weight, Ivysaur's legs and trunk grow thick and strong. If it starts spending more time lying in the sunlight, it's a sign that the bud will bloom into a large flower soon.",
  "attack": 30,
  "defense": 30,
  "height": 1,
  "type": "grass",
  "no": 2,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5740d9f4b5d3c29540fc485b"),
  "name": "Venusaur",
  "descritpion": "There is a large flower on Venusaur's back. The flower is said to take on vivid colors if it gets plenty of nutrition and sunlight. The flower's aroma soothes the emotions of people.",
  "attack": 40,
  "defense": 40,
  "height": 2,
  "type": "grass",
  "no": 3,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5740d9f4b5d3c29540fc485c"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
  "attack": 30,
  "defense": 20,
  "height": 0.6,
  "type": "fire",
  "no": 4,
  "moves": [
    "ataque rápido",
    "cabeçada",
    "desvio"
  ]
}
{
  "_id": ObjectId("5740d9f4b5d3c29540fc485d"),
  "name": "Charmeleon",
  "description": "Charmeleon mercilessly destroys its foes using its sharp claws. If it encounters a strong foe, it turns aggressive. In this excited state, the flame at the tip of its tail flares with a bluish white color.",
  "attack": 30,
  "defense": 30,
  "height": 1.1,
  "type": "fire",
  "no": 5,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5740d9f4b5d3c29540fc485e"),
  "name": "Charizard",
  "description": "Charizard flies around the sky in search of powerful opponents. It breathes fire of such great heat that it melts anything. However, it never turns its fiery breath on any opponent weaker than itself.",
  "attack": 40,
  "defense": 30,
  "height": 1.7,
  "type": "fire",
  "no": 6,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5741baa39ed40ebd7b7383a3"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe.",
  "attack": 48,
  "height": 0.5,
  "type": "water",
  "no": 7,
  "moves": [
    "ataque rápido",
    "cabeçada",
    "desvio"
  ]
}
{
  "_id": ObjectId("5741be11b652f8b30414147f"),
  "description": "Sem maiores informações.",
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "type": null
}
Fetched 8 record(s) in 5ms
```

## Listagem dos pokemons que tenham 'investida' e não menor ou igual a 49 (passo 7)
```
inspiron(mongod-3.2.6) be-mean-pokemons> var query = {$and: [{moves: {$in: [/investida/i]}}, {defense: {$not: {$lte:49}}}]}
inspiron(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5741baa39ed40ebd7b7383a2"),
  "name": "Pikachu",
  "description": "Rato elétrico fofinho.",
  "attack": 100,
  "height": 0.4,
  "type": "electric",
  "no": 25,
  "moves": [
    "ataque rápido",
    "cabeçada",
    "desvio",
    "investida"
  ]
}
Fetched 1 record(s) in 2ms
```

## Removendo os pokemons do tipo água com ataque menor que 50 (passo 8)
```
inspiron(mongod-3.2.6) be-mean-pokemons> var query = {$and: [{type: /water/i}, {attack: {$lt: 50}}]}
inspiron(mongod-3.2.6) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 3ms
WriteResult({
  "nRemoved": 1
})
```
