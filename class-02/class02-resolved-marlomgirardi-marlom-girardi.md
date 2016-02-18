###MongoDB - Aula 02 - Exercício
Autor: Marlom Girardi

##Criando database
```
marlom@dell-marlom:~$ mongo be-mean-pokemons
MongoDB shell version: 3.0.9
connecting to: be-mean-pokemons
Mongo-Hacker 0.0.12
Server has startup warnings: 
2016-02-14T13:46:18.743-0200 I CONTROL  [initandlisten] 
2016-02-14T13:46:18.743-0200 I CONTROL  [initandlisten] ** WARNING: /sys/kernel/mm/transparent_hugepage/enabled is 'always'.
2016-02-14T13:46:18.743-0200 I CONTROL  [initandlisten] **        We suggest setting it to 'never'
2016-02-14T13:46:18.743-0200 I CONTROL  [initandlisten] 
2016-02-14T13:46:18.743-0200 I CONTROL  [initandlisten] ** WARNING: /sys/kernel/mm/transparent_hugepage/defrag is 'always'.
2016-02-14T13:46:18.743-0200 I CONTROL  [initandlisten] **        We suggest setting it to 'never'
2016-02-14T13:46:18.743-0200 I CONTROL  [initandlisten] 
```

##Listando databases
```
dell-marlom(mongod-3.0.9) be-mean-pokemons> show dbs
be-mean           → 0.078GB
be-mean-instagram → 0.078GB
local             → 0.078GB
```

##Listando collections
```
dell-marlom(mongod-3.0.9) be-mean-pokemons> show collections

```

##Cadastro de pokemons
```
dell-marlom(mongod-3.0.9) be-mean-pokemons> var pokemons = [{'name':'Pikachu','description':'It raises its tail to check its sur roundings. The tail is sometimes struck by light ning in this pose.',attack: 55, defense: 40, height: 0.4},{'name':'Sandshrew','description':'To protect itself from attackers, it curls up into a ball. It lives in arid regions with minimal rainfall.',attack: 75, defense: 85, height: 0.6},{'name':'Nidoran','description':'Although small, its venomous barbs render this POKMON dangerous. The female has smaller horns.',attack: 47, defense: 52, height: 0.4},{'name':'Clefairy','description':'Adored for their cute looks and playfulness. They are thought to be rare, as they do not appear often.',attack: 45, defense: 48, height: 0.6},{'name':'Vulpix','description':'If it is attacked by an enemy that is stronger than itself, it feigns injury to fool the enemy and escapes.',attack: 41, defense: 40, height: 0.6}]

dell-marlom(mongod-3.0.9) be-mean-pokemons> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 76ms
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
dell-marlom(mongod-3.0.9) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("56c0bad68f26b51a97f400eb"),
  "name": "Pikachu",
  "description": "It raises its tail to check its sur roundings. The tail is sometimes struck by light ning in this pose.",
  "attack": 55,
  "defense": 40,
  "height": 0.4
}
{
  "_id": ObjectId("56c0bad68f26b51a97f400ec"),
  "name": "Sandshrew",
  "description": "To protect itself from attackers, it curls up into a ball. It lives in arid regions with minimal rainfall.",
  "attack": 75,
  "defense": 85,
  "height": 0.6
}
{
  "_id": ObjectId("56c0bad68f26b51a97f400ed"),
  "name": "Nidoran",
  "description": "Although small, its venomous barbs render this POKMON dangerous. The female has smaller horns.",
  "attack": 47,
  "defense": 52,
  "height": 0.4
}
{
  "_id": ObjectId("56c0bad68f26b51a97f400ee"),
  "name": "Clefairy",
  "description": "Adored for their cute looks and playfulness. They are thought to be rare, as they do not appear often.",
  "attack": 45,
  "defense": 48,
  "height": 0.6
}
{
  "_id": ObjectId("56c0bad68f26b51a97f400ef"),
  "name": "Vulpix",
  "description": "If it is attacked by an enemy that is stronger than itself, it feigns injury to fool the enemy and escapes.",
  "attack": 41,
  "defense": 40,
  "height": 0.6
}
Fetched 5 record(s) in 2ms
```

##Pokemon
```
var query = {name:'Nidoran'}
> var poke = db.pokemons.find(query)
> poke
{ "_id" : ObjectId("564921350910df3d8696d70d"), "name" : "Rapidash", "description" : "Ta pegando fogo bixo!", "type" : "fire", "attack" : 80, "defense" : 30, "height" : 1.7 }
```

##Atualização do Pokemon
```
dell-marlom(mongod-3.0.9) be-mean-pokemons> var query = {name:'Rapidash'}
dell-marlom(mongod-3.0.9) be-mean-pokemons> var poke = db.pokemons.findOne(query)
dell-marlom(mongod-3.0.9) be-mean-pokemons> poke.description = 'Hakuna matata'
Hakuna matata
dell-marlom(mongod-3.0.9) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```
