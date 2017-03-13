###MongoDB - Aula 02 - Exercício
Autor: Marlom Girardi

##Criando database
```
mariela@cem-008046106:~ $ mongo be-mean-pokemons;
MongoDB shell version v3.4.2
connecting to: mongodb://127.0.0.1:27017/be-mean-pokemons
MongoDB server version: 3.4.2
Mongo-Hacker 0.0.14
Server has startup warnings: 
2017-03-13T09:05:12.294-0300 I CONTROL  [initandlisten] 
2017-03-13T09:05:12.294-0300 I CONTROL  [initandlisten] ** WARNING: Access control is not enabled for the database.
2017-03-13T09:05:12.294-0300 I CONTROL  [initandlisten] **          Read and write access to data and configuration is unrestricted.
2017-03-13T09:05:12.294-0300 I CONTROL  [initandlisten] 
2017-03-13T09:05:12.294-0300 I CNOTROL  [initandlisten] 
2017-03-13T09:05:12.294-0300 I CONTROL  [initandlisten] ** WARNING: /sys/kernel/mm/transparent_hugepage/enabled is 'always'.
2017-03-13T09:05:12.294-0300 I CONTROL  [initandlisten] **        We suggest setting it to 'never'
2017-03-13T09:05:12.294-0300 I CONTROL  [initandlisten] 
2017-03-13T09:05:12.294-0300 I CONTROL  [initandlisten] ** WARNING: /sys/kernel/mm/transparent_hugepage/defrag is 'always'.
2017-03-13T09:05:12.294-0300 I CONTROL  [initandlisten] **        We suggest setting it to 'never'
2017-03-13T09:05:12.294-0300 I CONTROL  [initandlisten] 

```

##Listando databases
```
cem-008046106(mongod-3.4.2) be-mean-pokemons> show dbs
be-mean           → 0.078GB
be-mean-instagram → 0.078GB
local             → 0.078GB
test              → 0.078GB

```

##Listando collections
```
cem-008046106(mongod-3.4.2) be-mean-pokemons> show collections;

```

##Cadastro de pokemons
```
var pokemons = [{'name':'Pikachu','description':'It raises its tail to check its sur roundings. The tail is sometimes struck by light ning in this pose.',attack: 55, defense: 40, height: 0.4},{'name':'Sandshrew','description':'To protect itself from attackers, it curls up into a ball. It lives in arid regions with minimal rainfall.',attack: 75, defense: 85, height: 0.6},{'name':'Nidoran','description':'Although small, its venomous barbs render this POKMON dangerous. The female has smaller horns.',attack: 47, defense: 52, height: 0.4},{'name':'Clefairy','description':'Adored for their cute looks and playfulness. They are thought to be rare, as they do not appear often.',attack: 45, defense: 48, height: 0.6},{'name':'Vulpix','description':'If it is attacked by an enemy that is stronger than itself, it feigns injury to fool the enemy and escapes.',attack: 41, defense: 40, height: 0.6}]

cem-008046106(mongod-3.4.2) be-mean-pokemons> db.pokemons.insert(pokemons)
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

cem-008046106(mongod-3.4.2) be-mean-pokemons> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 220ms
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
cem-008046106(mongod-3.4.2) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("58c696f36403e83b151828a3"),
  "name": "Pikachu",
  "description": "It raises its tail to check its sur roundings. The tail is sometimes struck by light ning in this pose.",
  "attack": 55,
  "defense": 40,
  "height": 0.4
}
{
  "_id": ObjectId("58c696f36403e83b151828a4"),
  "name": "Sandshrew",
  "description": "To protect itself from attackers, it curls up into a ball. It lives in arid regions with minimal rainfall.",
  "attack": 75,
  "defense": 85,
  "height": 0.6
}
{
  "_id": ObjectId("58c696f36403e83b151828a5"),
  "name": "Nidoran",
  "description": "Although small, its venomous barbs render this POKMON dangerous. The female has smaller horns.",
  "attack": 47,
  "defense": 52,
  "height": 0.4
}
{
  "_id": ObjectId("58c696f36403e83b151828a6"),
  "name": "Clefairy",
  "description": "Adored for their cute looks and playfulness. They are thought to be rare, as they do not appear often.",
  "attack": 45,
  "defense": 48,
  "height": 0.6
}
{
  "_id": ObjectId("58c696f36403e83b151828a7"),
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
cem-008046106(mongod-3.4.2) be-mean-pokemons> var query = {name:'Nidoran'}
cem-008046106(mongod-3.4.2) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("58c696f36403e83b151828a5"),
  "name": "Nidoran",
  "description": "Although small, its venomous barbs render this POKMON dangerous. The female has smaller horns.",
  "attack": 47,
  "defense": 52,
  "height": 0.4
}
cem-008046106(mongod-3.4.2) be-mean-pokemons> var poke = db.pokemons.find(query)
cem-008046106(mongod-3.4.2) be-mean-pokemons> poke
{
  "_id": ObjectId("58c696f36403e83b151828a5"),
  "name": "Nidoran",
  "description": "Although small, its venomous barbs render this POKMON dangerous. The female has smaller horns.",
  "attack": 47,
  "defense": 52,
  "height": 0.4
}

```
##Atualização do Pokemon
```
cem-008046106(mongod-3.4.2) be-mean-pokemons> var query = {name : 'Clefairy'}
cem-008046106(mongod-3.4.2) be-mean-pokemons> var poke = db.pokemons.findOne(query)
cem-008046106(mongod-3.4.2) be-mean-pokemons> poke
{
  "_id": ObjectId("58c696f36403e83b151828a6"),
  "name": "Clefairy",
  "description": "Adored for their cute looks and playfulness. They are thought to be rare, as they do not appear often.",
  "attack": 45,
  "defense": 48,
  "height": 0.6
}
cem-008046106(mongod-3.4.2) be-mean-pokemons> poke.description = 'Pokemon pequeno perigoso'
Pokemon pequeno perigoso
cem-008046106(mongod-3.4.2) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

```
## Mostrar dado atualizado
```
cem-008046106(mongod-3.4.2) be-mean-pokemons> var query = {name : 'Clefairy'}
cem-008046106(mongod-3.4.2) be-mean-pokemons> var poke = db.pokemons.findOne(query)
cem-008046106(mongod-3.4.2) be-mean-pokemons> poke
{
  "_id": ObjectId("58c696f36403e83b151828a6"),
  "name": "Clefairy",
  "description": "Pokemon pequeno perigoso",
  "attack": 45,
  "defense": 48,
  "height": 0.6
}
```
