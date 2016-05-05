# MongoDB - Aula 04 - Exercício
autor: Raphael Lima

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.##
```
var query = { name: {$in: [/pikachu/i,/squirtle/i,/bulbassauro/i,/charmander/i]}};
var mod = { $pushAll: { moves: ['corrida','soco']}};
var opt = { multi: true };
debian(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, opt)
Updated 4 existing record(s) in 3ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```
debian(mongod-3.0.7) be-mean-pokemons> var query = {}
debian(mongod-3.0.7) be-mean-pokemons> var mod = {$push: {moves: "desvio"}}
debian(mongod-3.0.7) be-mean-pokemons> var opt = {multi: true}
debian(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, opt)
Updated 9 existing record(s) in 2ms
WriteResult({
  "nMatched": 9,
  "nUpserted": 0,
  "nModified": 9
})

```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
var query = { name: /AindaNaoExisteMon/i }
var mod = {
  "$setOnInsert": {
    "name": "Ainda nao existe mon",
    "attack": null,
    "defense": null,
    "height": null,
    "description": "Sem maiores informações",
    "type": null
  }
}
var opts = { upsert: true }
debian(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, opt)
Updated 1 new record(s) in 6ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("5650aa3c5c3f6add48d15142")
})
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
debian(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$all: ['investida','soco']}}
debian(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5650a19b5c3f6add48d1513e"),
  "name": "Pikachu",
  "attack": 100,
  "height": 0.5,
  "defense": 200,
  "description": "Rato Eletrico",
  "type": "eletrico",
  "moves": [
    "corrida",
    "soco",
    "desvio",
    "investida"
  ]
}
Fetched 1 record(s) in 1ms
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```
debian(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$in: ['soco']}}
debian(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5650a19b5c3f6add48d1513e"),
  "name": "Pikachu",
  "attack": 100,
  "height": 0.5,
  "defense": 200,
  "description": "Rato Eletrico",
  "type": "eletrico",
  "moves": [
    "corrida",
    "soco",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("5650a37d5c3f6add48d1513f"),
  "name": "Squirtle",
  "attack": 100,
  "height": 0.8,
  "defense": 80,
  "description": "Solta jato de aguaa",
  "type": "agua",
  "moves": [
    "corrida",
    "soco",
    "desvio"
  ]
}
{
  "_id": ObjectId("5650a3d25c3f6add48d15140"),
  "name": "Bulbassauro",
  "attack": 100,
  "height": 0.8,
  "defense": 80,
  "description": "Chicote de cipo",
  "type": "grama",
  "moves": [
    "corrida",
    "soco",
    "desvio"
  ]
}
{
  "_id": ObjectId("5650a4185c3f6add48d15141"),
  "name": "Charmander",
  "attack": 3100,
  "height": 0.4,
  "defense": 80,
  "description": "Cospe fogo",
  "type": "fogo",
  "moves": [
    "corrida",
    "soco",
    "desvio"
  ]
}
Fetched 4 record(s) in 2ms
```

##Pesquisar **todos** os pokemons que não são do tipo `eletrico`##
```
debian(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5647fad53b616ac39c6286dc"),
  "name": "Blastoise",
  "description": "Blastoise has water spouts that protrude from its shell",
  "type": "water",
  "attack": 85,
  "height": 16,
  "moves": [
    "desvio",
    "desvio",
    "desvio",
    "desvio"
  ]
}
{
  "_id": ObjectId("5647fb2f3b616ac39c6286dd"),
  "name": "Charizard",
  "description": "Charizard flies around the sky in search of powerful opponents",
  "type": "fire",
  "attack": 109,
  "height": 17,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5647fb363b616ac39c6286de"),
  "name": "Beedrill",
  "description": "Beedrill is extremely territorial",
  "type": "flying",
  "attack": 45,
  "height": 10,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5647fb3c3b616ac39c6286df"),
  "name": "Scizor",
  "description": "Scizor is a bipedal, insectoid Pokémon with a red, metallic exoskeleton. It has gray, retractable forewings and hind wings with simple, curved venation",
  "attack": 999,
  "defense": 999,
  "height": 33.33,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5647fb413b616ac39c6286e0"),
  "name": "Raticate",
  "description": "Mudança da descrição para atender o exercício",
  "type": "normal",
  "attack": 50,
  "height": 7,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5650a37d5c3f6add48d1513f"),
  "name": "Squirtle",
  "attack": 100,
  "height": 0.8,
  "defense": 80,
  "description": "Solta jato de aguaa",
  "type": "agua",
  "moves": [
    "corrida",
    "soco",
    "desvio"
  ]
}
{
  "_id": ObjectId("5650a3d25c3f6add48d15140"),
  "name": "Bulbassauro",
  "attack": 100,
  "height": 0.8,
  "defense": 80,
  "description": "Chicote de cipo",
  "type": "grama",
  "moves": [
    "corrida",
    "soco",
    "desvio"
  ]
}
{
  "_id": ObjectId("5650a4185c3f6add48d15141"),
  "name": "Charmander",
  "attack": 3100,
  "height": 0.4,
  "defense": 80,
  "description": "Cospe fogo",
  "type": "fogo",
  "moves": [
    "corrida",
    "soco",
    "desvio"
  ]
}
{
  "_id": ObjectId("5650aa3c5c3f6add48d15142"),
  "name": "Ainda nao existe mon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações",
  "type": null
}
Fetched 9 record(s) in 2ms
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```
debian(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{moves: {$in: ["investida"]}},{defense: {$gt: 49}}]}
debian(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5650a19b5c3f6add48d1513e"),
  "name": "Pikachu",
  "attack": 100,
  "height": 0.5,
  "defense": 200,
  "description": "Rato Eletrico",
  "type": "eletrico",
  "moves": [
    "corrida",
    "soco",
    "desvio",
    "investida"
  ]
}
Fetched 1 record(s) in 1ms
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
debian(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{type: "agua"}, {attack: {$lt: 50}}]}
debian(mongod-3.0.7) be-mean-pokemons> db.pokemons.remove(query)
Removed 0 record(s) in 4ms
WriteResult({
  "nRemoved": 0
})
```
