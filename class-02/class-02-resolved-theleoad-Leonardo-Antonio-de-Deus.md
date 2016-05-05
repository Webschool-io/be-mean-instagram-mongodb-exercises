# MongoDB - Aula 02 - Exercício
Autor: Leonardo

## Listagem das databases (passo 2)

```
Leonardos-MBP(mongod-3.2.0) be-mean> use be-mean-pokemons
switched to db be-mean-pokemons

Leonardos-MBP(mongod-3.2.0) be-mean-pokemons> show dbs
be-mean → 0.004GB
local   → 0.000GB
Leonardos-MBP(mongod-3.2.0) be-mean-pokemons>
```

## Listagem das coleções (passo 3)

```
Leonardos-MBP(mongod-3.2.0) be-mean-pokemons> show collections
Leonardos-MBP(mongod-3.2.0) be-mean-pokemons>
```

## Cadastro dos pokemons (passo 4)

```
Leonardos-MBP(mongod-3.2.0) be-mean-pokemons> var pokemons = [{
...   "name": "Pikachu",
...   "description": "Rato elétrico bem fofinho",
...   "type": "electric",
...   "attack": 100,
...   "height": 0.4
... },
... {
...   "name": "Bulbassauro",
...   "description": "Chicote de trepadeira",
...   "type": "grama",
...   "attack": 49,
...   "height": 0.4
... },
... {
...   "name": "Charmander",
...   "description": "Esse é o cão chupando manga de fofinho",
...   "type": "fogo",
...   "attack": 52,
...   "height": 0.6
... },
... {
...   "name": "Squirtle",
...   "description": "Ejeta água que passarinho não bebe",
...   "type": "água",
...   "attack": 48,
...   "height": 0.5
... },
... {
...   "name": "Caterpie",
...   "description": "Larva lutadora",
...   "type": "inseto",
...   "attack": 30,
...   "height": 0.3,
...   "defense": 35
... }]

Leonardos-MBP(mongod-3.2.0) be-mean-pokemons> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 867ms
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

```
Leonardos-MBP(mongod-3.2.0) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("5684422ed4a388ea71bd18db"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4
}
{
  "_id": ObjectId("5684422ed4a388ea71bd18dc"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("5684422ed4a388ea71bd18dd"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("5684422ed4a388ea71bd18de"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("5684422ed4a388ea71bd18df"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 5 record(s) in 5ms
```

## Pikachu (passo 6)

```
Leonardos-MBP(mongod-3.2.0) be-mean-pokemons> var query = {"name": "Pikachu"}
Leonardos-MBP(mongod-3.2.0) be-mean-pokemons> query
{
  "name": "Pikachu"
}
Leonardos-MBP(mongod-3.2.0) be-mean-pokemons> var pikachu = db.pokemons.findOne(query)
Leonardos-MBP(mongod-3.2.0) be-mean-pokemons> pikachu
{
  "_id": ObjectId("5684422ed4a388ea71bd18db"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4
}
```

## Atualização do Pikachu (passo 6)

```
Leonardos-MBP(mongod-3.2.0) be-mean-pokemons> pikachu.attack
100
Leonardos-MBP(mongod-3.2.0) be-mean-pokemons> pikachu.attack = 55
55
Leonardos-MBP(mongod-3.2.0) be-mean-pokemons> db.pokemons.save(pikachu)
Updated 1 existing record(s) in 32ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```
