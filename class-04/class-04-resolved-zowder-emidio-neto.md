# MongoDB - Aula 04 - Exercício
autor: Emídio de Paiva Neto

## Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
ubuntu(mongod-3.0.7) be-mean-teste> var query = {name: /pikachu/i}
ubuntu(mongod-3.0.7) be-mean-teste> var mod = {$pushAll: {moves: ['Golpe mortal', 'Pulo mortal']}}
ubuntu(mongod-3.0.7) be-mean-teste> db.pokemons.update(query,mod)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

ubuntu(mongod-3.0.7) be-mean-teste> var query = {name: /squirtle/i}
ubuntu(mongod-3.0.7) be-mean-teste> var mod = {$pushAll: {moves: ['Golpe mortal', 'Pulo mortal']}}
ubuntu(mongod-3.0.7) be-mean-teste> db.pokemons.update(query,mod)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

ubuntu(mongod-3.0.7) be-mean-teste> var query = {name: /charmander/i}
ubuntu(mongod-3.0.7) be-mean-teste> var mod = {$pushAll: {moves: ['Golpe mortal', 'Pulo mortal']}}
ubuntu(mongod-3.0.7) be-mean-teste> db.pokemons.update(query,mod)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

ubuntu(mongod-3.0.7) be-mean-teste> var query = {name: /Bulbassauro/i}
ubuntu(mongod-3.0.7) be-mean-teste> var mod = {$pushAll: {moves: ['Golpe mortal ultra', 'Pulo mortal ultra']}}
ubuntu(mongod-3.0.7) be-mean-teste> db.pokemons.update(query,mod)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

```

## Adicionar 1 movimento em todos os pokemons: desvio.

```
ubuntu(mongod-3.0.7) be-mean-teste> var query = {}
ubuntu(mongod-3.0.7) be-mean-teste> var mod = {$push: {moves: 'desvio'}}
ubuntu(mongod-3.0.7) be-mean-teste> var options = {multi: true}
ubuntu(mongod-3.0.7) be-mean-teste> db.pokemons.update(query,mod,options)
Updated 4 existing record(s) in 1ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})


```

## Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".

```
ubuntu(mongod-3.0.7) be-mean-teste> var query = {name: /AindaNaoExisteMon/i}
ubuntu(mongod-3.0.7) be-mean-teste> var mod = {$setOnInsert: {name: 'AindaNaoExisteMon', type:null, attack: null, defense: null, height: null, description: 'Sem maiores informações'}}
ubuntu(mongod-3.0.7) be-mean-teste> var options = {upsert: true}
ubuntu(mongod-3.0.7) be-mean-teste> db.pokemons.update(query, mod, options)

Updated 1 new record(s) in 1ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("5664681091b5f759b9bc595c")
})


```

## Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.


```
ubuntu(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$in: [/investida/i, /golpe mortal/i]}}
ubuntu(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
ubuntu(mongod-3.0.7) be-mean-pokemons> db.savepokemons.find(query)
{
  "_id": ObjectId("566365c797534bcf952d5736"),
  "name": "Charizard",
  "description": "Respira fogo que derrete qualquer coisa",
  "type": "fire",
  "attack": 80,
  "defense": 60,
  "height": 1.7,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("566365c797534bcf952d5737"),
  "name": "Vulpix",
  "description": "Possui umas caudas muito loucas",
  "type": "fire",
  "attack": 60,
  "defense": 40,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("566365c797534bcf952d5738"),
  "name": "Raichu",
  "description": "Irmão do Pikachu",
  "type": "electric",
  "attack": 110,
  "defense": 90,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("566365c797534bcf952d5739"),
  "name": "Blastoise",
  "description": "Blastoise tem bicas de água que se projetam de sua concha.",
  "type": "water",
  "attack": "110",
  "defense": 65,
  "height": 1.6,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("566453700e1afa7315cc2ef4"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "moves": [
    "investida",
    "desvio",
    "Golpe mortal"
  ],
  "active": false
}
{
  "_id": ObjectId("566365c797534bcf952d5735"),
  "name": "Wartotle",
  "description": "Os arranhões na sua concha são a prova de resistência deste Pokémon como um combatente.",
  "type": "water",
  "attack": "90",
  "defense": "40",
  "height": 1,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}


ubuntu(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$all: [/investida/i, /golpe mortal/i]}}
ubuntu(mongod-3.0.7) be-mean-pokemons> var favorito = {$and: [query, {name: /testemon/i}]}
ubuntu(mongod-3.0.7) be-mean-pokemons> db.savepokemons.find(favorito)
{
  "_id": ObjectId("566453700e1afa7315cc2ef4"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "moves": [
    "investida",
    "desvio",
    "Golpe mortal"
  ],
  "active": false
}
Fetched 1 record(s) in 1ms

```

## Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.
```
ubuntu(mongod-3.0.7) be-mean-teste> var query = {moves: {$all: [/golpe mortal/i, /pulo mortal/i]}}
ubuntu(mongod-3.0.7) be-mean-teste> db.pokemons.find(query)
{
  "_id": ObjectId("56634e147b3e97e09347bc78"),
  "name": "Bulbassauro",
  "description": "Chicote de trapadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "Golpe mortal ultra",
    "Pulo mortal ultra",
    "desvio"
  ]
}
{
  "_id": ObjectId("56634e647b3e97e09347bc79"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "Golpe mortal",
    "Pulo mortal",
    "desvio"
  ]
}
{
  "_id": ObjectId("56634ea87b3e97e09347bc7a"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "Golpe mortal",
    "Pulo mortal",
    "desvio"
  ]
}
{
  "_id": ObjectId("56634ebe7b3e97e09347bc7b"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "Golpe mortal",
    "Pulo mortal",
    "desvio"
  ]
}
Fetched 4 record(s) in 4ms


 var query = {moves: {$all: [/golpe mortal/i, /pulo mortal/i]}}
 var favorito = {$and: [query, {name: /testemon/i}]}
 db.savepokemons.find(favorito)

{
  "_id": ObjectId("566453700e1afa7315cc2ef4"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "moves": [
    "investida",
    "desvio",
    "Golpe mortal",
    "Pulo mortal"
  ],
  "active": false
}
Fetched 1 record(s) in 1ms

```

## Pesquisar todos os pokemons que não são do tipo elétrico.
```
 var query = {type: {$nin: ["electric"]}}
 db.savepokemons.find(query)

{
  "_id": ObjectId("566365c797534bcf952d5736"),
  "name": "Charizard",
  "description": "Respira fogo que derrete qualquer coisa",
  "type": "fire",
  "attack": 80,
  "defense": 60,
  "height": 1.7,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("566365c797534bcf952d5737"),
  "name": "Vulpix",
  "description": "Possui umas caudas muito loucas",
  "type": "fire",
  "attack": 60,
  "defense": 40,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("566365c797534bcf952d5739"),
  "name": "Blastoise",
  "description": "Blastoise tem bicas de água que se projetam de sua concha.",
  "type": "water",
  "attack": "110",
  "defense": 65,
  "height": 1.6,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("566453700e1afa7315cc2ef4"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "moves": [
    "investida",
    "desvio",
    "Golpe mortal",
    "Pulo mortal"
  ],
  "active": false
}
{
  "_id": ObjectId("566365c797534bcf952d5735"),
  "name": "Wartotle",
  "description": "Os arranhões na sua concha são a prova de resistência deste Pokémon como um combatente.",
  "type": "water",
  "attack": "90",
  "defense": "40",
  "height": 1,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}

```

## Pesquisar todos os pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49.
```
 var query = {$and: [{moves: {$in: ['investida']}}, {defense: {$not: {$lte: 49}}}]}
 
 db.savepokemons.find(query)

{
  "_id": ObjectId("566365c797534bcf952d5736"),
  "name": "Charizard",
  "description": "Respira fogo que derrete qualquer coisa",
  "type": "fire",
  "attack": 80,
  "defense": 60,
  "height": 1.7,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("566365c797534bcf952d5738"),
  "name": "Raichu",
  "description": "Irmão do Pikachu",
  "type": "electric",
  "attack": 110,
  "defense": 90,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("566365c797534bcf952d5739"),
  "name": "Blastoise",
  "description": "Blastoise tem bicas de água que se projetam de sua concha.",
  "type": "water",
  "attack": "110",
  "defense": 65,
  "height": 1.6,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("566453700e1afa7315cc2ef4"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "moves": [
    "investida",
    "desvio",
    "Golpe mortal",
    "Pulo mortal"
  ],
  "active": false
}
{
  "_id": ObjectId("566365c797534bcf952d5735"),
  "name": "Wartotle",
  "description": "Os arranhões na sua concha são a prova de resistência deste Pokémon como um combatente.",
  "type": "water",
  "attack": "90",
  "defense": "40",
  "height": 1,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
```

## Remova todos os pokemons do tipo água E com attack menor que 50.
```
 var query = {$and: [{type:/water/i}, {attack: {$lt: 50}}]}
 db.savepokemons.remove(query)

Removed 1 record(s) in 2ms
WriteResult({
  "nRemoved": 1
})

```

## Esse item não está no vídeo e se você fizer significa que você lê as coisas, nesse exercício demonstre qual a diferença entre os operadores $ne e $not.

```
$ne -> o $ne seleciona os documentos onde o valor do campo não é igual ou seja != para o valor especificado, isto inclui documentos que não contêm o campo. Ah, e também não aceita Regex.
$not -> Já o $not aceita regex, e executa uma operação lógica NOT, selecionando os documentos que não correspondem ao operador <expressão>. 

Resumindo: O operador $not para disjunções lógicas e o operador $ne para testar diretamente o conteúdo dos campos.
```
