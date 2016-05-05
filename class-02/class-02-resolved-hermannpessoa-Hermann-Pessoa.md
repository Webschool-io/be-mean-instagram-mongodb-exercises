# MongoDB - Aula 02 - Exercício
autor: HERMANN PESSOA

## Listagem das databases

```
environment(mongod-3.0.7) test> use be-mean-pokemons
switched to db be-mean-pokemons

environment(mongod-3.0.7) be-mean-pokemons> show dbs
be-mean-instagram → 0.078GB
be-mean           → 0.078GB
local             → 0.078GB

```

## Listagem das coleções

```
environment(mongod-3.0.7) be-mean-pokemons> show collections
environment(mongod-3.0.7) be-mean-pokemons>

```

## Cadastrando pokemons

```
var pokemons = [{"name":"Pikachu","description":"Rato elétrico bem fofinho","type":"electric","attack":55,"height":0.4,"defense":40},{"name":"Bulbassauro","description":"Chicote de trepadeira","type":"grama","attack":49,"height":0.4,"defense":49},{"name":"Charmander","description":"Esse é o cão chupando manga de fofinho","type":"fogo","attack":52,"height":0.6,"defense":43},{"name":"Squirtle","description":"Ejeta água que passarinho não bebe","type":"água","attack":48,"height":0.5,"defense":65},{"name":"Caterpie","description":"Larva lutadora","type":"inseto","attack":30,"height":0.3,"defense":35}]

environment(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 9ms
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
## Listando os pokemons

```
environment(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("56ca20e21aa449a200e3339a"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "defense": 40
}
{
  "_id": ObjectId("56ca20e21aa449a200e3339b"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defense": 49
}
{
  "_id": ObjectId("56ca20e21aa449a200e3339c"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "defense": 43
}
{
  "_id": ObjectId("56ca20e21aa449a200e3339d"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "defense": 65
}
{
  "_id": ObjectId("56ca20e21aa449a200e3339e"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 7 record(s) in 48ms

```
## Atualizando pokemon

```
environment(mongod-3.0.7) be-mean-pokemons> var q = {name: "Squirtle"}
environment(mongod-3.0.7) be-mean-pokemons> q
{
  "name": "Squirtle"
}
environment(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(q)
environment(mongod-3.0.7) be-mean-pokemons> poke
{
  "_id": ObjectId("56ca20e21aa449a200e3339d"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "defense": 65
}
environment(mongod-3.0.7) be-mean-pokemons> db.pokemons.findOne(q)
{
  "_id": ObjectId("56ca20e21aa449a200e3339d"),
  "name": "Squirtle",
  "description": "Pokemon Dazágua",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "defense": 65
}

```


