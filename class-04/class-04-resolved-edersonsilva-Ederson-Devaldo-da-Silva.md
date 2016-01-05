# MongoDB - Aula 04 - Exercício
autor: Ederson Devaldo da Silva

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
codevops(mongod-3.0.6) be-mean-pokemons> var query = {$or: [{name: /pikachu/i},{name: /squirtle/i},{name: /bulbassauro/i},{name: /charmander/i}]}
codevops(mongod-3.0.6) be-mean-pokemons> var mod = {$pushAll: {moves: ['Soco no cara','Bicuda nas costas']}}
codevops(mongod-3.0.6) be-mean-pokemons> query
{
  "$or": [
    {
      "name": /pikachu/i
    },
    {
      "name": /squirtle/i
    },
    {
      "name": /bulbassauro/i
    },
    {
      "name": /charmander/i
    }
  ]
}
codevops(mongod-3.0.6) be-mean-pokemons> mod
{
  "$pushAll": {
    "moves": [
      "Soco no cara",
      "Bicuda nas costas"
    ]
  }
}
codevops(mongod-3.0.6) be-mean-pokemons> var options = {multi: true}
codevops(mongod-3.0.6) be-mean-pokemons> db.pokemons.update(query,mod,options)
Updated 1 existing record(s) in 3ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
codevops(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56623dd5f3045dd41d6869d7"),
  "name": "Pikachu",
  "description": "Bicho muito loko",
  "type": "Eletric",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "choque do trovão",
    "Soco no cara",
    "Bicuda nas costas"
  ]
}
Fetched 1 record(s) in 1ms
```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

```
codevops(mongod-3.0.6) be-mean-pokemons> var query = {}
codevops(mongod-3.0.6) be-mean-pokemons> var mod = {$push: {moves: 'desvio'}}
codevops(mongod-3.0.6) be-mean-pokemons> var options = {multi: true}
codevops(mongod-3.0.6) be-mean-pokemons> db.pokemons.update(query,mod,options)
Updated 8 existing record(s) in 2ms
WriteResult({
  "nMatched": 8,
  "nUpserted": 0,
  "nModified": 8
})
codevops(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("566219f4f3045dd41d6869d2"),
  "name": "Metapod",
  "description": "The shell covering this Pokémons body is as hard as an iron slab.Metapod does not move very much. It stays still because it is preparing its soft innards for evolution inside the hard shell.",
  "type": "Bug",
  "attack": 10,
  "defense": 30,
  "height": 0.7,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56621a69f3045dd41d6869d3"),
  "name": "Nidorino",
  "description": "Nidorino has a horn that is harder than a diamond. If it senses a hostile presence, all the barbs on its back bristle up at once, and it challenges the foe with all its might.",
  "type": "Poison",
  "attack": 40,
  "defense": 30,
  "height": 0.9,
  "active": false,
  "moves": [
    "investida",
    "cabeçada de bode",
    "desvio"
  ]
}
{
  "_id": ObjectId("56621b2cf3045dd41d6869d4"),
  "name": "Golduck",
  "description": "The webbed flippers on its forelegs and hind legs and the streamlined body of Golduck give it frightening speed. This Pokémon is definitely much faster than even the most athletic swimmer.",
  "type": "Water",
  "attack": 40,
  "defense": 30,
  "height": 1.7,
  "active": false,
  "moves": [
    "investida",
    "patada de mula",
    "desvio"
  ]
}
{
  "_id": ObjectId("56621bd9f3045dd41d6869d5"),
  "name": "Primeape",
  "description": "When Primeape becomes furious, its blood circulation is boosted. In turn, its muscles are made even stronger. However, it also becomes much less intelligent at the same time.",
  "type": "Fighting",
  "attack": 50,
  "defense": 30,
  "height": 1,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56621cbcf3045dd41d6869d6"),
  "name": "Arcanine",
  "description": "Arcanine is known for its high speed. It is said to be capable of running over 6,200 miles in a single day and night. The fire that blazes wildly within this Pokémons body is its source of power.",
  "type": "Fire",
  "attack": 60,
  "defense": 40,
  "height": 1.9,
  "active": false,
  "moves": [
    "investida",
    "mordida atômica",
    "desvio"
  ]
}
{
  "_id": ObjectId("56623dd5f3045dd41d6869d7"),
  "name": "Pikachu",
  "description": "Bicho muito loko",
  "type": "Eletric",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "choque do trovão",
    "Soco no cara",
    "Bicuda nas costas",
    "desvio"
  ]
}
{
  "_id": ObjectId("566424dc6ce77cf10a85cc8f"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "height": 2.1,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5664352b7762e8e04ddf596e"),
  "active": false,
  "name": "NãoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações",
  "moves": [
    "investida",
    "desvio"
  ]
}
Fetched 8 record(s) in 7ms
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

```
codevops(mongod-3.0.6) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}
codevops(mongod-3.0.6) be-mean-pokemons> var mod = {$set: {active: true}, $setOnInsert: {name:"AindaNaoExistMon", attack: null, defense: null, height:null, description:"Sem maiores Informações"}}
codevops(mongod-3.0.6) be-mean-pokemons> var options = {upsert: true}
codevops(mongod-3.0.6) be-mean-pokemons>db.pokemons.update(query,mod,options)
Updated 1 new record(s) in 3ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("566477757762e8e04ddf596f")
})
codevops(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("566477757762e8e04ddf596f"),
  "active": true,
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores Informações"
}
Fetched 1 record(s) in 1ms
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

```
codevops(mongod-3.0.6) be-mean-pokemons> var query = {moves: {$all: ['investida','Bicuda nas costas']}}
codevops(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56623dd5f3045dd41d6869d7"),
  "name": "Pikachu",
  "description": "Bicho muito loko",
  "type": "Eletric",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "choque do trovão",
    "Soco no cara",
    "Bicuda nas costas",
    "desvio"
  ]
}
Fetched 1 record(s) in 3ms
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

```
codevops(mongod-3.0.6) be-mean-pokemons> var query = {moves: {$all: ['patada de mula','investida']}}
codevops(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56621b2cf3045dd41d6869d4"),
  "name": "Golduck",
  "description": "The webbed flippers on its forelegs and hind legs and the streamlined body of Golduck give it frightening speed. This Pokémon is definitely much faster than even the most athletic swimmer.",
  "type": "Water",
  "attack": 40,
  "defense": 30,
  "height": 1.7,
  "active": false,
  "moves": [
    "investida",
    "patada de mula",
    "desvio"
  ]
}
```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

```
codevops(mongod-3.0.6) be-mean-pokemons> var query = {type: {$ne: 'Eletric'} }
codevops(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("566219f4f3045dd41d6869d2"),
  "name": "Metapod",
  "description": "The shell covering this Pokémons body is as hard as an iron slab.Metapod does not move very much. It stays still because it is preparing its soft innards for evolution inside the hard shell.",
  "type": "Bug",
  "attack": 10,
  "defense": 30,
  "height": 0.7,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56621a69f3045dd41d6869d3"),
  "name": "Nidorino",
  "description": "Nidorino has a horn that is harder than a diamond. If it senses a hostile presence, all the barbs on its back bristle up at once, and it challenges the foe with all its might.",
  "type": "Poison",
  "attack": 40,
  "defense": 30,
  "height": 0.9,
  "active": false,
  "moves": [
    "investida",
    "cabeçada de bode",
    "desvio"
  ]
}
{
  "_id": ObjectId("56621b2cf3045dd41d6869d4"),
  "name": "Golduck",
  "description": "The webbed flippers on its forelegs and hind legs and the streamlined body of Golduck give it frightening speed. This Pokémon is definitely much faster than even the most athletic swimmer.",
  "type": "Water",
  "attack": 40,
  "defense": 30,
  "height": 1.7,
  "active": false,
  "moves": [
    "investida",
    "patada de mula",
    "desvio"
  ]
}
{
  "_id": ObjectId("56621bd9f3045dd41d6869d5"),
  "name": "Primeape",
  "description": "When Primeape becomes furious, its blood circulation is boosted. In turn, its muscles are made even stronger. However, it also becomes much less intelligent at the same time.",
  "type": "Fighting",
  "attack": 50,
  "defense": 30,
  "height": 1,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56621cbcf3045dd41d6869d6"),
  "name": "Arcanine",
  "description": "Arcanine is known for its high speed. It is said to be capable of running over 6,200 miles in a single day and night. The fire that blazes wildly within this Pokémons body is its source of power.",
  "type": "Fire",
  "attack": 60,
  "defense": 40,
  "height": 1.9,
  "active": false,
  "moves": [
    "investida",
    "mordida atômica",
    "desvio"
  ]
}
{
  "_id": ObjectId("566424dc6ce77cf10a85cc8f"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "height": 2.1,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5664352b7762e8e04ddf596e"),
  "active": false,
  "name": "NãoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("566477757762e8e04ddf596f"),
  "active": true,
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores Informações"
}
Fetched 8 record(s) in 5ms
```


## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```
codevops(mongod-3.0.6) be-mean-pokemons> var query = {$and: [{moves: {$in: [/investida/i]}},{defense: {$gte:49}}]}
codevops(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("566424dc6ce77cf10a85cc8f"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "height": 2.1,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}

```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
codevops(mongod-3.0.6) be-mean-pokemons> var query = {$and: [{type: {$in: [/water/i]}}, {attack: {$lt: 50}}]}
codevops(mongod-3.0.6) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 2ms
WriteResult({
  "nRemoved": 1
})
```
