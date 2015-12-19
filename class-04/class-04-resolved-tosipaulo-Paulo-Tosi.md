# MongoDB - Aula 04 - Exercício
autor: Paulo Tosi

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```javascript

var query = {$or : [{name: /arbok/i}, {name: /tossimon/i}]}

var attacks = ['investida', 'ataque rapido']

var mod = {$pushAll: {moves: attacks}}

var options = {multi: true}

db.pokemons.update(query, mod, options)

Updated 2 existing record(s) in 7ms
WriteResult({
  "nMatched": 2,
  "nUpserted": 0,
  "nModified": 2
})


```


## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

```javascript

var  query = {}

var mod = {$push: {moves: 'desvio'}}

var options = {multi: true}

db.pokemons.update(query, mod, options)

Updated 7 existing record(s) in 9ms
WriteResult({
  "nMatched": 7,
  "nUpserted": 0,
  "nModified": 7
})


```


## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

```javascript

var query = {/AindaNaoExisteMon/i}

var mod = {

    $setOnInsert : {
        name: 'AindaNaoExisteMon',
        description: 'Sem maiores informações',
        type: null,
        attack: null,
        defense: null,
        height: null
    }
}

var options = {upsert: true}

db.pokemons.update(query, mod, options)

Updated 1 new record(s) in 17ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564f4120d45c4e209a14f311")
})


```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

```javascript

var query = {moves: {$in: [/investida/i, /ataque rapido/i]}}

db.pokemons.find(query)

{
  "_id": ObjectId("5643fb9ee267de8e396719b3"),
  "name": "Fearow",
  "description": "passaro locao",
  "type": "passaro",
  "attack": 50,
  "defense": 30,
  "height": 1.2,
  "moves": [
    "investida",
    "ataque rapido",
    "desvio"
  ]
}
{
  "_id": ObjectId("5643fb9ee267de8e396719b4"),
  "name": "Arbok",
  "description": "Um cobra na ver",
  "type": "cobra",
  "attack": 40,
  "defense": 100,
  "height": 3.5,
  "moves": [
    "investida",
    "ataque rapido",
    "desvio"
  ]
}
{
  "_id": ObjectId("5643fb9ee267de8e396719b5"),
  "name": "Raticate",
  "description": "Rato estranho",
  "type": "rato",
  "attack": 40,
  "defense": 100,
  "height": 0.7,
  "moves": [
    "investida",
    "ataque rapido",
    "desvio"
  ]
}
{
  "_id": ObjectId("564e9d52f0a4ade03cc0ceea"),
  "name": "Tossimon",
  "description": "Marinheiro de primeira viagem no mean",
  "type": "Geek",
  "attack": 100,
  "defense": 90,
  "height": 1.7,
  "moves": [
    "investida",
    "ataque rapido",
    "desvio"
  ]
}
Fetched 4 record(s) in 7ms



```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

```javascript

var query = {moves: {$in: [/investida/i, /ataque rapido/i]}}

db.pokemons.find(query)

{
  "_id": ObjectId("5643fb9ee267de8e396719b3"),
  "name": "Fearow",
  "description": "passaro locao",
  "type": "passaro",
  "attack": 50,
  "defense": 30,
  "height": 1.2,
  "moves": [
    "investida",
    "ataque rapido",
    "desvio"
  ]
}
{
  "_id": ObjectId("5643fb9ee267de8e396719b4"),
  "name": "Arbok",
  "description": "Um cobra na ver",
  "type": "cobra",
  "attack": 40,
  "defense": 100,
  "height": 3.5,
  "moves": [
    "investida",
    "ataque rapido",
    "desvio"
  ]
}
{
  "_id": ObjectId("5643fb9ee267de8e396719b5"),
  "name": "Raticate",
  "description": "Rato estranho",
  "type": "rato",
  "attack": 40,
  "defense": 100,
  "height": 0.7,
  "moves": [
    "investida",
    "ataque rapido",
    "desvio"
  ]
}
{
  "_id": ObjectId("564e9d52f0a4ade03cc0ceea"),
  "name": "Tossimon",
  "description": "Marinheiro de primeira viagem no mean",
  "type": "Geek",
  "attack": 100,
  "defense": 90,
  "height": 1.7,
  "moves": [
    "investida",
    "ataque rapido",
    "desvio"
  ]
}
Fetched 4 record(s) in 7ms



```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

```javascript

var query = {type: {$nin: [/eletrico/i]}}

db.pokemons.find(query)

{
  "_id": ObjectId("5643fb9ee267de8e396719b3"),
  "name": "Fearow",
  "description": "passaro locao",
  "type": "passaro",
  "attack": 50,
  "defense": 30,
  "height": 1.2,
  "moves": [
    "investida",
    "ataque rapido",
    "desvio"
  ]
}
{
  "_id": ObjectId("5643fb9ee267de8e396719b4"),
  "name": "Arbok",
  "description": "Um cobra na ver",
  "type": "cobra",
  "attack": 40,
  "defense": 100,
  "height": 3.5,
  "moves": [
    "investida",
    "ataque rapido",
    "desvio"
  ]
}
{
  "_id": ObjectId("5643fb9ee267de8e396719b5"),
  "name": "Raticate",
  "description": "Rato estranho",
  "type": "rato",
  "attack": 40,
  "defense": 100,
  "height": 0.7,
  "moves": [
    "investida",
    "ataque rapido",
    "desvio"
  ]
}
{
  "_id": ObjectId("5643fb9ee267de8e396719b6"),
  "name": "Dilma",
  "description": "Uma filha da puta",
  "type": "Ladrão",
  "attack": 13,
  "defense": 100,
  "height": 1.3,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5643fb9ee267de8e396719b7"),
  "name": "PT",
  "description": "banco de filha da puta, cuzão do caralho",
  "type": "Ladrao",
  "attack": 13,
  "defense": 100,
  "height": 1.3,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564e9d52f0a4ade03cc0ceea"),
  "name": "Tossimon",
  "description": "Marinheiro de primeira viagem no mean",
  "type": "Geek",
  "attack": 100,
  "defense": 90,
  "height": 1.7,
  "moves": [
    "investida",
    "ataque rapido",
    "desvio"
  ]
}
{
  "_id": ObjectId("564f4120d45c4e209a14f311"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "defense": null,
  "height": null,
  "moves": [
    "desvio"
  ]
}
Fetched 7 record(s) in 6ms



```


## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

```javascript

var query  = {$and:[{moves: {$in: [/investida/i]}}, {defense: {$not: {$lte:49}}}]}

db.pokemons.find(query)

{
  "_id": ObjectId("5643fb9ee267de8e396719b4"),
  "name": "Arbok",
  "description": "Um cobra na ver",
  "type": "cobra",
  "attack": 40,
  "defense": 100,
  "height": 3.5,
  "moves": [
    "investida",
    "ataque rapido",
    "desvio"
  ]
}
{
  "_id": ObjectId("5643fb9ee267de8e396719b5"),
  "name": "Raticate",
  "description": "Rato estranho",
  "type": "rato",
  "attack": 40,
  "defense": 100,
  "height": 0.7,
  "moves": [
    "investida",
    "ataque rapido",
    "desvio"
  ]
}
{
  "_id": ObjectId("564e9d52f0a4ade03cc0ceea"),
  "name": "Tossimon",
  "description": "Marinheiro de primeira viagem no mean",
  "type": "Geek",
  "attack": 100,
  "defense": 90,
  "height": 1.7,
  "moves": [
    "investida",
    "ataque rapido",
    "desvio"
  ]
}

Fetched 3 record(s) in 3ms

```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.

```javascript

var query  = {$and:[{type: /agua/i}, {attack: {$lt:49}}]}

db.pokemons.remove(query)

WriteResult({
  "nRemoved": 0
})

```
