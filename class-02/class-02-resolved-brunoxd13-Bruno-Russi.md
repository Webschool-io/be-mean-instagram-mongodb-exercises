
# MongoDB - Aula 02 - Exercício
autor: Bruno Russi Lautenschlager

## Listagem das databases

```
> use be-mean-pokemons
switched to db be-mean-pokemons

> show dbs
> show dbs
Teste               0.078GB
be-mean-pokemons    0.078GB
busApp              0.078GB
local               0.078GB
screencast_restful  0.078GB
```

## Listagem das coleções

```
> show collections
system.indexes
teste
```

## Cadastro dos pokemons

```
var pokemons = [
  {
     name: 'Bobmom',
     description: 'Pokemon bob marley',
     type: 'chapado',
     attack: 420,
     defense: 420,
     height: 4.20
   },
   {
     name: 'LockMom',
     description: 'Pokemon lock',
     type: 'loko',
     attack: 100,
     defense: 10,
     height: 1.3
   },
   {
     name: 'SanoMom',
     description: 'pokemon sandia saia',
     type: 'San',
     attack: 860,
     defense: 978,
     height: 1.90
   },
   {
     name: 'OxiMom',
     description: 'Pokemom paraiba',
     type: 'paraiba',
     attack: 897,
     defense: 784,
     height: 1.60
   },
   {
     name: 'chikungunya',
     description: 'Passa peste pra geral',
     type: 'peste',
     attack: 666,
     defense: 666,
     height: 1.87
   }
 ]

 > db.pokemons.insert(pokemons)
 BulkWriteResult({
 	"writeErrors" : [ ],
 	"writeConcernErrors" : [ ],
 	"nInserted" : 5,
 	"nUpserted" : 0,
 	"nMatched" : 0,
 	"nModified" : 0,
 	"nRemoved" : 0,
 	"upserted" : [ ]
 })
```

## Lista dos pokemons

```
> db.pokemons.find()
{ "_id" : ObjectId("56dc9a7a20c79beeb285f0ec"), "name" : "Bobmom", "description" : "Pokemon bob marley", "type" : "chapado", "attack" : 420, "defense" : 420, "height" : 4.2 }
{ "_id" : ObjectId("56dc9a7a20c79beeb285f0ed"), "name" : "LockMom", "description" : "Pokemon lock", "type" : "loko", "attack" : 100, "defense" : 10, "height" : 1.3 }
{ "_id" : ObjectId("56dc9a7a20c79beeb285f0ee"), "name" : "SanoMom", "description" : "pokemon sandia saia", "type" : "San", "attack" : 860, "defense" : 978, "height" : 1.9 }
{ "_id" : ObjectId("56dc9a7a20c79beeb285f0ef"), "name" : "OxiMom", "description" : "Pokemom paraiba", "type" : "paraiba", "attack" : 897, "defense" : 784, "height" : 1.6 }
{ "_id" : ObjectId("56dc9a7a20c79beeb285f0f0"), "name" : "chikungunya", "description" : "Passa peste pra geral", "type" : "peste", "attack" : 666, "defense" : 666, "height" : 1.87 }

```

## Pokemon

```
> var query = {"name": "SanoMom"}
> var poke = db.pokemons.findOne(query)
> poke
{
	"_id" : ObjectId("56dc9a7a20c79beeb285f0ee"),
	"name" : "SanoMom",
	"description" : "pokemon sandia saia",
	"type" : "San",
	"attack" : 860,
	"defense" : 978,
	"height" : 1.9
}
```

## Atualização do Pokemon

```
> var query = {"name": "SanoMom"}
> var poke = db.pokemons.findOne(query)
> poke
{
	"_id" : ObjectId("56dc9a7a20c79beeb285f0ee"),
	"name" : "SanoMom",
	"description" : "pokemon sandia saia",
	"type" : "San",
	"attack" : 860,
	"defense" : 978,
	"height" : 1.9
}
> poke.attack = 666
666

> db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
```
