# MongoDB - Aula 04 - Exercício
autor: Renato Galvão

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: pikachu, squirtle, bulbassauro, charmander

```
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> var query = {name:{ $in: [/pikachu/i,/squirtle/i,/bulbasauro/i,/charmander/i]}}

Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> var mod = {$pushAll: {attacks: ['furunculo raivoso','peteca decepada']}}

Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> var options = { multi: true }

Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> db.pokemons.update(query,mod,options)
Updated 4 existing record(s) in 1ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})

```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.

```
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> db.pokemons.update({},mod,options)
Updated 9 existing record(s) in 1ms
WriteResult({
  "nMatched": 9,
  "nUpserted": 0,
  "nModified": 9
})

```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".

```
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> var mod = {$set:{name:'AindaNaoExisteMon'},$setOnInsert:{description:'Sem maiores informações',type:null,attack:null,height:null}}
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> mod
{
  "$set": {
    "name": "AindaNaoExisteMon"
  },
  "$setOnInsert": {
    "description": "Sem maiores informações",
    "type": null,
    "attack": null,
    "height": null
  }
}
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> var options = {upsert: true}
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> db.pokemons.update({},mod,options)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.

```
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> var query = {attacks: {$all:['investida','furunculo raivoso']}}
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> db.pokemons.find(query)

```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> var query = {attacks: {$all:['furunculo raivoso','peteca decepada']}}
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56c76201f19ff10e2384a014"),
  "name": "Pikachu",
  "description": "Rato eletríco do demonio",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "attacks": [
    "furunculo raivoso",
    "peteca decepada"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56c76236f19ff10e2384a015"),
  "name": "Bulbasauro",
  "description": "Bicho esquisito da porra",
  "type": "grass",
  "attack": 49,
  "height": 0.4,
  "attacks": [
    "furunculo raivoso",
    "peteca decepada"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56c7625bf19ff10e2384a016"),
  "name": "Charmander",
  "description": "Dragãozinho fazedor de zoiudo",
  "type": "fire",
  "attack": 52,
  "height": 0.6,
  "attacks": [
    "furunculo raivoso",
    "peteca decepada"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56c7627ef19ff10e2384a017"),
  "name": "Squirtle",
  "description": "Solta água pelo cu",
  "type": "water",
  "attack": 48,
  "height": 0.5,
  "attacks": [
    "furunculo raivoso",
    "peteca decepada"
  ],
  "moves": [
    "desvio"
  ]
}
Fetched 4 record(s) in 2ms

```

## Pesquisar **todos** os pokemons que não são do tipo `Drill`.

```
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> var query = {type:{$not:/drill/i}}
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56c1ce9965d70c166a207adf"),
  "type": "psychic",
  "name": "AindaNaoExisteMon",
  "attack": 200,
  "height": 0.9,
  "description": "bichão fodão voador do caraio alado",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56c1cf1965d70c166a207ae0"),
  "name": "dragonite",
  "description": "dragão que só voa a noite",
  "type": "dragon",
  "attack": 134,
  "height": 0.4,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56c1d02f65d70c166a207ae1"),
  "name": "dragonite",
  "description": "chocante",
  "type": "electric",
  "attack": 83,
  "height": 11,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56c1d05b65d70c166a207ae2"),
  "name": "magmar",
  "description": "queeeeeeente",
  "type": "fire",
  "attack": 95,
  "height": 13,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56c1d09165d70c166a207ae3"),
  "height": 0.3,
  "name": "Bostamon",
  "description": "Pokemon feito de cocozinho",
  "type": "bosta",
  "attack": 35,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56c76201f19ff10e2384a014"),
  "name": "Pikachu",
  "description": "Rato eletríco do demonio",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "attacks": [
    "furunculo raivoso",
    "peteca decepada"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56c76236f19ff10e2384a015"),
  "name": "Bulbasauro",
  "description": "Bicho esquisito da porra",
  "type": "grass",
  "attack": 49,
  "height": 0.4,
  "attacks": [
    "furunculo raivoso",
    "peteca decepada"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56c7625bf19ff10e2384a016"),
  "name": "Charmander",
  "description": "Dragãozinho fazedor de zoiudo",
  "type": "fire",
  "attack": 52,
  "height": 0.6,
  "attacks": [
    "furunculo raivoso",
    "peteca decepada"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56c7627ef19ff10e2384a017"),
  "name": "Squirtle",
  "description": "Solta água pelo cu",
  "type": "water",
  "attack": 48,
  "height": 0.5,
  "attacks": [
    "furunculo raivoso",
    "peteca decepada"
  ],
  "moves": [
    "desvio"
  ]
}
Fetched 9 record(s) in 3ms

```

## Pesquisar **todos** os pokemons que tenham o ataque `furunculo raivoso` **E** tenham a attack **não menor ou igual** a 49.

```
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> var query1 = {attacks:{$all:['furunculo raivoso']}}
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> var query2 = {attack: {$not: {$gte: 49}}}
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> var query = {$and:[query1,query2]}
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56c7627ef19ff10e2384a017"),
  "name": "Squirtle",
  "description": "Solta água pelo cu",
  "type": "water",
  "attack": 48,
  "height": 0.5,
  "attacks": [
    "furunculo raivoso",
    "peteca decepada"
  ],
  "moves": [
    "desvio"
  ]
}
Fetched 1 record(s) in 1ms

```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> var query = {type:'water',attack:{$lt:50}}
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 1ms
WriteResult({
  "nRemoved": 1
})

```
