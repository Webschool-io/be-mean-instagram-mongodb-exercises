# MongoDB - Aula 03 - Exercício
autor: Pedro Henrique Prado Oliveira

## 1. **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander;

```
var query = {name: /pikachu/i}
var mod = {$pushAll: {moves: ["Esfera Elétrica", "Cauda de Ferro"]}}
db.pokemons.update(query, mod)
Updated 1 existing record(s) in 124ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

var query = {name: /squirtle/i}
var mod = {$pushAll: {moves: ["bolhas", "Rajada de Bolhas"]}}
db.pokemons.update(query, mod)
Updated 1 existing record(s) in 5ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

var query = {name: /bulbassauro/i}
var mod = {$pushAll: {moves: ['Combater', 'Rugido']}}
db.pokemons.update(query, mod)
Updated 1 existing record(s) in 5ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

var query = {name: /charmander/i}
var mod = {$pushAll: {moves: ['Rosnar', 'Arranhão']}}
db.pokemons.update(query, mod)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```

## 2. **Adicionar** 1 movimento em todos os pokemons: 'desvio';

```
var query = {}
var mod = {$set:{moves:['desvio']}}
var options = {multi: true}
db.pokemons.update(query, mod, options)
Updated 10 existing record(s) in 54ms
WriteResult({
  "nMatched": 10,
  "nUpserted": 0,
  "nModified": 10
})
```

## 3. **Adicionar** o pokemon 'AindaNaoExisteMon' caso ele não exista com todos os dados com o valor 'null' e a descrição: "Sem maiores informações";

```
var query = {name: /aindanaoexistemon/i}
var mod = {$setOnInsert: {name: 'AindaNaoExisteMon', attack: null, heiight: null, defense: null, description: 'Sem maiores informações', moves:[]}}
var options = {upsert: true}
db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 3ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("56794bc942e486178bcdeab9")
})
```
## 4. Pesquisar todos os pokemons que possuam o ataque 'investida' e mais um que você adicionou, escolha seu pokemon favorito;

```
var query = {moves: {$in: ['investida', 'choque do trovão']}}
NBQ00-129(C:\Program Files\MongoDB\Server\3.0\bin\mongod.exe-3.0.6) be-mean-pokemons> db.pokemons.find(query)
{
 "_id": ObjectId("56705cd06defc2ee15b8bce4"),
 "name": "Pikachu",
 "description": "Primeiro pokemon",
 "type": "Eletric",
 "attack": 30,
 "defense": 20,
 "height": 0.4,
 "moves": [
   "desvio",
   "choque do trovão"
 ],
 "active": false
}
```
## 5. Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito;

```
var query = {moves: {$in: ['desvio']}}
db.pokemons.find(query)
{
  "_id": ObjectId("56705cd06defc2ee15b8bce3"),
  "name": "Charizard",
  "description": "Dragão",
  "type": "fire",
  "attack": 84,
  "defense": 78,
  "height": 1.7,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56705cd06defc2ee15b8bce5"),
  "name": "Mewtwo",
  "description": "Fodão",
  "type": "Psychic",
  "attack": 110,
  "defense": 90,
  "height": 2,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56705cd06defc2ee15b8bce6"),
  "name": "Gyarados",
  "description": "Quem nasceu para ser Magikarp, nunca vai ser Gyarados",
  "type": "Water",
  "attack": 125,
  "defense": 70,
  "height": 6.5,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56705cd06defc2ee15b8bce7"),
  "name": "Blastoise",
  "description": "Solta água pra krl",
  "type": "Water",
  "attack": 83,
  "defense": 100,
  "height": 1.6,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56719406bd6cb6bb42d00ec8"),
  "description": "Pokemon de teste",
  "name": "Testmon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56705cd06defc2ee15b8bce4"),
  "name": "Pikachu",
  "description": "Primeiro pokemon",
  "type": "Eletric",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "moves": [
    "desvio",
    "choque do trovão"
  ],
  "active": false
}
{
  "_id": ObjectId("5672e0406ebba88e60b0e28c"),
  "active": false,
  "name": "NaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5672fac9296725ca42c593ee"),
  "name": "Bulbassauro",
  "active": true,
  "type": "grass",
  "attacK": 60,
  "defense": 20,
  "height": 2.1,
  "description": "Chicoteador",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5672fac9296725ca42c593ef"),
  "name": "Charmander",
  "active": true,
  "type": "fire",
  "attack": 62,
  "defense": 50,
  "height": 2.8,
  "description": "Dragão de fogo",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56740f5b296725ca42c593f0"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "desvio"
  ]
}
```
## 6. Pesquisar **todos** que não são do tipo 'elétrico';

```
var query = {type: {$ne: 'elétrico'}}
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56705cd06defc2ee15b8bce3"),
  "name": "Charizard",
  "description": "Dragão",
  "type": "fire",
  "attack": 84,
  "defense": 78,
  "height": 1.7,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56705cd06defc2ee15b8bce5"),
  "name": "Mewtwo",
  "description": "Fodão",
  "type": "Psychic",
  "attack": 110,
  "defense": 90,
  "height": 2,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56705cd06defc2ee15b8bce6"),
  "name": "Gyarados",
  "description": "Quem nasceu para ser Magikarp, nunca vai ser Gyarados",
  "type": "Water",
  "attack": 125,
  "defense": 70,
  "height": 6.5,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56705cd06defc2ee15b8bce7"),
  "name": "Blastoise",
  "description": "Solta água pra krl",
  "type": "Water",
  "attack": 83,
  "defense": 100,
  "height": 1.6,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56719406bd6cb6bb42d00ec8"),
  "description": "Pokemon de teste",
  "name": "Testmon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56705cd06defc2ee15b8bce4"),
  "name": "Pikachu",
  "description": "Primeiro pokemon",
  "type": "Eletric",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "moves": [
    "desvio",
    "choque do trovão"
  ],
  "active": false
}
{
  "_id": ObjectId("5672e0406ebba88e60b0e28c"),
  "active": false,
  "name": "NaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5672fac9296725ca42c593ee"),
  "name": "Bulbassauro",
  "active": true,
  "type": "grass",
  "attacK": 60,
  "defense": 20,
  "height": 2.1,
  "description": "Chicoteador",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5672fac9296725ca42c593ef"),
  "name": "Charmander",
  "active": true,
  "type": "fire",
  "attack": 62,
  "defense": 50,
  "height": 2.8,
  "description": "Dragão de fogo",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56740f5b296725ca42c593f0"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56794c5e42e486178bcdeaba"),
  "name": "AindaNaoExiteMon",
  "attack": null,
  "heiight": null,
  "defense": null,
  "description": "Sem maiores informações",
  "moves": [ ]
}
{
  "_id": ObjectId("56794cad42e486178bcdeabb"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "heiight": null,
  "defense": null,
  "description": "Sem maiores informações",
  "moves": [ ]
}
```
## 7. Pesquisar **todos** pokemons que tenham o ataque 'investida' **E** tenham a defesa **não menor ou igual** a 49;

```
var query = {$and: [{moves:'investida'}, {defense: {$gt: 49}}]}
db.pokemons.find(query)
{
  "_id": ObjectId("56705cd06defc2ee15b8bce3"),
  "name": "Charizard",
  "description": "Dragão",
  "type": "fire",
  "attack": 84,
  "defense": 78,
  "height": 1.7,
  "active": false,
  "moves": [
    "investida"
  ]
}
{
  "_id": ObjectId("56705cd06defc2ee15b8bce5"),
  "name": "Mewtwo",
  "description": "Fodão",
  "type": "Psychic",
  "attack": 110,
  "defense": 90,
  "height": 2,
  "active": false,
  "moves": [
    "investida"
  ]
}
{
  "_id": ObjectId("56705cd06defc2ee15b8bce6"),
  "name": "Gyarados",
  "description": "Quem nasceu para ser Magikarp, nunca vai ser Gyarados",
  "type": "Water",
  "attack": 125,
  "defense": 70,
  "height": 6.5,
  "active": false,
  "moves": [
    "investida"
  ]
}
{
  "_id": ObjectId("56705cd06defc2ee15b8bce7"),
  "name": "Blastoise",
  "description": "Solta água pra krl",
  "type": "Water",
  "attack": 83,
  "defense": 100,
  "height": 1.6,
  "active": false,
  "moves": [
    "investida"
  ]
}
{
  "_id": ObjectId("56719406bd6cb6bb42d00ec8"),
  "description": "Pokemon de teste",
  "name": "Testmon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "investida"
  ]
}
{
  "_id": ObjectId("5672fac9296725ca42c593ef"),
  "name": "Charmander",
  "active": true,
  "type": "fire",
  "attack": 62,
  "defense": 50,
  "height": 2.8,
  "description": "Dragão de fogo",
  "moves": [
    "investida"
  ]
}
```
## 8. Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
var query = {$and: [{type: /água/i}, {attack: {$lt:50}}]}
db.pokemons.find(query)
{
  "_id": ObjectId("56740f5b296725ca42c593f0"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "investida"
  ]
}
```
