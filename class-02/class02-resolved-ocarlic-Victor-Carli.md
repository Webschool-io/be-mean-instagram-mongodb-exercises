###MongoDB - Aula 02 - Exercício

Autor: Victor Carli

##Criando database

```
d0x@carli:~$ mongo be-mean-pokemons
MongoDB shell version: 2.6.10
connecting to: be-mean-pokemons

```

##Listando databases

```
admin             (empty)
be-mean           0.078GB
be-mean-pokemons  (empty)
local             0.078GB
pokemons          (empty)
test              0.078GB

```

##Listando collections

```
d0x-PC(mongod-2.6.10) be-mean-pokemons> show collections
d0x-PC(mongod-2.6.10) be-mean-pokemons> 

```

##Cadastro de pokemons

```
d0x-PC(mongod-2.6.10) be-mean-pokemons> var pokemon = {'name': 'Zubat','description':'morcego roxo sem olho','type':'Poison', attack: 20, defense: 30, height: 0.8}
d0x-PC(mongod-2.6.10) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 817ms
WriteResult({
  "nInserted": 1
})
d0x-PC(mongod-2.6.10) be-mean-pokemons> var pokemon = {'name': 'Blastoise','description':'Tartaruga tipo bombeira','type':'Água', attack: 40, defense: 35, height: 1.6}
d0x-PC(mongod-2.6.10) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})
d0x-PC(mongod-2.6.10) be-mean-pokemons> var pokemon = {'name': 'Raticate','description':'Rato de esgoto','type':'Normal', attack: 40, defense: 40, height: 0.7}
d0x-PC(mongod-2.6.10) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 1116ms
WriteResult({
  "nInserted": 1
})
d0x-PC(mongod-2.6.10) be-mean-pokemons> var pokemon = {'name': 'Kadabra','description':'Raposa grande de colher','type':'Psychic', attack: 60, defense: 50, height: 1.3}
d0x-PC(mongod-2.6.10) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 4ms
WriteResult({
  "nInserted": 1
})
d0x-PC(mongod-2.6.10) be-mean-pokemons> var pokemon = {'name': 'Raichu','description':'Evolução do Pikachu','type':'eletric', attack: 50, defense: 45, height: 0.8}
d0x-PC(mongod-2.6.10) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})

```

##Lista dos pokemons

```
d0x-PC(mongod-2.6.10) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("58a1073b22450349d35f9e53"),
  "name": "Zubat",
  "description": "morcego roxo sem olho",
  "type": "Poison",
  "attack": 20,
  "defense": 30,
  "height": 0.8
}
{
  "_id": ObjectId("58a1075122450349d35f9e54"),
  "name": "Blastoise",
  "description": "Tartaruga tipo bombeira",
  "type": "Água",
  "attack": 40,
  "defense": 35,
  "height": 1.6
}
{
  "_id": ObjectId("58a1075d22450349d35f9e55"),
  "name": "Raticate",
  "description": "Rato de esgoto",
  "type": "Normal",
  "attack": 40,
  "defense": 40,
  "height": 0.7
}
{
  "_id": ObjectId("58a1076a22450349d35f9e56"),
  "name": "Kadabra",
  "description": "Raposa grande de colher",
  "type": "Psychic",
  "attack": 60,
  "defense": 50,
  "height": 1.3
}
{
  "_id": ObjectId("58a1077522450349d35f9e57"),
  "name": "Raichu",
  "description": "Evolução do Pikachu",
  "type": "eletric",
  "attack": 50,
  "defense": 45,
  "height": 0.8
}
Fetched 5 record(s) in 7ms
d0x-PC(mongod-2.6.10) be-mean-pokemons> 

```
##Pokemon

```
d0x-PC(mongod-2.6.10) be-mean-pokemons> var query = {'name':'Zubat'}
d0x-PC(mongod-2.6.10) be-mean-pokemons> var poke = db.pokemons.findOne(query)
d0x-PC(mongod-2.6.10) be-mean-pokemons> poke
{
  "_id": ObjectId("58a1073b22450349d35f9e53"),
  "name": "Zubat",
  "description": "morcego roxo sem olho",
  "type": "Poison",
  "attack": 20,
  "defense": 30,
  "height": 0.8
}

```
##Atualização do Pokemon

```
d0x-PC(mongod-2.6.10) be-mean-pokemons> poke.description
morcego roxo sem olho
d0x-PC(mongod-2.6.10) be-mean-pokemons> poke.description = 'morcego sem olho da cor roxa'
morcego sem olho da cor roxa
d0x-PC(mongod-2.6.10) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 16ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

d0x-PC(mongod-2.6.10) be-mean-pokemons> poke
{
  "_id": ObjectId("58a1073b22450349d35f9e53"),
  "name": "Zubat",
  "description": "morcego sem olho da cor roxa",
  "type": "Poison",
  "attack": 20,
  "defense": 30,
  "height": 0.8
}

```
