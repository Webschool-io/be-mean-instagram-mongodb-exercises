# MongoDB - Aula 04 - Exercício
autor: Yuri Henrique Sales da Costa

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
Megazord(mongod-3.0.7) be-mean> var query = {name: /pikachu/i}
Megazord(mongod-3.0.7) be-mean> var mod = {$pushAll: {moves: ['Choque do trovão', 'esfera elétrica']}}

Megazord(mongod-3.0.7) be-mean> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 4ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

Megazord(mongod-3.0.7) be-mean> var query = {name: /bulbassauro/i}
Megazord(mongod-3.0.7) be-mean> var mod = {$pushAll: {moves: ['raio solar', 'dança de pétalas']}}

Megazord(mongod-3.0.7) be-mean> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 9ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

Megazord(mongod-3.0.7) be-mean> var query = {name: /charmander/i}
Megazord(mongod-3.0.7) be-mean> var mod = {$pushAll: {moves: ['Explosão de chamas', 'Arranhão']}}

Megazord(mongod-3.0.7) be-mean> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 3ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

Megazord(mongod-3.0.7) be-mean> var query = {name: /squirtle/i}
Megazord(mongod-3.0.7) be-mean> var mod = {$pushAll: {moves: ['Bolhas', 'Raio de gelo']}}

Megazord(mongod-3.0.7) be-mean> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 4ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```
Megazord(mongod-3.0.7) be-mean> var query =  {}
Megazord(mongod-3.0.7) be-mean> var mod = {$push: {moves: 'desvio'}}
Megazord(mongod-3.0.7) be-mean> var options = {multi: true}

Megazord(mongod-3.0.7) be-mean> db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 5ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
Megazord(mongod-3.0.7) be-mean> var query = {name: /AindaNaoExisteMon/i}
Megazord(mongod-3.0.7) be-mean> var mod = {$setOnInsert: {name: 'AindaNaoExisteMon', type: null, attack: null, defense: null, height: null, descrption: 'Sem maiores informações'}}
Megazord(mongod-3.0.7) be-mean> var options = {upsert: true}

Megazord(mongod-3.0.7) be-mean> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 4ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("565215d2ca018621e148fa33")
})
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
Megazord(mongod-3.0.7) be-mean> var query = {moves: {$in: [/investida/i, /Raio de gelo/i]}}

Megazord(mongod-3.0.7) be-mean> db.pokemons.find(query)
{
  "_id": ObjectId("56520dacd9a99b5cbf188af4"),
  "name": "Squirtle",
  "type": "Water",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "description": "Tartaruga bonitinha",
  "moves": [
    "Bolhas",
    "Raio de gelo",
    "desvio"
  ]
}
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```
Megazord(mongod-3.0.7) be-mean> var query = {moves: {$in: [/arranhao/i, /chama/i]}}

Megazord(mongod-3.0.7) be-mean> db.pokemons.find(query)
{
  "_id": ObjectId("56520e56d9a99b5cbf188af6"),
  "name": "Charmander",
  "type": "Fire",
  "defense": 43,
  "height": 0.6,
  "description": "Capetinha",
  "moves": [
    "Explosão de chamas",
    "Arranhão",
    "desvio"
  ],
  "attack": 52
}
```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```
Megazord(mongod-3.0.7) be-mean> var query = {type: {$not: /eletric/i}}

Megazord(mongod-3.0.7) be-mean> db.pokemons.find(query)
{
  "_id": ObjectId("56520dacd9a99b5cbf188af4"),
  "name": "Squirtle",
  "type": "Water",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "description": "Tartaruga bonitinha",
  "moves": [
    "Bolhas",
    "Raio de gelo",
    "desvio"
  ]
}
{
  "_id": ObjectId("56520e56d9a99b5cbf188af6"),
  "name": "Charmander",
  "type": "Fire",
  "defense": 43,
  "height": 0.6,
  "description": "Capetinha",
  "moves": [
    "Explosão de chamas",
    "Arranhão",
    "desvio"
  ],
  "attack": 52
}
{
  "_id": ObjectId("56520e1ad9a99b5cbf188af5"),
  "name": "Bulbassauro",
  "type": "Grass",
  "attack": 49,
  "defense": 49,
  "height": 0.7,
  "description": "Bicho com um repolho nas costas",
  "moves": [
    "raio solar",
    "dança de pétalas",
    "desvio"
  ]
}
{
  "_id": ObjectId("565215d2ca018621e148fa33"),
  "name": "AindaNaoExisteMon",
  "type": null,
  "attack": null,
  "defense": null,
  "height": null,
  "descrption": "Sem maiores informações"
}
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```
Megazord(mongod-3.0.7) be-mean> var query1 = {moves: {$in: [/investida/i]}}
Megazord(mongod-3.0.7) be-mean> var query2 = {defense: {$not: {$lte: 49}}}
Megazord(mongod-3.0.7) be-mean> var query3 = {$and: [query1, query2]}

Megazord(mongod-3.0.7) be-mean> db.pokemons.find(query3)
Fetched 0 record(s) in 2ms
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
Megazord(mongod-3.0.7) be-mean> var query1 = {type:/water/i}
Megazord(mongod-3.0.7) be-mean> var query2 = {attack: {$lt: 50}}
Megazord(mongod-3.0.7) be-mean> var query3 = {$and: [query1, query2]}

Megazord(mongod-3.0.7) be-mean> db.pokemons.remove(query3)
Removed 1 record(s) in 4ms
WriteResult({
  "nRemoved": 1
})
```
