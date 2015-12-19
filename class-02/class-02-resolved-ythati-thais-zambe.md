# MongoDB - Aula 02 - Exercício
Autor: Thais Zambe

## Listagem das databases (passo 2)
```javascript
wolkenritter(mongod-3.0.6) be-mean-pokemons> show dbs
local            → 0.078GB
be-mean-pokemons → 0.078GB
```

## Listagem das coleções (passo 3)
```javascript
wolkenritter(mongod-3.0.6) be-mean-pokemons> show collections
pokemons       → 0.000MB / 0.008MB
system.indexes → 0.000MB / 0.008MB
```

## Cadastro dos pokemons (passo 4)
```javascript
wolkenritter(mongod-3.0.6) be-mean-pokemons> var pokemon = [{ 'name':'Zorua','description':'Raposa metida','type': 'dark', attack: 65, height: 0.7 },{ 'name':'Charmeleon','description':'Charmander revolts','type': 'fire', 'attack': 64, height: 1.09 },{ 'name':'Gourgeist','description':'Abóbora Nicky Minaj','type': 'ghost', 'attack': 90, height: 1.7 },{ 'name':'Aron','description':'Coisa desconhecida mas fofinha','type': 'steel', 'attack': 70, height: 0.4 },{ 'name':'Mawile','description':'Aquele Ukyo do Samurai Shodown','type':'steel','attack':85,'height':0.6 }]
wolkenritter(mongod-3.0.6) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 4ms
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

## Lista dos pokemons (passo 5)
```javascript
wolkenritter(mongod-3.0.6) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("564894bf8c1c831aa98033f7"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("564894bf8c1c831aa98033f8"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("564894bf8c1c831aa98033f9"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("564894bf8c1c831aa98033fa"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("564898108c1c831aa98033fb"),
  "name": "Zorua",
  "description": "Raposa metida",
  "type": "dark",
  "attack": 65,
  "height": 0.7
}
{
  "_id": ObjectId("564898108c1c831aa98033fc"),
  "name": "Charmeleon",
  "description": "Charmander revolts",
  "type": "fire",
  "attack": 64,
  "height": 1.09
}
{
  "_id": ObjectId("564898108c1c831aa98033fd"),
  "name": "Gourgeist",
  "description": "Abóbora Nicky Minaj",
  "type": "ghost",
  "attack": 90,
  "height": 1.7
}
{
  "_id": ObjectId("564898108c1c831aa98033fe"),
  "name": "Aron",
  "description": "Coisa desconhecida mas fofinha",
  "type": "steel",
  "attack": 70,
  "height": 0.4
}
{
  "_id": ObjectId("564898108c1c831aa98033ff"),
  "name": "Mawile",
  "description": "Aquele Ukyo do Samurai Shodown",
  "type": "steel",
  "attack": 85,
  "height": 0.6
}
Fetched 9 record(s) in 2ms
```

## Aron (passo 6)
```javascript
wolkenritter(mongod-3.0.6) be-mean-pokemons> var poke = db.pokemons.findOne({name:'Aron'})
```

## Atualização de Aron (passo 6)
```javascript
wolkenritter(mongod-3.0.6) be-mean-pokemons> poke.description = 'Coisa estranha furadinha e fofinha'
Coisa estranha furadinha e fofinha
wolkenritter(mongod-3.0.6) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 4ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```

