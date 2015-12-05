#MongoDB - Aula 04 - Exercício
Autor: Cauê Bruno de Almeida

## 1. Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

Não tenho esses pokémons não sei o porquê. Mas vou fazer com outros que tenho.

```
var query = {name: {
    $in: [
        /pickachu/i,
        /dog pi/i,
        /Blastoise/i,
        /Mew/i
    ]}
}

var attacks = [
    'PLA',
    'POW'
]

var options = {multi: true}

var mod = {$pushAll: {moves: attacks}}

be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 5 existing record(s) in 2ms
WriteResult({
  "nMatched": 5,
  "nUpserted": 0,
  "nModified": 5
})
```

## 2. Adicionar 1 movimento em todos os pokemons: `desvio`.

```
var query = {}
var mod = {$push: {moves: 'desvio'}}
var options = {multi: true}

be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 8 existing record(s) in 2ms
WriteResult({
  "nMatched": 8,
  "nUpserted": 0,
  "nModified": 8
})
```

## 3. Adicionar o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: 'Sem maiores informações'.

```
var query = { name : /AindaNaoExisteMon/i }
var mod = {
    $setOnInsert : {
        name : 'AindaNaoExisteMon',
        description : 'Sem maiores informações',
        type : null,
        attack : null,
        defense : null,
        height : null,
        active : null,
        moves : null
    }
}

var options = {upsert : true}

be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 3ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564e57f06ff7a1d633369357")
})
```

## 4. Pesquisar todos os pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha o seu pokemon favorito.

```
var query = {moves : {$in : [/investida/i , /xaplal/i ]}}

be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5645223f141cff9e62ddfbe7"),
  "name": "Charmilion",
  "description": "Foguinho",
  "type": "bird",
  "attack": 35,
  "defense": 20,
  "height": 0.25,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56452240141cff9e62ddfbe9"),
  "name": "Mew Two",
  "description": "Opa já era",
  "type": "null",
  "attack": 40000,
  "defense": 40000,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "PLA",
    "POW",
    "desvio"
  ]
}
{
  "_id": ObjectId("56452240141cff9e62ddfbea"),
  "name": "Blastoise",
  "description": "O rei das água",
  "type": "turtle",
  "attack": 50,
  "defense": 30,
  "height": 20,
  "active": false,
  "moves": [
    "investida",
    "PLA",
    "POW",
    "desvio"
  ]
}
{
  "_id": ObjectId("56452240141cff9e62ddfbeb"),
  "name": "Dog Pi",
  "description": "Non ecxiste",
  "type": "ball",
  "attack": 0.1,
  "defense": 0.5,
  "height": 0.01,
  "active": false,
  "moves": [
    "investida",
    "PLA",
    "POW",
    "desvio"
  ]
}
{
  "_id": ObjectId("564a58b642d23c8c2ce6d1bd"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8100,
  "defense": 8000,
  "moves": [
    "investida",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("5645233d141cff9e62ddfbec"),
  "name": "pickachu",
  "description": "Non ecxiste",
  "type": "electric",
  "attack": 0.1,
  "defense": 0.5,
  "height": 0.01,
  "moves": [
    "investida",
    "choque do trovão",
    "PLA",
    "POW",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("564d02922dc71abf3dc1f721"),
  "active": false,
  "name": "naoexistemon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "No information",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56452240141cff9e62ddfbe8"),
  "name": "Mew",
  "description": "hMMMMMMmmmm",
  "type": "null",
  "attack": 10000,
  "defense": 10000,
  "height": 0.1,
  "active": false,
  "moves": [
    "investida",
    "PLA",
    "POW",
    "PLA",
    "POW",
    "desvio"
  ],
  "move": [
    "PLA",
    "POW"
  ]
}
Fetched 8 record(s) in 3ms
```

## 5. Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```
var query = { moves : {$all : [ /pla/i, /pow/i ] } }

be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56452240141cff9e62ddfbe9"),
  "name": "Mew Two",
  "description": "Opa já era",
  "type": "null",
  "attack": 40000,
  "defense": 40000,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "PLA",
    "POW",
    "desvio"
  ]
}
{
  "_id": ObjectId("56452240141cff9e62ddfbea"),
  "name": "Blastoise",
  "description": "O rei das água",
  "type": "turtle",
  "attack": 50,
  "defense": 30,
  "height": 20,
  "active": false,
  "moves": [
    "investida",
    "PLA",
    "POW",
    "desvio"
  ]
}
{
  "_id": ObjectId("56452240141cff9e62ddfbeb"),
  "name": "Dog Pi",
  "description": "Non ecxiste",
  "type": "ball",
  "attack": 0.1,
  "defense": 0.5,
  "height": 0.01,
  "active": false,
  "moves": [
    "investida",
    "PLA",
    "POW",
    "desvio"
  ]
}
{
  "_id": ObjectId("5645233d141cff9e62ddfbec"),
  "name": "pickachu",
  "description": "Non ecxiste",
  "type": "electric",
  "attack": 0.1,
  "defense": 0.5,
  "height": 0.01,
  "moves": [
    "investida",
    "choque do trovão",
    "PLA",
    "POW",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("56452240141cff9e62ddfbe8"),
  "name": "Mew",
  "description": "hMMMMMMmmmm",
  "type": "null",
  "attack": 10000,
  "defense": 10000,
  "height": 0.1,
  "active": false,
  "moves": [
    "investida",
    "PLA",
    "POW",
    "PLA",
    "POW",
    "desvio"
  ],
  "move": [
    "PLA",
    "POW"
  ]
}
Fetched 5 record(s) in 5ms
```

## 6. Pesquisar todos pokemons que não são do tipo `elétrico`.

```
var query = {type : {$ne : 'electric' }}

be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5645223f141cff9e62ddfbe7"),
  "name": "Charmilion",
  "description": "Foguinho",
  "type": "bird",
  "attack": 35,
  "defense": 20,
  "height": 0.25,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56452240141cff9e62ddfbe9"),
  "name": "Mew Two",
  "description": "Opa já era",
  "type": "null",
  "attack": 40000,
  "defense": 40000,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "PLA",
    "POW",
    "desvio"
  ]
}
{
  "_id": ObjectId("56452240141cff9e62ddfbea"),
  "name": "Blastoise",
  "description": "O rei das água",
  "type": "turtle",
  "attack": 50,
  "defense": 30,
  "height": 20,
  "active": false,
  "moves": [
    "investida",
    "PLA",
    "POW",
    "desvio"
  ]
}
{
  "_id": ObjectId("56452240141cff9e62ddfbeb"),
  "name": "Dog Pi",
  "description": "Non ecxiste",
  "type": "ball",
  "attack": 0.1,
  "defense": 0.5,
  "height": 0.01,
  "active": false,
  "moves": [
    "investida",
    "PLA",
    "POW",
    "desvio"
  ]
}
{
  "_id": ObjectId("564a58b642d23c8c2ce6d1bd"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8100,
  "defense": 8000,
  "moves": [
    "investida",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("564d02922dc71abf3dc1f721"),
  "active": false,
  "name": "naoexistemon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "No information",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56452240141cff9e62ddfbe8"),
  "name": "Mew",
  "description": "hMMMMMMmmmm",
  "type": "null",
  "attack": 10000,
  "defense": 10000,
  "height": 0.1,
  "active": false,
  "moves": [
    "investida",
    "PLA",
    "POW",
    "PLA",
    "POW",
    "desvio"
  ],
  "move": [
    "PLA",
    "POW"
  ]
}
{
  "_id": ObjectId("564e57f06ff7a1d633369357"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "defense": null,
  "height": null,
  "active": null,
  "moves": null
}
Fetched 8 record(s) in 4ms
```

## 7. Pesquisar todos pokemons que tenham o ataque `investida` **E** tenham defesa **não menor ou igual** a 49.

```
var query = { $and : [{ attack : {$in : [/investida/i ]}, attack : {$not : {$lte : 49}} }] }

be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
```

## 8. Remove **todos** os pokemons do tipo água e com attack menor que 50.

```
var query = { $and : [ {type : 'water'}, {attack : {$lt : 50}} ] }

be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms

be-mean-pokemons> db.pokemons.remove(query)
Removed 0 record(s) in 577ms
WriteResult({
  "nRemoved": 0
})
```

## 9. Esse item não está no vídeo e se você fizer significa que você lê as coisas, nesse exercício demonstre qual a diferença entre os operadores $ne e $not.

O `$not` nega a expressão que você vai escrever. Então é tipo um `if (!true)`.

Já o `$ne` vai recuperar os documentos cujo o valor seja diferente do passado como parâmetro.