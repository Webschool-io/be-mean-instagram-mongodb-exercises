# MongoDB - Aula 02 - Exercício
autor: Marcos Dias da Conceição

## Criação da database be-mean-pokemons (passo 1)
```
use be-mean-pokemons
switched to db be-mean-pokemons

```

## Listagem das databases (passo 2)
```
show dbs
be-mean-instagram → 0.078GB
test              → 0.078GB
be-mean           → 0.078GB
teste             → 0.078GB
local             → 0.078GB
admin             → (empty)

```

## Listagem das coleções (passo 3)
```
show collections
system.indexes → 0.000MB / 0.008MB
teste          → 0.000MB / 0.008MB

```

## Cadastro dos pokemons (passo 4)
```
var pokemon = [
  {name: 'Charizard', description: 'Dragão de fogo badass', type: 'fogo', attack: 84, height: 1.7},
  {name: 'Gengar', description: 'Fantasminha não camarada', type: 'fantasma', attack: 65, height: 1.5},
  {name: 'Pidgeotto', description: 'Pombo nervoso', type: 'normal', attack: 60, height: 1.09},
  {name: 'Raichu', description: 'Primo do Pikachu', type: 'elétrico', attack: 90, height: 0.79},
  {name: 'Parasect', description: 'Cogumelo, paz e amor', type: 'grama', attack: 95, height: 0.99}
]
db.pokemons.save(pokemon)

Inserted 1 record(s) in 159ms
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
var lista = db.pokemons.find()
lista

{
  "_id": ObjectId("56819e1f8e301f18c67d3414"),
  "name": "Charizard",
  "description": "Dragão de fogo badass",
  "type": "fogo",
  "attack": 84,
  "height": 1.7
}
{
  "_id": ObjectId("56819e1f8e301f18c67d3415"),
  "name": "Gengar",
  "description": "Fantasminha não camarada",
  "type": "fantasma",
  "attack": 65,
  "height": 1.5
}
{
  "_id": ObjectId("56819e1f8e301f18c67d3416"),
  "name": "Pidgeotto",
  "description": "Pombo nervoso",
  "type": "normal",
  "attack": 60,
  "height": 1.09
}
{
  "_id": ObjectId("56819e1f8e301f18c67d3417"),
  "name": "Raichu",
  "description": "Primo do Pikachu",
  "type": "elétrico",
  "attack": 90,
  "height": 0.79
}
{
  "_id": ObjectId("56819e1f8e301f18c67d3418"),
  "name": "Parasect",
  "description": "Cogumelo, paz e amor",
  "type": "grama",
  "attack": 95,
  "height": 0.99
}
Fetched 5 record(s) in 1ms

```

## Raichu (passo 6)
`var poke = db.pokemons.findOne({name: 'Raichu'})`

## Atualização do Raichu (passo 7)
```
poke.description = 'Rato chocante nível 2'
db.pokemons.save(poke)

Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

```
