# MongoDB - Aula 02 - Exercício
autor: Cristiano Mesquita

## Criando Database

ubuntu(mongod-2.6.10) be-mean-instagram> use be-mean-pokemons
switched to db be-mean-pokemons
ubuntu(mongod-2.6.10) be-mean-pokemons>

## Listando Databases no servidor

ubuntu(mongod-2.6.10) be-mean-pokemons> show dbs
admin                   → (empty)
be-mean-instagram       → 0.078GB
be-mean-instagram-teste → 0.078GB
be-mean-pokemons        → (empty)
local                   → 0.078GB
ubuntu(mongod-2.6.10) be-mean-pokemons> 

## Listando Collections na Database be-mean-pokemons

ubuntu(mongod-2.6.10) be-mean-pokemons> show collections
ubuntu(mongod-2.6.10) be-mean-pokemons> 

## Inserindo pokemons na base be-mean-pokemons

ubuntu(mongod-2.6.10) be-mean-pokemons> var pokemons =[ {name:"Jigglypuff",description:"Cute, charm and competitive",attack:2,defense:1,height:0.5},{name:"Charizard",description:"Blaze",attack:4,defense:3,height:1.7},{name:"Wartortle",description:"Torrent",attack:3,defense:4,height:1.0},{name:"Butterfree",description:"Compound eyes",attack:2,defense:2,height:1.1},{name:"Metapod",description:"Shed skin",attack:1,defense:3,height:0.7}];
ubuntu(mongod-2.6.10) be-mean-pokemons> 

ubuntu(mongod-2.6.10) be-mean-pokemons> db.pokemons.save(pokemons);
Inserted 1 record(s) in 834ms
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
ubuntu(mongod-2.6.10) be-mean-pokemons> 

## Listando pokemons na base be-mean-pokemons

ubuntu(mongod-2.6.10) be-mean-pokemons> db.pokemons.find({});
{
  "_id": ObjectId("574b1303c162d1f1b51cd39d"),
  "name": "Jigglypuff",
  "description": "Cute, charm and competitive",
  "attack": 2,
  "defense": 1,
  "height": 0.5
}
{
  "_id": ObjectId("574b1303c162d1f1b51cd39e"),
  "name": "Charizard",
  "description": "Blaze",
  "attack": 4,
  "defense": 3,
  "height": 1.7
}
{
  "_id": ObjectId("574b1303c162d1f1b51cd39f"),
  "name": "Wartortle",
  "description": "Torrent",
  "attack": 3,
  "defense": 4,
  "height": 1
}
{
  "_id": ObjectId("574b1303c162d1f1b51cd3a0"),
  "name": "Butterfree",
  "description": "Compound eyes",
  "attack": 2,
  "defense": 2,
  "height": 1.1
}
{
  "_id": ObjectId("574b1303c162d1f1b51cd3a1"),
  "name": "Metapod",
  "description": "Shed skin",
  "attack": 1,
  "defense": 3,
  "height": 0.7
}
Fetched 5 record(s) in 2ms

## Pesquisando um determinado pokemon

ubuntu(mongod-2.6.10) be-mean-pokemons> var poke = db.pokemons.findOne({name:"Metapod"})
ubuntu(mongod-2.6.10) be-mean-pokemons> poke
{
  "_id": ObjectId("574b1303c162d1f1b51cd3a1"),
  "name": "Metapod",
  "description": "Shed skin",
  "attack": 1,
  "defense": 3,
  "height": 0.7
}
ubuntu(mongod-2.6.10) be-mean-pokemons> 

## Modificando a descrição do Metapod e Salvando

ubuntu(mongod-2.6.10) be-mean-pokemons> poke.description
Shed skin
ubuntu(mongod-2.6.10) be-mean-pokemons> poke.description = "Nova descrição do Metapod"
Nova descrição do Metapod
ubuntu(mongod-2.6.10) be-mean-pokemons> db.pokemons.save(poke);
Updated 1 existing record(s) in 35ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
ubuntu(mongod-2.6.10) be-mean-pokemons> poke
{
  "_id": ObjectId("574b1303c162d1f1b51cd3a1"),
  "name": "Metapod",
  "description": "Nova descrição do Metapod",
  "attack": 1,
  "defense": 3,
  "height": 0.7
}
ubuntu(mongod-2.6.10) be-mean-pokemons>







