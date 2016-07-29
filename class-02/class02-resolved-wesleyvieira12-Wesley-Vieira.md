###MongoDB - Aula 02 - Exercício
Autor: Wesley Vieira

##Criando database
```
wesley@wesley:~/mongo-hacker$ mongo be-mean-pokemons
MongoDB shell version: 3.2.8
connecting to: be-mean-pokemons
Mongo-Hacker 0.0.13
Server has startup warnings: 
2016-07-13T20:34:38.530-0300 I CONTROL  [initandlisten] 
2016-07-13T20:34:38.530-0300 I CONTROL  [initandlisten] ** WARNING: /sys/kernel/mm/transparent_hugepage/enabled is 'always'.
2016-07-13T20:34:38.530-0300 I CONTROL  [initandlisten] **        We suggest setting it to 'never'
2016-07-13T20:34:38.530-0300 I CONTROL  [initandlisten] 
2016-07-13T20:34:38.530-0300 I CONTROL  [initandlisten] ** WARNING: /sys/kernel/mm/transparent_hugepage/defrag is 'always'.
2016-07-13T20:34:38.531-0300 I CONTROL  [initandlisten] **        We suggest setting it to 'never'
2016-07-13T20:34:38.531-0300 I CONTROL  [initandlisten] 
```

##Listando databases
```
wesley(mongod-3.2.8) be-mean-pokemons> show dbs
be-mean → 0.005GB
local   → 0.000GB
test    → 0.000GB
```

##Listando collections
```
wesley(mongod-3.2.8) be-mean-pokemons> show collections

```

##Cadastro de pokemons
```
wesley(mongod-3.2.8) be-mean-pokemons> var pokemons = [{'name':'Pikachu','description':'It raises its tail to check its sur roundings. The tail is sometimes struck by light ning in this pose.',attack: 55, defense: 40, height: 0.4},{'name':'Sandshrew','description':'To protect itself from attackers, it curls up into a ball. It lives in arid regions with minimal rainfall.',attack: 75, defense: 85, height: 0.6},{'name':'Nidoran','description':'Although small, its venomous barbs render this POKMON dangerous. The female has smaller horns.',attack: 47, defense: 52, height: 0.4},{'name':'Clefairy','description':'Adored for their cute looks and playfulness. They are thought to be rare, as they do not appear often.',attack: 45, defense: 48, height: 0.6},{'name':'Vulpix','description':'If it is attacked by an enemy that is stronger than itself, it feigns injury to fool the enemy and escapes.',attack: 41, defense: 40, height: 0.6}]
wesley(mongod-3.2.8) be-mean-pokemons> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 144ms
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
wesley(mongod-3.2.8) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("578786a137ee18af2beb82c1"),
  "name": "Pikachu",
  "description": "It raises its tail to check its sur roundings. The tail is sometimes struck by light ning in this pose.",
  "attack": 55,
  "defense": 40,
  "height": 0.4
}
{
  "_id": ObjectId("578786a137ee18af2beb82c2"),
  "name": "Sandshrew",
  "description": "To protect itself from attackers, it curls up into a ball. It lives in arid regions with minimal rainfall.",
  "attack": 75,
  "defense": 85,
  "height": 0.6
}
{
  "_id": ObjectId("578786a137ee18af2beb82c3"),
  "name": "Nidoran",
  "description": "Although small, its venomous barbs render this POKMON dangerous. The female has smaller horns.",
  "attack": 47,
  "defense": 52,
  "height": 0.4
}
{
  "_id": ObjectId("578786a137ee18af2beb82c4"),
  "name": "Clefairy",
  "description": "Adored for their cute looks and playfulness. They are thought to be rare, as they do not appear often.",
  "attack": 45,
  "defense": 48,
  "height": 0.6
}
{
  "_id": ObjectId("578786a137ee18af2beb82c5"),
  "name": "Vulpix",
  "description": "If it is attacked by an enemy that is stronger than itself, it feigns injury to fool the enemy and escapes.",
  "attack": 41,
  "defense": 40,
  "height": 0.6
}
Fetched 5 record(s) in 6ms
```

##Buscando e atualizando descrição do pikachu
```
wesley(mongod-3.2.8) be-mean-pokemons> var q = {name:'Pikachu'}
wesley(mongod-3.2.8) be-mean-pokemons> var poke = db.pokemons.findOne(q)
wesley(mongod-3.2.8) be-mean-pokemons> poke.description='O melhor pokemon'
O melhor pokemon
wesley(mongod-3.2.8) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

```
