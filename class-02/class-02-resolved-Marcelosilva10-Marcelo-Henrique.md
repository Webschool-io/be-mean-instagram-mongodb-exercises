#MongoDB - Aula 02 - Exercício

autor: Marcelo Henrique

##Listagem de Database

MarceloLocal(mongod-2.4.9) be-mean-instagram> use be-mean-pokemons
switched to db be-mean-pokemons
MarceloLocal(mongod-2.4.9) be-mean-pokemons> 

Lista de DBS

MarceloLocal(mongod-2.4.9) be-mean-pokemons> show dbs
local             → 0.031GB
exercises         → 0.125GB
be-mean           → 0.250GB
be-mean-instagram → 0.063GB

Show collections

MarceloLocal(mongod-2.4.9) be-mean-pokemons> show collections
MarceloLocal(mongod-2.4.9) be-mean-pokemons> var pokemons = [{'nome':'Mewtwo','description':'Pscico muito foda','type':'Psychic',attack:93, height: 2.0},{'nome':'New','description':'Pscico bonzinho','type':'Psychic',attack:73, height: 0.4},{'nome':'Lugia','description':'Provoca furaca catrina por 40 dias','type':'Psychic/Flying',attack:60, height: 5.2},{'nome':'Kyurem','description':'Pokemon transforma em qualquer um','type':'Dragon/Ice',attack:67, height: 3.0},{'nome':'Djalga','description':'Volta no tempo','type':'Dragon',attack:80, height: 5.4}]

MarceloLocal(mongod-2.4.9) be-mean-pokemons> pokemons
[
  {
    "nome": "Mewtwo",
    "description": "Pscico muito foda",
    "type": "Psychic",
    "attack": 93,
    "height": 2
  },
  {
    "nome": "New",
    "description": "Pscico bonzinho",
    "type": "Psychic",
    "attack": 73,
    "height": 0.4
  },
  {
    "nome": "Lugia",
    "description": "Provoca furaca catrina por 40 dias",
    "type": "Psychic/Flying",
    "attack": 60,
    "height": 5.2
  },
  {
    "nome": "Kyurem",
    "description": "Pokemon transforma em qualquer um",
    "type": "Dragon/Ice",
    "attack": 67,
    "height": 3
  },
  {
    "nome": "Djalga",
    "description": "Volta no tempo",
    "type": "Dragon",
    "attack": 80,
    "height": 5.4
  }
]

MarceloLocal(mongod-2.4.9) be-mean-pokemons> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 317ms

## Lista dos pokemons

MarceloLocal(mongod-2.4.9) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("564f45dbd9992fae819fb007"),
  "nome": "Mewtwo",
  "description": "Pscico muito foda",
  "type": "Psychic",
  "attack": 93,
  "height": 2
}
{
  "_id": ObjectId("564f45dbd9992fae819fb008"),
  "nome": "New",
  "description": "Pscico bonzinho",
  "type": "Psychic",
  "attack": 73,
  "height": 0.4
}
{
  "_id": ObjectId("564f45dbd9992fae819fb009"),
  "nome": "Lugia",
  "description": "Provoca furaca catrina por 40 dias",
  "type": "Psychic/Flying",
  "attack": 60,
  "height": 5.2
}
{
  "_id": ObjectId("564f45dbd9992fae819fb00a"),
  "nome": "Kyurem",
  "description": "Pokemon transforma em qualquer um",
  "type": "Dragon/Ice",
  "attack": 67,
  "height": 3
}
{
  "_id": ObjectId("564f45dbd9992fae819fb00b"),
  "nome": "Djalga",
  "description": "Volta no tempo",
  "type": "Dragon",
  "attack": 80,
  "height": 5.4
}
Fetched 5 record(s) in 57ms

var query ={"nome": "Lugia"}

MarceloLocal(mongod-2.4.9) be-mean-pokemons> query
{
  "nome": "Lugia"
}
MarceloLocal(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564f45dbd9992fae819fb009"),
  "nome": "Lugia",
  "description": "Provoca furaca catrina por 40 dias",
  "type": "Psychic/Flying",
  "attack": 60,
  "height": 5.2
}
Fetched 1 record(s) in 377ms


/*-----------------------*/

MarceloLocal(mongod-2.4.9) be-mean-pokemons> var poke = db.pokemons.findOne(query)
MarceloLocal(mongod-2.4.9) be-mean-pokemons> poke
{
  "_id": ObjectId("564f45dbd9992fae819fb009"),
  "nome": "Lugia",
  "description": "Provoca furaca catrina por 40 dias",
  "type": "Psychic/Flying",
  "attack": 60,
  "height": 5.2
}

MarceloLocal(mongod-2.4.9) be-mean-pokemons> poke.description
Provoca furaca catrina por 40 dias
MarceloLocal(mongod-2.4.9) be-mean-pokemons> poke.description = "Faz temptestades"
Faz temptestades
MarceloLocal(mongod-2.4.9) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 269ms
MarceloLocal(mongod-2.4.9) be-mean-pokemons> db.pokemons.findOne(query)
{
  "_id": ObjectId("564f45dbd9992fae819fb009"),
  "nome": "Lugia",
  "description": "Faz temptestades",
  "type": "Psychic/Flying",
  "attack": 60,
  "height": 5.2
}