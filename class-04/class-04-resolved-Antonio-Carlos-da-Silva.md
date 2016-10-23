# MongoDB - Aula 04 - Exercício
autor: Antonio Carlos da Silva 

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander;

``` 
var query = {name: /pikachu/i}
var mod = {$pushAll: {moves: ['esfera elétrica', 'investida trovão']}}
db.pokemons.update(query, mod)
db.pokemons.find(query)
{
  "_id": ObjectId("57faee89839f432738478490"),
  "name": "Pikachu",
  "description": "Sempre que se depara com algo novo, ele dispara  um choque de elétrico",
  "type": "electric",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "esfera elétrica",
    "investida trovão"
  ]
}

var query = {name: /bulbasaur/i}
var mod = {$pushAll: {moves: ['raio solar', 'dança de pétalas']}}
db.pokemons.update(query, mod)
{
  "_id": ObjectId("57faee89839f432738478489"),
  "name": "bulbasaur",
  "description": "Ṕode ser visto dormindo na luz solar. Por absorver os raios do sol.",
  "type": "grass",
  "attack": 30,
  "defense": 20,
  "height": 0.7,
  "moves": [
    "investida",
    "folha navalha",
    "raio solar",
    "dança de pétalas"
  ]
}

var query = {name: /Charmander/i}
var mod = {$pushAll: {moves: ['brasas', 'encarar']}}
db.pokemons.update(query, mod)
{
  "_id": ObjectId("57faee89839f43273847848c"),
  "name": "Charmander",
  "description": "A chama que arde na ponta da cauda é uma indicação das suas emoções. Se o Pokémon fica furioso, a chama queima ferozmente.",
  "type": "fire",
  "attack": 30,
  "defense": 20,
  "height": 0.6,
  "moves": [
    "investida",
    "lança-chamas",
    "brasas",
    "encarar"
  ]
}


var query = {name: /Caterpie/i}
var mod = {$pushAll: {moves: ['alguma coisa', 'outra coisa']}}
db.pokemons.update(query, mod)
{
  "_id": ObjectId("57faee89839f43273847848e"),
  "name": "Caterpie",
  "description": "Apetite voraz e odor forte.",
  "type": "bug",
  "attack": 20,
  "defense": 20,
  "height": 0.3,
  "moves": [
    "investida",
    "alguma coisa",
    "outra coisa"
  ]
} 
```

## **Adicionar** 1 movimento em todos os pokemons: 'desvio';

```
var query = {}
var mod = {$push: {moves: 'desvio'}}
var options =  {multi: true}
db.pokemons.update(query, mod, options)
Updated 8 existing record(s) in 1ms
WriteResult({
  "nMatched": 8,
  "nUpserted": 0,
  "nModified": 8
})

db.pokemons.find()
{
  "_id": ObjectId("57faee89839f43273847848b"),
  "name": "Venusaur",
  "description": "Há uma grande flor na parte traseira. A flor é dito para ter  cores vivas. O aroma da flor acalma as emoções das pessoas.",
  "type": "grass",
  "attack": 40,
  "defense": 40,
  "height": 2,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57faee89839f43273847848c"),
  "name": "Charmander",
  "description": "A chama que arde na ponta da cauda é uma indicação das suas emoções. Se o Pokémon fica furioso, a chama queima ferozmente.",
  "type": "fire",
  "attack": 30,
  "defense": 20,
  "height": 0.6,
  "moves": [
    "investida",
    "lança-chamas",
    "brasas",
    "encarar",
    "desvio"
  ]
}
{
  "_id": ObjectId("57faee89839f43273847848d"),
  "name": "Charizard",
  "description": "voa em torno do céu em busca de adversários poderosos.",
  "type": "fire",
  "attack": 40,
  "defense": 30,
  "height": 1.7,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57faee89839f43273847848e"),
  "name": "Caterpie",
  "description": "Apetite voraz e odor forte.",
  "type": "bug",
  "attack": 20,
  "defense": 20,
  "height": 0.3,
  "moves": [
    "investida",
    "alguma coisa",
    "outra coisa",
    "desvio"
  ]
}
{
  "_id": ObjectId("57faee89839f43273847848a"),
  "name": "Ivysaur",
  "description": "Se ele começa a passar mais tempo deitado ao sol, é um sinal de que  vai florescer uma grande flor em breve.",
  "type": "grass",
  "attack": 30,
  "defense": 30,
  "height": 1,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57faee89839f432738478490"),
  "name": "Pikachu",
  "description": "Sempre que se depara com algo novo, ele dispara  um choque de elétrico",
  "type": "electric",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "esfera elétrica",
    "investida trovão",
    "desvio"
  ]
}
{
  "_id": ObjectId("57faee89839f432738478489"),
  "name": "bulbasaur",
  "description": "Ṕode ser visto dormindo na luz solar. Por absorver os raios do sol.",
  "type": "grass",
  "attack": 30,
  "defense": 20,
  "height": 0.7,
  "moves": [
    "investida",
    "folha navalha",
    "raio solar",
    "dança de pétalas",
    "desvio"
  ]
}
{
  "_id": ObjectId("57faee89839f43273847848f"),
  "name": "Beedrill",
  "description": "Extremamente territorial. Ninguém deve aproximar seu ninho para sua própria segurança.",
  "type": "bug",
  "attack": 50,
  "defense": 20,
  "height": 1,
  "moves": [
    "investida",
    "desvio"
  ]
}
Fetched 8 record(s) in 2ms
```

## **Adicionar** o pokemon 'AindaNaoExisteMon' caso ele não exista com todos os dados com o valor 'null' e a descrição: "Sem maiores informações";

```
var query = {name: /AindaNaoExisteMon/i}
var mod = {$setOnInsert:
{
    name: 'AindaNaoExisteMon',
    type: null,
    attack: null,
    defence: null,
    heigth: null,
    descriptions: 'Sem maiores informações'
    }
}
var options = {upsert: true}
db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 1ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("5803e03ce757ec89529f2440")
})
db.pokemons.find(query)
{
  "_id": ObjectId("5803e03ce757ec89529f2440"),
  "name": "AindaNaoExisteMon",
  "type": null,
  "attack": null,
  "defence": null,
  "heigth": null,
  "descriptions": "Sem maiores informações"
}
Fetched 1 record(s) in 1ms 
```

## Pesquisar todos o pokemons que possuam o ataque 'investida' e mais um que você adicionou, escolha seu pokemon favorito;

```
var query = {moves: {$in: [/investida/i, /dança de pétalas/i]}}
db.pokemons.find(query)
{
  "_id": ObjectId("57faee89839f43273847848b"),
  "name": "Venusaur",
  "description": "Há uma grande flor na parte traseira. A flor é dito para ter  cores vivas. O aroma da flor acalma as emoções das pessoas.",
  "type": "grass",
  "attack": 40,
  "defense": 40,
  "height": 2,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57faee89839f43273847848c"),
  "name": "Charmander",
  "description": "A chama que arde na ponta da cauda é uma indicação das suas emoções. Se o Pokémon fica furioso, a chama queima ferozmente.",
  "type": "fire",
  "attack": 30,
  "defense": 20,
  "height": 0.6,
  "moves": [
    "investida",
    "lança-chamas",
    "brasas",
    "encarar",
    "desvio"
  ]
}
{
  "_id": ObjectId("57faee89839f43273847848d"),
  "name": "Charizard",
  "description": "voa em torno do céu em busca de adversários poderosos.",
  "type": "fire",
  "attack": 40,
  "defense": 30,
  "height": 1.7,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57faee89839f43273847848e"),
  "name": "Caterpie",
  "description": "Apetite voraz e odor forte.",
  "type": "bug",
  "attack": 20,
  "defense": 20,
  "height": 0.3,
  "moves": [
    "investida",
    "alguma coisa",
    "outra coisa",
    "desvio"
  ]
}
{
  "_id": ObjectId("57faee89839f43273847848a"),
  "name": "Ivysaur",
  "description": "Se ele começa a passar mais tempo deitado ao sol, é um sinal de que  vai florescer uma grande flor em breve.",
  "type": "grass",
  "attack": 30,
  "defense": 30,
  "height": 1,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57faee89839f432738478490"),
  "name": "Pikachu",
  "description": "Sempre que se depara com algo novo, ele dispara  um choque de elétrico",
  "type": "electric",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "esfera elétrica",
    "investida trovão",
    "desvio"
  ]
}
{
  "_id": ObjectId("57faee89839f432738478489"),
  "name": "bulbasaur",
  "description": "Ṕode ser visto dormindo na luz solar. Por absorver os raios do sol.",
  "type": "grass",
  "attack": 30,
  "defense": 20,
  "height": 0.7,
  "moves": [
    "investida",
    "folha navalha",
    "raio solar",
    "dança de pétalas",
    "desvio"
  ]
}
{
  "_id": ObjectId("57faee89839f43273847848f"),
  "name": "Beedrill",
  "description": "Extremamente territorial. Ninguém deve aproximar seu ninho para sua própria segurança.",
  "type": "bug",
  "attack": 50,
  "defense": 20,
  "height": 1,
  "moves": [
    "investida",
    "desvio"
  ]
}
Fetched 8 record(s) in 2ms
 
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito;

```
var query = {moves: {$all: [/investida trovão/i, /esfera elétrica/i]}}
db.pokemons.find(query)
{
  "_id": ObjectId("57faee89839f432738478490"),
  "name": "Pikachu",
  "description": "Sempre que se depara com algo novo, ele dispara  um choque de elétrico",
  "type": "electric",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "esfera elétrica",
    "investida trovão",
    "desvio"
  ]
}
Fetched 1 record(s) in 0ms
  
```

## Pesquisar **todos** os pokemons que não são do tipo 'elétrico';

``` 
var query = {type: {$not: [/electric/i]}}
db.pokemons.find(query)
Error: error: {
  "waitedMS": NumberLong("0"),
  "ok": 0,
  "errmsg": "$not needs a regex or a document",
  "code": 2
}
var query = {type: {$nin: [/electric/i]}}
db.pokemons.find(query)
{
  "_id": ObjectId("57faee89839f43273847848b"),
  "name": "Venusaur",
  "description": "Há uma grande flor na parte traseira. A flor é dito para ter  cores vivas. O aroma da flor acalma as emoções das pessoas.",
  "type": "grass",
  "attack": 40,
  "defense": 40,
  "height": 2,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57faee89839f43273847848c"),
  "name": "Charmander",
  "description": "A chama que arde na ponta da cauda é uma indicação das suas emoções. Se o Pokémon fica furioso, a chama queima ferozmente.",
  "type": "fire",
  "attack": 30,
  "defense": 20,
  "height": 0.6,
  "moves": [
    "investida",
    "lança-chamas",
    "brasas",
    "encarar",
    "desvio"
  ]
}
{
  "_id": ObjectId("57faee89839f43273847848d"),
  "name": "Charizard",
  "description": "voa em torno do céu em busca de adversários poderosos.",
  "type": "fire",
  "attack": 40,
  "defense": 30,
  "height": 1.7,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57faee89839f43273847848e"),
  "name": "Caterpie",
  "description": "Apetite voraz e odor forte.",
  "type": "bug",
  "attack": 20,
  "defense": 20,
  "height": 0.3,
  "moves": [
    "investida",
    "alguma coisa",
    "outra coisa",
    "desvio"
  ]
}
{
  "_id": ObjectId("57faee89839f43273847848a"),
  "name": "Ivysaur",
  "description": "Se ele começa a passar mais tempo deitado ao sol, é um sinal de que  vai florescer uma grande flor em breve.",
  "type": "grass",
  "attack": 30,
  "defense": 30,
  "height": 1,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57faee89839f432738478489"),
  "name": "bulbasaur",
  "description": "Ṕode ser visto dormindo na luz solar. Por absorver os raios do sol.",
  "type": "grass",
  "attack": 30,
  "defense": 20,
  "height": 0.7,
  "moves": [
    "investida",
    "folha navalha",
    "raio solar",
    "dança de pétalas",
    "desvio"
  ]
}
{
  "_id": ObjectId("57faee89839f43273847848f"),
  "name": "Beedrill",
  "description": "Extremamente territorial. Ninguém deve aproximar seu ninho para sua própria segurança.",
  "type": "bug",
  "attack": 50,
  "defense": 20,
  "height": 1,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5803e03ce757ec89529f2440"),
  "name": "AindaNaoExisteMon",
  "type": null,
  "attack": null,
  "defence": null,
  "heigth": null,
  "descriptions": "Sem maiores informações"
}
Fetched 8 record(s) in 4ms

```

## Pesquisar **todos** os pokemons que tenham o ataque 'investida' **E** tenham a defesa **não menor ou igual** a 49;

```
var query = {$and: [{moves:{$in:['investida']}}, {attack:{$not:{$lte:49}}}]}
db.pokemons.find(query)
{
  "_id": ObjectId("57faee89839f43273847848f"),
  "name": "Beedrill",
  "description": "Extremamente territorial. Ninguém deve aproximar seu ninho para sua própria segurança.",
  "type": "bug",
  "attack": 50,
  "defense": 20,
  "height": 1,
  "moves": [
    "investida",
    "desvio"
  ]
}
Fetched 1 record(s) in 1ms
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
var query = { $and: [{type: /Water/i}, {attack: {$lt:50}}]}
db.pokemons.remove(query)
Removed 0 record(s) in 2ms
WriteResult({
  "nRemoved": 0
})
  
```
