## Exercíco

**Adicionar**
2 ataques ao mesmo tempo para os seguintes pokemons:
Pikachu, Squirtle, Bulbassauro e Charmander.

```
var query = { height : { $not : { $gt: 1 } } }

var attacks = ['HEAL', 'ataque rápido']

var mod = {$pushAll: {moves: attacks}}

var options = {multi: true}

db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 4ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
```

**Adicionar** 1 movimento em todos os pokemons: desvio.

```
var query = {}
var mod = {$push: {moves: "desvio"}}
var options = {multi: true}
db.pokemons.update(query, mod, options)
Updated 11 existing record(s) in 3ms
WriteResult({
  "nMatched": 11,
  "nUpserted": 0,
  "nModified": 11
})

```

**Adicionar** o pokemon AindaNaoExisteMon
caso ele não exista com todos os dados com o valor null
e a descrição: "Sem maiores informações".

```
var query = {name: /AindaNaoExisteMon/i}

var mod = {   $set: {active: true},   $setOnInsert: {name: "AindaNaoExisteMon", attack: null, defense: null, height: null, description: "Sem maiores informações"} }

var options = {upsert: true}

db.pokemons.update(query, mod, options)

```

Pesquisar **todos** os pokemons que possuam os
ataques que você adicionou,
escolha seu pokemon favorito.

```
var query = { moves : { $all :[ 'ataque rápido' , 'HEAL' ] } }

db.pokemons.find(query)
{
 "_id": ObjectId("56cd0a6b01cde121db2aab31"),
 "name": "Pikachu",
 "description": "Camundongo fotovoltaico",
 "type": "eletrico",
 "attack": 100,
 "height": 0.5,
 "active": false,
 "moves": [
   "investida",
   "choque do trovão",
   "HEAL",
   "ataque rápido",
   "desvio"
 ]
}
{
 "_id": ObjectId("56d4ecc6695485546704f365"),
 "active": false,
 "name": "Squirtle",
 "attack": 48,
 "defense": 80,
 "height": 0.5,
 "description": "Ejeta Agua que piu piu nao bebe",
 "moves": [
   "investida",
   "hidro bomba",
   "HEAL",
   "ataque rápido",
   "desvio"
 ]
}
{
 "_id": ObjectId("56d4f686b8a34ca1810e4a80"),
 "description": "Cão chupando manga de fofura com fogo no rabo",
 "type": "Fogo",
 "attack": 52,
 "height": 0.6,
 "active": false,
 "name": "Charmander",
 "moves": [
   "investida",
   "lança-chamas",
   "HEAL",
   "ataque rápido",
   "desvio"
 ]
}
{
 "_id": ObjectId("56d4f733b8a34ca1810e4a81"),
 "name": "Bulbassauro",
 "description": "Chicote de trepadeira",
 "type": "grama",
 "attack": 49,
 "height": 0.4,
 "active": false,
 "moves": [
   "investida",
   "folha navalha",
   "HEAL",
   "ataque rápido",
   "desvio"
 ]
}
Fetched 4 record(s) in 12ms
```

Pesquisar **todos** os pokemons que não são do tipo elétrico.

```
var query = { type : { $not :  /eletrico/i  } }
db.pokemons.find(query)
{
  "_id": ObjectId("56785f5db851c1d5742cb994"),
  "name": "venusaur",
  "description": "Dinossauro Mutante Gigante pai, ancestral das tartarugas ninjas",
  "type": "leaf",
  "attack": 82,
  "height": 20,
  "defense": 83,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5678620ab851c1d5742cb997"),
  "name": "charizard",
  "description": "Dinossauro Mutante Gigante Voador Cospe Fogo, evolução do charmander",
  "type": "fire",
  "attack": 84,
  "height": 17,
  "defense": 78,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56786220b851c1d5742cb998"),
  "name": "blastoise",
  "description": "Tartaruga Mutante Gigante Nadadora Cospe Água, evolução do squirtle, ancestral do Mandu",
  "type": "water",
  "attack": 83,
  "height": 16,
  "defense": 100,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5678624fb851c1d5742cb999"),
  "name": "butterfree",
  "description": "Borboleta que voa, evolução do catterpie",
  "type": "leaf",
  "attack": 45,
  "height": 11,
  "defense": 50,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56786266b851c1d5742cb99a"),
  "name": "raichu",
  "description": "Ratazana elétrica tipo Itaipu",
  "type": "electric",
  "attack": 90,
  "height": 8,
  "defense": 60,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56786288b851c1d5742cb99b"),
  "name": "dugtrio",
  "description": "Sociedade de minhocas mutantes engraçadas",
  "type": "earth",
  "attack": 80,
  "height": 7,
  "defense": 50,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5678629eb851c1d5742cb99c"),
  "name": "psyduck",
  "description": "Pato com forte enxaqueca e poderes similares ao Charles Xavier",
  "type": "water-psychic",
  "attack": 52,
  "height": 8,
  "defense": 48,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56cd0a6b01cde121db2aab31"),
  "name": "Pikachu",
  "description": "Camundongo fotovoltaico",
  "type": "eletrico",
  "attack": 100,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "choque do trovão",
    "HEAL",
    "ataque rápido",
    "desvio"
  ]
}
{
  "_id": ObjectId("56d4ecc6695485546704f365"),
  "active": false,
  "name": "Squirtle",
  "attack": 48,
  "defense": 80,
  "height": 0.5,
  "description": "Ejeta Agua que piu piu nao bebe",
  "moves": [
    "investida",
    "hidro bomba",
    "HEAL",
    "ataque rápido",
    "desvio"
  ]
}
{
  "_id": ObjectId("56d4f686b8a34ca1810e4a80"),
  "description": "Cão chupando manga de fofura com fogo no rabo",
  "type": "Fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "name": "Charmander",
  "moves": [
    "investida",
    "lança-chamas",
    "HEAL",
    "ataque rápido",
    "desvio"
  ]
}
{
  "_id": ObjectId("56d4f733b8a34ca1810e4a81"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "HEAL",
    "ataque rápido",
    "desvio"
  ]
}
{
  "_id": ObjectId("56d598735ff87d6c5f7d807b"),
  "active": true,
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 12 record(s) in 15ms

```

Pesquisar **todos** pokemons que tenham o ataque investida E
tenham a defesa não menor ou igual a 49.

```
var query = { $and: [ { moves: "investida" }, { defense : { $not : { $lte : 49 } } } ] }

db.pokemons.find(query)

```

Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
var query = {type: /water/i}
db.pokemons.remove(query)

```
