# MongoDB - Aula 04 - Exercício
autor: Dayvson Sales

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```javascript
var query = {$or: [{name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbassauro/i}, {name: /charmander/i}]}  
var mod = {$pushAll: {moves: ['ninja', 'solta fogo']}}  
db.pokemons.update(query, mod)  
Updated 1 record(s) in 1ms  
```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```javascript
var query = {}  
var mod = {$pushAll: {moves: ['desvio']}}  
var options = {multi: true}  
db.pokemons.update(query, mod, options)  
Updated 1 record(s) in 1ms  
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```javascript
var query = {name: /AindaNaoExisteMon/i}  
var mod = {$setOnInsert: {  
  name: "AindaNaoExisteMon"  
  , attack: null  
  , height: null  
  , defense: null  
  , moves: []  
  , description: "Sem maiores informações"  
}}  
var options = {upsert: true}  
db.pokemons.update(query, mod, options)  
Updated 1 new record(s) in 2ms  
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```javascript
var query = {moves: {$in: ['investida', 'desvio']}}  
db.pokemons.find(query)  
{
  "_id": ObjectId("564cc53fb129ddfeb2964098"),
  "moves": [
    "desvio"
  ],
  "name": "pika"
}

```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```javascript
var query = {moves: {$in: ['desvio']}}  
db.pokemons.find(query)  
{
  "_id": ObjectId("564cc53fb129ddfeb2964098"),
  "moves": [
    "desvio"
  ],
  "name": "pika"
}
```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```javascript
var query = {moves: {$nin: ['eletrico']}}  
db.pokemons.find(query)  
{
  "_id": ObjectId("564cc53fb129ddfeb2964098"),
  "moves": [
    "desvio"
  ],
  "name": "pika"
}
{
  "_id": ObjectId("564cc6cdd291f795f4e7bf4a"),
  "attack": null,
  "defense": null,
  "description": "Sem maiores informações",
  "height": null,
  "moves": [ ],
  "name": "AindaNaoExisteMon"
}
Fetched 2 record(s) in 1ms

```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```javascript
var query = {  
  "$and": [  
    {  
      "moves": {  
        "$in": [    
          "investida"  
        ]  
      }  
    },  
    {  
      "defense": {  
        "$lte": 49  
      }  
    }  
  ]  
}  
db.pokemons.find(query)  
Fetched 0 record(s) in 0ms
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```javascript
var query = {$and: [{type: {$in: ['agua']}}, {attack: {$lt: 50}}]}  
db.pokemons.remove(query)  
Removed 0 record(s) in 1ms
```

