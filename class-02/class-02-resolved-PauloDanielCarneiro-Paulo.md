# MongoDB - Aula 02 - Exercício
autor: Paulo Daniel Carneiro

## Criando database
```
Paulo-PC(mongod-3.0.12) be-mean> use be-mean-pokemons
switched to db be-mean-pokemons
```

## Listando databases no servidor
```
Paulo-PC(mongod-3.0.12) be-mean-pokemons> show dbs
be-mean → 0.078GB
local   → 0.078GB
```

## Listando coleções dessa database
```
Paulo-PC(mongod-3.0.12) be-mean-pokemons> show collections
Paulo-PC(mongod-3.0.12) be-mean-pokemons> 
```
Name, description attack defence height
var pokemons = [{"name": "bulbasaur", "description": "Pokemon planta", "type": "grass", "attack": 45, "defense": 30, "height": 7},{ "name" : "Charmander", "description" : "A chama que arde na ponta da sua cauda é uma indicação das suas emoções", "type" : "fogo", "attack" : 30, "height" : 0.6, "defense" : 20 }, { "name" : "Charizard", "description" : "Bicho feio que voa e cospe fogo", "type" : "fogo", "attack" : 40, "height" : 1.7, "defense" : 30 }, {name: "Venusaur", description: "There is a large flower on Venusaur's back", "type":"plant", attack: 4, defense: 4, height: 6.07}, {name: "Charmeleon", description: "Charmeleon mercilessly destroys its foes using its sharp claws","type":"fire", attack: 3, defense: 3, height: 3.07}]
## Inserindo pokemons
```
Paulo-PC(mongod-3.0.12) be-mean-pokemons> var pokemons = [{"name": "bulbasaur", "description": "Pokemon planta", "type": "grass", "attack": 45, "defense": 30, "height": 7},{ "name" : "Charmander", "description" : "A chama que arde na ponta da sua cauda é uma indicação das suas emoções", "type" : "fogo", "attack" : 30, "height" : 0.6, "defense" : 20 }, { "name" : "Charizard", "description" : "Bicho feio que voa e cospe fogo", "type" : "fogo", "attack" : 40, "height" : 1.7, "defense" : 30 }, {name: "Venusaur", description: "There is a large flower on Venusaur's back", "type":"plant", attack: 4, defense: 4, height: 6.07}, {name: "Charmeleon", description: "Charmeleon mercilessly destroys its foes using its sharp claws","type":"fire", attack: 3, defense: 3, height: 3.07}]

Paulo-PC(mongod-3.0.12) be-mean-pokemons> pokemons
[
  {
    "name": "bulbasaur",
    "description": "Pokemon planta",
    "type": "grass",
    "attack": 45,
    "defense": 30,
    "height": 7
  },
  {
    "name": "Charmander",
    "description": "A chama que arde na ponta da sua cauda é uma indicação das suas emoções",
    "type": "fogo",
    "attack": 30,
    "height": 0.6,
    "defense": 20
  },
  {
    "name": "Charizard",
    "description": "Bicho feio que voa e cospe fogo",
    "type": "fogo",
    "attack": 40,
    "height": 1.7,
    "defense": 30
  },
  {
    "name": "Venusaur",
    "description": "There is a large flower on Venusaur's back",
    "type": "plant",
    "attack": 4,
    "defense": 4,
    "height": 6.07
  },
  {
    "name": "Charmeleon",
    "description": "Charmeleon mercilessly destroys its foes using its sharp claws",
    "type": "fire",
    "attack": 3,
    "defense": 3,
    "height": 3.07
  }
]

Paulo-PC(mongod-3.0.12) be-mean-pokemons> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 820ms
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

## Lista de Pokemons
```
Paulo-PC(mongod-3.0.12) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("57d0b65537e697e8ef7398c9"),
  "name": "bulbasaur",
  "description": "Pokemon planta",
  "type": "grass",
  "attack": 45,
  "defense": 30,
  "height": 7
}
{
  "_id": ObjectId("57d0b65537e697e8ef7398ca"),
  "name": "Charmander",
  "description": "A chama que arde na ponta da sua cauda é uma indicação das suas emoções",
  "type": "fogo",
  "attack": 30,
  "height": 0.6,
  "defense": 20
}
{
  "_id": ObjectId("57d0b65537e697e8ef7398cb"),
  "name": "Charizard",
  "description": "Bicho feio que voa e cospe fogo",
  "type": "fogo",
  "attack": 40,
  "height": 1.7,
  "defense": 30
}
{
  "_id": ObjectId("57d0b65537e697e8ef7398cc"),
  "name": "Venusaur",
  "description": "There is a large flower on Venusaur's back",
  "type": "plant",
  "attack": 4,
  "defense": 4,
  "height": 6.07
}
{
  "_id": ObjectId("57d0b65537e697e8ef7398cd"),
  "name": "Charmeleon",
  "description": "Charmeleon mercilessly destroys its foes using its sharp claws",
  "type": "fire",
  "attack": 3,
  "defense": 3,
  "height": 3.07
}
Fetched 5 record(s) in 91ms
```

## Buscando um pokemon e armazenando em uma variavel poke
```
Paulo-PC(mongod-3.0.12) be-mean-pokemons> var query = {"name": "Charmeleon"}
Paulo-PC(mongod-3.0.12) be-mean-pokemons> query
{
  "name": "Charmeleon"
}
Fetched 1 record(s) in 1ms
Paulo-PC(mongod-3.0.12) be-mean-pokemons> var poke = db.pokemons.findOne(query)
Paulo-PC(mongod-3.0.12) be-mean-pokemons> poke
{
  "_id": ObjectId("57d0b65537e697e8ef7398cd"),
  "name": "Charmeleon",
  "description": "Charmeleon mercilessly destroys its foes using its sharp claws",
  "type": "fire",
  "attack": 3,
  "defense": 3,
  "height": 3.07
}

```

## Alterando a description
```
Paulo-PC(mongod-3.0.12) be-mean-pokemons> poke.description
Charmeleon mercilessly destroys its foes using its sharp claws
Paulo-PC(mongod-3.0.12) be-mean-pokemons> poke.description = "Charmeleon fights everywhere!"
Charmeleon fights everywhere!
Paulo-PC(mongod-3.0.12) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 76ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
Paulo-PC(mongod-3.0.12) be-mean-pokemons> db.pokemons.findOne(query)
{
  "_id": ObjectId("57d0b65537e697e8ef7398cd"),
  "name": "Charmeleon",
  "description": "Charmeleon fights everywhere!",
  "type": "fire",
  "attack": 3,
  "defense": 3,
  "height": 3.07
}
```
