# MongoDB - Aula 04 - Exercício
autor: Bruno Russi Lautenschlager

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```js
> var query = {name: /Pikachu/i}
> var mod = {$pushAll: {moves: ['esfera elétrica', 'investida trovão']}}
> db.pokemons.update(query, mod)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })

> var query = {name: /Squirtle/i}
> var mod = {$pushAll: {moves: ['raio de gelo', 'giro rápido']}}
> db.pokemons.update(query, mod)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })


> var query = {name: /Bulbassauro/i}
> var mod = {$pushAll: {moves: ['raio solar', 'dança de pétalas']}}
> db.pokemons.update(query, mod)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })

> var query = {name: /Charmander/i}
> var mod = {$pushAll: {moves: ['brasas', 'encarar']}}
> db.pokemons.update(query, mod)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.

```js
> var query = {}
> var mod = {$push: {moves: 'desvio'}}
> var options = {multi: true}
> db.pokemons.update(query, mod, options)
WriteResult({ "nMatched" : 9, "nUpserted" : 0, "nModified" : 9 })
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".

```js
debian(mongod-3.0.7) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}
debian(mongod-3.0.7) be-mean-pokemons> var mod = {$setOnInsert:
  {
    name: 'AindaNaoExisteMon',
    type: null,
    attack: null,
    defense: null,
    height: null,
    description: 'Sem maiores informações'
   }
}
debian(mongod-3.0.7) be-mean-pokemons> var options = {upsert: true}
debian(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 30ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("56dd10c733a2be335b535c26")
})
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.

```js
debian(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$in: [/investida/i, /esfera elétrica/i]}}
debian(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56dcbe46874e289e60d249c0"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "esfera elétrica",
    "investida trovão",
    "desvio"
  ]
}
Fetched 1 record(s) in 1ms
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```js
debian(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$all: [/desvio/i, /esfera elétrica/i]}}
debian(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56dcbe46874e289e60d249c0"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "esfera elétrica",
    "investida trovão",
    "desvio"
  ]
}
Fetched 1 record(s) in 1ms
```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.

```js
debian(mongod-3.0.7) be-mean-pokemons> var query = {type: {$not: /elétrico/i}}
debian(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56dc9a7a20c79beeb285f0ec"),
  "name": "BobMom",
  "description": "Pokemon bob marley",
  "type": "chapado",
  "attack": 420,
  "defense": 420,
  "height": 4.2,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56dc9a7a20c79beeb285f0ed"),
  "name": "LockMom",
  "description": "Pokemon lock",
  "type": "loko",
  "attack": 100,
  "defense": 10,
  "height": 1.3,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56dc9a7a20c79beeb285f0ee"),
  "name": "SanoMom",
  "description": "pokemon sandia saia",
  "type": "San",
  "attack": 666,
  "defense": 978,
  "height": 1.9,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56dc9a7a20c79beeb285f0ef"),
  "name": "OxiMom",
  "description": "Pokemom paraiba",
  "type": "paraiba",
  "attack": 897,
  "defense": 784,
  "height": 1.6,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56dc9a7a20c79beeb285f0f0"),
  "name": "chikungunya",
  "description": "Passa peste pra geral",
  "type": "peste",
  "attack": 666,
  "defense": 666,
  "height": 1.87,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56dcbe9c874e289e60d249c1"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "raio solar",
    "dança de pétalas",
    "desvio"
  ]
}
{
  "_id": ObjectId("56dcbeaf874e289e60d249c2"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "brasas",
    "encarar",
    "desvio"
  ]
}
{
  "_id": ObjectId("56dcbfa4874e289e60d249c3"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "raio de gelo",
    "giro rápido",
    "desvio"
  ]
}
{
  "_id": ObjectId("56dcc639874e289e60d249c4"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "height": 2.1
}
{
  "_id": ObjectId("56dd10c733a2be335b535c26"),
  "name": "AindaNaoExisteMon",
  "type": null,
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 10 record(s) in 9ms
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.

**Se você não tiver Pokemons com valores de `defense` então faça a query para o campo `attack`, como feito abaixo:**

```js
debian(mongod-3.0.7) be-mean-pokemons> var query = {$and: [ {moves: {$in: ['investida']}}, {attack: {$not: {$lte: 49}}} ]}
debian(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms

debian(mongod-3.0.7) be-mean-pokemons> var query = {$and: [ {moves: {$in: ['investida']}}, {defense: {$not: {$lte: 49}}} ]}
debian(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms

```

## Remova **todos** os pokemons do tipo água E com attack menor que 50.

```js
debian(mongod-3.0.7) be-mean-pokemons> var query = {$and: [ {type: /água/i}, {attack: {$lt: 50}} ]}
debian(mongod-3.0.7) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 13ms
WriteResult({
  "nRemoved": 1
})
```
