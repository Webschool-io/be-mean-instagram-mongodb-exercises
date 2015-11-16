# MongoDB - Aula 02 - Exercício
autor: Leandro Ferreira


### Etapa 1


```
leandro-IE-G31TM7(mongod-3.0.7) test> use be-mean-pokemons
switched to db be-mean-pokemons
```

### Etapa 2

```
leandro-IE-G31TM7(mongod-3.0.7) be-mean-pokemons> show dbs
be-mean-instagram  0.078GB
local              0.078GB
be-mean            0.078GB
```


### Etapa 3

```
leandro-IE-G31TM7(mongod-3.0.7) be-mean-pokemons> show collections
```

### Etapa 4

```
var arrayPokenons = [{'name':'Butterfree', 'description':'Borboleta Feia','type':'inseto','attack':2,'height':1.1 }
,{'name':'Wartortle',  'description':'Tartaruga ninja','type':'Água','attack':50,'height':1.0 }
,{'name':'Venusaur', 'description':'Cultivador de ervas','type':'grama','attack':60,'height':0.5 }
,{'name':'Metapod', 'description':'Peso de papel','type':'inseto','attack':2,'height':0.7 }
,{'name':'Rattata', 'description':'Rato demoníaco','type':'normal','attack':9,'height':0.3 }]

leandro-IE-G31TM7(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(arrayPokenons)
Inserted 1 record(s) in 325ms
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

### Etapa 5

```
leandro-IE-G31TM7(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("56455653c0d5a7a0b114d565"),
  "name": "Butterfree",
  "description": "Borboleta Feia",
  "type": "inseto",
  "attack": 2,
  "height": 1.1
}
{
  "_id": ObjectId("56455653c0d5a7a0b114d566"),
  "name": "Wartortle",
  "description": "Tartaruga ninja",
  "type": "Água",
  "attack": 50,
  "height": 1
}
{
  "_id": ObjectId("56455653c0d5a7a0b114d567"),
  "name": "Venusaur",
  "description": "Cultivador de ervas",
  "type": "grama",
  "attack": 60,
  "height": 0.5
}
{
  "_id": ObjectId("56455653c0d5a7a0b114d568"),
  "name": "Metapod",
  "description": "Peso de papel",
  "type": "inseto",
  "attack": 2,
  "height": 0.7
}
{
  "_id": ObjectId("56455653c0d5a7a0b114d569"),
  "name": "Rattata",
  "description": "Rato demoníaco",
  "type": "normal",
  "attack": 9,
  "height": 0.3
}
Fetched 5 record(s) in 3ms
```

### Etapa 6


```

leandro-IE-G31TM7(mongod-3.0.7) be-mean-pokemons> var query = {name : 'Rattata'}
leandro-IE-G31TM7(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(query)
leandro-IE-G31TM7(mongod-3.0.7) be-mean-pokemons> poke.type = 'demoníaco'
leandro-IE-G31TM7(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 7ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```
