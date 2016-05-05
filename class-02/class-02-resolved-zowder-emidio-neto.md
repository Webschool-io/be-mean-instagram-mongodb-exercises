# MongoDB - Aula 02 - Exercício
autor: Emídio de Paiva Neto

## Criando database (passo 1)

```
wasdev@ubuntu:~$ mongo be-mean-pokemons
MongoDB shell version: 3.0.7
connecting to: be-mean-pokemons
Mongo-Hacker 0.0.9
ubuntu(mongod-3.0.7) be-mean-pokemons> 

```

## Listando databases (passo 2)

```
ubuntu(mongod-3.0.7) be-mean-pokemons> show dbs
pokemons          → 0.078GB
local             → 0.078GB
be-mean           → 0.078GB
be-mean-teste     → 0.078GB
be-mean-instagram → 0.078GB

```

## Listando collections da database be-mean-pokemons (passo 3)

```
ubuntu(mongod-3.0.7) be-mean-pokemons> show collections
ubuntu(mongod-3.0.7) be-mean-pokemons> 

```

## Cadastro dos pokemons (passo 4)

```
ubuntu(mongod-3.0.7) be-mean-pokemons> var pokemons = [

 { 'name':'Wartotle', 'description':'Os arranhões na sua concha são a prova de resistência deste Pokémon como um combatente.', 'type':'water', 'attack':'90', 'defense':'40', height: 1.0},
 { 'name':'Charizard', 'description':'Respira fogo que derrete qualquer coisa', 'type':'fire', 'attack':80, 'defense':60, height:1.7, },
 { 'name':'Vulpix', 'description':'Possui umas caudas muito loucas', 'type':'fire', 'attack':60, 'defense':40, height:0.6 },
 { 'name':'Raichu', 'description':'Solta vários raio muito doido', 'type':'electric', 'attack':110, 'defense':90, height:0.8 },
 { 'name':'Blastoise', 'description':'Blastoise tem bicas de água que se projetam de sua concha.',      'type':'water','attack':'110','defense':65,height:1.6}

]

ubuntu(mongod-3.0.7) be-mean-pokemons> db.savepokemons.save(pokemons)
Inserted 1 record(s) in 128ms
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

## Lista de todos os pokemons da collections pokemons (passo 5)

```
ubuntu(mongod-3.0.7) be-mean-pokemons> db.savepokemons.find()
{
  "_id": ObjectId("566365c797534bcf952d5735"),
  "name": "Wartotle",
  "description": "Os arranhões na sua concha são a prova de resistência deste Pokémon como um combatente.",
  "type": "water",
  "attack": "90",
  "defense": "40",
  "height": 1
}
{
  "_id": ObjectId("566365c797534bcf952d5736"),
  "name": "Charizard",
  "description": "Respira fogo que derrete qualquer coisa",
  "type": "fire",
  "attack": 80,
  "defense": 60,
  "height": 1.7
}
{
  "_id": ObjectId("566365c797534bcf952d5737"),
  "name": "Vulpix",
  "description": "Possui umas caudas muito loucas",
  "type": "fire",
  "attack": 60,
  "defense": 40,
  "height": 0.6
}
{
  "_id": ObjectId("566365c797534bcf952d5738"),
  "name": "Raichu",
  "description": "Solta vários raio muito doido",
  "type": "electric",
  "attack": 110,
  "defense": 90,
  "height": 0.8
}
{
  "_id": ObjectId("566365c797534bcf952d5739"),
  "name": "Blastoise",
  "description": "Blastoise tem bicas de água que se projetam de sua concha.",
  "type": "water",
  "attack": "110",
  "defense": 65,
  "height": 1.6
}


```

## Query para buscar um pokemon (passo 6)

```
ubuntu(mongod-3.0.7) be-mean-pokemons> var search = {name:'Raichu'}
ubuntu(mongod-3.0.7) be-mean-pokemons> var poke = db.savepokemons.findOne(search)
ubuntu(mongod-3.0.7) be-mean-pokemons> poke
{
  "_id": ObjectId("566365c797534bcf952d5738"),
  "name": "Raichu",
  "description": "Solta vários raio muito doido",
  "type": "electric",
  "attack": 110,
  "defense": 90,
  "height": 0.8
}

```

## Atualização do Pokemon selecionado (passo 7)

```
ubuntu(mongod-3.0.7) be-mean-pokemons> poke.description = "Irmão do Pikachu"
Irmão do Pikachu
ubuntu(mongod-3.0.7) be-mean-pokemons> db.savepokemons.save(poke)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

```

