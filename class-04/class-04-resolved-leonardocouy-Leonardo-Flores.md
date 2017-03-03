# MongoDB - Aula 04 - Exercício
autor: **Leonardo Flores**

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> var query = {name: {$in: ['Pikachu', 'Squirtle', 'Bulbasaur', 'Charmander']}}
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> var mod = {$set: {moves: ['tackle', 'dodge']}}
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> var opt = {multi: true}
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> db.pokemons.update(query, mod, opt)
Updated 4 existing record(s) in 5ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

```
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> var mod = {$addToSet: {moves: "desvio"}}
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> var opt = {multi: true}
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> db.pokemons.update({}, mod, opt)

Updated 610 existing record(s) in 9ms
WriteResult({
  "nMatched": 610,
  "nUpserted": 0,
  "nModified": 610
})
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

```
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> var query = {name: 'AindaNaoExisteMon'}
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> var mod = {$setOnInsert: pokemon}
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> var opt = {upsert: true}
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons>
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> db.pokemons.update(query, mod, opt)
Updated 1 new record(s) in 2ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("56ffb5e428187ac9e5f6b260")
})
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

```
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> var query = {moves: {$all: ['investida', 'tackle']}}
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```

#### Meu pokemon favorito é:

```
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> var query = {name: /pikachu/i}
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
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
    "tackle",
    "dodge",
    "desvio"
  ]
}
Fetched 1 record(s) in 2ms
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

```
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> var query = {moves: {$all: ['dodge', 'tackle', 'desvio']}}
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564b1dad25337263280d047a"),
  "attack": 52,
  "created": "2013-11-03T15:05:41.271082",
  "defense": 43,
  "height": "6",
  "hp": 39,
  "name": "Charmander",
  "speed": 65,
  "types": [
    "fire"
  ],
  "moves": [
    "tackle",
    "dodge",
    "desvio"
  ]
}
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
    "tackle",
    "dodge",
    "desvio"
  ]
}
{
  "_id": ObjectId("564b1db425337263280d04b6"),
  "attack": 48,
  "created": "2013-11-03T15:05:41.278310",
  "defense": 65,
  "height": "5",
  "hp": 44,
  "name": "Squirtle",
  "speed": 43,
  "types": [
    "water"
  ],
  "moves": [
    "tackle",
    "dodge",
    "desvio"
  ]
}
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
    "tackle",
    "dodge",
    "desvio"
  ]
}
Fetched 4 record(s) in 2ms
```

#### Meu pokemon favorito é:

```
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> var query = {name: /pikachu/i}
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
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
    "tackle",
    "dodge",
    "desvio"
  ]
}
Fetched 1 record(s) in 2ms
```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

```
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> var query = {types: {$nin: ['electric']}}
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> var fields = {_id: 0, name: 1, moves: 1}
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query, fields)
{
  "name": "Rattata",
  "moves": [
    "desvio"
  ]
}
{
  "name": "Charmander",
  "moves": [
    "tackle",
    "dodge",
    "desvio"
  ]
}
{
  "name": "Wartortle",
  "moves": [
    "desvio"
  ]
}
{
  "name": "Spearow",
  "moves": [
    "desvio"
  ]
}
{
  "name": "Caterpie",
  "moves": [
    "desvio"
  ]
}
{
  "name": "Metapod",
  "moves": [
    "desvio"
  ]
}
{
  "name": "Kakuna",
  "moves": [
    "desvio"
  ]
}
{
  "name": "Farfetchd",
  "moves": [
    "desvio"
  ]
}
{
  "name": "Blastoise",
  "moves": [
    "desvio"
  ]
}
{
  "name": "Charmeleon",
  "moves": [
    "desvio"
  ]
}
{
  "name": "Butterfree",
  "moves": [
    "desvio"
  ]
}
{
  "name": "Seel",
  "moves": [
    "desvio"
  ]
}
{
  "name": "Doduo",
  "moves": [
    "desvio"
  ]
}
{
  "name": "Gastly",
  "moves": [
    "desvio"
  ]
}
{
  "name": "Dodrio",
  "moves": [
    "desvio"
  ]
}
{
  "name": "Dewgong",
  "moves": [
    "desvio"
  ]
}
{
  "name": "Cloyster",
  "moves": [
    "desvio"
  ]
}
{
  "name": "Muk",
  "moves": [
    "desvio"
  ]
}
{
  "name": "Poliwhirl",
  "moves": [
    "desvio"
  ]
}
{
  "name": "Poliwag",
  "moves": [
    "desvio"
  ]
}
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

```
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> var query = {$and: [{moves: {$in: ['investida']}}, {defense: {$not: {$lte: 49}}}]}
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> var query = {$and: [{types: 'water'}, {attack: {$lt: 50}}]}
MBP-de-Leonardo(mongod-3.2.1) be-mean-pokemons> db.pokemons.remove(query)
Removed 21 record(s) in 3ms
WriteResult({
  "nRemoved": 21
})
```