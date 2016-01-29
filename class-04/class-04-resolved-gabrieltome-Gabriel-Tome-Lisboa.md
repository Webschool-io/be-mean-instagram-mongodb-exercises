# MongoDB - Aula 04 - Exercício
autor: Gabriel Tomé

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> var query = { $or: [{name: /Pikachu/i},{name: /Squirtle/i},{name: /Bulbassauro/i},{name: /Charmander/i}]}
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> query
{
  "$or": [
    {
      "name": /Pikachu/i
    },
    {
      "name": /Squirtle/i
    },
    {
      "name": /Bulbassauro/i
    },
    {
      "name": /Charmander/i
    }
  ]
}
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> mod
{
  "$pushAll": {
    "moves": [
      "Choque",
      "Punch"
    ]
  }
}


```


## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

```
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> var query = {}

MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> var mod = {$set: {moves: 'desvio'}}

MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> var options = {multi:true}

MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> db.pokemons.update(query,mod,options)
Updated 5 existing record(s) in 273ms
WriteResult({
  "nMatched": 5,
  "nUpserted": 0,
  "nModified": 5
})
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

```
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}

MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> var mod = {$setOnInsert: {name:null,attack:null,defense:null,height:null,description:"Sem maiores informações"}}
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> mod
{
  "$setOnInsert": {
    "name": null,
    "attack": null,
    "defense": null,
    "height": null,
    "description": "Sem maiores informações"
  }
}

MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> var options = {upsert:true}

MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> db.pokemons.update(query,mod,options)
Updated 1 new record(s) in 130ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("56658849de67f95581ddd1f9")
})

MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56658849de67f95581ddd1f9"),
  "name": null,
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 1 record(s) in 2ms
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##


```
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> var query = {moves: {$in: [/desvio/i,/investida/i]}}
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> query
{
  "moves": {
    "$in": [
      /desvio/i,
      /investida/i
    ]
  }
}
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> db.pokemons.find(query)

```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

```
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> var query = {moves: {$in: ['Armlock','Hadouken']}}
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56551778c6086b7b42449018"),
  "name": "Magikarp",
  "description": "Quem nasceu pra Magikarp nunca será um Gyarados",
  "type": "Água",
  "attack": 10,
  "defense": 10,
  "height": 0.5,
  "active": false,
  "moves": [
    "Armlock",
    "Hadouken"
  ]
}
Fetched 1 record(s) in 4ms

```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

```
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> var query = {type: {$not: [/elétrico/i]}}
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> db.pokemons.find(query)


```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

```
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> var query = {$and: [{attack:"investida"},{defense:{$gt:49}}]}
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms

```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> var query = {$and: [{type:"água"},{attack:{$lt:50}}]}
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> query
{
  "$and": [
    {
      "type": "água"
    },
    {
      "attack": {
        "$lt": 50
      }
    }
  ]
}
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> db.pokemons.remove(query)
Removed 0 record(s) in 4ms
WriteResult({
  "nRemoved": 0
})

```