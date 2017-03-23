# MongoDB - Aula 04 - Exercício
autor: Mariela Atausinchi

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
cem-008046106(mongod-3.4.2) test> var attacks =  ["Losango aberto","Voadora quantica"]
cem-008046106(mongod-3.4.2) test> var mod = {$pushAll:{moves:attacks}}
cem-008046106(mongod-3.4.2) test> var query = {$or : [{name:'Pikachu'}, {name:'Squirtle'}, {name:'Bulbassauro'}, {name: 'Charmander'}]}
cem-008046106(mongod-3.4.2) test> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})


```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

```
cem-008046106(mongod-3.4.2) test> var mod = {$push:{moves: 'desvio'}}
cem-008046106(mongod-3.4.2) test> var query = {}
cem-008046106(mongod-3.4.2) test> var options = {multi: true}
cem-008046106(mongod-3.4.2) test> db.pokemons.update(query, mod, options)
Updated 6 existing record(s) in 1ms
WriteResult({
  "nMatched": 6,
  "nUpserted": 0,
  "nModified": 6
})


```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

```
cem-008046106(mongod-3.4.2) test> var query = {name: /AindaNaoExisteMon/i}
cem-008046106(mongod-3.4.2) test> var mod = {$setOnInsert :{name: 'AindaNaoExisteMon', description: 'Sem maiores informações', type:null, attack:null, defense:null, height:null}}
cem-008046106(mongod-3.4.2) test> var options = {upsert: true}
cem-008046106(mongod-3.4.2) test> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 1ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("58c704386498c5d5cf95ef1e")
})


```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

```
cem-008046106(mongod-3.4.2) test> var query = {moves: /investida/i}
cem-008046106(mongod-3.4.2) test> db.pokemons.find(query)
{
  "_id": ObjectId("58c68ca6cf14125a4c53faf5"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "desvio"
  ]
}
{
  "_id": ObjectId("58c68cbacf14125a4c53faf6"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "desvio"
  ]
}
{
  "_id": ObjectId("58c68cd3cf14125a4c53faf7"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "desvio"
  ]
}
{
  "_id": ObjectId("58c6c041dd752d2fd37398aa"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "moves": [
    "investida",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("58c6ddc76498c5d5cf95ed17"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("58c68bd8cf14125a4c53faf4"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "Losango aberto",
    "Voadora quantica",
    "desvio"
  ],
  "active": false
}
Fetched 6 record(s) in 0ms


```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

```
cem-008046106(mongod-3.4.2) test> var query = {moves: {$in [/Losango aberto/i,/Voadora quantica/i]}}
2017-03-13T17:50:27.487-0300 E QUERY    [thread1] SyntaxError: missing : after property id @(shell):1:25
cem-008046106(mongod-3.4.2) test> var query = {moves: {$in: [/Losango aberto/i,/Voadora quantica/i]}}
cem-008046106(mongod-3.4.2) test> db.pokemons.find(query)
{
  "_id": ObjectId("58c68bd8cf14125a4c53faf4"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "Losango aberto",
    "Voadora quantica",
    "desvio"
  ],
  "active": false
}
Fetched 1 record(s) in 0ms


```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

```

cem-008046106(mongod-3.4.2) test> var query = {type: {$ne: "elétrico"}}
cem-008046106(mongod-3.4.2) test> db.pokemons.find(query)
{
  "_id": ObjectId("58c68ca6cf14125a4c53faf5"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "desvio"
  ]
}
{
  "_id": ObjectId("58c68cbacf14125a4c53faf6"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "desvio"
  ]
}
{
  "_id": ObjectId("58c68cd3cf14125a4c53faf7"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "desvio"
  ]
}
{
  "_id": ObjectId("58c6c041dd752d2fd37398aa"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "moves": [
    "investida",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("58c6ddc76498c5d5cf95ed17"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("58c704386498c5d5cf95ef1e"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "defense": null,
  "height": null
}
Fetched 6 record(s) in 1ms


```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

```
cem-008046106(mongod-3.4.2) test> var query = {$and:[{moves:{$in:["investida"]}},{defense:{$not:{$lte:49}}}]}
cem-008046106(mongod-3.4.2) test> db.pokemons.find(query)
{
  "_id": ObjectId("58c68ca6cf14125a4c53faf5"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "desvio"
  ]
}
{
  "_id": ObjectId("58c68cbacf14125a4c53faf6"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "desvio"
  ]
}
{
  "_id": ObjectId("58c68cd3cf14125a4c53faf7"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "desvio"
  ]
}
{
  "_id": ObjectId("58c6c041dd752d2fd37398aa"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "moves": [
    "investida",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("58c6ddc76498c5d5cf95ed17"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("58c68bd8cf14125a4c53faf4"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "elétrico",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "Losango aberto",
    "Voadora quantica",
    "desvio"
  ],
  "active": false
}
Fetched 6 record(s) in 3ms



```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
cem-008046106(mongod-3.4.2) test> var query = {$and:[{type: 'água'},{attack: {$lt: 50}}]}
cem-008046106(mongod-3.4.2) test> db.pokemons.find(query)
{
  "_id": ObjectId("58c68cd3cf14125a4c53faf7"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "desvio"
  ]
}
Fetched 1 record(s) in 0ms
cem-008046106(mongod-3.4.2) test> db.pokemons.remove(query)
Removed 1 record(s) in 1ms
WriteResult({
  "nRemoved": 1
})
cem-008046106(mongod-3.4.2) test> db.pokemons.find(query)
Fetched 0 record(s) in 0ms


```
