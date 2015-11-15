# MongoDB - Aula 02 - Exercício
autor: Jéssica Cristina Carneiro

### Criando database be-mean-pokemons
```
> use be-mean-pokemons
switched to db be-mean-pokemons
```

### Listando dos databases
```
> show dbs
be-mean-instagram  0.078GB
be-mean            0.078GB
local              0.078GB
pokemons           0.078GB
test               0.078GB
```

### Listando as coleções
```
> show collections
> db.getCollectionNames()
[ ]
```

### Inserindo os pokemons
```
> var pokemons = [
 {
    "name": "Weedle",
    "description": "Larva esquisita com ferrões",
    "attack": 35,
    "height": 3
  },
  {
    "name": "Vulpix",
    "description": "Raposa fofinha de rabo peludo",
    "attack": 41,
    "height": 6
  },
  {
    "name": "Parasect",
    "description": "Caranguejo misteriosamente forte",
    "attack": 95,
    "height": 10
  },
  {
    "name": "Primeape",
    "description": "Bola peluda lutadora",
    "attack": 105,
    "height": 10
  },
  {
    "name": "Butterfree",
    "description": "Borboletinha perigosa",
    "attack": 45,
    "height": 11
  }
]
> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 3ms
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

### Listando os pokemons
```
> db.pokemons.find()
{
  "_id": ObjectId("5648bbd2b1734be0946e5284"),
  "name": "Weedle",
  "description": "Larva esquisita com ferrões",
  "attack": 35,
  "height": 3
}
{
  "_id": ObjectId("5648bbd2b1734be0946e5285"),
  "name": "Vulpix",
  "description": "Raposa fofinha de rabo peludo",
  "attack": 41,
  "height": 6
}
{
  "_id": ObjectId("5648bbd2b1734be0946e5286"),
  "name": "Parasect",
  "description": "Caranguejo misteriosamente forte",
  "attack": 95,
  "height": 10
}
{
  "_id": ObjectId("5648bbd2b1734be0946e5287"),
  "name": "Primeape",
  "description": "Bola peluda lutadora",
  "attack": 105,
  "height": 10
}
{
  "_id": ObjectId("5648bbd2b1734be0946e5288"),
  "name": "Butterfree",
  "description": "Borboletinha perigosa",
  "attack": 45,
  "height": 11
}
Fetched 5 record(s) in 2ms
```

### Alterando a descrição de um pokemon
```
> var poke = db.pokemons.findOne({'name': 'Parasect'})
> poke.description = "Caranguejo cheio de pintinhas"
Caranguejo cheio de pintinhas
> db.pokemons.save(poke)
Updated 1 existing record(s) in 8ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```