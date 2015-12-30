# MongoDB - Aula 02 - Exercício
autor: Werner Eduard Gutschow

## Listagem das databases (passo 2)

wernerlinux(mongod-3.0.8) be-mean-instagram> use be-mean-pokemons
switched to db be-mean-pokemons
wernerlinux(mongod-3.0.8) be-mean-pokemons> show dbs
local             → 0.078GB
be-mean-instagram → 0.078GB
be-mean           → 0.078GB


## Listagem das coleções (passo 3)

wernerlinux(mongod-3.0.8) be-mean-pokemons> show collections
wernerlinux(mongod-3.0.8) be-mean-pokemons>

## Cadastro dos pokemons (passo 4)

var pokemon = [{'name':'Charizard','description':'Meio alternativo para quem não tem churrasqueira','Type':'fogo', attack:40,height: 5.7},{'name':'Blastoise','description':'Canhão de água','Type':'água', attack:40,height: 5.3},{'name':'Magneton','description':' Ímã de geladeira potente','Type':'Magnetico', attack:30,height: 3.3},{'name':'Bergmite','description':'Ótimo para resfriar sua bebida','Type':'Gelo', attack:40,height: 3.3},{'name':'Pangoro','description':'Panda vida Loka','Type':'Dounting', attack:60,height: 6.11}]

wernerlinux(mongod-3.0.8) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 262ms
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


## Lista dos pokemons (passo 5)

wernerlinux(mongod-3.0.8) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("5681c6780dba9fd60c24f21c"),
  "name": "Charizard",
  "description": "Meio alternativo para quem não tem churrasqueira",
  "Type": "fogo",
  "attack": 40,
  "height": 5.7
}
{
  "_id": ObjectId("5681c6780dba9fd60c24f21d"),
  "name": "Blastoise",
  "description": "Canhão de água",
  "Type": "água",
  "attack": 40,
  "height": 5.3
}
{
  "_id": ObjectId("5681c6780dba9fd60c24f21e"),
  "name": "Magneton",
  "description": " Ímã de geladeira potente",
  "Type": "Magnetico",
  "attack": 30,
  "height": 3.3
}
{
  "_id": ObjectId("5681c6780dba9fd60c24f21f"),
  "name": "Bergmite",
  "description": "Ótimo para resfriar sua bebida",
  "Type": "Gelo",
  "attack": 40,
  "height": 3.3
}
{
  "_id": ObjectId("5681c6780dba9fd60c24f220"),
  "name": "Pangoro",
  "description": "Panda vida Loka",
  "Type": "Dounting",
  "attack": 60,
  "height": 6.11
}
Fetched 5 record(s) in 3ms


## Pikachu (passo 6)

wernerlinux(mongod-3.0.8) be-mean-pokemons> var query = {name: 'Pangoro'}
wernerlinux(mongod-3.0.8) be-mean-pokemons> var poke = db.pokemons.findOne(query)
wernerlinux(mongod-3.0.8) be-mean-pokemons> poke
{
  "_id": ObjectId("5681c6780dba9fd60c24f220"),
  "name": "Pangoro",
  "description": "Panda vida Loka",
  "Type": "Dounting",
  "attack": 60,
  "height": 6.11
}



## Atualização do Pikachu (passo 6)

wernerlinux(mongod-3.0.8) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 3ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})



wernerlinux(mongod-3.0.8) be-mean-pokemons> db.pokemons.findOne(query)
{
  "_id": ObjectId("5681c6780dba9fd60c24f220"),
  "name": "Pangoro",
  "description": "Urso Bombadao",
  "Type": "Dounting",
  "attack": 60,
  "height": 6.11

}






