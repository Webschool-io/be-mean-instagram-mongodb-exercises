# MongoDB - Aula 04 - Exercício
> Autor: Nil Késede

## Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Blastoise, Bulbasaur e Charizard
```js
> var query = { name: /pikachu/i }
> var mod = { $pushAll: { moves:  ['choque do trovão', 'bola elétrica'] } }
> db.pokemons.update(query, mod)
>
> var query = { name: /blastoise/i }
> var mod = { $pushAll: { moves:  ['pistola de água', 'chicote da cauda'] } }
> db.pokemons.update(query, mod)
>
> var query = { name: /bulbasaur/i }
> var mod = { $pushAll: { moves:  ['folha tempestade', 'folha magica'] } }
> db.pokemons.update(query, mod)
>
> var query = { name: /charizard/i}
> var mod = { $pushAll: { moves:  ['rosnar', 'estouro de chama'] } }
> db.pokemons.update(query, mod)
```

## Adicionar 1 movimento em todos os pokemons: `desvio`
```js
> var query = {}
> var mod = { $push: { moves: 'desvio' } }
> var options = { multi: true }
> db.pokemons.update(query, mod, options)
Updated 7 existing record(s) in 1ms
WriteResult({
  "nMatched": 7,
  "nUpserted": 0,
  "nModified": 7
})
```

## Adicionar o Pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações"
```js
> var query = { name: /AindaNaoExisteMon/i }
> var mod = {
    $setOnInsert: {
        name: 'AindaNaoExisteMon',
        attack: null,
        defense: null,
        height: null,
        description: 'Sem maiores informações'
    }
}
> var options = { upsert: true }
> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 2ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("56d874f6d1dc39da12f703df")
})
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito
```js
> var query = { moves: { $in: [/investida/i, /choque do trovão/i] } }
> db.pokemons.find(query)
{
  "_id": ObjectId("564b1db125337263280d04a7"),
  "attack": 55,
  "created": "2013-11-03T15:05:41.317235",
  "defense": 40,
  "height": "4",
  "hp": 35,
  "name": "Pikachu",
  "speed": 90,
  "types": [
    "electric"
  ],
  "moves": [
    "choque do trovão",
    "bola elétrica",
    "desvio"
  ]
}
Fetched 1 record(s) in 3ms
```

## Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito
```js
> var query = {
    moves: {
        $all: [/desvio/i, /folha tempestade/i]
    }
}
> db.pokemons.find(query)
{
  "_id": ObjectId("564b1de325337263280d068c"),
  "attack": 49,
  "created": "2013-11-03T15:05:41.260678",
  "defense": 49,
  "height": "7",
  "hp": 45,
  "name": "Bulbasaur",
  "speed": 45,
  "types": [
    "poison",
    "grass"
  ],
  "moves": [
    "folha tempestade",
    "folha magica",
    "desvio"
  ]
}
Fetched 1 record(s) in 1ms
```

## Pesquisar todos os pokemons que não são do tipo `elétrico`
```js
> var query = { type: { $not: /elétrico/i } }
> db.pokemons.find(query)
{
  "_id": ObjectId("56d86019fbf65093d68eab03"),
  "name": "Bulbasaur",
  "description": "Pokemon fofinho que solta umas folha envenenada",
  "type": "Grama",
  "atack": 49,
  "defense": 49,
  "height": 7,
  "moves": [
    "investida",
    "defender",
    "desvio"
  ]
}
{
  "_id": ObjectId("56d86019fbf65093d68eab04"),
  "name": "Charizard",
  "description": "Dragão boladão",
  "type": "Fogo",
  "attack": 84,
  "defense": 78,
  "height": 17,
  "moves": [
    "investida",
    "defender",
    "desvio"
  ]
}
{
  "_id": ObjectId("56d86019fbf65093d68eab05"),
  "name": "Blastoise",
  "description": "Tem uns canhão de água nas costas foda pra carai",
  "type": "Água",
  "attack": 83,
  "defense": 100,
  "height": 16,
  "moves": [
    "investida",
    "defender",
    "desvio"
  ]
}
{
  "_id": ObjectId("56d86019fbf65093d68eab07"),
  "name": "Snorlax",
  "description": "Pokemon dorminhoco",
  "type": "Normal",
  "attack": 110,
  "defense": 65,
  "height": 21,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56d86019fbf65093d68eab08"),
  "name": "Psyduck",
  "description": "Pato loko de droga",
  "type": "Água",
  "attack": 52,
  "defense": 48,
  "height": 8,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56d86019fbf65093d68eab09"),
  "name": "Onix",
  "description": "Cobra de pedra gigante",
  "type": "Água",
  "attack": 45,
  "defense": 160,
  "height": 88,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56d874f6d1dc39da12f703df"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 7 record(s) in 5ms
```

## Pesquisar todos os Pokemons que tenham o ataque `investida` e tenham a defesa não menor ou igual a `49`
```js
> var query = {
    $and: [
        {
            moves: { $in: [/investida/i] } },
            { attack: { $not: { $lte: 49 } }
        }
    ]
}
> db.pokemons.find(query)
{
  "_id": ObjectId("56d86019fbf65093d68eab03"),
  "name": "Bulbasaur",
  "description": "Pokemon fofinho que solta umas folha envenenada",
  "type": "Grama",
  "atack": 49,
  "defense": 49,
  "height": 7,
  "moves": [
    "investida",
    "defender",
    "desvio"
  ]
}
{
  "_id": ObjectId("56d86019fbf65093d68eab04"),
  "name": "Charizard",
  "description": "Dragão boladão",
  "type": "Fogo",
  "attack": 84,
  "defense": 78,
  "height": 17,
  "moves": [
    "investida",
    "defender",
    "desvio"
  ]
}
{
  "_id": ObjectId("56d86019fbf65093d68eab05"),
  "name": "Blastoise",
  "description": "Tem uns canhão de água nas costas foda pra carai",
  "type": "Água",
  "attack": 83,
  "defense": 100,
  "height": 16,
  "moves": [
    "investida",
    "defender",
    "desvio"
  ]
}
{
  "_id": ObjectId("56d86019fbf65093d68eab06"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "Elétrico",
  "attack": 55,
  "defense": 40,
  "height": 4,
  "moves": [
    "investida",
    "defender",
    "desvio",
    "choque eletrico"
  ]
}
Fetched 4 record(s) in 2ms
```

## Remova todos os pokemons do tipo `água` e com attack menor que `50`
```js
> var query = {
    $and: [
        { type: /água/i },
        { attack: { $lt: 50 } }
    ]
}
> db.pokemons.remove(query)
Removed 1 record(s) in 5ms
WriteResult({
  "nRemoved": 1
})
```
