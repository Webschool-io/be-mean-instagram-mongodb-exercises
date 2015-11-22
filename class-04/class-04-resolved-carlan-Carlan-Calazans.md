# MongoDB - Aula 04 - Exercício
autor: Carlan Calazans

## Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e509"),
  "name": "Pikachu",
  "description": "Descricao modificada",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "defense": 34
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50a"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defense": 45
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50b"),
  "name": "Charmander",
  "description": "Esse é o co chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "defense": 14
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50c"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho no bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "defense": 67
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50d"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 22
}
Fetched 5 record(s) in 72ms
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> var q = { name: { $in: [ /Pikachu/, /Squirtle/, /Bulbassauro/, /Charmander/ ] } }
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> var m = { $pushAll: { moves: [ 'Soco', 'Chute' ] } }
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> var o = { multi:true }
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(q, m, o)
Updated 4 existing record(s) in 184ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(q)
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e509"),
  "name": "Pikachu",
  "description": "Descricao modificada",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "defense": 34,
  "moves": [
    "Soco",
    "Chute"
  ]
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50a"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defense": 45,
  "moves": [
    "Soco",
    "Chute"
  ]
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50b"),
  "name": "Charmander",
  "description": "Esse é o co chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "defense": 14,
  "moves": [
    "Soco",
    "Chute"
  ]
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50c"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho no bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "defense": 67,
  "moves": [
    "Soco",
    "Chute"
  ]
}
Fetched 4 record(s) in 5ms
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e509"),
  "name": "Pikachu",
  "description": "Descricao modificada",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "defense": 34,
  "moves": [
    "Soco",
    "Chute"
  ]
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50a"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defense": 45,
  "moves": [
    "Soco",
    "Chute"
  ]
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50b"),
  "name": "Charmander",
  "description": "Esse é o co chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "defense": 14,
  "moves": [
    "Soco",
    "Chute"
  ]
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50c"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho no bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "defense": 67,
  "moves": [
    "Soco",
    "Chute"
  ]
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50d"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 22
}
Fetched 5 record(s) in 3ms
```

## Adicionar 1 movimento em todos os pokemons: desvio.

```
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> var q = {}
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> var m = { $push: { moves: 'Desvio' } }
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> var o = { multi:true }
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(q, m, o)
Updated 5 existing record(s) in 2ms
WriteResult({
  "nMatched": 5,
  "nUpserted": 0,
  "nModified": 5
})
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(q)
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e509"),
  "name": "Pikachu",
  "description": "Descricao modificada",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "defense": 34,
  "moves": [
    "Soco",
    "Chute",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50a"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defense": 45,
  "moves": [
    "Soco",
    "Chute",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50b"),
  "name": "Charmander",
  "description": "Esse é o co chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "defense": 14,
  "moves": [
    "Soco",
    "Chute",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50c"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho no bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "defense": 67,
  "moves": [
    "Soco",
    "Chute",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50d"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 22,
  "moves": [
    "Desvio"
  ]
}
Fetched 5 record(s) in 2ms
```

## Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".

```
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> var q = { name : /AindaNaoExisteMon/ }
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(q)
Fetched 0 record(s) in 208ms
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> var poke = { name: 'AindaNaoExisteMon', type: null, attack: null, height: null, defense: null, moves: [], description: 'Sem maiores informacoes' }
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> var o = { upsert: true }
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(q, poke, o)
Updated 1 new record(s) in 1ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564fb6c478c4918f5df30d2f")
})
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(q)
{
  "_id": ObjectId("564fb6c478c4918f5df30d2f"),
  "name": "AindaNaoExisteMon",
  "type": null,
  "attack": null,
  "height": null,
  "defense": null,
  "moves": [ ],
  "description": "Sem maiores informacoes"
}
Fetched 1 record(s) in 0ms
```

## Pesquisar todos o pokemons que possuam o ataque desvio (era investida) e mais um que você adicionou, escolha seu pokemon favorito.

```
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> var q = { moves: { $all: [/desvio/i, /soco/i] } }
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(q)
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e509"),
  "name": "Pikachu",
  "description": "Descricao modificada",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "defense": 34,
  "moves": [
    "Soco",
    "Chute",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50a"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defense": 45,
  "moves": [
    "Soco",
    "Chute",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50b"),
  "name": "Charmander",
  "description": "Esse é o co chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "defense": 14,
  "moves": [
    "Soco",
    "Chute",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50c"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho no bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "defense": 67,
  "moves": [
    "Soco",
    "Chute",
    "Desvio"
  ]
}
Fetched 4 record(s) in 6ms
```

## Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> var q = { moves: { $all: [/soco/i, /chute/i, /desvio/i] } }
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(q)
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e509"),
  "name": "Pikachu",
  "description": "Descricao modificada",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "defense": 34,
  "moves": [
    "Soco",
    "Chute",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50a"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defense": 45,
  "moves": [
    "Soco",
    "Chute",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50b"),
  "name": "Charmander",
  "description": "Esse é o co chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "defense": 14,
  "moves": [
    "Soco",
    "Chute",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50c"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho no bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "defense": 67,
  "moves": [
    "Soco",
    "Chute",
    "Desvio"
  ]
}
Fetched 4 record(s) in 2ms
```

## Pesquisar todos os pokemons que não são do tipo elétrico.

```
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> var q = { type: { $nin: [/eletric/i] } }
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(q)
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50a"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defense": 45,
  "moves": [
    "Soco",
    "Chute",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50b"),
  "name": "Charmander",
  "description": "Esse é o co chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "defense": 14,
  "moves": [
    "Soco",
    "Chute",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50c"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho no bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "defense": 67,
  "moves": [
    "Soco",
    "Chute",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50d"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 22,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564fb6c478c4918f5df30d2f"),
  "name": "AindaNaoExisteMon",
  "type": null,
  "attack": null,
  "height": null,
  "defense": null,
  "moves": [ ],
  "description": "Sem maiores informacoes"
}
Fetched 5 record(s) in 2ms
```

## Pesquisar todos pokemons que tenham o ataque desvio (era investida) E tenham a defesa não menor ou igual a 49.

```
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> var q = { $and: [ { moves: { $in: [/desvio/i] } }, { defense: { $not: { $lte: 49 } } } ] }
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(q)
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50c"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho no bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "defense": 67,
  "moves": [
    "Soco",
    "Chute",
    "Desvio"
  ]
}
Fetched 1 record(s) in 59ms
```

## Remova todos os pokemons do tipo água e com attack menor que 50.

```
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> var q = { $and: [ { type: { $in: [/água/i] } }, { attack: { $lt: 50 } } ] }
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.remove(q)
Removed 1 record(s) in 582ms
WriteResult({
  "nRemoved": 1
})
```

## Nesse exercício demonstre qual a diferença entre os operadores $ne e $not.

```
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> var q = { name: { $eq: 'Pikachu'} }
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(q)
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e509"),
  "name": "Pikachu",
  "description": "Descricao modificada",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "defense": 34,
  "moves": [
    "Soco",
    "Chute",
    "Desvio"
  ]
}
Fetched 1 record(s) in 27ms
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> var qne = { name: { $ne: 'Pikachu' } }
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(qne)
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50a"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defense": 45,
  "moves": [
    "Soco",
    "Chute",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50b"),
  "name": "Charmander",
  "description": "Esse é o co chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "defense": 14,
  "moves": [
    "Soco",
    "Chute",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50d"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 22,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564fb6c478c4918f5df30d2f"),
  "name": "AindaNaoExisteMon",
  "type": null,
  "attack": null,
  "height": null,
  "defense": null,
  "moves": [ ],
  "description": "Sem maiores informacoes"
}
Fetched 4 record(s) in 1ms
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> var qnot = { name: { $not: { $eq: 'Pikachu'} } }
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(qnot)
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50a"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defense": 45,
  "moves": [
    "Soco",
    "Chute",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50b"),
  "name": "Charmander",
  "description": "Esse é o co chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "defense": 14,
  "moves": [
    "Soco",
    "Chute",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50d"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 22,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564fb6c478c4918f5df30d2f"),
  "name": "AindaNaoExisteMon",
  "type": null,
  "attack": null,
  "height": null,
  "defense": null,
  "moves": [ ],
  "description": "Sem maiores informacoes"
}
Fetched 4 record(s) in 5ms

bemeaninstagram(mongod-3.0.7) be-mean-pokemons> var qnot2 = { name: { $not: /pikachu/i } }
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(qnot2)
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50a"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defense": 45,
  "moves": [
    "Soco",
    "Chute",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50b"),
  "name": "Charmander",
  "description": "Esse é o co chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "defense": 14,
  "moves": [
    "Soco",
    "Chute",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b8a7e89cbf7e2a621e50d"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 22,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564fb6c478c4918f5df30d2f"),
  "name": "AindaNaoExisteMon",
  "type": null,
  "attack": null,
  "height": null,
  "defense": null,
  "moves": [ ],
  "description": "Sem maiores informacoes"
}
Fetched 4 record(s) in 2ms
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> var qnoterr = { name: { $not: 'Pikachu' } }
bemeaninstagram(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(qnoterr)
Error: error: {
  "$err": "Can't canonicalize query: BadValue $not needs a regex or a document",
  "code": 17287
}
```

Resumindo:

1) `$ne` não necessita de nenhum operador para negar. O foco deste operador é o valor do campo.
2) `$not` necessita de um operador para negar. O foco é um operador antecessor.
2.1) Uma regex pode ser considerado como um operador de igualdade.