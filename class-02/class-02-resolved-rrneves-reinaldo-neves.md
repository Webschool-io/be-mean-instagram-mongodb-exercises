# MongoDB - Aula 02 - Exercício
autor: Reinaldo Neves

## criar banco de dados (passo 1)

```
use be-mean-pokemons
switched to db be-mean-pokemons
```

## Listagem das databases (passo 2)

```
show dbs

be-mean-instagram  0.078GB
be-mean            0.078GB
local              0.078GB
```

## Listagem das coleções (passo 3)

```
show collections
```

## Cadastro dos pokemons (passo 4)

```
var pokemon = {'name':'Pikachu','description':'Rato elétrico bem fofinho','type': 'electric', attack: 55, height: 0.4}
db.pokemons.insert(pokemon)

Inserted 1 record(s) in 864ms
WriteResult({
    "nInserted": 1
})


var pokemon = [ {'name':'Durant','description':'Formiga de aço','type': 'inseto','attack': 48, 'height': 0.3 },{'name':'Bulbassauro','description':'Chicote de trepadeira','type': 'grama', 'attack': 49, height: 0.7 },{'name':'Charmander','description':'Dragão','type': 'fogo', 'attack': 52, height: 0.6 },{'name':'Squirtle','description':'Ejeta água','type': 'água', 'attack': 48, 'height': 0.5 },{'name':'Raikou','description':'Encarna a velocidade do raio','type': 'elétrico', 'attack': 85, 'height': 1.9 },{'name':'Charizard','description':'Respira fogo de grande calor','type': 'fogo', 'attack': 84, 'height': 1.7 },{'name':'Beedrill','description':'Extremamente territorial, ataca em enxame','type': 'inseto', 'attack': 80, 'height': 1.0 },{'name':'Rattata ','description':'Muito cauteloso','type': 'normal', 'attack': 56, 'height': 0.3 } ]
db.pokemons.save(pokemon)

Inserted 1 record(s) in 9ms
BulkWriteResult({
    "writeErrors": [ ],
    "writeConcernErrors": [ ],
    "nInserted": 8,
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
    "_id": ObjectId("564a8d36b94d933d6fdc63b8"),
    "name": "Pikachu",
    "description": "Rato elétrico bem fofinho",
    "type": "electric",
    "attack": 55,
    "height": 0.4
}
{
    "_id": ObjectId("564a8e9833cc991a7ab907d4"),
    "name": "Durant",
    "description": "Formiga de aço",
    "type": "inseto",
    "attack": 48,
    "height": 0.3
}
{
    "_id": ObjectId("564a8e9833cc991a7ab907d5"),
    "name": "Bulbassauro",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 49,
    "height": 0.7
}
{
    "_id": ObjectId("564a8e9833cc991a7ab907d6"),
    "name": "Charmander",
    "description": "Dragão",
    "type": "fogo",
    "attack": 52,
    "height": 0.6
}
{
    "_id": ObjectId("564a8e9833cc991a7ab907d7"),
    "name": "Squirtle",
    "description": "Ejeta água",
    "type": "água",
    "attack": 48,
    "height": 0.5
}
{
    "_id": ObjectId("564a8e9833cc991a7ab907d8"),
    "name": "Raikou",
    "description": "Encarna a velocidade do raio",
    "type": "elétrico",
    "attack": 85,
    "height": 1.9
}
{
    "_id": ObjectId("564a8e9833cc991a7ab907d9"),
    "name": "Charizard",
    "description": "Respira fogo de grande calor",
    "type": "fogo",
    "attack": 84,
    "height": 1.7
}
{
    "_id": ObjectId("564a8e9833cc991a7ab907da"),
    "name": "Beedrill",
    "description": "Extremamente territorial, ataca em enxame",
    "type": "inseto",
    "attack": 80,
    "height": 1
}
{
    "_id": ObjectId("564a8e9833cc991a7ab907db"),
    "name": "Rattata ",
    "description": "Muito cauteloso",
    "type": "normal",
    "attack": 56,
    "height": 0.3
}
Fetched 9 record(s) in 180ms
```

## Raikou (passo 6)

```
var query = {'name': 'Raikou' }
var poke = db.pokemons.findOne(query)
poke
{
    "_id": ObjectId("564a8e9833cc991a7ab907d8"),
    "name": "Raikou"
    "description": "Encarna a velocidade do raio",
    "type": "elétrico",
    "attack": 85,
    "height": 1.9 
}
```

## Atualização do Raikou (passo 6)

```
var query = {'name': 'Raikou' }
var poke = db.pokemons.findOne(query)
poke.description = 'Velocidade do raio e ondas de choque'
Velocidade do raio e ondas de choque 

poke
{
    "_id": ObjectId("564a8e9833cc991a7ab907d8"),
    "name": "Raikou",
    "description": "Velocidade do raio e ondas de choque",
    "type": "elétrico",
    "attack": 85,
    "height": 1.9
} 

db.pokemons.save(poke) 
Updated 1 existing record(s) in 51ms
WriteResult({
    "nMatched": 1,
    "nUpserted": 0,
    "nModified": 1
})    

var pokeAlterado = db.pokemons.findOne(query)

pokeAlterado
{
    "_id": ObjectId("564a8e9833cc991a7ab907d8"),
    "name": "Raikou",
    "description": "Velocidade do raio e ondas de choque",
    "type": "elétrico",
    "attack": 85,
    "height": 1.9
}
```
