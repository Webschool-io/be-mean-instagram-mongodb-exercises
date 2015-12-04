# MongoDB - Aula 04 - Exercício
autor: Giuseppe Antonelli Santos

## Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Electrike, Blastoise, Charizard e Exeggcute
```
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean-pokemons> var query = {$or: [{name: /blastoise/i}, {name: /charizard/i}, {name: /electrike/i}, {name: /exeggcute/i}]}
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll: {moves: ['soco imaginario', 'chute psiquico']}}
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean-pokemons> var opts = {multi: true}
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, opts)
Updated 4 existing record(s) in 5ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
```

## Adicionar 1 movimento em todos os pokemons: desvio
```
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean-pokemons> var query = {}
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean-pokemons> var mod = {$push: {moves: "desvio"}}
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean-pokemons> var opts = {multi: true}
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, opts)
Updated 5 existing record(s) in 2ms
WriteResult({
  "nMatched": 5,
  "nUpserted": 0,
  "nModified": 5
})
```

## Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações"
```
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean-pokemons> var mod = {$setOnInsert: {name: "AindaNaoExisteMon", attack: null, height: null, defense: null, moves: [], description: "Sem maiores informações"}}
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean-pokemons> var opts = {upsert: true}
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, opts)
Updated 1 new record(s) in 1ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("5653df58781f8750caa216b9")
})
```

## Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito
```
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$in: ['investida', /chute psiquico/i]}}
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5653cdacb5a20e0455611504"),
  "name": "Electrike",
  "description": "Electrike stores electricity in its long body hair",
  "type": "Eletric",
  "attack": 30,
  "height": 0.6,
  "moves": [
    "soco imaginario",
    "chute psiquico",
    "desvio"
  ]
}
{
  "_id": ObjectId("5653cdf2b5a20e0455611505"),
  "name": "Blastoise",
  "description": "Blastoise has water spouts th at protrude from its shell",
  "type": "Water",
  "attack": 40,
  "height": 1.6,
  "moves": [
    "soco imaginario",
    "chute psiquico",
    "desvio"
  ]
}
{
  "_id": ObjectId("5653ce4fb5a20e0455611508"),
  "name": "Exeggcute",
  "description": "Often mistaken for eggs. When disturbed, they quickly gather and attack in swarms.",
  "type": "grass",
  "attack": 40,
  "height": 4,
  "moves": [
    "soco imaginario",
    "chute psiquico",
    "desvio"
  ]
}
{
  "_id": ObjectId("5653ce07b5a20e0455611506"),
  "name": "Charizard",
  "description": "Charizard flies around the sk y in search of powerful opponents.",
  "type": "Fire",
  "attack": 40,
  "height": 1.7,
  "moves": [
    "soco imaginario",
    "chute psiquico",
    "desvio"
  ]
}
Fetched 4 record(s) in 2ms
```

## Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito
```
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$in: [/soco imaginario/i, /chute psiquico/i, /desvio/i]}}
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5653cdacb5a20e0455611504"),
  "name": "Electrike",
  "description": "Electrike stores electricity in its long body hair",
  "type": "Eletric",
  "attack": 30,
  "height": 0.6,
  "moves": [
    "soco imaginario",
    "chute psiquico",
    "desvio"
  ]
}
{
  "_id": ObjectId("5653cdf2b5a20e0455611505"),
  "name": "Blastoise",
  "description": "Blastoise has water spouts th at protrude from its shell",
  "type": "Water",
  "attack": 40,
  "height": 1.6,
  "moves": [
    "soco imaginario",
    "chute psiquico",
    "desvio"
  ]
}
{
  "_id": ObjectId("5653ce0fb5a20e0455611507"),
  "name": "Marowak",
  "description": "The bone it holds is its key weapon. It throws the bone skillfully like a boomerang to KO targets.",
  "type": "ground",
  "attack": 80,
  "height": 10,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5653ce4fb5a20e0455611508"),
  "name": "Exeggcute",
  "description": "Often mistaken for eggs. When disturbed, they quickly gather and attack in swarms.",
  "type": "grass",
  "attack": 40,
  "height": 4,
  "moves": [
    "soco imaginario",
    "chute psiquico",
    "desvio"
  ]
}
{
  "_id": ObjectId("5653ce07b5a20e0455611506"),
  "name": "Charizard",
  "description": "Charizard flies around the sk y in search of powerful opponents.",
  "type": "Fire",
  "attack": 40,
  "height": 1.7,
  "moves": [
    "soco imaginario",
    "chute psiquico",
    "desvio"
  ]
}
Fetched 5 record(s) in 2ms
```

## Pesquisar todos os pokemons que não são do tipo elétrico
```
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean-pokemons> var query = {type: {$ne: 'Eletric'}}
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5653cdf2b5a20e0455611505"),
  "name": "Blastoise",
  "description": "Blastoise has water spouts th at protrude from its shell",
  "type": "Water",
  "attack": 40,
  "height": 1.6,
  "moves": [
    "soco imaginario",
    "chute psiquico",
    "desvio"
  ]
}
{
  "_id": ObjectId("5653ce0fb5a20e0455611507"),
  "name": "Marowak",
  "description": "The bone it holds is its key weapon. It throws the bone skillfully like a boomerang to KO targets.",
  "type": "ground",
  "attack": 80,
  "height": 10,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5653ce4fb5a20e0455611508"),
  "name": "Exeggcute",
  "description": "Often mistaken for eggs. When disturbed, they quickly gather and attack in swarms.",
  "type": "grass",
  "attack": 40,
  "height": 4,
  "moves": [
    "soco imaginario",
    "chute psiquico",
    "desvio"
  ]
}
{
  "_id": ObjectId("5653ce07b5a20e0455611506"),
  "name": "Charizard",
  "description": "Charizard flies around the sk y in search of powerful opponents.",
  "type": "Fire",
  "attack": 40,
  "height": 1.7,
  "moves": [
    "soco imaginario",
    "chute psiquico",
    "desvio"
  ]
}
{
  "_id": ObjectId("5653df58781f8750caa216b9"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "height": null,
  "defense": null,
  "moves": [ ],
  "description": "Sem maiores informações"
}
Fetched 5 record(s) in 2ms
```

## Pesquisar todos os pokemons que tenham o ataque desvio E tenham a attack não menor ou igual a 40
```
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{moves: {$in: [/desvio/i]}}, {attack: {$gt: 40}}]}
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5653ce0fb5a20e0455611507"),
  "name": "Marowak",
  "description": "The bone it holds is its key weapon. It throws the bone skillfully like a boomerang to KO targets.",
  "type": "ground",
  "attack": 80,
  "height": 10,
  "moves": [
    "desvio"
  ]
}
Fetched 1 record(s) in 1ms
```

## Remova todos os pokemons do tipo água e com attack menor que 50
```
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{type: /water/i}, {attack: {$lt: 50}}]}
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 1ms
WriteResult({
  "nRemoved": 1
})
```