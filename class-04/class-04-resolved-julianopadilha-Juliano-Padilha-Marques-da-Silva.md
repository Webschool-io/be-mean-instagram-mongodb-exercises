# MongoDB - Aula 04 - Exercício
Autor: Juliano Padilha

## Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro, Charmander.

```
be-mean-instagram> var query = {$or: [{name: 'Pikachu'}, {name: 'Squirtle'}, {name: 'Charmander'}, {name: 'Bulbassauro'}]}

be-mean-instagram> var mod = {$pushAll: {moves: ['investida', 'superSpeed']}}

be-mean-instagram> var options = {multi: true}

be-mean-instagram> db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 2ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})

be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5778984dfbb4a2cbca1161ce"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "superSpeed",
  ]
}
{
  "_id": ObjectId("5778996afbb4a2cbca1161cf"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": "49",
  "height": 0.4,
  "moves": [
    "investida",
    "superSpeed"
  ]
}
{
  "_id": ObjectId("577899bffbb4a2cbca1161d0"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": "52",
  "height": 0.6,
  "moves": [
    "investida",
    "superSpeed"
  ]
}
{
  "_id": ObjectId("577899f8fbb4a2cbca1161d1"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": "48",
  "height": 0.5,
  "moves": [
    "investida",
    "superSpeed"
  ]
}
Fetched 4 record(s) in 3ms
```

## Adicionar um movimento em todos os Pokemons 'desvio'.

```
be-mean-instagram> var query = {}

be-mean-instagram> var mod = {$pushAll: {moves: ['desvio']}}

be-mean-instagram> var options = {multi: true}

be-mean-instagram> db.pokemons.update(query, mod, options)
Updated 5 existing record(s) in 2ms
WriteResult({
  "nMatched": 5,
  "nUpserted": 0,
  "nModified": 5
})

be-mean-instagram> db.pokemons.find()
{
  "_id": ObjectId("5778984dfbb4a2cbca1161ce"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "superSpeed",
    "desvio"
  ]
}
{
  "_id": ObjectId("5778996afbb4a2cbca1161cf"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": "49",
  "height": 0.4,
  "moves": [
    "investida",
    "superSpeed",
    "desvio"
  ]
}
{
  "_id": ObjectId("577899bffbb4a2cbca1161d0"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": "52",
  "height": 0.6,
  "moves": [
    "investida",
    "superSpeed",
    "desvio"
  ]
}
{
  "_id": ObjectId("577899f8fbb4a2cbca1161d1"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": "48",
  "height": 0.5,
  "moves": [
    "investida",
    "superSpeed",
    "desvio"
  ]
}
{
  "_id": ObjectId("57789ceda1daa07096d6b63d"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": "30",
  "height": 0.3,
  "defense": 35,
  "moves": [
    "desvio"
  ]
}
Fetched 5 record(s) in 4ms
```

## Adicionar o Pokemons 'AindaNaoExisteMon' caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".

```
be-mean-instagram> var query = {name: /AindaNaoExisteMon/i}

be-mean-instagram> var mod = {$setOnInsert: {name: 'AindaNaoExisteMon', description: 'Sem maiores informações', type: null, attack: null, height: null, defense: null, moves: []}}

be-mean-instagram> var options = {upsert: true}

be-mean-instagram> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 34ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("5779d87aa8eb0e9b4a3a8c38")
})

db.pokemons.find(ObjectId("5779d87aa8eb0e9b4a3a8c38"))
{
  "_id": ObjectId("5779d87aa8eb0e9b4a3a8c38"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null,
  "defense": null,
  "moves": [ ]
}
Fetched 1 record(s) in 3ms
```

## Pesquisar todos os Pokemons que possuam o ataque 'investida' e mais um que você adicionou, escolha seu Pokemon favorito.

```
be-mean-instagram> var query = {moves: {$in: ['investida', 'desvio']}}

be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5778984dfbb4a2cbca1161ce"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "superSpeed",
    "desvio"
  ]
}
{
  "_id": ObjectId("5778996afbb4a2cbca1161cf"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": "49",
  "height": 0.4,
  "moves": [
    "investida",
    "superSpeed",
    "desvio"
  ]
}
{
  "_id": ObjectId("577899bffbb4a2cbca1161d0"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": "52",
  "height": 0.6,
  "moves": [
    "investida",
    "superSpeed",
    "desvio"
  ]
}
{
  "_id": ObjectId("577899f8fbb4a2cbca1161d1"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": "48",
  "height": 0.5,
  "moves": [
    "investida",
    "superSpeed",
    "desvio"
  ]
}
{
  "_id": ObjectId("57789ceda1daa07096d6b63d"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": "30",
  "height": 0.3,
  "defense": 35,
  "moves": [
    "desvio"
  ]
}
Fetched 5 record(s) in 4ms
```

## Pesquisar todos os Pokemons que possuam ataques que você adicionou, escolha seu Pokemons favorito.

```
be-mean-instagram> var query = {moves: {$all: ['superSpeed', 'investida	']}}

be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5778984dfbb4a2cbca1161ce"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "superSpeed",
    "desvio"
  ]
}
{
  "_id": ObjectId("5778996afbb4a2cbca1161cf"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": "49",
  "height": 0.4,
  "moves": [
    "investida",
    "superSpeed",
    "desvio"
  ]
}
{
  "_id": ObjectId("577899bffbb4a2cbca1161d0"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": "52",
  "height": 0.6,
  "moves": [
    "investida",
    "superSpeed",
    "desvio"
  ]
}
{
  "_id": ObjectId("577899f8fbb4a2cbca1161d1"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": "48",
  "height": 0.5,
  "moves": [
    "investida",
    "superSpeed",
    "desvio"
  ]
}
Fetched 4 record(s) in 5ms
```

## Pesquisar todos os Pokemons que não são do tipo elétrico

```
be-mean-instagram> var query = {type: {$ne: 'eletric'}}

be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5778996afbb4a2cbca1161cf"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": "49",
  "height": 0.4,
  "moves": [
    "investida",
    "superSpeed",
    "desvio"
  ]
}
{
  "_id": ObjectId("577899bffbb4a2cbca1161d0"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": "52",
  "height": 0.6,
  "moves": [
    "investida",
    "superSpeed",
    "desvio"
  ]
}
{
  "_id": ObjectId("577899f8fbb4a2cbca1161d1"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": "48",
  "height": 0.5,
  "moves": [
    "investida",
    "superSpeed",
    "desvio"
  ]
}
{
  "_id": ObjectId("57789ceda1daa07096d6b63d"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": "30",
  "height": 0.3,
  "defense": 35,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5779d87aa8eb0e9b4a3a8c38"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null,
  "defense": null,
  "moves": [ ]
}
Fetched 5 record(s) in 5ms
```

## Pesquisar todos os Pokemons que tenham o ataque 'investida' e tenham o attack não menor ou igual a 49.

```
be-mean-instagram> var query = {$and: [ {moves: {$in: ['investida']}}, {attack: {$not: {$lte: '49'}}} ]}

be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5778984dfbb4a2cbca1161ce"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "superSpeed",
    "desvio"
  ]
}
{
  "_id": ObjectId("577899bffbb4a2cbca1161d0"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": "52",
  "height": 0.6,
  "moves": [
    "investida",
    "superSpeed",
    "desvio"
  ]
}
Fetched 2 record(s) in 2ms
```

## Remova todos os pokemons do tipo água E com attack menor que 50.

```
be-mean-instagram> var query = {$and: [{type:/água/i}, {attack: {$lt: '50'}}]}
be-mean-instagram> db.pokemons.remove(query)
{
  "_id": ObjectId("577899f8fbb4a2cbca1161d1"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": "48",
  "height": 0.5,
  "moves": [
    "investida",
    "superSpeed",
    "desvio"
  ]
}
Fetched 1 record(s) in 3ms

be-mean-instagram> db.pokemons.remove(query)
Removed 1 record(s) in 40ms
WriteResult({
  "nRemoved": 1
})

```