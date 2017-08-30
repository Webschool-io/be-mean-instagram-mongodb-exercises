# MongoDB - Aula 02 - Exercício
Autor: Rafael Barros

## Criando uma database chamada be-mean-pokemons

```
use be-mean-pokemons
switched to db be-mean-pokemons
```

## Listando todas databases

```
DEV(mongod-3.4.6) be-mean-pokemons> show dbs
admin            → 0.000GB
be-mean          → 0.005GB
be-mean-pokemons → 0.000GB
local            → 0.000GB
```
## Listando coleções existentes em be-mean-pokemons

```
DEV(mongod-3.4.6) be-mean-pokemons> show collections
local_teste → 0.000MB / 0.016MB
```

## Inserindo 5 pokemons

```
var pokemons = [
	{'name':'Pikachu','description':'Rato elétrico bem fofinho','type':'eletric',attack: 55, height: 0.4},
	{'name':'Bulbassauro','description':'Chicote de trepadeira','type': 'grama', 'attack': 49, height: 0.4 },
	{'name':'Charmander','description':'Esse é o cão chupando manga de fofinho','type': 'fogo', 'attack': 52, height: 0.6 },
	{'name':'Squirtle','description': 'Ejeta água que passarinho não bebe','type': 'água', 'attack': 48, height: 0.5 },
	{'name':'Caterpie','description':'Inseto bem fofinho','type':'Bug',attack: 30, height: 0.3}
]

DEV(mongod-3.4.6) be-mean-pokemons> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 14ms
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
## Listar pokemons existentes

```
DEV(mongod-3.4.6) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("5977f7b9a11aa5d85502aa74"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("5977f7b9a11aa5d85502aa75"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("5977f7b9a11aa5d85502aa76"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("5977f7b9a11aa5d85502aa77"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("5977f7b9a11aa5d85502aa78"),
  "name": "Caterpie",
  "description": "Inseto bem fofinho",
  "type": "Bug",
  "attack": 30,
  "height": 0.3
}
Fetched 5 record(s) in 14ms
```

## Buscando Squirtle

```
DEV(mongod-3.4.6) be-mean-pokemons> var query = {name: 'Squirtle'}
DEV(mongod-3.4.6) be-mean-pokemons> var poke = db.pokemons.find(query)
DEV(mongod-3.4.6) be-mean-pokemons> poke
{
  "_id": ObjectId("5977f7b9a11aa5d85502aa77"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 1 record(s) in 4ms
```
## Modificando a description e salvando

```
DEV(mongod-3.4.6) be-mean-pokemons> var query = {name: 'Squirtle'}
DEV(mongod-3.4.6) be-mean-pokemons> var poke = db.pokemons.findOne(query)
DEV(mongod-3.4.6) be-mean-pokemons> poke.description = "Ejeta água mais que uma Baleia"
Ejeta água mais que uma Baleia

DEV(mongod-3.4.6) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

DEV(mongod-3.4.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5977f7b9a11aa5d85502aa77"),
  "name": "Squirtle",
  "description": "Ejeta água mais que uma Baleia",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 1 record(s) in 4ms
```
