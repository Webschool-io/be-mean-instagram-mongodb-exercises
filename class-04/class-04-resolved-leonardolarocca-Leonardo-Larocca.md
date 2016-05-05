## MongoDb - Aula 04 - Exercício
Autor: Leonardo Larocca

## 1 -  Adicionando 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
asus(mongod-3.0.8) be-mean-instagram> var query = {$or:[ {name:/pikachu/i}, {name:/squirtle/i}, {name:/bulbassauro/i}, {name:/charmander/i}]}
asus(mongod-3.0.8) be-mean-instagram> var mod = {$pushAll: {moves: ["Soco Forte","Soquinho"]}}
asus(mongod-3.0.8) be-mean-instagram> var options = {multi: true}
asus(mongod-3.0.8) be-mean-instagram> db.pokemons.update(query,mod,options)
Updated 4 existing record(s) in 3ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
asus(mongod-3.0.8) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5659fc16c60ae54398d6a83c"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "Investida",
    "Soco Forte",
    "Soquinho"
  ],
  "active": false
}
{
  "_id": ObjectId("5659fd16c60ae54398d6a83d"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "Investida",
    "Soco Forte",
    "Soquinho"
  ]
}
{
  "_id": ObjectId("5659fd5cc60ae54398d6a83e"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "Investida",
    "Soco Forte",
    "Soquinho"
  ]
}
{
  "_id": ObjectId("5659fe3ec60ae54398d6a83f"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "Investida",
    "Soco Forte",
    "Soquinho"
  ]
}
Fetched 4 record(s) in 3ms


```

## 2 - Adicionar 1 movimento em todos os pokemons: `desvio`.
```
asus(mongod-3.0.8) be-mean-instagram> query
{
  
}
asus(mongod-3.0.8) be-mean-instagram> mod
{
  "$pushAll": {
    "moves": [
      "Desvio"
    ]
  }
}
asus(mongod-3.0.8) be-mean-instagram> options
{
  "multi": true
}
asus(mongod-3.0.8) be-mean-instagram> db.pokemons.update(query,mod,options)
Updated 7 existing record(s) in 41ms
WriteResult({
  "nMatched": 7,
  "nUpserted": 0,
  "nModified": 7
})


```

## 3 - Adicionar o pokemon `AindaNaoExisteMon` com todos os dados com o valor `null` e a descrição: "Sem maiores informações".
```
asus(mongod-3.0.8) be-mean-instagram> var query = {name: /NaoExisteMon/i}
asus(mongod-3.0.8) be-mean-instagram> var mod = {$set: {active: true}, $setOnInsert: {name: "NaoExisteMon", attack: null, defense: null, height: null, description: "Sem maiores informações."}}
asus(mongod-3.0.8) be-mean-instagram> var options= {upsert: true}
asus(mongod-3.0.8) be-mean-instagram> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 4ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("5698753edb4337fb600d8b3e")
})
asus(mongod-3.0.8) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5698753edb4337fb600d8b3e"),
  "active": true,
  "name": "NaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações."
}
Fetched 1 record(s) in 1ms

```

## 4 - Pesquisando todos os pokemons que possuam o ataque `investida`  mais o pokemon favorito.
```
asus(mongod-3.0.8) be-mean-instagram> var query = {$or: [{name:/pikachu/i},{moves:/investida/i}]}
asus(mongod-3.0.8) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5659fc16c60ae54398d6a83c"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "Investida",
    "Soco Forte",
    "Soquinho",
    "Desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("5659fd16c60ae54398d6a83d"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "Investida",
    "Soco Forte",
    "Soquinho",
    "Desvio"
  ]
}
{
  "_id": ObjectId("5659fd5cc60ae54398d6a83e"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "Investida",
    "Soco Forte",
    "Soquinho",
    "Desvio"
  ]
}
{
  "_id": ObjectId("5659fe3ec60ae54398d6a83f"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "Investida",
    "Soco Forte",
    "Soquinho",
    "Desvio"
  ]
}
{
  "_id": ObjectId("565a025bc60ae54398d6a841"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "active": false,
  "moves": [
    "Investida",
    "Desvio"
  ]
}
{
  "_id": ObjectId("5695cc7ddb4337fb600d8b3c"),
  "active": false,
  "moves": [
    "Investida",
    "Desvio"
  ]
}
Fetched 6 record(s) in 5ms
asus(mongod-3.0.8) be-mean-instagram> 

```

## 5 - Pesquisando todos os pokemons que possuam os ataques que foram adicionados mais o pokemon favorito.
```
asus(mongod-3.0.8) be-mean-instagram>  var query = {moves:{$in:[/soco forte/i,/soquinho/i]}}
asus(mongod-3.0.8) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5659fc16c60ae54398d6a83c"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "Investida",
    "Soco Forte",
    "Soquinho",
    "Desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("5659fd16c60ae54398d6a83d"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "Investida",
    "Soco Forte",
    "Soquinho",
    "Desvio"
  ]
}
{
  "_id": ObjectId("5659fd5cc60ae54398d6a83e"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "Investida",
    "Soco Forte",
    "Soquinho",
    "Desvio"
  ]
}
{
  "_id": ObjectId("5659fe3ec60ae54398d6a83f"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "Investida",
    "Soco Forte",
    "Soquinho",
    "Desvio"
  ]
}
Fetched 4 record(s) in 3ms


```

## 6 - Pesquisando todos os pokemons que são do tipo `elétrico`.
```
asus(mongod-3.0.8) be-mean-instagram> var query = {type:/eletric/i}
asus(mongod-3.0.8) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5659fc16c60ae54398d6a83c"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "Investida",
    "Soco Forte",
    "Soquinho",
    "Desvio"
  ],
  "active": false
}
Fetched 1 record(s) in 1ms

```

## 7 - Pesquisando todos os pokemons que tenham o ataque `investida` e tenham a defesa não menor igual a 49.
```
asus(mongod-3.0.8) be-mean-instagram> var query = {$or:[{defense:{lt:49}},{moves:/investida/i}]}
asus(mongod-3.0.8) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5659fc16c60ae54398d6a83c"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "Investida",
    "Soco Forte",
    "Soquinho",
    "Desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("5659fd16c60ae54398d6a83d"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "Investida",
    "Soco Forte",
    "Soquinho",
    "Desvio"
  ]
}
{
  "_id": ObjectId("5659fd5cc60ae54398d6a83e"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "Investida",
    "Soco Forte",
    "Soquinho",
    "Desvio"
  ]
}
{
  "_id": ObjectId("5659fe3ec60ae54398d6a83f"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "Investida",
    "Soco Forte",
    "Soquinho",
    "Desvio"
  ]
}
{
  "_id": ObjectId("565a025bc60ae54398d6a841"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "active": false,
  "moves": [
    "Investida",
    "Desvio"
  ]
}
{
  "_id": ObjectId("5695cc7ddb4337fb600d8b3c"),
  "active": false,
  "moves": [
    "Investida",
    "Desvio"
  ]
}
Fetched 6 record(s) in 5ms

```

## 8 - Removendo todos os pokemons do tipo água com ataque menor que 50.
```
asus(mongod-3.0.8) be-mean-instagram> var query = {$and: [{type: /agua/i},{attack:{$lt:50}}]}
asus(mongod-3.0.8) be-mean-instagram> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
asus(mongod-3.0.8) be-mean-instagram> db.pokemons.remove(query)
Removed 0 record(s) in 12ms
WriteResult({
  "nRemoved": 0
})
asus(mongod-3.0.8) be-mean-instagram> 


```