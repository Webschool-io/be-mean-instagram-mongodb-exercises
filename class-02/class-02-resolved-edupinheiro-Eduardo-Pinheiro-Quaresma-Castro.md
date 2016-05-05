# MongoDB - Aula 02 - Exercício
autor: Eduardo Pinheiro Quaresma Castro
## 01 -  Criando database chamada be-mean-pokemons
```
Cybertron(mongod-3.0.9) test> use be-mean-pokemons
switched to db be-mean-pokemons
```

## 02 - Listando databases do servidor
```
Cybertron(mongod-3.0.9) be-mean-pokemons> show dbs
be-mean          → 0.078GB
be-mean-pokemons → 0.078GB
local            → 0.078GB
```

## 03 - Listando collections da database be-mean-pokemons
```
Cybertron(mongod-3.0.9) be-mean-pokemons> show collections
Cybertron(mongod-3.0.9) be-mean-pokemons>
```

## 04 - Inserindo 5 pokemons na database
```
Cybertron(mongod-3.0.9) be-mean-pokemons> var pokemons = [{name:'Pikachu', description:'An eletric mouse', type:'eletric', attack: 55, defense:40, height:0.4}, {name:'Bulbasaur', description:'Chicote de trepadeira', type:'grass', attack:49, defense:49, height:0.7}, {name:'Charmander', description:'Esse é o cão chupando manga de tão fofinho', type:'fire', attack:52, defense:43, height:0.6}, {name:'Squirtle', description:'Ejeta água que passarinho não bebe', type:'water', attack:48, defense:65, height:0.5}, {name:'Caterpie', description:'Serve pra nada', type:'bug', attack:30, defense:35, height:0.3}]

Cybertron(mongod-3.0.9) be-mean-pokemons> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 513ms
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

## 05 - Listando os pokemons inseridos
```
Cybertron(mongod-3.0.9) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("56ac4978853bf472d952c28d"),
  "name": "Pikachu",
  "description": "An eletric mouse",
  "type": "eletric",
  "attack": 55,
  "defense": 40,
  "height": 0.4
}
{
  "_id": ObjectId("56ac4978853bf472d952c28e"),
  "name": "Bulbasaur",
  "description": "Chicote de trepadeira",
  "type": "grass",
  "attack": 49,
  "defense": 49,
  "height": 0.7
}
{
  "_id": ObjectId("56ac4978853bf472d952c28f"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de tão fofinho",
  "type": "fire",
  "attack": 52,
  "defense": 43,
  "height": 0.6
}
{
  "_id": ObjectId("56ac4978853bf472d952c290"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "water",
  "attack": 48,
  "defense": 65,
  "height": 0.5
}
{
  "_id": ObjectId("56ac4978853bf472d952c291"),
  "name": "Caterpie",
  "description": "Serve pra nada",
  "type": "bug",
  "attack": 30,
  "defense": 35,
  "height": 0.3
}
Fetched 5 record(s) in 1ms
```

## 06 - Procurando o pokemon Pikachu e armazenando-o na variável poke
```
Cybertron(mongod-3.0.9) be-mean-pokemons> var query = {name: 'Pikachu'}
Cybertron(mongod-3.0.9) be-mean-pokemons> query
{
  "name": "Pikachu"
}

Cybertron(mongod-3.0.9) be-mean-pokemons> var poke = db.pokemons.findOne(query)
Cybertron(mongod-3.0.9) be-mean-pokemons> poke
{
  "_id": ObjectId("56ac4978853bf472d952c28d"),
  "name": "Pikachu",
  "description": "An eletric mouse",
  "type": "eletric",
  "attack": 55,
  "defense": 40,
  "height": 0.4
}
```

## 07 - Modificando sua description e salvando-o na database
```
Cybertron(mongod-3.0.9) be-mean-pokemons> poke.description = "An boring eletric mouse"
An boring eletric mouse

Cybertron(mongod-3.0.9) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 130ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

Cybertron(mongod-3.0.9) be-mean-pokemons> poke
{
  "_id": ObjectId("56ac4978853bf472d952c28d"),
  "name": "Pikachu",
  "description": "An boring eletric mouse",
  "type": "eletric",
  "attack": 55,
  "defense": 40,
  "height": 0.4
}
```