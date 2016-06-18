# MongoDB - Aula 04 - Exercício
autor: Cleyton Antonio dos Santos

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbasauro e Charmander.

```
var query = {$or: [{name: /Pikachu/i}, {name: /Squirtle/i}, {name: /Bulbasauro/i}, {name: /Charmander/i}]}
var mod = {$pushAll: {moves: ["Investida", "Metamorfose", "Fúria"]}}
var options = {multi: 1}

stunerx(mongod-2.6.10) be-mean-pokemons> db.pokemons.update(query, mod, options)

Updated 4 existing record(s) in 6ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})


```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.

```
var query = {"_id": ObjectId("5764a08d6123f59178c65289")}
var mod = {$push: {moves: "Raio do trovão"}}
var options = {multi: 1}

var query = {"_id": ObjectId("5764a08d6123f59178c6528a")}
var mod = {$push: {moves: "Fogo do vulcão"}}
var options = {multi: 1}

var query = {"_id": ObjectId("5764a08d6123f59178c6528b")}
var mod = {$push: {moves: "Chicote da floresta"}}
var options = {multi: 1}

var query = {"_id": ObjectId("5764a08d6123f59178c6528c")}
var mod = {$push: {moves: "Jato do tsunami"}}
var options = {multi: 1}

stunerx(mongod-2.6.10) be-mean-pokemons> db.pokemons.update(query, mod, options)

Updated 9 existing record(s) in 16ms
WriteResult({
  "nMatched": 9,
  "nUpserted": 0,
  "nModified": 9
})



```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".

```
var query = {name:/AindaNaoExisteMon/i}

var mod = {$set:{active:true}, $setOnInsert:{name :null, attack: null, defense: null, height: null, description: 'Sem maiores informações'}}

var options = {upsert:true}

stunerx(mongod-2.6.10) be-mean-pokemons> db.pokemons.update(query,mod,options)

Updated 1 new record(s) in 7ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("5764a56efffef3b70b4e3c3b")
})


```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.

```
var query = {moves: {$all: [/jato do tsunami/i, /fogo do vulcão/i]}}
db.pokemons.find(query);

stunerx(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("5764a08d6123f59178c6528a"),
  "name": "Charmander",
  "description": "O mais mitologico dos pokemons",
  "type": "fogo",
  "attack": 3,
  "height": 0.6,
  "moves": [
    "Desvio",
    "Investida",
    "Metamorfose",
    "Fúria",
    "Fogo do vulcão"
  ]
}
Fetched 1 record(s) in 5ms



```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```
var query = {moves: {$in: [/fúria/i]}}
stunerx(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("5764a08d6123f59178c6528a"),
  "name": "Charmander",
  "description": "O mais mitologico dos pokemons",
  "type": "fogo",
  "attack": 3,
  "height": 0.6,
  "moves": [
    "Desvio",
    "Investida",
    "Metamorfose",
    "Fúria",
    "Fogo do vulcão"
  ]
}
{
  "_id": ObjectId("5764a08d6123f59178c6528b"),
  "name": "Bulbasauro",
  "description": "Tem uma semente nas costas",
  "type": "grama",
  "attack": 3,
  "height": 0.7,
  "moves": [
    "Desvio",
    "Investida",
    "Metamorfose",
    "Fúria",
    "Chicote da floresta"
  ]
}
{
  "_id": ObjectId("5764a08d6123f59178c65289"),
  "name": "Pikachu",
  "description": "Solta raio memo",
  "type": "eletrico",
  "attack": 3,
  "height": 0.4,
  "moves": [
    "Desvio",
    "Investida",
    "Metamorfose",
    "Fúria",
    "Raio do trovão"
  ]
}
{
  "_id": ObjectId("5764a08d6123f59178c6528c"),
  "name": "Squirtle",
  "description": "Nada pra caraio",
  "type": "agua",
  "attack": 3,
  "height": 0.5,
  "moves": [
    "Desvio",
    "Investida",
    "Metamorfose",
    "Fúria",
    "Jato do tsunami"
  ]
}
Fetched 4 record(s) in 4ms

```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.

```
var query = {type: {$not: /eletrico/i}}
stunerx(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("57643a3ad7ba6d657212bc44"),
  "name": "Metapod",
  "description": "The shell covering this Pokémon's body is as hard as an iron slab",
  "type": "inseto",
  "attack": 1,
  "height": 0.7,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("57643a3ad7ba6d657212bc45"),
  "name": "Pidgey",
  "description": "Pidgey tem um extremo senso de direção",
  "type": "voador",
  "attack": 2,
  "height": 0.3,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("57643a3ad7ba6d657212bc46"),
  "name": "Jigglypuff",
  "description": "Esse pokemon pode cantar",
  "type": "fada",
  "attack": 2,
  "height": 0.5,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("57643a3ad7ba6d657212bc47"),
  "name": "Growlithe",
  "description": "Cachorro louco monstrão",
  "type": "fogo",
  "attack": 4,
  "height": 0.7,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("57643a3ad7ba6d657212bc48"),
  "name": "Psyduck",
  "description": "Psyduck tem um poder misterioso",
  "type": "agua",
  "attack": 3,
  "height": 0.8,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("5764a08d6123f59178c6528a"),
  "name": "Charmander",
  "description": "O mais mitologico dos pokemons",
  "type": "fogo",
  "attack": 3,
  "height": 0.6,
  "moves": [
    "Desvio",
    "Investida",
    "Metamorfose",
    "Fúria",
    "Fogo do vulcão"
  ]
}
{
  "_id": ObjectId("5764a08d6123f59178c6528b"),
  "name": "Bulbasauro",
  "description": "Tem uma semente nas costas",
  "type": "grama",
  "attack": 3,
  "height": 0.7,
  "moves": [
    "Desvio",
    "Investida",
    "Metamorfose",
    "Fúria",
    "Chicote da floresta"
  ]
}
{
  "_id": ObjectId("5764a08d6123f59178c6528c"),
  "name": "Squirtle",
  "description": "Nada pra caraio",
  "type": "agua",
  "attack": 3,
  "height": 0.5,
  "moves": [
    "Desvio",
    "Investida",
    "Metamorfose",
    "Fúria",
    "Jato do tsunami"
  ]
}
{
  "_id": ObjectId("5764a56efffef3b70b4e3c3b"),
  "active": true,
  "name": null,
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações",
  "moves": [
    "Desvio"
  ]
}
Fetched 9 record(s) in 7ms


```

## Pesquisar **todos** pokemons que tenham o ataque `investida` **E** tenham a attack **não menor ou igual** a 1.

```
var query = {$and: [{moves: {$all: [/investida/i]}, attack: {$lte: 3}}]}

stunerx(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("5764a08d6123f59178c6528a"),
  "name": "Charmander",
  "description": "O mais mitologico dos pokemons",
  "type": "fogo",
  "attack": 3,
  "height": 0.6,
  "moves": [
    "Desvio",
    "Investida",
    "Metamorfose",
    "Fúria",
    "Fogo do vulcão"
  ]
}
{
  "_id": ObjectId("5764a08d6123f59178c6528b"),
  "name": "Bulbasauro",
  "description": "Tem uma semente nas costas",
  "type": "grama",
  "attack": 3,
  "height": 0.7,
  "moves": [
    "Desvio",
    "Investida",
    "Metamorfose",
    "Fúria",
    "Chicote da floresta"
  ]
}
{
  "_id": ObjectId("5764a08d6123f59178c65289"),
  "name": "Pikachu",
  "description": "Solta raio memo",
  "type": "eletrico",
  "attack": 3,
  "height": 0.4,
  "moves": [
    "Desvio",
    "Investida",
    "Metamorfose",
    "Fúria",
    "Raio do trovão"
  ]
}
{
  "_id": ObjectId("5764a08d6123f59178c6528c"),
  "name": "Squirtle",
  "description": "Nada pra caraio",
  "type": "agua",
  "attack": 3,
  "height": 0.5,
  "moves": [
    "Desvio",
    "Investida",
    "Metamorfose",
    "Fúria",
    "Jato do tsunami"
  ]
}
Fetched 4 record(s) in 3ms

```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
var query = {$and: [{type: /agua/i, attack: {$lt: 50}}]}
stunerx(mongod-2.6.10) be-mean-pokemons> db.pokemons.remove(query)
Removed 2 record(s) in 26ms
WriteResult({
  "nRemoved": 2
})


```