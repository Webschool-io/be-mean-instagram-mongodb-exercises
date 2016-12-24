# MongoDB - Aula 04 - Exercício

autor: Carlos Machel

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
var query = {name: /pikachu/i};
var mod = {$push: {moves: {$each: ['Teia Elétrica', 'Faísca']} } }
db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})


var query = {name: /squirtle/i};
var mod = {$push: {moves: {$each: ['Bolhas', 'Mergulho']} } }
db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

var query = {name: /bulbassauro/i};
var mod = {$push: {moves: {$each: ['Peso Pesado', 'Planta Mortal']} } }
db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})


var query = {name: /charmander/i};
var mod = {$push: {moves: {$each: ['Soco de Fogo', 'Chute Flamejante']} } }
db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

```
var query = {}
var mod = {$addToSet: {moves: 'desvio'} }
var options = {multi: true}

db.pokemons.update(query, mod, options);
Updated 13 existing record(s) in 1ms
WriteResult({
  "nMatched": 13,
  "nUpserted": 0,
  "nModified": 13
})

```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

```
var query = {name: /aindanaoexistemon/i};
var mod = { $setOnInsert: { name: 'AindaNaoExisteMon', description: 'Sem maiores informações', type: null, attack: null, height: null, moves: null} }
var options = {upsert: true} 

db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 10ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("569facd4ecbcc36cc47e0874")
})
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

```
var query = { moves: {$in : [/investida/i, /lança-chamas/i]  } }

db.pokemons.find(query)
{
  "_id": ObjectId("56832af31cef7dcd89e2deb9"),
  "name": "Golbat",
  "description": "Morceguinho que adora sugar sangue.",
  "type": "Poison",
  "attack": 40,
  "defense": 30,
  "height": 1.6,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56832af31cef7dcd89e2deba"),
  "name": "Zubat",
  "description": "Morceguinho que se queima no sol.",
  "type": "Poison",
  "attack": 20,
  "defense": 20,
  "height": 0.8,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56832af31cef7dcd89e2debb"),
  "name": "Psyduck",
  "description": "Pato muito doido que usa um poder misterioso",
  "type": "Eletric",
  "attack": 30,
  "defense": 20,
  "height": 0.8,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56832af31cef7dcd89e2debc"),
  "name": "Mankey",
  "description": "Macaquinho que quando fica nervoso sai da reta.",
  "type": "Fighting",
  "attack": 40,
  "defense": 20,
  "height": 0.5,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56832af31cef7dcd89e2debd"),
  "name": "Cubone",
  "description": "Chora pela mãe que nunca mais vai ver =( ",
  "type": "Ground",
  "attack": 30,
  "defense": 40,
  "height": 0.4,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56832af31cef7dcd89e2debe"),
  "name": "Heracross",
  "description": "Besouro sinistro de forte. Derruba até uma árvore.",
  "type": "Bug",
  "attack": 60,
  "defense": 30,
  "height": 1.5,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56832c197ecdbeff48ee7b5c"),
  "name": "Oddish",
  "description": "Batata que se enfia no solo pra pegar nutrientes.",
  "type": "Grass",
  "attack": 30,
  "defense": 30,
  "height": 0.5,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56832c197ecdbeff48ee7b5e"),
  "name": "Geodude",
  "description": "Pedra redonda e rabugente.",
  "attack": 48,
  "defense": 40,
  "height": 0.4,
  "moves": [
    "investida",
    "desvio"
  ],
  "type": "pedra"
}
{
  "_id": ObjectId("569c9f52a20f8b163c55b5b6"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": true,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56832c197ecdbeff48ee7b5d"),
  "name": "Pikachu",
  "description": "Rato elétrico.",
  "type": "Eletric",
  "attack": 30,
  "defense": 25,
  "height": 0.4,
  "moves": [
    "choque elétrico",
    "ataque rápido",
    "bola elétrica",
    "investida",
    "choque do trovão",
    "Teia Elétrica",
    "Faísca",
    "desvio"
  ]
}
{
  "_id": ObjectId("569f1e79e21098832232acef"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "lança-chamas",
    "investida",
    "Soco de Fogo",
    "Chute Flamejante",
    "desvio"
  ],
  "defense": 25
}
{
  "_id": ObjectId("569f1e79e21098832232acee"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "folha navalha",
    "investida",
    "Peso Pesado",
    "Planta Mortal",
    "desvio"
  ],
  "defense": 25
}
{
  "_id": ObjectId("569fac5aeaff1840aa91cb65"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "investida",
    "Bolhas",
    "Mergulho",
    "desvio"
  ],
  "defense": 25
}
Fetched 13 record(s) in 2ms


```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

```
var query = {moves: {$all: [/folha navalha/i, /peso pesado/i ] }}

db.pokemons.find(query)
{
  "_id": ObjectId("569f1e79e21098832232acee"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "folha navalha",
    "investida",
    "Peso Pesado",
    "Planta Mortal",
    "desvio"
  ],
  "defense": 25
}
Fetched 1 record(s) in 1ms

```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

```
var query = {type: {$not: /eletric/i}}

db.pokemons.find(query)
{
  "_id": ObjectId("56832af31cef7dcd89e2deb9"),
  "name": "Golbat",
  "description": "Morceguinho que adora sugar sangue.",
  "type": "Poison",
  "attack": 40,
  "defense": 30,
  "height": 1.6,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56832af31cef7dcd89e2deba"),
  "name": "Zubat",
  "description": "Morceguinho que se queima no sol.",
  "type": "Poison",
  "attack": 20,
  "defense": 20,
  "height": 0.8,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56832af31cef7dcd89e2debc"),
  "name": "Mankey",
  "description": "Macaquinho que quando fica nervoso sai da reta.",
  "type": "Fighting",
  "attack": 40,
  "defense": 20,
  "height": 0.5,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56832af31cef7dcd89e2debd"),
  "name": "Cubone",
  "description": "Chora pela mãe que nunca mais vai ver =( ",
  "type": "Ground",
  "attack": 30,
  "defense": 40,
  "height": 0.4,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56832af31cef7dcd89e2debe"),
  "name": "Heracross",
  "description": "Besouro sinistro de forte. Derruba até uma árvore.",
  "type": "Bug",
  "attack": 60,
  "defense": 30,
  "height": 1.5,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56832c197ecdbeff48ee7b5c"),
  "name": "Oddish",
  "description": "Batata que se enfia no solo pra pegar nutrientes.",
  "type": "Grass",
  "attack": 30,
  "defense": 30,
  "height": 0.5,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56832c197ecdbeff48ee7b5e"),
  "name": "Geodude",
  "description": "Pedra redonda e rabugente.",
  "attack": 48,
  "defense": 40,
  "height": 0.4,
  "moves": [
    "investida",
    "desvio"
  ],
  "type": "pedra"
}
{
  "_id": ObjectId("569c9f52a20f8b163c55b5b6"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": true,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("569f1e79e21098832232acef"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "lança-chamas",
    "investida",
    "Soco de Fogo",
    "Chute Flamejante",
    "desvio"
  ],
  "defense": 25
}
{
  "_id": ObjectId("569f1e79e21098832232acee"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "folha navalha",
    "investida",
    "Peso Pesado",
    "Planta Mortal",
    "desvio"
  ],
  "defense": 25
}
{
  "_id": ObjectId("569fac5aeaff1840aa91cb65"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "investida",
    "Bolhas",
    "Mergulho",
    "desvio"
  ],
  "defense": 25
}
{
  "_id": ObjectId("569facd4ecbcc36cc47e0874"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null,
  "moves": null
}
Fetched 12 record(s) in 1ms

```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##


```  
var query = { $and : [ { moves: { $in : [/investida/i ] }  }, { defense : { $not : { $lte : 49 } } }  ] }

 db.pokemons.find(query)
{
  "_id": ObjectId("569c9f52a20f8b163c55b5b6"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": true,
  "moves": [
    "investida",
    "desvio"
  ]
}
Fetched 1 record(s) in 1ms

```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
var query = {$and: [ {type: /água/i}, {attack: {$lt: 50} } ] } 

db.pokemons.find(query)
{
  "_id": ObjectId("569fac5aeaff1840aa91cb65"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "investida",
    "Bolhas",
    "Mergulho",
    "desvio"
  ],
  "defense": 25
}
Fetched 1 record(s) in 0ms


db.pokemons.remove(query)
Removed 1 record(s) in 2ms
WriteResult({
  "nRemoved": 1
})

```

## Esse item não está no vídeo e se você fizer significa que você lê as coisas, nesse exercício demonstre qual a diferença entre os operadores $ne e $not

```
var query = { attack : { $not: { $gt: 20 } } }

 db.pokemons.find(query)
{
  "_id": ObjectId("56832af31cef7dcd89e2deba"),
  "name": "Zubat",
  "description": "Morceguinho que se queima no sol.",
  "type": "Poison",
  "attack": 20,
  "defense": 20,
  "height": 0.8,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("569facd4ecbcc36cc47e0874"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null,
  "moves": null
}
Fetched 2 record(s) in 1ms


```

```
var query = { attack : { $ne: 20 }  }

db.pokemons.find(query)
{
  "_id": ObjectId("56832af31cef7dcd89e2deb9"),
  "name": "Golbat",
  "description": "Morceguinho que adora sugar sangue.",
  "type": "Poison",
  "attack": 40,
  "defense": 30,
  "height": 1.6,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56832af31cef7dcd89e2debb"),
  "name": "Psyduck",
  "description": "Pato muito doido que usa um poder misterioso",
  "type": "Eletric",
  "attack": 30,
  "defense": 20,
  "height": 0.8,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56832af31cef7dcd89e2debc"),
  "name": "Mankey",
  "description": "Macaquinho que quando fica nervoso sai da reta.",
  "type": "Fighting",
  "attack": 40,
  "defense": 20,
  "height": 0.5,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56832af31cef7dcd89e2debd"),
  "name": "Cubone",
  "description": "Chora pela mãe que nunca mais vai ver =( ",
  "type": "Ground",
  "attack": 30,
  "defense": 40,
  "height": 0.4,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56832af31cef7dcd89e2debe"),
  "name": "Heracross",
  "description": "Besouro sinistro de forte. Derruba até uma árvore.",
  "type": "Bug",
  "attack": 60,
  "defense": 30,
  "height": 1.5,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56832c197ecdbeff48ee7b5c"),
  "name": "Oddish",
  "description": "Batata que se enfia no solo pra pegar nutrientes.",
  "type": "Grass",
  "attack": 30,
  "defense": 30,
  "height": 0.5,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56832c197ecdbeff48ee7b5e"),
  "name": "Geodude",
  "description": "Pedra redonda e rabugente.",
  "attack": 48,
  "defense": 40,
  "height": 0.4,
  "moves": [
    "investida",
    "desvio"
  ],
  "type": "pedra"
}
{
  "_id": ObjectId("569c9f52a20f8b163c55b5b6"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": true,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56832c197ecdbeff48ee7b5d"),
  "name": "Pikachu",
  "description": "Rato elétrico.",
  "type": "Eletric",
  "attack": 30,
  "defense": 25,
  "height": 0.4,
  "moves": [
    "choque elétrico",
    "ataque rápido",
    "bola elétrica",
    "investida",
    "choque do trovão",
    "Teia Elétrica",
    "Faísca",
    "desvio"
  ]
}
{
  "_id": ObjectId("569f1e79e21098832232acef"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "lança-chamas",
    "investida",
    "Soco de Fogo",
    "Chute Flamejante",
    "desvio"
  ],
  "defense": 25
}
{
  "_id": ObjectId("569f1e79e21098832232acee"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "folha navalha",
    "investida",
    "Peso Pesado",
    "Planta Mortal",
    "desvio"
  ],
  "defense": 25
}
{
  "_id": ObjectId("569facd4ecbcc36cc47e0874"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null,
  "moves": null
}
Fetched 12 record(s) in 103ms

```