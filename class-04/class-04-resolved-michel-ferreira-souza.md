# MongoDB - Aula 04 - Exercício
autor: [Michel Ferreira Souza](https://github.com/souzacristsf)  

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

``` 
Souza(mongod-3.0.8) be-mean-instagram> var attacks = ['Chupa essa manga', 'Vai cagar um coco']
Souza(mongod-3.0.8) be-mean-instagram> var query = {$or: [{name: /pikachu/i}, {name: /Squirtle/i}, {name: /Bulbassauro/i}, {name: /Charmander/i}]}
Souza(mongod-3.0.8) be-mean-instagram> var mod = {$pushAll: {moves: attacks}}
Souza(mongod-3.0.8) be-mean-instagram> var options = { multi: true };

Souza(mongod-3.0.8) be-mean-instagram> db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 2ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})

Souza(mongod-3.0.8) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5674ac74d12632ef2d1a59d3"),
  "name": "Pikachu",
  "description": "Rato eletrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "Chupa essa manga",
    "Vai cagar um coco",
    "Chupa essa manga",
    "Vai cagar um coco"
  ],
  "active": false
}
{
  "_id": ObjectId("5674afcca2c7534bd63c5b3b"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "Chupa essa manga",
    "Vai cagar um coco",
    "Chupa essa manga",
    "Vai cagar um coco"
  ]
}
{
  "_id": ObjectId("5674afd6a2c7534bd63c5b3c"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "Chupa essa manga",
    "Vai cagar um coco"
  ]
}
{
  "_id": ObjectId("5674afdea2c7534bd63c5b3d"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "Chupa essa manga",
    "Vai cagar um coco"
  ]
}
Fetched 4 record(s) in 3ms
``` 

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

``` 
Souza(mongod-3.0.8) be-mean-instagram> var query = {}
Souza(mongod-3.0.8) be-mean-instagram> var mod = {$push: {moves: 'desvio'}}
Souza(mongod-3.0.8) be-mean-instagram> var options = {multi: true}
Souza(mongod-3.0.8) be-mean-instagram> db.pokemons.update(query, mod, options)
Updated 7 existing record(s) in 2ms
WriteResult({
  "nMatched": 7,
  "nUpserted": 0,
  "nModified": 7
})
``` 

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

``` 
Souza(mongod-3.0.8) be-mean-instagram> var query = {name: /AindaNaoExisteMon/i}
Souza(mongod-3.0.8) be-mean-instagram> var mod = {   $set: {active: true},   $setOnInsert: {name: "AindaNaoExisteMon", type: null, attack: null, defense: null, height: null, description: "Sem maiores informações"} }
Souza(mongod-3.0.8) be-mean-instagram> var options = {upsert: true}
Souza(mongod-3.0.8) be-mean-instagram> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 4ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("5679e354e1bc6b3f716ae211")
})
Souza(mongod-3.0.8) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5679e354e1bc6b3f716ae211"),
  "active": true,
  "name": "AindaNaoExisteMon",
  "type": null,
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 1 record(s) in 1ms
``` 

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

``` 
Souza(mongod-3.0.8) be-mean-instagram> var query = {moves: {$in: [/investida/i, /vai cagar um coco/i]}}
Souza(mongod-3.0.8) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56786db492d46b4f834736dd"),
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
  "_id": ObjectId("5679c33c8dd4704b21071a8d"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5679cc7a512b91d7df2ca4a9"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5674ac74d12632ef2d1a59d3"),
  "name": "Pikachu",
  "description": "Rato eletrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "Chupa essa manga",
    "Vai cagar um coco",
    "Chupa essa manga",
    "Vai cagar um coco",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("5674afcca2c7534bd63c5b3b"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "Chupa essa manga",
    "Vai cagar um coco",
    "Chupa essa manga",
    "Vai cagar um coco",
    "desvio"
  ]
}
{
  "_id": ObjectId("5674afd6a2c7534bd63c5b3c"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "Chupa essa manga",
    "Vai cagar um coco",
    "desvio"
  ]
}
{
  "_id": ObjectId("5674afdea2c7534bd63c5b3d"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "Chupa essa manga",
    "Vai cagar um coco",
    "desvio"
  ]
}
Fetched 7 record(s) in 4ms
``` 

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

```
Souza(mongod-3.0.8) be-mean-instagram> var query = {moves: {$all: [/chupa essa manga/i, /vai cagar um coco/i]}}
Souza(mongod-3.0.8) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5674ac74d12632ef2d1a59d3"),
  "name": "Pikachu",
  "description": "Rato eletrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "Chupa essa manga",
    "Vai cagar um coco",
    "Chupa essa manga",
    "Vai cagar um coco",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("5674afcca2c7534bd63c5b3b"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "Chupa essa manga",
    "Vai cagar um coco",
    "Chupa essa manga",
    "Vai cagar um coco",
    "desvio"
  ]
}
{
  "_id": ObjectId("5674afd6a2c7534bd63c5b3c"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "Chupa essa manga",
    "Vai cagar um coco",
    "desvio"
  ]
}
{
  "_id": ObjectId("5674afdea2c7534bd63c5b3d"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "Chupa essa manga",
    "Vai cagar um coco",
    "desvio"
  ]
}
Fetched 4 record(s) in 3ms
``` 

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

```
Souza(mongod-3.0.8) be-mean-instagram> var query = {type: {$not: /elétrico/i}}
Souza(mongod-3.0.8) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56786db492d46b4f834736dd"),
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
  "_id": ObjectId("5679c33c8dd4704b21071a8d"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5679cc7a512b91d7df2ca4a9"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5674ac74d12632ef2d1a59d3"),
  "name": "Pikachu",
  "description": "Rato eletrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "Chupa essa manga",
    "Vai cagar um coco",
    "Chupa essa manga",
    "Vai cagar um coco",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("5674afcca2c7534bd63c5b3b"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "Chupa essa manga",
    "Vai cagar um coco",
    "Chupa essa manga",
    "Vai cagar um coco",
    "desvio"
  ]
}
{
  "_id": ObjectId("5674afd6a2c7534bd63c5b3c"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "Chupa essa manga",
    "Vai cagar um coco",
    "desvio"
  ]
}
{
  "_id": ObjectId("5674afdea2c7534bd63c5b3d"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "Chupa essa manga",
    "Vai cagar um coco",
    "desvio"
  ]
}
{
  "_id": ObjectId("5679e354e1bc6b3f716ae211"),
  "active": true,
  "name": "AindaNaoExisteMon",
  "type": null,
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 8 record(s) in 4ms
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

```
Souza(mongod-3.0.8) be-mean-instagram> var query = {$and: [{moves: {$in: ['investida']}}, {attack: {$not: {$lte: 49}}}]}
Souza(mongod-3.0.8) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5679c33c8dd4704b21071a8d"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5679cc7a512b91d7df2ca4a9"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5674ac74d12632ef2d1a59d3"),
  "name": "Pikachu",
  "description": "Rato eletrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "Chupa essa manga",
    "Vai cagar um coco",
    "Chupa essa manga",
    "Vai cagar um coco",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("5674afd6a2c7534bd63c5b3c"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "Chupa essa manga",
    "Vai cagar um coco",
    "desvio"
  ]
}
Fetched 4 record(s) in 2ms
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
Souza(mongod-3.0.8) be-mean-instagram> var query = {$and: [{type: /água/i}, {attack: {$lt: 50}}]}
Souza(mongod-3.0.8) be-mean-instagram> query
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
Souza(mongod-3.0.8) be-mean-instagram> db.pokemons.remove(query)
Removed 1 record(s) in 2ms
WriteResult({
  "nRemoved": 1
})
```

## Esse item não está no vídeo e se você fizer significa que você lê as coisas, nesse exercício demonstre qual a diferença entre os operadores $ne e $not..##

```
$ne: retorna os documentos onde o valor do campo não é igual, ou seja diferente, isso inclui documentos que não contêm o campo e não suporta REGEX.

$not: Realiza uma lógica NOT. Retorna objetos que não correspondem ao operador de negação. Isto inclui documentos que não contêm o campo e suporta REGEX.

```


