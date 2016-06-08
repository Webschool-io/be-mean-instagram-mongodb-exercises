MongoDb - Aula 02 - Exercício
Autor: Caio Henrique Ribeiro Martins

##Criar database chamada be-mean-pokemons
caio-pc(mongod-3.2.7) be-mean-instagram> use be-mean-pokemons
switched to db be-mean-pokemons

##Listagem de todas dbs
caio-pc(mongod-3.2.7) be-mean-pokemons> show dbs
be-mean           → 0.005GB
be-mean-instagram → 0.000GB
local             → 0.000GB

##Listagem de todas as collections
caio-pc(mongod-3.2.7) be-mean-pokemons> show collections


##Criar cinco pokemons

be-mean-pokemons> var pokemon = {'name':'Beedrill','description':'Abelha louca','type':'inseto','attack':30,'height':0.33}
caio-pc(mongod-3.2.7) be-mean-pokemons> db.pokemons.save(pokemon)
Inserted 1 record(s) in 401ms
WriteResult({
  "nInserted": 1
})
caio-pc(mongod-3.2.7) be-mean-pokemons> db.pokemons.save({'name':'Drilbur','description':'Tamandua','type':'chão','attack':20,'height':0.20})
Inserted 1 record(s) in 90ms
WriteResult({
  "nInserted": 1
})
caio-pc(mongod-3.2.7) be-mean-pokemons> db.pokemons.save({'name':'Simisage','description':'Macaco verde','type':'grama','attack':35,'height':0.37})
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})
caio-pc(mongod-3.2.7) be-mean-pokemons> db.pokemons.save({'name':'Bulbasaur','description':'Bicho que atira sementes','type':'grama','attack':20,'height':0.50})
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})
caio-pc(mongod-3.2.7) be-mean-pokemons> db.pokemons.save({'name':'Leafeon','description':'Bicho que parece um gato mas não é','type':'grama','attack':40,'height':0.45})
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})
caio-pc(mongod-3.2.7) be-mean-pokemons> db.pokemons.save({'name':'Basculin','description':'Peixe feio para caralho','type':'Água','attack':23,'height':0.40})
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})


##Listar todos os pokemons

db.pokemons.find()
{
  "_id": ObjectId("57582f70380bcf6f30d066fb"),
  "name": "Beedrill",
  "description": "Abelha louca",
  "type": "inseto",
  "attack": 30,
  "height": 0.33
}
{
  "_id": ObjectId("5758300c380bcf6f30d066fc"),
  "name": "Drilbur",
  "description": "Tamandua",
  "type": "chão",
  "attack": 20,
  "height": 0.2
}
{
  "_id": ObjectId("57583055380bcf6f30d066fd"),
  "name": "Simisage",
  "description": "Macaco verde",
  "type": "grama",
  "attack": 35,
  "height": 0.37
}
{
  "_id": ObjectId("5758309f380bcf6f30d066fe"),
  "name": "Bulbasaur",
  "description": "Bicho que atira sementes",
  "type": "grama",
  "attack": 20,
  "height": 0.5
}
{
  "_id": ObjectId("575830f5380bcf6f30d066ff"),
  "name": "Leafeon",
  "description": "Bicho que parece um gato mas não é",
  "type": "grama",
  "attack": 40,
  "height": 0.45
}
{
  "_id": ObjectId("57583139380bcf6f30d06700"),
  "name": "Basculin",
  "description": "Peixe feio para caralho",
  "type": "Água",
  "attack": 23,
  "height": 0.4
}
Fetched 6 record(s) in 1472ms


##Buscar um pokemon

caio-pc(mongod-3.2.7) be-mean-pokemons> var poke = db.pokemons.findOne({'name':'Drilbur'})


##Editar a description do pokemon escolhido

poke.description = 'Alterando descrição pq mandaram fazer isso'
Alterando descrição pq mandaram fazer isso
caio-pc(mongod-3.2.7) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 63ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})


