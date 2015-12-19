# MongoDB - Aula 04 - Exercício
autor: Franklin Dias

## 1. Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons, Bulbassauro e Charmander.

```javascript
localhost(mongod-2.6.11) pokemons> var query = { $or: [ {name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbassauro/i}, {name: /charmander/i} ]}
localhost(mongod-2.6.11) pokemons> var mod = { $inc: { attack: 2}}
localhost(mongod-2.6.11) pokemons> var options = { multi: true}
localhost(mongod-2.6.11) pokemons> db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 2ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})

```

## 2. Adicionar 1 movimento em todos os pokemons: 'desvio'.

```javascript
localhost(mongod-2.6.11) pokemons> var query = {}
localhost(mongod-2.6.11) pokemons> var mod = {$push: {moves: 'desvio'}}
localhost(mongod-2.6.11) pokemons> var options = {multi:true}
localhost(mongod-2.6.11) pokemons> db.pokemons.update(query, mod, options)
Updated 7 existing record(s) in 3ms
WriteResult({
  "nMatched": 7,
  "nUpserted": 0,
  "nModified": 7
})
```

## 3. Adicionar o pokemon 'AindaNaoExisteMon' caso ele nao exista com todos os dados com o valor 'null' e a descricao: 'Sem maiores informacoes'.

```javascript
localhost(mongod-2.6.11) pokemons> var query = { nome: /AindaNaoExisteMon/i}
localhost(mongod-2.6.11) pokemons> var mod = {
         $setOnInsert :
             {
               "active": false,
               "nome": "AindaNaoExisteMon",
               "attack": null,
               "defense": null,
               "height": null,
               "description": "Sem maiores informações",
             }
     }
localhost(mongod-2.6.11) pokemons> var options = { upsert: true}
localhost(mongod-2.6.11) pokemons> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 2ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564cc152f8f1603abb41c84c")
})
```

## 4. Pesquisar todos os pokemons que possuam o ataque 'investida' e mais um que voce adicionou, escolha seu pokemon favorito.

```javascript
localhost(mongod-2.6.11) pokemons> var query = { moves: { $all:  ["investida", "refletir dano"]}}
localhost(mongod-2.6.11) pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564352f48b7f0c7f55da6513"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 54,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "refletir dano",
    "jogar laminas",
    "desvio"
  ]
}
{
  "_id": ObjectId("56435395a887a8736a8f27d5"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 50,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "refletir dano",
    "jogar laminas",
    "desvio"
  ]
}

Fetched 2 record(s) in 1ms
```


## 5. Pesquisar todos os pokemons que possuam os ataques que voce adicionou, escolha seu pokemon favorito.

```javascript
localhost(mongod-2.6.11) pokemons> var query = { moves: { $all: ["investida", "refletir dano", "desvio"]}}
localhost(mongod-2.6.11) pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564352f48b7f0c7f55da6513"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 54,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "refletir dano",
    "jogar laminas",
    "desvio"
  ]
}
{
  "_id": ObjectId("56435395a887a8736a8f27d5"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 50,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "refletir dano",
    "jogar laminas",
    "desvio"
  ]
}

Fetched 2 record(s) in 1ms
```1

## 6. Pesquisar todos os pokemons que nao sao do tipo 'eletrico'.

```javascript
localhost(mongod-2.6.11) pokemons> var query = { type: {$ne: "electric"}}
localhost(mongod-2.6.11) pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56435452a887a8736a8f27d6"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",1
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564cae1db25c89b0f63ed471"),
  "description": "Mudei a descricao",
  "name": "Testmon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564cb6bbf8f1603abb41c84a"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564352f48b7f0c7f55da6513"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 54,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "refletir dano",
    "jogar laminas",
    "desvio"
  ]
}
{
  "_id": ObjectId("56435395a887a8736a8f27d5"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 50,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "refletir dano",
    "jogar laminas",
    "desvio"
  ]
}
{
  "_id": ObjectId("564352e58b7f0c7f55da6512"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 51,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "refletir dano",
    "jogar laminas",
    "desvio"
  ]
}
{
  "_id": ObjectId("564cc152f8f1603abb41c84c"),
  "active": false,
  "nome": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 7 record(s) in 5ms

```

## 7. Pesquisar todos os pokemons que tenha o ataque 'investida' E tenham a defesa nao menor ou igual a  49.

```javascript
localhost(mongod-2.6.11) pokemons> var query1 = { $all: ["investida"]}
localhost(mongod-2.6.11) pokemons> var query2 = { $not: { $gte: 49}}
localhost(mongod-2.6.11) pokemons> var query = { moves: query1, attack: query2 }
localhost(mongod-2.6.11) pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56435452a887a8736a8f27d6"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564cb6bbf8f1603abb41c84a"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
Fetched 2 record(s) in 1ms
```

## 8. Remova todos os pokemons do tipo agua e com attack menor que 50.

```javascript
localhost(mongod-2.6.11) pokemons> var query = { $and: [ { type: "água"},{ attack: { $lt: 50}} ] }
localhost(mongod-2.6.11) pokemons> db.pokemons.remove(query)
Removed 0 record(s) in 2ms
WriteResult({
  "nRemoved": 0
})

```

