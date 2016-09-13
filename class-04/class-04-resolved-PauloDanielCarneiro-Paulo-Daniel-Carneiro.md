# MongoDB - Aula 04 - Exercício
Autor: Paulo Daniel Carneiro

## Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
Paulo-PC(mongod-3.0.12) be-mean-pokemons> var query = {name: {$in: [/pikachu/i, /squirtle/i, /bulbasaur/i, /charmander/i]}}
Paulo-PC(mongod-3.0.12) be-mean-pokemons> var mod = {$pushAll: {moves: ['slash', 'tackle']}}
Paulo-PC(mongod-3.0.12) be-mean-pokemons> var options = {multi: true}
Paulo-PC(mongod-3.0.12) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 42ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
```

## Adicionar 1 movimento em todos os pokemons: desvio.

```
Paulo-PC(mongod-3.0.12) be-mean-pokemons> var mod = {$push: {moves: 'desvio'}}
Paulo-PC(mongod-3.0.12) be-mean-pokemons> var query = {}
Paulo-PC(mongod-3.0.12) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 8 existing record(s) in 1ms
WriteResult({
  "nMatched": 8,
  "nUpserted": 0,
  "nModified": 8
})
```

## Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".

```
Paulo-PC(mongod-3.0.12) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}
Paulo-PC(mongod-3.0.12) be-mean-pokemons> var mod = {$set: {active: true}, $setOnInsert: {name: "AindaNaoExisteMon", attack: null, defense: null, type: null, height: null, moves: null, description: "Sem maiores informações"}}
Paulo-PC(mongod-3.0.12) be-mean-pokemons> var options = {upsert: true}
Paulo-PC(mongod-3.0.12) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 18ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("57d7576576ac9eea2c099a24")
})
```

## Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.

```
Paulo-PC(mongod-3.0.12) be-mean-pokemons> var query = {moves: {$in: ['investida']}}
Paulo-PC(mongod-3.0.12) be-mean-pokemons> var poke = {name: 'mew', moves: ['investida']}
Paulo-PC(mongod-3.0.12) be-mean-pokemons> db.pokemons.insert(poke)
Inserted 1 record(s) in 25ms
WriteResult({
  "nInserted": 1
})
Paulo-PC(mongod-3.0.12) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57d0b65537e697e8ef7398c9"),
  "name": "bulbasaur",
  "description": "Pokemon planta",
  "type": "grass",
  "attack": 45,
  "defense": 30,
  "height": 7,
  "moves": [
    "investida",
    "slash",
    "tackle",
    "desvio"
  ]
}
{
  "_id": ObjectId("57d0b65537e697e8ef7398cb"),
  "name": "Charizard",
  "description": "Bicho feio que voa e cospe fogo",
  "type": "fogo",
  "attack": 40,
  "height": 1.7,
  "defense": 30,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57d0b65537e697e8ef7398cc"),
  "name": "Venusaur",
  "description": "There is a large flower on Venusaur's back",
  "type": "plant",
  "attack": 4,
  "defense": 4,
  "height": 6.07,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57d0b65537e697e8ef7398cd"),
  "name": "Charmeleon",
  "description": "Charmeleon fights everywhere!",
  "type": "fire",
  "attack": 3,
  "defense": 3,
  "height": 3.07,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57d4c617fd7d299247d4a5ac"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57d74c2efd7d299247d4a5ad"),
  "name": "Pikachu",
  "attack": 20,
  "defense": 15,
  "height": 0.3,
  "description": "Rato eletrico",
  "moves": [
    "investida",
    "slash",
    "tackle",
    "desvio"
  ]
}
{
  "_id": ObjectId("57d74c78fd7d299247d4a5ae"),
  "name": "Squirtle",
  "attack": 20,
  "defense": 15,
  "height": 0.3,
  "description": "Tartaruga com golpe d'agua",
  "moves": [
    "investida",
    "slash",
    "tackle",
    "desvio"
  ]
}
{
  "_id": ObjectId("57d0b65537e697e8ef7398ca"),
  "name": "Charmander",
  "description": "A chama que arde na ponta da sua cauda é uma indicação das suas emoções",
  "type": "fogo",
  "attack": 30,
  "height": 0.6,
  "defense": 20,
  "moves": [
    "investida",
    "slash",
    "tackle",
    "desvio"
  ]
}
{
  "_id": ObjectId("57d75ad9fd7d299247d4a5af"),
  "name": "mew",
  "moves": [
    "investida"
  ]
}
Fetched 9 record(s) in 2ms
```

## Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```
Paulo-PC(mongod-3.0.12) be-mean-pokemons> var query = {moves: {$in: ['desvio', 'investida', 'tackle']}}
Paulo-PC(mongod-3.0.12) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57d0b65537e697e8ef7398c9"),
  "name": "bulbasaur",
  "description": "Pokemon planta",
  "type": "grass",
  "attack": 45,
  "defense": 30,
  "height": 7,
  "moves": [
    "investida",
    "slash",
    "tackle",
    "desvio"
  ]
}
{
  "_id": ObjectId("57d0b65537e697e8ef7398cb"),
  "name": "Charizard",
  "description": "Bicho feio que voa e cospe fogo",
  "type": "fogo",
  "attack": 40,
  "height": 1.7,
  "defense": 30,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57d0b65537e697e8ef7398cc"),
  "name": "Venusaur",
  "description": "There is a large flower on Venusaur's back",
  "type": "plant",
  "attack": 4,
  "defense": 4,
  "height": 6.07,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57d0b65537e697e8ef7398cd"),
  "name": "Charmeleon",
  "description": "Charmeleon fights everywhere!",
  "type": "fire",
  "attack": 3,
  "defense": 3,
  "height": 3.07,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57d4c617fd7d299247d4a5ac"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57d74c2efd7d299247d4a5ad"),
  "name": "Pikachu",
  "attack": 20,
  "defense": 15,
  "height": 0.3,
  "description": "Rato eletrico",
  "moves": [
    "investida",
    "slash",
    "tackle",
    "desvio"
  ]
}
{
  "_id": ObjectId("57d74c78fd7d299247d4a5ae"),
  "name": "Squirtle",
  "attack": 20,
  "defense": 15,
  "height": 0.3,
  "description": "Tartaruga com golpe d'agua",
  "moves": [
    "investida",
    "slash",
    "tackle",
    "desvio"
  ]
}
{
  "_id": ObjectId("57d0b65537e697e8ef7398ca"),
  "name": "Charmander",
  "description": "A chama que arde na ponta da sua cauda é uma indicação das suas emoções",
  "type": "fogo",
  "attack": 30,
  "height": 0.6,
  "defense": 20,
  "moves": [
    "investida",
    "slash",
    "tackle",
    "desvio"
  ]
}
{
  "_id": ObjectId("57d75ad9fd7d299247d4a5af"),
  "name": "mew",
  "moves": [
    "investida"
  ]
}
Fetched 9 record(s) in 51ms
```

## Pesquisar todos os pokemons que não são do tipo elétrico.

```
Paulo-PC(mongod-3.0.12) be-mean-pokemons> var query = {types: {$nin: ['electric']}}
Paulo-PC(mongod-3.0.12) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57d0b65537e697e8ef7398c9"),
  "name": "bulbasaur",
  "description": "Pokemon planta",
  "type": "grass",
  "attack": 45,
  "defense": 30,
  "height": 7,
  "moves": [
    "investida",
    "slash",
    "tackle",
    "desvio"
  ]
}
{
  "_id": ObjectId("57d0b65537e697e8ef7398cb"),
  "name": "Charizard",
  "description": "Bicho feio que voa e cospe fogo",
  "type": "fogo",
  "attack": 40,
  "height": 1.7,
  "defense": 30,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57d0b65537e697e8ef7398cc"),
  "name": "Venusaur",
  "description": "There is a large flower on Venusaur's back",
  "type": "plant",
  "attack": 4,
  "defense": 4,
  "height": 6.07,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57d0b65537e697e8ef7398cd"),
  "name": "Charmeleon",
  "description": "Charmeleon fights everywhere!",
  "type": "fire",
  "attack": 3,
  "defense": 3,
  "height": 3.07,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57d4c617fd7d299247d4a5ac"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57d74c2efd7d299247d4a5ad"),
  "name": "Pikachu",
  "attack": 20,
  "defense": 15,
  "height": 0.3,
  "description": "Rato eletrico",
  "moves": [
    "investida",
    "slash",
    "tackle",
    "desvio"
  ]
}
{
  "_id": ObjectId("57d74c78fd7d299247d4a5ae"),
  "name": "Squirtle",
  "attack": 20,
  "defense": 15,
  "height": 0.3,
  "description": "Tartaruga com golpe d'agua",
  "moves": [
    "investida",
    "slash",
    "tackle",
    "desvio"
  ]
}
{
  "_id": ObjectId("57d0b65537e697e8ef7398ca"),
  "name": "Charmander",
  "description": "A chama que arde na ponta da sua cauda é uma indicação das suas emoções",
  "type": "fogo",
  "attack": 30,
  "height": 0.6,
  "defense": 20,
  "moves": [
    "investida",
    "slash",
    "tackle",
    "desvio"
  ]
}
{
  "_id": ObjectId("57d75ad9fd7d299247d4a5af"),
  "name": "mew",
  "moves": [
    "investida"
  ]
}
Fetched 9 record(s) in 51ms
```

## Pesquisar todos os pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49.

```
Paulo-PC(mongod-3.0.12) be-mean-pokemons> var query = {$and: [{moves: {$in: ['investida']}}, {defense: {$not: {$lte: 49}}}]}
Paulo-PC(mongod-3.0.12) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57d4c617fd7d299247d4a5ac"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57d75ad9fd7d299247d4a5af"),
  "name": "mew",
  "moves": [
    "investida"
  ]
}
Fetched 2 record(s) in 25ms
```

## Remova todos os pokemons do tipo água e com attack menor que 50.

```
Paulo-PC(mongod-3.0.12) be-mean-pokemons> var query = {$and: [{type: {$in: ['water']}}, {attack: {$lt: 50}}]}
Paulo-PC(mongod-3.0.12) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
Paulo-PC(mongod-3.0.12) be-mean-pokemons> db.pokemons.remove(query)
Removed 0 record(s) in 23ms
WriteResult({
  "nRemoved": 0
})
```
