# MongoDB - Aula 04 - Exercício
autor: Vinicius da Silva Lourenço

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
be-mean-instagram> var query = {name: /pikachu/i}
be-mean-instagram> var mod={$pushAll:{moves:['patada', 'raio']}}
be-mean-instagram> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 4ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

be-mean-instagram> var query = {name: /squirtle/i}
be-mean-instagram> var mod={$pushAll:{moves:['jato de água', 'cabeçada']}}
be-mean-instagram> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

be-mean-instagram> var query = {name: /bulbassauro/i}
be-mean-instagram> var mod={$pushAll:{moves:['chicote de vinhas', 'raio solar']}}
be-mean-instagram> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

be-mean-instagram> var query = {name: /charmander/i}
be-mean-instagram> var mod={$pushAll:{moves:['mordida', 'soco de fogo']}}
be-mean-instagram> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```
be-mean-instagram> var query = {}
be-mean-instagram> var mod={$push:{moves:'desvio'}}
be-mean-instagram> var options={multi:true}
be-mean-instagram> db.pokemons.update(query, mod, options)
Updated 8 existing record(s) in 2ms
WriteResult({
  "nMatched": 8,
  "nUpserted": 0,
  "nModified": 8
})
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
be-mean-instagram> var query = {name: 'AindaNaoExisteMon'}
be-mean-instagram> var mod={
$set:{active:false},
$setOnInsert:{
name:"AindaNaoExisteMon",
description:"Sem maiores informações",
type:null,
attack:null,
defense:null,
height:null
}
}
be-mean-instagram> var options={upsert:true}
be-mean-instagram> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 5ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("56bd31c725dcd4b04ed8462f")
})

```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
be-mean-instagram> var query = {moves:{$all: ['investida', 'soco de fogo']}}
be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56ba657ef10882b9b487255a"),
  "name": "Charmander",
  "description": "Esse pokemon está em chamas",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "mordida",
    "soco de fogo",
    "desvio"
  ]
}
Fetched 1 record(s) in 2ms
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```
be-mean-instagram> var query = {moves:{$in: ['patada', 'raio', 'jato de água', 'cabeçada', 'chicote de vinhas', 'raio solar', 'mordida', 'soco de fogo']}}
be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56ba6455f10882b9b4872558"),
  "name": "Pikachu",
  "description": "Rato elétrico",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "patada",
    "raio",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("56ba651df10882b9b4872559"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "chicote de vinhas",
    "raio solar",
    "desvio"
  ]
}
{
  "_id": ObjectId("56ba657ef10882b9b487255a"),
  "name": "Charmander",
  "description": "Esse pokemon está em chamas",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "mordida",
    "soco de fogo",
    "desvio"
  ]
}
{
  "_id": ObjectId("56ba65bdf10882b9b487255b"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "jato de água",
    "cabeçada",
    "desvio"
  ]
}
Fetched 4 record(s) in 4ms
```
## Pesquisar **todos** os pokemons que não são do tipo `eletric`.##
```
be-mean-instagram> var query= {type:{$ne:'eletric'}}
be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56ba651df10882b9b4872559"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "chicote de vinhas",
    "raio solar",
    "desvio"
  ]
}
{
  "_id": ObjectId("56ba657ef10882b9b487255a"),
  "name": "Charmander",
  "description": "Esse pokemon está em chamas",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "mordida",
    "soco de fogo",
    "desvio"
  ]
}
{
  "_id": ObjectId("56ba65bdf10882b9b487255b"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "jato de água",
    "cabeçada",
    "desvio"
  ]
}
{
  "_id": ObjectId("56ba6718f10882b9b487255c"),
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
  "_id": ObjectId("56bbd66e292ad340b03b4308"),
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "height": 2.1,
  "description": "Pokemon de teste",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56bd1e6e25dcd4b04ed8462d"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56bd1f6925dcd4b04ed8462e"),
  "active": false,
  "name": "NaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56bd31c725dcd4b04ed8462f"),
  "name": "AindaNaoExisteMon",
  "active": false,
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "defense": null,
  "height": null
}
Fetched 8 record(s) in 7ms
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```
be-mean-instagram> var query= {$and:[{moves:{$in:['investida']}}, {defense:{$not:{$lte:49}}}]}
be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56ba6455f10882b9b4872558"),
  "name": "Pikachu",
  "description": "Rato elétrico",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "patada",
    "raio",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("56ba651df10882b9b4872559"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "chicote de vinhas",
    "raio solar",
    "desvio"
  ]
}
{
  "_id": ObjectId("56ba657ef10882b9b487255a"),
  "name": "Charmander",
  "description": "Esse pokemon está em chamas",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "mordida",
    "soco de fogo",
    "desvio"
  ]
}
{
  "_id": ObjectId("56ba65bdf10882b9b487255b"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "jato de água",
    "cabeçada",
    "desvio"
  ]
}
{
  "_id": ObjectId("56bbd66e292ad340b03b4308"),
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "height": 2.1,
  "description": "Pokemon de teste",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56bd1e6e25dcd4b04ed8462d"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56bd1f6925dcd4b04ed8462e"),
  "active": false,
  "name": "NaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações",
  "moves": [
    "investida",
    "desvio"
  ]
}
Fetched 7 record(s) in 5ms
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
be-mean-instagram> var query= {$and:[{type:'água'}, {attack:{$lt:50}}]}
be-mean-instagram> db.pokemons.remove(query)
Removed 1 record(s) in 2ms
WriteResult({
  "nRemoved": 1
})
```
