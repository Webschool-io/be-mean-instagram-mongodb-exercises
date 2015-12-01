# MongoDB - Aula 02 - Exercicio
autor: Ronald Huggler

## Criando a database  
```
huggler@Huggler-HP:~$ mongo be-mean-pokemons
MongoDB shell version: 2.6.11
connecting to: be-mean-pokemons
Mongo-Hacker 0.0.9
Huggler-HP(mongod-2.6.11) be-mean-pokemons>
```

## Listando databases  
```
Huggler-HP(mongod-2.6.11) be-mean-pokemons> show dbs
be-mean-instagram → 0.078GB
be-mean           → 0.078GB
local             → 0.078GB
admin             → (empty)
```

## Listando collections  
```
Huggler-HP(mongod-2.6.11) be-mean-pokemons> show collections
pokemons       → 0.000MB / 0.008MB
system.indexes → 0.000MB / 0.008MB
```

## Adicionando pokemons  
```
Huggler-HP(mongod-2.6.11) be-mean-pokemons> var pokemon = {'name':'Blastoise','description':'Tartaruga gigante fodástica','type':'agua', attack: 83, defese: 100, height: 16}
Huggler-HP(mongod-2.6.11) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 4ms
WriteResult({
  "nInserted": 1
})

Huggler-HP(mongod-2.6.11) be-mean-pokemons> var pokemon = {'name':'Gardevoir','description':'Fada controladora de mentes','type':'psiquico', attack: 65, defese: 65, height: 16}
Huggler-HP(mongod-2.6.11) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})

Huggler-HP(mongod-2.6.11) be-mean-pokemons> var pokemon = {'name':'Abra','description':'Ratinho mais fofinho','type':'psiquico', attack: 20, defese: 15, height: 9}
Huggler-HP(mongod-2.6.11) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 23ms
WriteResult({
  "nInserted": 1
})

Huggler-HP(mongod-2.6.11) be-mean-pokemons> var pokemon = {'name':'Scyther','description':'Inseto da foice perigosa','type':'inseto', attack: 110, defese: 80, height: 15}
Huggler-HP(mongod-2.6.11) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 11ms
WriteResult({
  "nInserted": 1
})

Huggler-HP(mongod-2.6.11) be-mean-pokemons> var pokemon = {'name':'Lapras','description':'Monstro do lago Ness','type':'agua', attack: 85, defese: 80, height: 25}
Huggler-HP(mongod-2.6.11) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})
```

## Listando os pokemons  
```
Huggler-HP(mongod-2.6.11) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("565341dcb7a5009ddde95f1d"),
  "name": "Blastoise",
  "description": "Tartaruga gigante fodástica",
  "type": "water",
  "attack": 83,
  "defese": 100,
  "height": 16
}
{
  "_id": ObjectId("565342ceb7a5009ddde95f1e"),
  "name": "Gardevoir",
  "description": "Fada controladora de mentes",
  "type": "psiquico",
  "attack": 65,
  "defese": 65,
  "height": 16
}
{
  "_id": ObjectId("56534379b7a5009ddde95f1f"),
  "name": "Abra",
  "description": "Ratinho mais fofinho",
  "type": "psiquico",
  "attack": 20,
  "defese": 15,
  "height": 9
}
{
  "_id": ObjectId("565344814012b2a728ba0b8c"),
  "name": "Scyther",
  "description": "Inseto da foice perigosa",
  "type": "inseto",
  "attack": 110,
  "defese": 80,
  "height": 15
}
{
  "_id": ObjectId("565345924012b2a728ba0b8d"),
  "name": "Lapras",
  "description": "Monstro do lago Ness",
  "type": "agua",
  "attack": 85,
  "defese": 80,
  "height": 25
}
Fetched 5 record(s) in 5ms
```

## Buscando pokemons  
```
Huggler-HP(mongod-2.6.11) be-mean-pokemons> var query = {name: 'Abra'}
Huggler-HP(mongod-2.6.11) be-mean-pokemons> var poke = db.pokemons.findOne(query)
Huggler-HP(mongod-2.6.11) be-mean-pokemons> poke
{
  "_id": ObjectId("56534379b7a5009ddde95f1f"),
  "name": "Abra",
  "description": "Ratinho mais fofinho",
  "type": "psiquico",
  "attack": 20,
  "defese": 15,
  "height": 9
}
```

## Modificando pokemons  
```
Huggler-HP(mongod-2.6.11) be-mean-pokemons> poke.description = "Ratinho amarelo mais fofinho"
Ratinho amarelo mais fofinho
Huggler-HP(mongod-2.6.11) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```
