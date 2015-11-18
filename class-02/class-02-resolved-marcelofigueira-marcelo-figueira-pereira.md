Listagem das databases (passo 2)
marcelo-note(mongod-2.6.10) be-mean-pokemons> show dbs
be-mean                   → 0.078GB
be-mean-instagram         → 0.078GB
local                     → 0.078GB
be-mean-pokemons          → 0.078GB
be-mean-instagram-teste   → 0.078GB
admin                     → (empty)
be-mean-instagram-mongodb → (empty)



Listagem das coleções (passo 3)
marcelo-note(mongod-2.6.10) be-mean-pokemons> show collections
pokemons       → 0.000MB / 0.008MB
system.indexes → 0.000MB / 0.008MB


Cadastro dos pokemons (passo 4)
marcelo-note(mongod-2.6.10) be-mean-pokemons> var pokemon = {'name':'Sandshrew','description':'Tatu bola paraense','type':'electric',attack:55, height:0.2}
marcelo-note(mongod-2.6.10) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 4ms
WriteResult({
  "nInserted": 1
})
ETC....

Lista dos pokemons (passo 5)
marcelo-note(mongod-2.6.10) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("5648c7aaa11628f93b7cb11c"),
  "name": "Pikachu",
  "description": "Rato lindão amarelo",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("5648c9ce63153daa33cba5cf"),
  "name": "Sandshrew",
  "description": "Tatu bola paraense",
  "type": "electric",
  "attack": 55,
  "height": 0.2
}
{
  "_id": ObjectId("5648ca4a63153daa33cba5d0"),
  "name": "Finneon",
  "description": "Peixinho fudido",
  "type": "water",
  "attack": 30,
  "height": 0.4
}
{
  "_id": ObjectId("5648cabf63153daa33cba5d1"),
  "name": "Bastiodon",
  "description": "Cara de pedra",
  "type": "Rock",
  "attack": 30,
  "height": 0.3
}
{
  "_id": ObjectId("5648cb2b63153daa33cba5d2"),
  "name": "Abra",
  "description": "Filho do kadabra",
  "type": "Psychic",
  "attack": 10,
  "height": 0.1
}
{
  "_id": ObjectId("5648cb6663153daa33cba5d3"),
  "name": "Kadabra",
  "description": "evolução do abra",
  "type": "Psychic",
  "attack": 20,
  "height": 0.3
}
Fetched 6 record(s) in 1ms



buscar poke  (passo 6)
marcelo-note(mongod-2.6.10) be-mean-pokemons> var busca = {name: 'Abra'}
marcelo-note(mongod-2.6.10) be-mean-pokemons> var poke = db.pokemons.find(busca)
marcelo-note(mongod-2.6.10) be-mean-pokemons> poke
{
  "_id": ObjectId("5648cb2b63153daa33cba5d2"),
  "name": "Abra",
  "description": "Filho do kadabra",
  "type": "Psychic",
  "attack": 10,
  "height": 0.1
}
Fetched 1 record(s) in 1ms
marcelo-note(mongod-2.6.10) be-mean-pokemons> poke.name
marcelo-note(mongod-2.6.10) be-mean-pokemons> var poke = db.pokemons.findOne(busca)
marcelo-note(mongod-2.6.10) be-mean-pokemons> poke.name
Abra



Atualização do Poke (passo 6)

marcelo-note(mongod-2.6.10) be-mean-pokemons> poke.description = 'Descrição editada do abra'
Descrição editada do abra
marcelo-note(mongod-2.6.10) be-mean-pokemons> poke
{
  "_id": ObjectId("5648cb2b63153daa33cba5d2"),
  "name": "Abra",
  "description": "Descrição editada do abra",
  "type": "Psychic",
  "attack": 10,
  "height": 0.1
}
