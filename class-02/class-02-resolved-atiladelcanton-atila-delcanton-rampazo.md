###MongoDB - Aula 02 - Exercício
Autor: Átila Delcanton Rampazo

##Criando database
```
arampazo@arampazo:~$ mongo be-mean-pokemons
MongoDB shell version: 3.0.8
connecting to: be-mean-pokemons
Mongo-Hacker 0.0.9
Server has startup warnings: 
2015-12-27T22:42:42.459-0200 I CONTROL  [initandlisten] 
2015-12-27T22:42:42.459-0200 I CONTROL  [initandlisten] ** WARNING: /sys/kernel/mm/transparent_hugepage/enabled is 'always'.
2015-12-27T22:42:42.459-0200 I CONTROL  [initandlisten] **        We suggest setting it to 'never'
2015-12-27T22:42:42.459-0200 I CONTROL  [initandlisten] 
2015-12-27T22:42:42.459-0200 I CONTROL  [initandlisten] ** WARNING: /sys/kernel/mm/transparent_hugepage/defrag is 'always'.
2015-12-27T22:42:42.459-0200 I CONTROL  [initandlisten] **        We suggest setting it to 'never'
2015-12-27T22:42:42.459-0200 I CONTROL  [initandlisten] 
```

##Listando databases
```
arampazo(mongod-3.0.8) be-mean-pokemons> show dbs
local             → 0.078GB
be-mean           → 0.078GB
be-mean-instagram → 0.078GB

```

##Listando collections
```
arampazo(mongod-3.0.8) be-mean-pokemons> show collections

```

##Cadastro dos pokemons
```
 var arrPokemons = [{'name':'Skitty','description':'It shows its cute side by chasing its own tail until it gets dizzy.','type':'normal', attack: 45, defense: 45, height: 6},{'name':'Fearow','description':'It has the stamina to fly all day on its broad wings. It fights by using its sharp beak.','type':'flying', attack: 90, defense: 65, height: 12},{'name':'Vivillon','description':'Vivillon with many different patterns are found all over the world. These patterns are affected by the climate of their habitat.','type':'flying', attack: 52, defense: 50, height: 0},{'name':'Ponyta','description':'It is a weak run ner immediately after birth. It gradually becomes faster by chasing after its parents.','type':'flying', fire: 85, defense: 55, height: 0},{'name':'Farfetchd','description':'It always walks about with a plant stalk clamped in its beak. The stalk is used for building its nest.','type':'flying', attack: 52, defense: 55, height: 8}]

arampazo(mongod-3.0.8) be-mean-pokemons> db.pokemons.save(arrPokemons)
Inserted 1 record(s) in 476ms
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

##Lista de todos os pokemons
```
arampazo(mongod-3.0.8) be-mean-pokemons> db.pokemons.find({}).pretty()
{
  "_id": ObjectId("568090abbb9cf17a6a566f90"),
  "name": "Skitty",
  "description": "It shows its cute side by chasing its own tail until it gets dizzy.",
  "type": "normal",
  "attack": 45,
  "defense": 45,
  "height": 6
}
{
  "_id": ObjectId("568090abbb9cf17a6a566f91"),
  "name": "Fearow",
  "description": "It has the stamina to fly all day on its broad wings. It fights by using its sharp beak.",
  "type": "flying",
  "attack": 90,
  "defense": 65,
  "height": 12
}
{
  "_id": ObjectId("568090abbb9cf17a6a566f92"),
  "name": "Vivillon",
  "description": "Vivillon with many different patterns are found all over the world. These patterns are affected by the climate of their habitat.",
  "type": "flying",
  "attack": 52,
  "defense": 50,
  "height": 0
}
{
  "_id": ObjectId("568090abbb9cf17a6a566f93"),
  "name": "Ponyta",
  "description": "It is a weak run ner immediately after birth. It gradually becomes faster by chasing after its parents.",
  "type": "flying",
  "fire": 85,
  "defense": 55,
  "height": 0
}
{
  "_id": ObjectId("568090abbb9cf17a6a566f94"),
  "name": "Farfetchd",
  "description": "It always walks about with a plant stalk clamped in its beak. The stalk is used for building its nest.",
  "type": "flying",
  "attack": 52,
  "defense": 55,
  "height": 8
}
Fetched 5 record(s) in 20ms


```
##Query para buscar o pokemon
```
arampazo(mongod-3.0.8) be-mean-pokemons> var query = {name:'Ponyta'}
arampazo(mongod-3.0.8) be-mean-pokemons> var poke = db.pokemons.findOne(query)

```

##Atualizando a descrição do Pokemon
```
arampazo(mongod-3.0.8) be-mean-pokemons> poke.description = "Ponyta eu escolho você"
Ponyta eu escolho você

arampazo(mongod-3.0.8) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 4ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

```
