#MongoDB - Aula 02 - Exercício
autor: Cristyan Rossi

## Crie uma database (passo 1)
```
mongo be-mean-pokemons
```

## Listagem das databases (passo 2)
```
$ mongo be-mean-pokemons

MongoDB shell version: 3.2.1
connecting to: be-mean-pokemons
Mongo-Hacker 0.0.4
show dbs
be-mean-instagram  0.078GB
be-mean-teste      0.078GB
be-mean            0.078GB
local              0.078GB
```

## Listagem das coleções (passo 3)
```
MongoDB shell version: 3.2.1
connecting to: be-mean-pokemons
Mongo-Hacker 0.0.4
show collections
```

## Inserir Pokemons (passo 4)
```
var pokemon = [{name:'Charizard', description: 'Dragão voador', type: 'inseto', attack: 30, height: 90.5, defense: 80},{name: 'Pidgeotto', description: 'Passáro voador', type: 'ave', attack: 10, height: 30, defense: 25},{name:'Kakuna', description: 'inseto imóvel', type: 'inseto', attack: 03, height: 10, defense: 09},{name:'Rattata', description: 'rato perigoso', type: 'roedor', attack: 10, height: 3.5, defense: 05 },{name:'Vulpix', description: 'raposa filhote', type: 'canino', attack: 10, height: 4.5, defense: 06}]
db.pokemons.insert(pokemon)
Inserted 1 record(s) in 2ms
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
db.pokemons.find()
{
    "_id": ObjectId("56acf7347cea4eaf5a4d9a53"),
    "name": "Charizard",
    "description": "Dragão voador",
    "type": "inseto",
    "attack": 30,
    "height": 90.5,
    "defense": 80
}
{
    "_id": ObjectId("56acf7347cea4eaf5a4d9a54"),
    "name": "Pidgeotto",
    "description": "Passáro voador",
    "type": "ave",
    "attack": 10,
    "height": 30,
    "defense": 25
}
{
    "_id": ObjectId("56acf7347cea4eaf5a4d9a55"),
    "name": "Kakuna",
    "description": "inseto imóvel",
    "type": "inseto",
    "attack": 3,
    "height": 10,
    "defense": 9
}
{
    "_id": ObjectId("56acf7347cea4eaf5a4d9a56"),
    "name": "Rattata",
    "description": "rato perigoso",
    "type": "roedor",
    "attack": 10,
    "height": 3.5,
    "defense": 5
}
{
    "_id": ObjectId("56acf7347cea4eaf5a4d9a57"),
    "name": "Vulpix",
    "description": "raposa filhote",
    "type": "canino",
    "attack": 10,
    "height": 4.5,
    "defense": 6
}
Fetched 05 record(s) in 3ms
```

## Lista dos pokemons (passo 6)
```
var query = {"name":"Vulpix"}
{
    "name": "Vulpix"
}
db.pokemons.find(query)
var poke = db.pokemons.findOne(query)
poke
{
    "_id": ObjectId("56acf7347cea4eaf5a4d9a57"),
    "name": "Vulpix",
    "description": "raposa filhote",
    "type": "canino",
    "attack": 10,
    "height": 4.5,
    "defense": 6
}
```

## Atualização do Pokemon (passo 7)
```
var poke = db.pokemons.findOne(query)
poke
{
    "_id": ObjectId("56acf7347cea4eaf5a4d9a57"),
    "name": "Vulpix",
    "description": "raposa filhote",
    "type": "canino",
    "attack": 10,
    "height": 4.5
    "defense": 6
}
poke.description
raposa filhote
poke.description = "raposa filhote com cauda"
raposa filhote com cauda
db.pokemons.save(poke)
Updated 1 existing record(s) in 2ms
WriteResult({
    "nMatched": 1,
    "nUpserted": 0,
    "nModified": 1
})
db.pokemons.findOne(query)
{
    "_id": ObjectId("56acf7347cea4eaf5a4d9a57"),
    "name": "Vulpix",
    "description": "raposa filhote com cauda",
    "type": "canino",
    "attack": 10,
    "height": 4.5
    "defense": 6
}
```










