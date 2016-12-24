#MongoDB - Aula 02 - Exercício
Autor: Wellington Pinho

#Criando a database
```
well@well:~$ mongo be-mean-pokemons
MongoDB shell version: 3.2.10
connecting to: be-mean-pokemons
Mongo-Hacker 0.0.14
well(mongod-3.2.10) be-mean-pokemons>

```

#Listando databases
```
well(mongod-3.2.10) be-mean-pokemons> show dbs
local    → 0.078GB
pokemons → 0.078GB

```

#Listando collections
```
well(mongod-3.2.10) be-mean-pokemons> show collections
well(mongod-3.2.10) be-mean-pokemons> 

```

#Cadastro de pokemons
```
var pokemon = [{
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
}]

well(mongod-3.2.10) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 543ms
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

##Lista dos pokemons
```
well(mongod-3.2.10) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("57f4e7215d66da390f1f293e"),
  "name": "Terrakion",
  "Description": "Sua carga é forte o suficiente para quebrar através de uma parede de castelo gigante em um golpe.",
  "type": "Fire",
  "attack": 7,
  "Defense": 4,
  "Speed": 6,
  "height": 0.4
}
{
  "_id": ObjectId("57f4e7215d66da390f1f293f"),
  "name": "Infernape",
  "Description": "A sua coroa de fogo é indicativo de sua natureza ardente. Ele é batido por ninguém em termos de rapidez.",
  "type": "Rock",
  "attack": 5,
  "Defense": 3,
  "Speed": 6,
  "height": 0.4
}
{
  "_id": ObjectId("57f4e7215d66da390f1f2940"),
  "name": "Squirtle",
  "Description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 6,
  "Defense": 5,
  "Speed": 5,
  "height": 0.5
}
{
  "_id": ObjectId("57f4e7215d66da390f1f2941"),
  "name": "Metapod",
  "Description": "O escudo que cobre o corpo deste Pokémon é tão duro como uma laje de ferro.",
  "type": "Bug",
  "attack": 1,
  "Defense": 3,
  "Speed": 2,
  "height": 0.3
}
{
  "_id": ObjectId("57f4edab5d66da390f1f294c"),
  "name": "Arbok",
  "Description": "Este Pokémon é terrivelmente forte, a fim de se contraem as coisas com o seu corpo. Ele pode até mesmo achatar tambores de óleo de aço. ",
  "type": "Poison",
  "attack": 4,
  "Defense": 3,
  "Speed": 4,
  "height": 0.5
}

Fetched 5 record(s) in 8ms

```

##Pokemon
```
var buscar = {'name':'Squirtle'}
var poke = db.pokemons.find(buscar)
well(mongod-3.2.10) be-mean-pokemons> poke
{
  "_id": ObjectId("57f4edab5d66da390f1f294c"),
  "name": "Arbok",
  "Description": "Este Pokémon é terrivelmente forte, a fim de se contraem as coisas com o seu corpo. Ele pode até mesmo achatar tambores de óleo de aço. ",
  "type": "Poison",
  "attack": 4,
  "Defense": 3,
  "Speed": 4,
  "height": 0.5
}

Fetched 1 record(s) in 3ms

```

##Atualização do Pokemon
```
well(mongod-3.2.10) be-mean-pokemons> var poke = db.pokemons.findOne(buscar)
well(mongod-3.2.10) be-mean-pokemons> poke.Descripton = 'MUDEI AQUI MEU FIO! HAHAHEUEUAHAHA...'
MUDEI AQUI MEU FIO! HAHAHEUEUAHAHA...
well(mongod-3.2.10) be-mean-pokemons> 
well(mongod-3.2.10) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 3ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

VIZUALIZANDO A MUDANÇA NA DESCRIPTON DO POKEMONZITO
well(mongod-3.2.10) be-mean-pokemons> monzinho
{
  "_id": ObjectId("57f4edab5d66da390f1f294c"),
  "name": "Arbok",
  "Description": "Mudei aqui meu fio",
  "type": "Poison",
  "attack": 4,
  "Defense": 3,
  "Speed": 4,
  "height": 0.5
}

```





