# MongoDB - Aula 04 - Exercício
autor: Fellipe Pinheiro


## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
5e14de9d5d4e(mongod-3.0.7) be-mean-pokemons> var query = { $or: [ { name: /pikachu/i }, { name: /squirtle/i }, { name: /bulbassauro/i}, { name: /charmander/i} ] }

5e14de9d5d4e(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll: {moves: ['recuar', 'salto']}}

5e14de9d5d4e(mongod-3.0.7) be-mean-pokemons> var options = {multi: true}

5e14de9d5d4e(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)

Updated 4 existing record(s) in 25ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
```
```
#Resultado
5e14de9d5d4e(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5644910686df9c8bbaa1d172"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletrico",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "recuar",
    "salto"
  ]
}
{
  "_id": ObjectId("5644915586df9c8bbaa1d173"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "investida",
    "recuar",
    "salto"
  ]
}
{
  "_id": ObjectId("564491d086df9c8bbaa1d175"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "investida",
    "recuar",
    "salto"
  ]
}
{
  "_id": ObjectId("5644923386df9c8bbaa1d176"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "investida",
    "recuar",
    "salto"
  ]
}
Fetched 4 record(s) in 1ms

```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```
5e14de9d5d4e(mongod-3.0.7) be-mean-pokemons> var query = {}

5e14de9d5d4e(mongod-3.0.7) be-mean-pokemons> var mod = {$push: {moves: 'desvio'}}

5e14de9d5d4e(mongod-3.0.7) be-mean-pokemons> var options = {multi: true}

5e14de9d5d4e(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)

Updated 10 existing record(s) in 2ms
WriteResult({
  "nMatched": 10,
  "nUpserted": 0,
  "nModified": 10
})

```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
5e14de9d5d4e(mongod-3.0.7) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}

5e14de9d5d4e(mongod-3.0.7) be-mean-pokemons> var mod = {$set: {description: "Sem maiores informações"}, $setOnInsert: {name: "AindaNaoExisteMon", attack: null, height: null, defense: null, type: null, moves: []}}

5e14de9d5d4e(mongod-3.0.7) be-mean-pokemons> var options = {upsert: true}

5e14de9d5d4e(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)

Updated 1 new record(s) in 3ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564c8dbd69e9e63d2bfbc38f")
})


5e14de9d5d4e(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564c8dbd69e9e63d2bfbc38f"),
  "description": "Sem maiores informações",
  "name": "AindaNaoExisteMon",
  "attack": null,
  "height": null,
  "defense": null,
  "type": null,
  "moves": [ ]
}
Fetched 1 record(s) in 0ms


```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
5e14de9d5d4e(mongod-3.0.7) be-mean-pokemons> var query = { moves: {$in: ['investida', 'Redivar']}}

5e14de9d5d4e(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564355fa17c6388471074b2d"),
  "name": "Eevee",
  "description": "There are a lot of evolutions",
  "attack": 55,
  "defense": 50,
  "height": 3,
  "type": "normal",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56435a5ba43104534c4cf01d"),
  "name": "Jolteon",
  "description": "Electric evolution",
  "attack": 65,
  "defense": 60,
  "height": 8,
  "type": "electric",
  "moves": [
    "investida",
    "desvio",
    "Revidar"
  ]
}
{
  "_id": ObjectId("56435a5ba43104534c4cf01e"),
  "name": "Flareon",
  "description": "Fire evolution",
  "attack": 130,
  "defense": 60,
  "height": 9,
  "type": "fire",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56435a5ba43104534c4cf01f"),
  "name": "Vaporeon",
  "description": "Water evolution",
  "attack": 65,
  "defense": 60,
  "height": 10,
  "type": "water",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56435a5ba43104534c4cf020"),
  "name": "Leafeon",
  "description": "Graas evolution",
  "attack": 110,
  "defense": 130,
  "height": 10,
  "type": "grass",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644910686df9c8bbaa1d172"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletrico",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "recuar",
    "salto",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644915586df9c8bbaa1d173"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "investida",
    "recuar",
    "salto",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644918b86df9c8bbaa1d174"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564491d086df9c8bbaa1d175"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "investida",
    "recuar",
    "salto",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644923386df9c8bbaa1d176"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "investida",
    "recuar",
    "salto",
    "desvio"
  ]
}
Fetched 10 record(s) in 3ms

```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```
5e14de9d5d4e(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$in: ['recuar', 'salto']}}

5e14de9d5d4e(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5644910686df9c8bbaa1d172"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletrico",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "recuar",
    "salto",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644915586df9c8bbaa1d173"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "investida",
    "recuar",
    "salto",
    "desvio"
  ]
}
{
  "_id": ObjectId("564491d086df9c8bbaa1d175"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "investida",
    "recuar",
    "salto",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644923386df9c8bbaa1d176"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "investida",
    "recuar",
    "salto",
    "desvio"
  ]
}
Fetched 4 record(s) in 1ms

```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```
5e14de9d5d4e(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{type: {$ne: 'electric'}}, {type: {$ne: 'eletrico'}}]}

5e14de9d5d4e(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564355fa17c6388471074b2d"),
  "name": "Eevee",
  "description": "There are a lot of evolutions",
  "attack": 55,
  "defense": 50,
  "height": 3,
  "type": "normal",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56435a5ba43104534c4cf01e"),
  "name": "Flareon",
  "description": "Fire evolution",
  "attack": 130,
  "defense": 60,
  "height": 9,
  "type": "fire",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56435a5ba43104534c4cf01f"),
  "name": "Vaporeon",
  "description": "Water evolution",
  "attack": 65,
  "defense": 60,
  "height": 10,
  "type": "water",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56435a5ba43104534c4cf020"),
  "name": "Leafeon",
  "description": "Graas evolution",
  "attack": 110,
  "defense": 130,
  "height": 10,
  "type": "grass",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644915586df9c8bbaa1d173"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "investida",
    "recuar",
    "salto",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644918b86df9c8bbaa1d174"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564491d086df9c8bbaa1d175"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "investida",
    "recuar",
    "salto",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644923386df9c8bbaa1d176"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "investida",
    "recuar",
    "salto",
    "desvio"
  ]
}
{
  "_id": ObjectId("564c8dbd69e9e63d2bfbc38f"),
  "description": "Sem maiores informações",
  "name": "AindaNaoExisteMon",
  "attack": null,
  "height": null,
  "defense": null,
  "type": null,
  "moves": [ ]
}
Fetched 9 record(s) in 3ms

```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```
5e14de9d5d4e(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{moves: {$in: ['investida']}}, {defense: {$not: {$lte: 49}}}]}

5e14de9d5d4e(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564355fa17c6388471074b2d"),
  "name": "Eevee",
  "description": "There are a lot of evolutions",
  "attack": 55,
  "defense": 50,
  "height": 3,
  "type": "normal",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56435a5ba43104534c4cf01d"),
  "name": "Jolteon",
  "description": "Electric evolution",
  "attack": 65,
  "defense": 60,
  "height": 8,
  "type": "electric",
  "moves": [
    "investida",
    "desvio",
    "Revidar"
  ]
}
{
  "_id": ObjectId("56435a5ba43104534c4cf01e"),
  "name": "Flareon",
  "description": "Fire evolution",
  "attack": 130,
  "defense": 60,
  "height": 9,
  "type": "fire",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56435a5ba43104534c4cf01f"),
  "name": "Vaporeon",
  "description": "Water evolution",
  "attack": 65,
  "defense": 60,
  "height": 10,
  "type": "water",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56435a5ba43104534c4cf020"),
  "name": "Leafeon",
  "description": "Graas evolution",
  "attack": 110,
  "defense": 130,
  "height": 10,
  "type": "grass",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644910686df9c8bbaa1d172"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletrico",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "recuar",
    "salto",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644915586df9c8bbaa1d173"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "investida",
    "recuar",
    "salto",
    "desvio"
  ]
}
{
  "_id": ObjectId("564491d086df9c8bbaa1d175"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "investida",
    "recuar",
    "salto",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644923386df9c8bbaa1d176"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "investida",
    "recuar",
    "salto",
    "desvio"
  ]
}
Fetched 9 record(s) in 2ms


```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
5e14de9d5d4e(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{type: /água/i}, {attack: {$lt: 50}}]}

5e14de9d5d4e(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564491d086df9c8bbaa1d175"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "investida",
    "recuar",
    "salto",
    "desvio"
  ]
}
Fetched 1 record(s) in 8ms

5e14de9d5d4e(mongod-3.0.7) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 5ms
WriteResult({
  "nRemoved": 1
})

```

## Demonstre qual a diferença entre os operadores `$ne` e `$not`.
```
O operador `$not` é usando quando se deseja afetar(negar) outros operadores enquanto o `$ne` é usado para testar campos. Exemplos:

`{$not: {attack: {$lt: 50} } }` # O `$not` está negando o operador `$lt`.

`{attack: {$ne: 50} }` # O `$ne` esta testando o campo attack.

```