
MongoDb - Aula 02 - Exercício

Autor: Wellington Pin ho

Criar database chamada be-mean-pokemons

use be-mean-pokemons
switched to db be-mean-pokemons

Listagem de todas dbs

admin    → (empty)
local    → 0.078GB
pokemons → 0.078GB

Listagem de todas as collections

show collections
be-mean-pokemons>

Criar cinco pokemons e inseri-los

be-mean-pokemons> var pokemon = {
    'name': 'Terrakion',
    'Description': 'Sua carga é forte o suficiente para quebrar através de uma parede de castelo gigante em um golpe.',
    'type': 'Fire',
    'attack': 7,
    'Defense': 4,
    'Speed': 6,
    'height': 0.4
},{
    'name': 'Infernape',
    'Description': 'A sua coroa de fogo é indicativo de sua natureza ardente. Ele é batido por ninguém em termos de rapidez.',
    'type': 'Rock',
    'attack': 5,
    'Defense': 3,
    'Speed': 6,
    'height': 0.4
},{
    'name': 'Squirtle',
    'Description': 'Ejeta água que passarinho não bebe',
    'type': 'água',
    'attack': 6,
    'Defense': 5,
    'Speed': 5,
    'height': 0.5
},{
    'name': 'Metapod',
    'Description': 'O escudo que cobre o corpo deste Pokémon é tão duro como uma laje de ferro.',
    'type': 'Bug',
    'attack': 1,
    'Defense': 3,
    'Speed': 2,
    'height': 0.3
},{
    'name': 'Arbok',
    'Description': 'Este Pokémon é terrivelmente forte, a fim de se contraem as coisas com o seu corpo. Ele pode até mesmo achatar tambores de óleo de aço. ',
    'type': 'Poison',
    'attack': 4,
    'Defense': 3,
    'Speed': 4,
    'height': 0.5
}
//create collection
be-mean-pokemons> db.createCollection("pokemons")
be-mean-pokemons> db.pokemons.insert(pokemon)
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


Listar todos os pokemons

well(mongod-2.6.10) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("57f3d2f412bf166e8e9b677e"),
  "name": "Terrakion",
  "Description": "Sua carga é forte o suficiente para quebrar através de uma parede de castelo gigante em um golpe.",
  "type": "Fire",
  "attack": 7,
  "Defense": 4,
  "Speed": 6,
  "height": 0.4
}
{
  "_id": ObjectId("57f3d2f412bf166e8e9b677f"),
  "name": "Infernape",
  "Description": "A sua coroa de fogo é indicativo de sua natureza ardente. Ele é batido por ninguém em termos de rapidez.",
  "type": "Rock",
  "attack": 5,
  "Defense": 3,
  "Speed": 6,
  "height": 0.4
}
{
  "_id": ObjectId("57f3d2f412bf166e8e9b6780"),
  "name": "Squirtle",
  "Description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 6,
  "Defense": 5,
  "Speed": 5,
  "height": 0.5
}
{
  "_id": ObjectId("57f3d2f412bf166e8e9b6781"),
  "name": "Metapod",
  "Description": "O escudo que cobre o corpo deste Pokémon é tão duro como uma laje de ferro.",
  "type": "Bug",
  "attack": 1,
  "Defense": 3,
  "Speed": 2,
  "height": 0.3
}
{
  "_id": ObjectId("57f3d2f412bf166e8e9b6782"),
  "name": "Arbok",
  "Description": "Este Pokémon é terrivelmente forte, a fim de se contraem as coisas com o seu corpo. Ele pode até mesmo achatar tambores de óleo de aço. ",
  "type": "Poison",
  "attack": 4,
  "Defense": 3,
  "Speed": 4,
  "height": 0.5
}
Fetched 5 record(s) in 5ms

Buscar um pokemon

be-mean-pokemons> var poke = {'name':'Metapod'}
be-mean-pokemons> var pokes = db.pokemons.findOne(poke)
be-mean-pokemons> pokes
{
  "_id": ObjectId("57f3d2f412bf166e8e9b6781"),
  "name": "Metapod",
  "Description": "O escudo que cobre o corpo deste Pokémon é tão duro como uma laje de ferro.",
  "type": "Bug",
  "attack": 1,
  "Defense": 3,
  "Speed": 2,
  "height": 0.3
}


Editar a description do pokemon escolhido

well(mongod-2.6.10) be-mean-pokemons> pokes.Description = 'MUDEI AQUI MEU FIO!'
MUDEI AQUI MEU FIO!
well(mongod-2.6.10) be-mean-pokemons> pokes
{
  "_id": ObjectId("57f3d2f412bf166e8e9b6781"),
  "name": "Metapod",
  "Description": "MUDEI AQUI MEU FIO!",
  "type": "Bug",
  "attack": 1,
  "Defense": 3,
  "Speed": 2,
  "height": 0.3
}
well(mongod-2.6.10) be-mean-pokemons> db.pokemons.save(pokes)
Updated 1 existing record(s) in 24ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
