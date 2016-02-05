# MongoDB - Aula 02 - Exercício
autor: Bruno Novais

## criar banco de dados (passo 1)

```
use be-mean-pokemons
switched to db be-mean-pokemons
```

## Listagem das databases (passo 2)

```
show dbs
be-mean-instagram → 0.078GB
local             → 0.078GB
be-mean           → 0.078GB
admin             → (empty)
```

## Listagem das coleções (passo 3)

```
show collections
```

## Cadastro dos pokemons (passo 4)

```
var pokemons = [ {'name':'Caterpie','description':'Larva lutadora','type': 'inseto','attack': 30, 'height': 0.3, 'defense': 35},{'name':'Pikachu','description':'Rato elétrico bem fofinho','type': 'eletric','attack': 100, 'height': 0.4},{'name':'Bulbassauro','description':'Chicote de trepadeira','type': 'grama', 'attack': 49, height: 0.7 },{'name':'Charmander','description':'Esse é o cão chupando manga de fofinho','type': 'fogo', 'attack': 52, height: 0.6 },{'name':'Squirtle','description':'Ejeta água que passarinho nao bebe','type': 'água', 'attack': 48, 'height': 0.5 },{'name':'Raikou','description':'Encarna a velocidade do raio','type': 'elétrico', 'attack': 85, 'height': 1.9 },{'name':'Charizard','description':'Respira fogo de grande calor','type': 'fogo', 'attack': 84, 'height': 1.7 },{'name':'Beedrill','description':'Extremamente territorial, ataca em enxame','type': 'inseto', 'attack': 80, 'height': 1.0 },{'name':'Rattata ','description':'Muito cauteloso','type': 'normal', 'attack': 56, 'height': 0.3 } ]

db.pokemons.save(pokemons)

Inserted 1 record(s) in 248ms
BulkWriteResult({
  "writeErrors": [ ],
  "writeConcernErrors": [ ],
  "nInserted": 9,
  "nUpserted": 0,
  "nMatched": 0,
  "nModified": 0,
  "nRemoved": 0,
  "upserted": [ ]
})

```

## Lista dos pokemons (passo 5)

```
db.pokemons.find()
{
  "_id": ObjectId("56577f606559eb84fe2dfb15"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
{
  "_id": ObjectId("56577f606559eb84je2dfb16"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 100,
  "height": 0.4
}
{
  "_id": ObjectId("56577f606559eb84je2dfb17"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.7
}
{
  "_id": ObjectId("56577f606559eb84je2dfb18"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("56577f606559eb84je2dfb19"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho nao bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("56577f606559eb84je2dfb1a"),
  "name": "Raikou",
  "description": "Encarna a velocidade do raio",
  "type": "elétrico",
  "attack": 85,
  "height": 1.9
}
{
  "_id": ObjectId("56577f606559eb84je2dfb1b"),
  "name": "Charizard",
  "description": "Respira fogo de grande calor",
  "type": "fogo",
  "attack": 84,
  "height": 1.7
}
{
  "_id": ObjectId("56577f606559eb84je2dfb1c"),
  "name": "Beedrill",
  "description": "Extremamente territorial, ataca em enxame",
  "type": "inseto",
  "attack": 80,
  "height": 1
}
{
  "_id": ObjectId("56577f606559eb84je2dfb1d"),
  "name": "Rattata",
  "description": "Muito cauteloso",
  "type": "normal",
  "attack": 56,
  "height": 0.3
}
Fetched 9 record(s) in 3ms

```

##Buscando pokemon pelo nome (passo 6)

```
var query = {'name': 'Charizard' }
var pokemon = db.pokemons.findOne(query)
pokemon
{
  "_id": ObjectId("56577f606559eb84je2dfb1b"),
  "name": "Charizard",
  "description": "Respira fogo de grande calor",
  "type": "fogo",
  "attack": 84,
  "height": 1.7
}

```

##Alterando um valor e salvando (passo 7)

```
pokemon.attack = 83
83

pokemon
{
  "_id": ObjectId("56577f606559eb84je2dfb1b"),
  "name": "Charizard",
  "description": "Respira fogo de grande calor",
  "type": "fogo",
  "attack": 83,
  "height": 1.7
}


db.pokemons.save(pokemon)
Updated 1 existing record(s) in 3ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

db.pokemons.findOne(query)
{
  "_id": ObjectId("56577f606559eb84je2dfb1b"),
  "name": "Charizard",
  "description": "Respira fogo de grande calor",
  "type": "fogo",
  "attack": 83,
  "height": 1.7
}

```
