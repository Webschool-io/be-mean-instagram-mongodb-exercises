# MongoDB - Aula 04 - Exercício
autor: Romulo Mourão

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```

rmourao(mongod-3.0.7) be-mean-pokemons> var query = {name: /Pikachu/i}
rmourao(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll: {moves: ['trovoada', 'arranhão']}}
rmourao(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 20ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})


rmourao(mongod-3.0.7) be-mean-pokemons> var query = {name: /Squirtle/i}
rmourao(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll: {moves: ['jato de agua', 'cabeçada']}}
rmourao(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 13ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})


rmourao(mongod-3.0.7) be-mean-pokemons> var query = {name: /Bulbassauro/i}
rmourao(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll: {moves: ['raio solar', 'chicote']}}
rmourao(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 13ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})


rmourao(mongod-3.0.7) be-mean-pokemons> var query = {name: /Charmander/i}
rmourao(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll: {moves: ['bola de fogo', 'mordida']}}
rmourao(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 3ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

```
## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

```
rmourao(mongod-3.0.7) be-mean-pokemons> var query = {}
rmourao(mongod-3.0.7) be-mean-pokemons> var mod =  {$push:{moves:'desvio'}}
rmourao(mongod-3.0.7) be-mean-pokemons> var options = {multi:true}
rmourao(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query,mod,options)
Updated 10 existing record(s) in 3ms
WriteResult({
  "nMatched": 10,
  "nUpserted": 0,
  "nModified": 10
})

```
## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
rmourao(mongod-3.0.7) be-mean-pokemons> var query = {name: 'AindaNaoExisteMon'}
rmourao(mongod-3.0.7) be-mean-pokemons> var mod = {$setOnInsert: {name: 'AindaNaoExisteMon', type: null, attack: null, defense: null, height: null, description: 'Sem maiores informações'}}
rmourao(mongod-3.0.7) be-mean-pokemons> var options = {upsert:true}
rmourao(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query,mod,options)
Updated 1 new record(s) in 3ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("5650731f80bb33ff29a56f20")
})

```
## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
rmourao(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$in: [/investida/i,/cabeçada/i]}}
rmourao(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 10 record(s) in 10ms


```
## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```
rmourao(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$all: [/raio solar/i,/chicote/i]}}
rmourao(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5644c90a2ea0618e48bdc922"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "raio solar",
    "chicote",
    "desvio"
  ]
}
Fetched 1 record(s) in 1ms


```
## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```
rmourao(mongod-3.0.7) be-mean-pokemons> var query = {type: {$not: /elétrico/i}}
rmourao(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56439264ec4acad482954439"),
  "name": "articuno",
  "description": "Pavão azul de gelo",
  "defense": 50,
  "height": 1.5,
  "attack": 50,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56439264ec4acad48295443a"),
  "name": "aerodactyl",
  "description": "dragão voador",
  "defense": 49,
  "height": 7.3,
  "attack": 47,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56439264ec4acad48295443b"),
  "name": "porygon",
  "description": "bicho estranho",
  "defense": 35,
  "height": 1.3,
  "attack": 30,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56439264ec4acad48295443c"),
  "name": "umbreon",
  "description": "raposa preta",
  "defense": 40,
  "height": 2.4,
  "attack": 56,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644c90a2ea0618e48bdc922"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "raio solar",
    "chicote",
    "desvio"
  ]
}
{
  "_id": ObjectId("564a3e8750be0b4503793e6b"),
  "description": "pokemons de teste",
  "name": "Testmon",
  "attack": 8101,
  "defense": 8000,
  "moves": [
    "investida",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("5644c90a2ea0618e48bdc923"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança chamas",
    "bola de fogo",
    "mordida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644c90a2ea0618e48bdc924"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "jato de agua",
    "cabeçada",
    "desvio"
  ]
}
{
  "_id": ObjectId("5650731f80bb33ff29a56f20"),
  "name": "AindaNaoExisteMon",
  "type": null,
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 9 record(s) in 5ms


```
## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```
rmourao(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{moves:{$in:['investida']}},{attack: {$not:{$lte: 49}}}]}
rmourao(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56439264ec4acad482954438"),
  "name": "zapdos",
  "description": "Passaro elétrico",
  "defense": 50,
  "height": 2.3,
  "attack": 60,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ],
  "type": "elétrico"
}
{
  "_id": ObjectId("56439264ec4acad482954439"),
  "name": "articuno",
  "description": "Pavão azul de gelo",
  "defense": 50,
  "height": 1.5,
  "attack": 50,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56439264ec4acad48295443c"),
  "name": "umbreon",
  "description": "raposa preta",
  "defense": 40,
  "height": 2.4,
  "attack": 56,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564a3e8750be0b4503793e6b"),
  "description": "pokemons de teste",
  "name": "Testmon",
  "attack": 8101,
  "defense": 8000,
  "moves": [
    "investida",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("5644c90a2ea0618e48bdc923"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança chamas",
    "bola de fogo",
    "mordida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644c90a2ea0618e48bdc921"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "Elétrico",
  "attack": 55,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "choque do trovão",
    "trovoada",
    "arranhão",
    "desvio"
  ]
}
Fetched 6 record(s) in 3ms

```
## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
rmourao(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{type: /água/i}, {attack: {$lt:50}}]}
rmourao(mongod-3.0.7) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 2ms
WriteResult({
  "nRemoved": 1
})

```
