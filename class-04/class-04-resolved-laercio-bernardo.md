# MongoDB - Aula 04 - Exercício
autor: Laércio Bernardo

## Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
var query = {name:{$in:[/pikachu/i,/squirtle/i,/bulbassaur/i]}}

var mod = {$push:{moves:{$each:['Ataque Rápido','Esquivar']}}}

var opt = {multi:true}

db.pokemons.update(query,mod,opt)

Updated 3 existing record(s) in 15ms
WriteResult({
  "nMatched": 3,
  "nUpserted": 0,
  "nModified": 3
})
```

## Adicionar 1 movimento em todos os pokemons: `desvio`.

```
var query = {}

var mod = {$push:{moves:'Desvio'}}

var opt = {multi:true}

db.pokemons.update(query,mod,opt)

Updated 6 existing record(s) in 2ms
WriteResult({
  "nMatched": 6,
  "nUpserted": 0,
  "nModified": 6
})
                                                        
```

## Adicionar o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com valor `null`e a descrição: "Sem maiores informações"

```

var query = {name:/AindaNaoExisteMon/i}

var mod = {$set:{name:'AindaNaoExisteMon'},$setOnInsert:{description:'Sem maiores informações', type:null, attack: null, height: null, active: null, moves: null}}

var opt = {upsert: true}
db.pokemons.update(query,mod,opt)
Updated 1 new record(s) in 2ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("56e57eafd7783bd9ba5abb00")
})

```

## Pesquisar todos os pokemons que possua o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.


```
var query = {moves:{$in:[/investida/i,/esquivar/i]}}
db.pokemons.find(query)
{
  "_id": ObjectId("56e312e47bd8601e11ec92c9"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "investida",
    "Desvio"
  ]
}
{
  "_id": ObjectId("56e555a0d7783bd9ba5abafe"),
  "active": false,
  "moves": [
    "investida",
    "Desvio"
  ]
}
{
  "_id": ObjectId("56e182b4142fa7b81344cdd0"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "Choque do Trovão",
    "Ataque Rápido",
    "Esquivar",
    "Desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("56e182b8142fa7b81344cdd2"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "Lança Chamas",
    "Ataque Rápido",
    "Esquivar",
    "Desvio"
  ]
}
{
  "_id": ObjectId("56e182b6142fa7b81344cdd1"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "Folha Navalha",
    "Ataque Rápido",
    "Esquivar",
    "Desvio"
  ]
}
{
  "_id": ObjectId("56e182ba142fa7b81344cdd3"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "Hidro Bomba",
    "Ataque Rápido",
    "Esquivar",
    "Desvio"
  ]
}
Fetched 6 record(s) in 12ms
 
```
## Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```
var query = {moves:{$in:[/investida/i,/ataque rapido/i]}}
db.pokemons.find(query)
{
  "_id": ObjectId("56e312e47bd8601e11ec92c9"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "investida",
    "Desvio"
  ]
}
{
  "_id": ObjectId("56e555a0d7783bd9ba5abafe"),
  "active": false,
  "moves": [
    "investida",
    "Desvio"
  ]
}
{
  "_id": ObjectId("56e182b4142fa7b81344cdd0"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "Choque do Trovão",
    "Ataque Rápido",
    "Esquivar",
    "Desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("56e182b8142fa7b81344cdd2"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "Lança Chamas",
    "Ataque Rápido",
    "Esquivar",
    "Desvio"
  ]
}
{
  "_id": ObjectId("56e182b6142fa7b81344cdd1"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "Folha Navalha",
    "Ataque Rápido",
    "Esquivar",
    "Desvio"
  ]
}
{
  "_id": ObjectId("56e182ba142fa7b81344cdd3"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "Hidro Bomba",
    "Ataque Rápido",
    "Esquivar",
    "Desvio"
  ]
}
Fetched 6 record(s) in 7ms


```

## Pesquisar todos que não são do tipo `elétrico`

```
var query = {type:{$ne:'Elétrico'}}
db.pokemons.find(query)
{
  "_id": ObjectId("56e312e47bd8601e11ec92c9"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "investida",
    "Desvio"
  ]
}
{
  "_id": ObjectId("56e555a0d7783bd9ba5abafe"),
  "active": false,
  "moves": [
    "investida",
    "Desvio"
  ]
}
{
  "_id": ObjectId("56e182b4142fa7b81344cdd0"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "Choque do Trovão",
    "Ataque Rápido",
    "Esquivar",
    "Desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("56e182b8142fa7b81344cdd2"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "Lança Chamas",
    "Ataque Rápido",
    "Esquivar",
    "Desvio"
  ]
}
{
  "_id": ObjectId("56e182b6142fa7b81344cdd1"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "Folha Navalha",
    "Ataque Rápido",
    "Esquivar",
    "Desvio"
  ]
}
{
  "_id": ObjectId("56e182ba142fa7b81344cdd3"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "Hidro Bomba",
    "Ataque Rápido",
    "Esquivar",
    "Desvio"
  ]
}
{
  "_id": ObjectId("56e57eafd7783bd9ba5abb00"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null,
  "active": null,
  "moves": null
}
Fetched 7 record(s) in 4ms

```

## Pesquisar **todos** pokemons que tenham o ataque `investida` **E** tenham a defesa não menor ou igual a 49

```
var query = {$and:[{attack:{$gte:49}},{moves:{$in:[/investida/i]}}]}
db.pokemons.find(query)
{
  "_id": ObjectId("56e312e47bd8601e11ec92c9"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "investida",
    "Desvio"
  ]
}
{
  "_id": ObjectId("56e182b4142fa7b81344cdd0"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "Choque do Trovão",
    "Ataque Rápido",
    "Esquivar",
    "Desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("56e182b8142fa7b81344cdd2"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "Lança Chamas",
    "Ataque Rápido",
    "Esquivar",
    "Desvio"
  ]
}
{
  "_id": ObjectId("56e182b6142fa7b81344cdd1"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "Folha Navalha",
    "Ataque Rápido",
    "Esquivar",
    "Desvio"
  ]
}
Fetched 4 record(s) in 3ms


```

## Remova **todos** os pokemons do tipo água **E** com attack menor que 50

```
var query = {$and:[{attack:{$lt:50}},{type:/água/i}]}

db.pokemons.remove(query)

Removed 1 record(s) in 18ms
WriteResult({
  "nRemoved": 1
})

```