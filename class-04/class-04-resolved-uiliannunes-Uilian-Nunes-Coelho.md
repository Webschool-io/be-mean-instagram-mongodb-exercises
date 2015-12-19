# MongoDB - Aula 04 - Exercício
autor: Uilian Nunes Coelho

## Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander

```
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> var query = {name:/pikachu/i}
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> var mod = {$pushAll: {moves:['investida','evasiva']}}
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> db.pokemons.update(query,mod)

MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> var query = {name: /Squirtle/i}
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> var mod = {$pushAll: {moves:['investida','evasiva']}, $setOnInsert:{name:"Squirtle", description: "Sem maiores informações", type: null, attack: null, height: null}}
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> var options = {upsert: true}
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> db.pokemons.update(query, mod, options)

MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> var query = {name: /Bulbassauro/i}
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> var mod = {$pushAll: {moves:['investida','evasiva']}, $setOnInsert:{name:"Bulbassauro", description: "Sem maiores informações", type: null, attack: null, height: null}}
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> var options = {upsert: true}
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> db.pokemons.update(query, mod, options)

MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> var query = {name: /Charmander/i}
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> var mod = {$pushAll: {moves:['investida','evasiva']}, $setOnInsert:{name:"Charmander", description: "Sem maiores informações", type: null, attack: null, height: null}}
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> var options = {upsert: true}
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> db.pokemons.update(query, mod, options)

```

## Adicionar 1 movimento em todos os pokemons: desvio.

```
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> var query = {}
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> var mod = {$push: {moves: 'desvio'}}
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> var options = {multi: true}
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 11 existing record(s) in 28ms
WriteResult({
  "nMatched": 11,
  "nUpserted": 0,
  "nModified": 11
})

```

## Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".

```
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> var mod = {$setOnInsert: {name:'AindaNaoExisteMon', description:'Sem Maiores Informações', attack: null, defense: null, height: null, type: null, moves:[]}}
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> var options = {upsert: true}
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 72ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("56552aba7ff3d5c60b686852")
})

```

## Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.

```
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> var query = {moves: {$in: ['investida','evasiva']}}
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5654f3f1cd1bdd189cd39d6e"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "evasiva",
    "desvio"
  ]
}
{
  "_id": ObjectId("5655272d7ff3d5c60b68684f"),
  "moves": [
    "investida",
    "evasiva",
    "desvio"
  ],
  "name": "Squirtle",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null
}
{
  "_id": ObjectId("565527b27ff3d5c60b686850"),
  "moves": [
    "investida",
    "evasiva",
    "desvio"
  ],
  "name": "Bulbassauro",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null
}
{
  "_id": ObjectId("565527ef7ff3d5c60b686851"),
  "moves": [
    "investida",
    "evasiva",
    "desvio"
  ],
  "name": "Charmander",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null
}
Fetched 4 record(s) in 3ms

```

## Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> var query = {moves: {$in: ['evasiva','desvio']}}
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564687f79f36874a98ff79bf"),
  "name": "Zubat",
  "description": "Zubat is a Poison/Flying type Pokémon introduced in Generation 1. It is known as the Bat Pokémon",
  "type": "Poison/Flying",
  "attack": 45,
  "height": 0.79,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564687f79f36874a98ff79c2"),
  "name": "Dragonite",
  "description": "Dragãozinho do Mal",
  "type": "Dragon/Flying",
  "attack": 134,
  "height": 2.21,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564687f79f36874a98ff79c3"),
  "name": "Raichu",
  "description": "Raichu is an Electric type Pokémon introduced in Generation 1. It is known as the Mouse Pokémon",
  "type": "electric",
  "attack": 90,
  "height": 0.79,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564687f79f36874a98ff79c4"),
  "name": "Pidgeot",
  "description": "Pidgeot is a Normal/Flying type Pokémon introduced in Generation 1. It is known as the Bird Pokémon",
  "type": "Flying",
  "attack": 80,
  "height": 1.5,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564fb465010a0d37f0f2516e"),
  "name": "Cacnea",
  "description": "Cacnea is a Grass type Pokémon introduced in Generation 3. It is known as the Cactus Pokémon.",
  "type": "Grass",
  "attack": 85,
  "height": 0.4,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5654f3f1cd1bdd189cd39d6e"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "evasiva",
    "desvio"
  ]
}
{
  "_id": ObjectId("5655272d7ff3d5c60b68684f"),
  "moves": [
    "investida",
    "evasiva",
    "desvio"
  ],
  "name": "Squirtle",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null
}
{
  "_id": ObjectId("565527b27ff3d5c60b686850"),
  "moves": [
    "investida",
    "evasiva",
    "desvio"
  ],
  "name": "Bulbassauro",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null
}
{
  "_id": ObjectId("565527ef7ff3d5c60b686851"),
  "moves": [
    "investida",
    "evasiva",
    "desvio"
  ],
  "name": "Charmander",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null
}
{
  "_id": ObjectId("564687f79f36874a98ff79c0"),
  "name": "Jigglypuff",
  "description": "Jigglypuff is a Normal/Fairy type Pokémon introduced in Generation 1. It is known as the Balloon Pokémon",
  "type": "Fairy",
  "attack": 45,
  "height": 0.51,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564687f79f36874a98ff79c1"),
  "name": "Vileplume",
  "description": "Vileplume is a Grass/Poison type Pokémon introduced in Generation 1. It is known as the Flower Pokémon",
  "type": "Grass/Poison",
  "attack": 80,
  "height": 1.19,
  "moves": [
    "desvio"
  ]
}
Fetched 11 record(s) in 4ms

```


##Pesquisar todos os pokemons que não são do tipo elétrico.

```
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> var query = {type: {$ne:'electric'}}
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564687f79f36874a98ff79bf"),
  "name": "Zubat",
  "description": "Zubat is a Poison/Flying type Pokémon introduced in Generation 1. It is known as the Bat Pokémon",
  "type": "Poison/Flying",
  "attack": 45,
  "height": 0.79,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564687f79f36874a98ff79c2"),
  "name": "Dragonite",
  "description": "Dragãozinho do Mal",
  "type": "Dragon/Flying",
  "attack": 134,
  "height": 2.21,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564687f79f36874a98ff79c4"),
  "name": "Pidgeot",
  "description": "Pidgeot is a Normal/Flying type Pokémon introduced in Generation 1. It is known as the Bird Pokémon",
  "type": "Flying",
  "attack": 80,
  "height": 1.5,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564fb465010a0d37f0f2516e"),
  "name": "Cacnea",
  "description": "Cacnea is a Grass type Pokémon introduced in Generation 3. It is known as the Cactus Pokémon.",
  "type": "Grass",
  "attack": 85,
  "height": 0.4,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5655272d7ff3d5c60b68684f"),
  "moves": [
    "investida",
    "evasiva",
    "desvio"
  ],
  "name": "Squirtle",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null
}
{
  "_id": ObjectId("565527b27ff3d5c60b686850"),
  "moves": [
    "investida",
    "evasiva",
    "desvio"
  ],
  "name": "Bulbassauro",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null
}
{
  "_id": ObjectId("565527ef7ff3d5c60b686851"),
  "moves": [
    "investida",
    "evasiva",
    "desvio"
  ],
  "name": "Charmander",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null
}
{
  "_id": ObjectId("564687f79f36874a98ff79c0"),
  "name": "Jigglypuff",
  "description": "Jigglypuff is a Normal/Fairy type Pokémon introduced in Generation 1. It is known as the Balloon Pokémon",
  "type": "Fairy",
  "attack": 45,
  "height": 0.51,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564687f79f36874a98ff79c1"),
  "name": "Vileplume",
  "description": "Vileplume is a Grass/Poison type Pokémon introduced in Generation 1. It is known as the Flower Pokémon",
  "type": "Grass/Poison",
  "attack": 80,
  "height": 1.19,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56552aba7ff3d5c60b686852"),
  "name": "AindaNaoExisteMon",
  "description": "Sem Maiores Informações",
  "attack": null,
  "defense": null,
  "height": null,
  "type": null,
  "moves": [ ]
}
Fetched 10 record(s) in 19ms

```

##Pesquisar todos os pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49.

```
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> var query = {$and: [{moves: {$in:['investida']}}, {defense: {$not: {$lte:49}}}]}
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5654f3f1cd1bdd189cd39d6e"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "evasiva",
    "desvio"
  ]
}
{
  "_id": ObjectId("5655272d7ff3d5c60b68684f"),
  "moves": [
    "investida",
    "evasiva",
    "desvio"
  ],
  "name": "Squirtle",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null
}
{
  "_id": ObjectId("565527b27ff3d5c60b686850"),
  "moves": [
    "investida",
    "evasiva",
    "desvio"
  ],
  "name": "Bulbassauro",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null
}
{
  "_id": ObjectId("565527ef7ff3d5c60b686851"),
  "moves": [
    "investida",
    "evasiva",
    "desvio"
  ],
  "name": "Charmander",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null
}
Fetched 4 record(s) in 22ms

```
##Remova todos os pokemons do tipo água e com attack menor que 50.

```
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> var query = {$and: [{type: /water/i}, {attack: {$lt: 50}}]}
MacBook-Pro-de-Uilian-Nunes(mongod-3.0.3) be-mean-pokemons> db.pokemons.remove(query)
Removed 0 record(s) in 54ms
WriteResult({
  "nRemoved": 0
})

```

##Esse item não está no vídeo e se você fizer significa que você lê as coisas, nesse exercício demonstre qual a diferença entre os operadores $ne e $not.

```

$ne - Significa not equal ou não igual/diferente, ou seja ao realizar uma query e incluir o $ne ele irá negar a condição passada e retornar os documentos que sejam diferentes, por exemplo:

var query = {name: {$ne: 'pikachu'}

Porém, não pode ser usado Regex!!

$not - Já com o $not podemos ter tratamento para o caso de case-sensitive por exemplo, ele atuará de forma parecida com o $ne, retornando os resultados que não condizem com a regra passada por parametro.

(Não sei se está claro, mas é a forma como entendi :D )

```



