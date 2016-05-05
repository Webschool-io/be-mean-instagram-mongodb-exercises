# MongoDB - Aula 04 - Exercício
autor: **PABLO BOZZI FLORES OLIVEIRA**

## 1. Todos os pokemons
```
mean(mongod-3.0.7) be-mean> var query={}
mean(mongod-3.0.7) be-mean> db.pokemons.find(query)
{
  "_id": ObjectId("56429e14b01582a9e4951d61"),
  "name": "Pickachu",
  "description": "Raio elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "choque do trovão"
  ]
}
{
  "_id": ObjectId("56429e6eb01582a9e4951d62"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha"
  ]
}
{
  "_id": ObjectId("56429ea8b01582a9e4951d63"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.8,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas"
  ]
}
{
  "_id": ObjectId("5642a5eab01582a9e4951d65"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "active": false,
  "moves": [
    "investida"
  ]
}
{
  "_id": ObjectId("564cfcaa72218c8b0cd21a5e"),
  "active": false,
  "moves": [
    "investida"
  ]
}
{
  "_id": ObjectId("5642a495b01582a9e4951d64"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba"
  ]
}
Fetched 6 record(s) in 18ms
```

## 2. Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pickachu, Squirtle, Bulbassauro e Charmander
```
mean(mongod-3.0.7) be-mean> var query={$or:[{name:/pikachu/i},{name:/squirtle/i},{name:/bulbassauro/i},{name:/charmander/i}]};
mean(mongod-3.0.7) be-mean> var mod={$pushAll:{moves:['ataque1','ataque2']}};
mean(mongod-3.0.7) be-mean> var options={multi:true};
mean(mongod-3.0.7) be-mean> db.pokemons.update(query,mod,options)
Updated 3 existing record(s) in 1ms
WriteResult({
  "nMatched": 3,
  "nUpserted": 0,
  "nModified": 3
})
mean(mongod-3.0.7) be-mean> db.pokemons.find(query)
{
  "_id": ObjectId("56429e6eb01582a9e4951d62"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "ataque1",
    "ataque2"
  ]
}
{
  "_id": ObjectId("56429ea8b01582a9e4951d63"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.8,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "ataque1",
    "ataque2"
  ]
}
{
  "_id": ObjectId("5642a495b01582a9e4951d64"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "ataque1",
    "ataque2"
  ]
}
Fetched 3 record(s) in 2ms
```

## 3. Adicionar 1 movimento em todos os pokemons: desvio
```
mean(mongod-3.0.7) be-mean> var query={}
mean(mongod-3.0.7) be-mean> var mod={$push:{moves:'desvio'}}
mean(mongod-3.0.7) be-mean> var options={multi:true}
mean(mongod-3.0.7) be-mean> db.pokemons.update(query,mod,options)
Updated 6 existing record(s) in 1ms
WriteResult({
  "nMatched": 6,
  "nUpserted": 0,
  "nModified": 6
})
mean(mongod-3.0.7) be-mean> db.pokemons.find(query)
{
  "_id": ObjectId("56429e14b01582a9e4951d61"),
  "name": "Pickachu",
  "description": "Raio elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "choque do trovão",
    "desvio"
  ]
}
{
  "_id": ObjectId("56429e6eb01582a9e4951d62"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "ataque1",
    "ataque2",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a5eab01582a9e4951d65"),
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
  "_id": ObjectId("564cfcaa72218c8b0cd21a5e"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56429ea8b01582a9e4951d63"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.8,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "ataque1",
    "ataque2",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a495b01582a9e4951d64"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "ataque1",
    "ataque2",
    "desvio"
  ]
}
Fetched 6 record(s) in 4ms
```

## 4. Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com valor null e a descrição: Sem maiores informações
```
mean(mongod-3.0.7) be-mean> var query={name:/AindaNaoExisteMon/i}
mean(mongod-3.0.7) be-mean> var mod={$setOnInsert:{name:'AindaNaoExisteMon',attack:null,height:null,defense:null,moves:null,description:'Sem maiores informações'}}
mean(mongod-3.0.7) be-mean> var options={upsert:true}
mean(mongod-3.0.7) be-mean> db.pokemons.update(query,mod,options)
Updated 1 new record(s) in 1ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564d1c5d72218c8b0cd21a60")
})
mean(mongod-3.0.7) be-mean> db.pokemons.find(query)
{
  "_id": ObjectId("564d1c5d72218c8b0cd21a60"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "height": null,
  "defense": null,
  "moves": null,
  "description": "Sem maiores informações"
}
Fetched 1 record(s) in 1ms
```

## 5. Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito
```
mean(mongod-3.0.7) be-mean> var query={moves:{$in:['ataque1','ataque2']}}
mean(mongod-3.0.7) be-mean> db.pokemons.find(query)
{
  "_id": ObjectId("56429e6eb01582a9e4951d62"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "ataque1",
    "ataque2",
    "desvio"
  ]
}
{
  "_id": ObjectId("56429ea8b01582a9e4951d63"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.8,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "ataque1",
    "ataque2",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a495b01582a9e4951d64"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "ataque1",
    "ataque2",
    "desvio"
  ]
}
Fetched 3 record(s) in 2ms
```

## 6. Pesquisar todos os pokemons que não são do tipo 'elétrico'
```
mean(mongod-3.0.7) be-mean> var query={type:{$not:/eletric/i}}
mean(mongod-3.0.7) be-mean> db.pokemons.find(query)
{
  "_id": ObjectId("56429e6eb01582a9e4951d62"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "ataque1",
    "ataque2",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a5eab01582a9e4951d65"),
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
  "_id": ObjectId("564cfcaa72218c8b0cd21a5e"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56429ea8b01582a9e4951d63"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.8,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "ataque1",
    "ataque2",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a495b01582a9e4951d64"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "ataque1",
    "ataque2",
    "desvio"
  ]
}
{
  "_id": ObjectId("564d1c5d72218c8b0cd21a60"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "height": null,
  "defense": null,
  "moves": null,
  "description": "Sem maiores informações"
}
Fetched 6 record(s) in 2ms
```

## 7. Pesquisar todos os pokemons que tenham o ataque 'investida' e tenham a defesa não menor ou igual a 49
```
mean(mongod-3.0.7) be-mean> var query={$and:[{moves:{$in:[/investida/i]}},{defense:{$gt:49}}]}
mean(mongod-3.0.7) be-mean> query
{
  "$and": [
    {
      "moves": {
        "$in": [
          /investida/i
        ]
      }
    },
    {
      "defense": {
        "$gt": 49
      }
    }
  ]
}
mean(mongod-3.0.7) be-mean> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
```

## 8. Remova todos os pokemons do tipo 'água' e com ataque menor que 50
```
mean(mongod-3.0.7) be-mean> var query={$and:[{type:/água/i},{attack:{$lt:50}}]}
mean(mongod-3.0.7) be-mean> query
{
  "$and": [
    {
      "type": /água/i
    },
    {
      "attack": {
        "$lt": 50
      }
    }
  ]
}
mean(mongod-3.0.7) be-mean> db.pokemons.remove(query)
Removed 1 record(s) in 2ms
WriteResult({
  "nRemoved": 1
})
```

## 9. Diferença entre os operadores `$ne` e `$not`

O operador `$not` é o operador lógico **NÃO**, logo ele nega uma expressão. 
Sintaxe: { <campo>: { $not: { <expressão> } } }
Ex:

### 9.1. Quantidade de pokemons cuja defesa NÃO é menor que 75
```
mean(mongod-3.0.7) be-mean> db.pokemons.count({defense:{$not:{$lt:75}}})
244
```

Logo 244 de 610 pokemons possuem defesa maior ou igual a 75.

Já o operador `$ne` seleciona os documentos onde o valor do campo não é igual (**!=**) ao valor especificado.
Sintaxe: db.pokemons.find( { <campo>: { $ne: <valor> } } )

### 9.2. Quantidade de pokemons cuja defesa é diferente de 75
```
mean(mongod-3.0.7) be-mean> db.pokemons.count({defense:{$ne:75}})
590
```

Logo 590 de 610 pokemons possuem defesa diferente de 75.
