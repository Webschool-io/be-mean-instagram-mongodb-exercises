
MongoDb - Aula 02 - Exercício

Autor: Alex Lobo de O. Rodrigues

Criar database chamada be-mean-pokemons

use be-mean-pokemons
switched to db be-mean-pokemons

Listagem de todas dbs

show dbs
be-mean       → 0.203GB
be-mean-teste → 0.203GB
local         → 0.078GB


Listagem de todas as collections

show collections
be-mean-pokemons>

Criar cinco pokemons e inseri-los

be-mean-pokemons> var pokemon = {'name':'Pikachu','description':'Raio do poder', attack:12, defense:13, height: 0.4}
//create collection
be-mean-pokemons> db.createCollection("pokemons")
be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 1ms

be-mean-pokemons> var pokemon = {'name':'Bulbasauro','description':'Overgrow', attack:12, defense:13, height: 0.4}
be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 1ms

be-mean-pokemons> var pokemon = {'name':'Charizard','description':'Fogo', attack:12, defense:13, height: 0.4}
be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 1ms

be-mean-pokemons> var pokemon = {'name':'Pidgey','description':'Fogo', attack:12, defense:13, height: 0.4}
be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 0ms

be-mean-pokemons> var pokemon = {'name':'Snorlax','description':'Fogo', attack:12, defense:13, height: 0.4}
be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 1ms


Listar todos os pokemons

be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("57b8762f628b2d9cc662bf6a"),
  "name": "Pikachu",
  "description": "Raio do poder",
  "attack": 12,
  "defense": 13,
  "height": 0.4
}
{
  "_id": ObjectId("57b87688628b2d9cc662bf6b"),
  "name": "Bulbasauro",
  "description": "Overgrow",
  "attack": 12,
  "defense": 13,
  "height": 0.4
}
{
  "_id": ObjectId("57b8769d628b2d9cc662bf6c"),
  "name": "Charizard",
  "description": "Fogo",
  "attack": 12,
  "defense": 13,
  "height": 0.4
}
{
  "_id": ObjectId("57b876ad628b2d9cc662bf6d"),
  "name": "Pidgey",
  "description": "Fogo",
  "attack": 12,
  "defense": 13,
  "height": 0.4
}
{
  "_id": ObjectId("57b876c0628b2d9cc662bf6e"),
  "name": "Snorlax",
  "description": "Fogo",
  "attack": 12,
  "defense": 13,
  "height": 0.4
}
Fetched 5 record(s) in 4ms

Buscar um pokemon

be-mean-pokemons> var query = {name: 'Pikachu'}
var poke = db.pokemons.findOne(query)
poke
{
  "_id": ObjectId("57b8762f628b2d9cc662bf6a"),
  "name": "Pikachu",
  "description": "Raio do poder",
  "attack": 12,
  "defense": 13,
  "height": 0.4
}

Editar a description do pokemon escolhido

be-mean-pokemons> poke.description = 'Raio mudado'
Raio mudado

be-mean-pokemons> db.pokemons.save(poke)
