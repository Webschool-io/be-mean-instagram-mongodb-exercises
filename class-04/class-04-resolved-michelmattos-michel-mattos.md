# MongoDB - Aula 04 - Exercício
autor: Michel Mattos

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```javascript
> var query = { $or: [{name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbassauro/i}, {name: /charmander/i}] }
> var mod = { $pushAll: {moves: ['hadouken', 'shoryuken']} }
> var opt = { multi: 1 }
> db.pokemons.update(q, mod, opt)
Updated 4 existing record(s) in 7ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})

> db.pokemons.find(query)
{
  "_id": ObjectId("56480a2d29b9c62e120d5166"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "hadouken",
    "shoryuken"
  ],
  "active": false
}
{
  "_id": ObjectId("56480b3a29b9c62e120d5167"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "hadouken",
    "shoryuken"
  ]
}
{
  "_id": ObjectId("56480b6829b9c62e120d5168"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "hadouken",
    "shoryuken"
  ]
}
{
  "_id": ObjectId("56480b9429b9c62e120d5169"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "hadouken",
    "shoryuken"
  ]
}
Fetched 4 record(s) in 9ms
```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```javascript
> var mod = { $push: {moves: 'desvio'} }
> var opt = { multi: 1 }
> db.pokemons.update({}, mod, opt)
Updated 5 existing record(s) in 4ms
WriteResult({
  "nMatched": 5,
  "nUpserted": 0,
  "nModified": 5
})
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```javascript
> var query = { name: /aindanaoexistemon/i }
> var poke = { name: 'AindaNaoExisteMon', description: 'Sem maiores informações', type: null, attack: null, height: null, active: null, moves: null, defense: null }
> poke
{
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null,
  "active": null,
  "moves": null,
  "defense": null
}
> var mod = { $setOnInsert: poke }
> var opt = { upsert: 1 }
> db.pokemons.update(query, mod, opt)
Updated 1 new record(s) in 1ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564e81e982524e40d07eeb65")
})
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```javascript
> var query = { moves: {$all: [/investida/i, /hadouken/i]} }
> db.pokemons.find(query)
{
  "_id": ObjectId("56480b3a29b9c62e120d5167"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "hadouken",
    "shoryuken",
    "desvio"
  ]
}
{
  "_id": ObjectId("56480a2d29b9c62e120d5166"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "hadouken",
    "shoryuken",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("56480b6829b9c62e120d5168"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "hadouken",
    "shoryuken",
    "desvio"
  ]
}
{
  "_id": ObjectId("56480b9429b9c62e120d5169"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "hadouken",
    "shoryuken",
    "desvio"
  ]
}
Fetched 4 record(s) in 10ms

> var poke = db.pokemons.findOne({ name: /charmander/i })
> poke
{
  "_id": ObjectId("56480b6829b9c62e120d5168"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "hadouken",
    "shoryuken",
    "desvio"
  ]
}
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```javascript
> var query = { moves: {$all: [/shoryuken/i, /hadouken/i]} }
> db.pokemons.find(query)
{
  "_id": ObjectId("56480b3a29b9c62e120d5167"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "hadouken",
    "shoryuken",
    "desvio"
  ]
}
{
  "_id": ObjectId("56480a2d29b9c62e120d5166"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "hadouken",
    "shoryuken",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("56480b6829b9c62e120d5168"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "hadouken",
    "shoryuken",
    "desvio"
  ]
}
{
  "_id": ObjectId("56480b9429b9c62e120d5169"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "hadouken",
    "shoryuken",
    "desvio"
  ]
}
Fetched 4 record(s) in 11ms

> var poke = db.pokemons.findOne({ name: /charmander/i })
> poke
{
  "_id": ObjectId("56480b6829b9c62e120d5168"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "hadouken",
    "shoryuken",
    "desvio"
  ]
}
```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```javascript
> var query = { type: {$not: /eletric/i} }
> db.pokemons.find(query)
{
  "_id": ObjectId("56480b3a29b9c62e120d5167"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "hadouken",
    "shoryuken",
    "desvio"
  ]
}
{
  "_id": ObjectId("56480c9129b9c62e120d516a"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56480b6829b9c62e120d5168"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "hadouken",
    "shoryuken",
    "desvio"
  ]
}
{
  "_id": ObjectId("56480b9429b9c62e120d5169"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "hadouken",
    "shoryuken",
    "desvio"
  ]
}
{
  "_id": ObjectId("564e81e982524e40d07eeb65"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null,
  "active": null,
  "moves": null,
  "defense": null
}
Fetched 5 record(s) in 11ms
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```javascript
> var query = { moves: {$in: [/investida/i]}, defense: {$gt: 49} }
> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```javascript
> var query = { type: /água/i, attack: {$lt: 50} }
> db.pokemons.remove(query)
Removed 1 record(s) in 1ms
WriteResult({
  "nRemoved": 1
})
```