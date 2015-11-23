# MongoDB - Aula 04 - Exercício

autor: **Lucas Moreira**

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
var query = {name: {$in: [/pikachu/i, /squirtle/i, /charmander/i]}}
var options = {multi: true}
var mod = {$pushAll: {moves: ['Voadora cabulosa', 'Golpe maroto']}}
db.pokemons.update(query, mod, options)
Updated 3 existing record(s) in 8ms
WriteResult({
  "nMatched": 3,
  "nUpserted": 0,
  "nModified": 3
})

db.pokemons.find(query)
{
  "_id": ObjectId("5642723a76cb4bb0ef93cbb8"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "Voadora cabulosa",
    "Golpe maroto"
  ],
  "active": false
}
{
  "_id": ObjectId("564272c076cb4bb0ef93cbba"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "lança chamas",
    "Voadora cabulosa",
    "Golpe maroto"
  ]
}
{
  "_id": ObjectId("564272f276cb4bb0ef93cbbb"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "artive": true,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "Voadora cabulosa",
    "Golpe maroto"
  ]
}
Fetched 3 record(s) in 7ms
```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

```
var query = {}
options
{
  "multi": true
}
var mod = {$push: {moves: 'desvio'}}
db.pokemons.update(query, mod, options)
Updated 7 existing record(s) in 2ms
WriteResult({
  "nMatched": 7,
  "nUpserted": 0,
  "nModified": 7
})
db.pokemons.find()
{
  "_id": ObjectId("5642727676cb4bb0ef93cbb9"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5642744276cb4bb0ef93cbbc"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "heigth": 0.3,
  "defense": 35,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5649f8d3df5657464de14870"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564c80645726fe40b91cc241"),
  "artive": true,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5642723a76cb4bb0ef93cbb8"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "active": false,
  "moves": [
    "Voadora cabulosa",
    "Golpe maroto",
    "desvio"
  ]
}
{
  "_id": ObjectId("564272c076cb4bb0ef93cbba"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.5,
  "active": false,
  "moves": [
    "Voadora cabulosa",
    "Golpe maroto",
    "desvio"
  ]
}
{
  "_id": ObjectId("564272f276cb4bb0ef93cbbb"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "artive": true,
  "active": false,
  "moves": [
    "Voadora cabulosa",
    "Golpe maroto",
    "desvio"
  ]
}
Fetched 7 record(s) in 3ms
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

```
var query = {name: /AindaNaoExisteMon/i}
var mod = {$set: {active: true}, $setOnInsert: {name: 'AindaNaoExisteMon', attack: null, defense: null, height: null, description: 'Sem maiores informações'}}
var options = {upsert: true}
db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 3ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564ca7035726fe40b91cc243")
})
db.pokemons.find(query)
{
  "_id": ObjectId("564ca7035726fe40b91cc243"),
  "active": true,
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 1 record(s) in 1ms
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

```
var query = {moves: {$in: ['investida', /voadora cabulosa/i]}}
db.pokemons.find(query)
{
  "_id": ObjectId("5642723a76cb4bb0ef93cbb8"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "active": false,
  "moves": [
    "Voadora cabulosa",
    "Golpe maroto",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("564272c076cb4bb0ef93cbba"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.5,
  "active": false,
  "moves": [
    "Voadora cabulosa",
    "Golpe maroto",
    "desvio"
  ]
}
{
  "_id": ObjectId("564272f276cb4bb0ef93cbbb"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "artive": true,
  "active": false,
  "moves": [
    "Voadora cabulosa",
    "Golpe maroto",
    "desvio"
  ]
}
Fetched 3 record(s) in 3ms
```

**Meu Pokemon Favorito:** Pikachu.

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

```
var query = {moves: {$in: [/voadora cabulosa/i, /golpe maroto/i]}}
db.pokemons.find(query)
{
  "_id": ObjectId("5642723a76cb4bb0ef93cbb8"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "active": false,
  "moves": [
    "Voadora cabulosa",
    "Golpe maroto",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("564272c076cb4bb0ef93cbba"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.5,
  "active": false,
  "moves": [
    "Voadora cabulosa",
    "Golpe maroto",
    "desvio"
  ]
}
{
  "_id": ObjectId("564272f276cb4bb0ef93cbbb"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "artive": true,
  "active": false,
  "moves": [
    "Voadora cabulosa",
    "Golpe maroto",
    "desvio"
  ]
}
Fetched 3 record(s) in 8ms
```

**Meu Pokemon Favorito:** Pikachu.

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

```
var query = {type: {$ne: 'eletric'}}
db.pokemons.find(query)
{
  "_id": ObjectId("5642727676cb4bb0ef93cbb9"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5642744276cb4bb0ef93cbbc"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "heigth": 0.3,
  "defense": 35,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5649f8d3df5657464de14870"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564c80645726fe40b91cc241"),
  "artive": true,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564272c076cb4bb0ef93cbba"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.5,
  "active": false,
  "moves": [
    "Voadora cabulosa",
    "Golpe maroto",
    "desvio"
  ]
}
{
  "_id": ObjectId("564ca7035726fe40b91cc243"),
  "active": true,
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 6 record(s) in 8ms
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

```
var query = {$and: [{moves: {$in: ['investida']}}, {defense: {$not: {$lte: 49}}}]}
db.pokemons.find(query)
{
  "_id": ObjectId("5642723a76cb4bb0ef93cbb8"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "active": false,
  "moves": [
    "Voadora cabulosa",
    "Golpe maroto",
    "desvio",
    "investida"
  ]
}
Fetched 1 record(s) in 8ms
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
var query = {$and: [{type: /água/i}, {attack: {$lt: 50}}]}
db.pokemons.find(query)
{
  "_id": ObjectId("564272f276cb4bb0ef93cbbb"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "artive": true,
  "active": false,
  "moves": [
    "Voadora cabulosa",
    "Golpe maroto",
    "desvio"
  ]
}
db.pokemons.remove(query)
Removed 1 record(s) in 8ms
WriteResult({
  "nRemoved": 1
})
db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```

## Esse item não está no vídeo e se você fizer significa que você lê as coisas, nesse exercício demonstre qual a diferença entre os operadores $ne e $not.

```
$ne: (Not Equals - Diferente) não funciona com regex.
$not: (Operador Lógico de Negação) funciona somente regex ou com documentos.
```
