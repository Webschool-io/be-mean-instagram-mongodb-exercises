## MongoDb Aula - 04

Autor: Vítor Capretz

## 1. Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, squirtle, bulbassauro e charmander
```
var query = {name: {$in: ["Pikachu", "Squirtle", "Bulbassauro", "Charmander"]}}
var mod = {$pushAll: {moves: ["investida master", "desvio matrix"]}}
var options = {multi: true}

vitor-ThinkPad-T440(mongod-2.6.10) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 1ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})

```
## 2. Adicionar 1 movimento em todos os pokemons: "desvio"

```
var query = {}
var mod = {$push: {moves: "desvio"}}
var options = {multi: true}

vitor-ThinkPad-T440(mongod-2.6.10) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 10 existing record(s) in 1ms
WriteResult({
  "nMatched": 10,
  "nUpserted": 0,
  "nModified": 10
})

```

## 3. Adicionar o pokemon 'AindaNaoExisteMon' caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações"
```
var query = {name: "AindaNaoExisteMon"}
var mod = {$set: {active: true}, $setOnInsert: {
	name: "AindaNaoExisteMon",
	description: "Sem maiores informações",
	attack: null, 
	defense: null, 
	type: null, 
	height: null
}}
var options = {upsert: true}

vitor-ThinkPad-T440(mongod-2.6.10) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 1ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("5749cf0eb3d3017f19d5469e")
})
```

## 4. Pesquisar todos os pokemons que possuam o ataque 'investida' e mais um que você adicionou, escolha seu pokemon favorito 
```
var query = {moves: {$in: [/investida/i, /lança-chamas/i]}}
vitor-ThinkPad-T440(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57476d07361178273f8391dc"),
  "name": "Jigglypuff",
  "description": "prof da aula de historia",
  "type": "Fada",
  "attack": 45,
  "defense": 40,
  "height": 0.51,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("574779c0361178273f8391dd"),
  "name": "Pidgey",
  "description": "rolinha que nao voa",
  "attack": 45,
  "defense": 40,
  "height": 0.3,
  "type": "Voador",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57478e67361178273f8391df"),
  "name": "Oddish",
  "description": "Beterraba?",
  "type": "Grama",
  "attack": 50,
  "defense": 55,
  "height": 0.51,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57478e67361178273f8391e0"),
  "name": "Abra",
  "description": "finge q faz mágica",
  "type": "Psíquico",
  "attack": 20,
  "defense": 15,
  "height": 0.89,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57478e67361178273f8391e1"),
  "name": "Bellsprout",
  "description": "plantinha do plants vs zombies",
  "type": "Grama",
  "attack": 75,
  "defense": 35,
  "height": 0.71,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57487e9f71835441079b6ef8"),
  "description": "pokemon de teste arrumado",
  "name": "Testmon",
  "attack": 8000,
  "defense": 8000,
  "height": 1,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57476d07361178273f8391d8"),
  "name": "Bulbassauro",
  "description": "aquele verde",
  "type": "Grama",
  "attack": 49,
  "defense": 49,
  "height": 0.4,
  "active": true,
  "moves": [
    "investida",
    "folha navalha",
    "investida master",
    "desvio matrix",
    "desvio"
  ]
}
{
  "_id": ObjectId("57476d07361178273f8391d9"),
  "name": "Charmander",
  "description": "o que vira o charizard (fodelao)",
  "type": "Fogo",
  "attack": 52,
  "defense": 43,
  "height": 0.6,
  "moves": [
    "investida",
    "lança-chamas",
    "investida master",
    "desvio matrix",
    "desvio"
  ]
}
{
  "_id": ObjectId("57476d07361178273f8391da"),
  "name": "Squirtle",
  "description": "esse evoluido tbm eh massa",
  "type": "Água",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "moves": [
    "investida",
    "hidrobomba",
    "investida master",
    "desvio matrix",
    "desvio"
  ]
}
{
  "_id": ObjectId("57476d07361178273f8391db"),
  "name": "Pikachu",
  "description": "pokemon de poser",
  "type": "Elétrico",
  "attack": 120,
  "defense": 40,
  "height": 0.41,
  "moves": [
    "investida",
    "choque do trovão",
    "investida master",
    "desvio matrix",
    "desvio"
  ]
}
Fetched 10 record(s) in 1ms


```

## 5. Pesquisar todos os pokemons que possuam ataques que você adicionou, escolha seu pokemon favorito
```
var query = {moves: {$in: ["investida master", "desvio matrix"]}}
vitor-ThinkPad-T440(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57476d07361178273f8391d8"),
  "name": "Bulbassauro",
  "description": "aquele verde",
  "type": "Grama",
  "attack": 49,
  "defense": 49,
  "height": 0.4,
  "active": true,
  "moves": [
    "investida",
    "folha navalha",
    "investida master",
    "desvio matrix",
    "desvio"
  ]
}
{
  "_id": ObjectId("57476d07361178273f8391d9"),
  "name": "Charmander",
  "description": "o que vira o charizard (fodelao)",
  "type": "Fogo",
  "attack": 52,
  "defense": 43,
  "height": 0.6,
  "moves": [
    "investida",
    "lança-chamas",
    "investida master",
    "desvio matrix",
    "desvio"
  ]
}
{
  "_id": ObjectId("57476d07361178273f8391da"),
  "name": "Squirtle",
  "description": "esse evoluido tbm eh massa",
  "type": "Água",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "moves": [
    "investida",
    "hidrobomba",
    "investida master",
    "desvio matrix",
    "desvio"
  ]
}
{
  "_id": ObjectId("57476d07361178273f8391db"),
  "name": "Pikachu",
  "description": "pokemon de poser",
  "type": "Elétrico",
  "attack": 120,
  "defense": 40,
  "height": 0.41,
  "moves": [
    "investida",
    "choque do trovão",
    "investida master",
    "desvio matrix",
    "desvio"
  ]
}
Fetched 4 record(s) in 0ms


```
## 6. Pesquisar todos que não são do tipo 'elétrico'
```
var query = {type: {$not: /elétrico/i}}
vitor-ThinkPad-T440(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57476d07361178273f8391dc"),
  "name": "Jigglypuff",
  "description": "prof da aula de historia",
  "type": "Fada",
  "attack": 45,
  "defense": 40,
  "height": 0.51,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("574779c0361178273f8391dd"),
  "name": "Pidgey",
  "description": "rolinha que nao voa",
  "attack": 45,
  "defense": 40,
  "height": 0.3,
  "type": "Voador",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57478e67361178273f8391df"),
  "name": "Oddish",
  "description": "Beterraba?",
  "type": "Grama",
  "attack": 50,
  "defense": 55,
  "height": 0.51,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57478e67361178273f8391e0"),
  "name": "Abra",
  "description": "finge q faz mágica",
  "type": "Psíquico",
  "attack": 20,
  "defense": 15,
  "height": 0.89,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57478e67361178273f8391e1"),
  "name": "Bellsprout",
  "description": "plantinha do plants vs zombies",
  "type": "Grama",
  "attack": 75,
  "defense": 35,
  "height": 0.71,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57487e9f71835441079b6ef8"),
  "description": "pokemon de teste arrumado",
  "name": "Testmon",
  "attack": 8000,
  "defense": 8000,
  "height": 1,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57476d07361178273f8391d8"),
  "name": "Bulbassauro",
  "description": "aquele verde",
  "type": "Grama",
  "attack": 49,
  "defense": 49,
  "height": 0.4,
  "active": true,
  "moves": [
    "investida",
    "folha navalha",
    "investida master",
    "desvio matrix",
    "desvio"
  ]
}
{
  "_id": ObjectId("57476d07361178273f8391d9"),
  "name": "Charmander",
  "description": "o que vira o charizard (fodelao)",
  "type": "Fogo",
  "attack": 52,
  "defense": 43,
  "height": 0.6,
  "moves": [
    "investida",
    "lança-chamas",
    "investida master",
    "desvio matrix",
    "desvio"
  ]
}
{
  "_id": ObjectId("57476d07361178273f8391da"),
  "name": "Squirtle",
  "description": "esse evoluido tbm eh massa",
  "type": "Água",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "moves": [
    "investida",
    "hidrobomba",
    "investida master",
    "desvio matrix",
    "desvio"
  ]
}
{
  "_id": ObjectId("5749cf0eb3d3017f19d5469e"),
  "name": "AindaNaoExisteMon",
  "active": true,
  "description": "Sem maiores informações",
  "attack": null,
  "defense": null,
  "type": null,
  "height": null
}
Fetched 10 record(s) in 4ms

```

## 7. Pesquisar todos pokemons que tenham ataque 'investida' e tenham a defesa não menor ou igual a 49
```
var query = {
	$and: [
		{moves: {$in: ["investida"]}}, 
		{defense: {$not: {$lte: 49}}}
	]
}

vitor-ThinkPad-T440(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57478e67361178273f8391df"),
  "name": "Oddish",
  "description": "Beterraba?",
  "type": "Grama",
  "attack": 50,
  "defense": 55,
  "height": 0.51,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57487e9f71835441079b6ef8"),
  "description": "pokemon de teste arrumado",
  "name": "Testmon",
  "attack": 8000,
  "defense": 8000,
  "height": 1,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57476d07361178273f8391da"),
  "name": "Squirtle",
  "description": "esse evoluido tbm eh massa",
  "type": "Água",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "moves": [
    "investida",
    "hidrobomba",
    "investida master",
    "desvio matrix",
    "desvio"
  ]
}
Fetched 3 record(s) in 1ms

```

## 8. Remova todos os pokemons do tipo `água` e com attack menor que 50.
```
var query = {$and: [{type: /água/}, {attack: {$lt: 50}}]}
vitor-ThinkPad-T440(mongod-2.6.10) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 0ms
WriteResult({
  "nRemoved": 1
})

```
