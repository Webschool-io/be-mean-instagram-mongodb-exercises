#Exercício 4 - MongoDB - BeMEAN#

##Aluno: Leonardo Ribeiro##


###Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander###
```
var query = { $or: [ {name: "Pikachu"}, {name: "Squirtle"}, {name: "Bulbassauro"}, {name: "Charmander"} ] }
var mod = {$set: {moves: ['Ataque Rápido', 'Defesa Alta']}}
var options = {multi: true}
b.pokemons.update(query,mod,options)
Updated 4 existing record(s) in 1ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
```

###Adicionar 1 movimento em todos os pokemons: desvio###
```
iMac-de-Leonardo(mongod-3.2.7) be-mean-pokemons> var query = {}
iMac-de-Leonardo(mongod-3.2.7) be-mean-pokemons> var mod = {$set: {moves: ["Desvio"]}}
iMac-de-Leonardo(mongod-3.2.7) be-mean-pokemons> db.pokemons.update(query,mod,options)
Updated 8 existing record(s) in 1ms
WriteResult({
  "nMatched": 8,
  "nUpserted": 0,
  "nModified": 8
})
```

###Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações"###
```
var query = { name: "AindaNaoExisteMon", description: "Sem maiores informações", attack: null, defense: null, height: null, type: null }
db.pokemons.save(query)
Inserted 1 record(s) in 4ms
WriteResult({
  "nInserted": 1
})
```

###Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito###
```
var query= {moves: {$in: ["Investida"]}}
iMac-de-Leonardo(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5783d060dc6eb212ff9808e7"),
  "name": "Pikachu",
  "description": "Pikachu is an Electric type Pokémon introduced in Generation 1. It is known as the Mouse Pokémon",
  "attack": 229,
  "defense": 196,
  "height": 0.4,
  "type": "ELECTRIC",
  "moves": [
    "Desvio",
    "Investida"
  ]
}
{
  "_id": ObjectId("5783d0dcdc6eb212ff9808eb"),
  "name": "Caterpie",
  "description": "Caterpie has a voracious appetite. It can devour leaves bigger than its body right before your eyes. From its antenna, this Pokémon releases a terrifically strong odor.",
  "attack": 200,
  "defense": 200,
  "height": 0.3,
  "type": "grass",
  "moves": [
    "Desvio",
    "Investida"
  ]
}
Fetched 2 record(s) in 0ms
```

###Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito###
```
be-mean-pokemons> var query= {moves: {$in: ["Investida", "Desvio", "Ataque Rápido", "Defesa Alta"]}}
iMac-de-Leonardo(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5783d060dc6eb212ff9808e7"),
  "name": "Pikachu",
  "description": "Pikachu is an Electric type Pokémon introduced in Generation 1. It is known as the Mouse Pokémon",
  "attack": 229,
  "defense": 196,
  "height": 0.4,
  "type": "ELECTRIC",
  "moves": [
    "Desvio",
    "Investida"
  ]
}
{
  "_id": ObjectId("5783d086dc6eb212ff9808e8"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "attack": 300,
  "defense": 200,
  "height": 0.7,
  "type": "grass",
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("5783d0a7dc6eb212ff9808e9"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
  "attack": 300,
  "defense": 200,
  "height": 0.6,
  "type": "grass",
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("5783d0bfdc6eb212ff9808ea"),
  "name": "Squirtle",
  "description": "Pokemon que lança liquido venenoso",
  "attack": 300,
  "defense": 300,
  "height": 0.5,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("5783d0dcdc6eb212ff9808eb"),
  "name": "Caterpie",
  "description": "Caterpie has a voracious appetite. It can devour leaves bigger than its body right before your eyes. From its antenna, this Pokémon releases a terrifically strong odor.",
  "attack": 200,
  "defense": 200,
  "height": 0.3,
  "type": "grass",
  "moves": [
    "Desvio",
    "Investida"
  ]
}
{
  "_id": ObjectId("5783d0eddc6eb212ff9808ec"),
  "name": "Butterfree",
  "description": "Butterfree has a superior ability to search for delicious honey from flowers. It can even search out, extract, and carry honey from flowers that are blooming over six miles from its nest.",
  "attack": 200,
  "defense": 200,
  "height": 1.1,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("5783d0fadc6eb212ff9808ed"),
  "name": "Abra",
  "description": "Abra sleeps for eighteen hours a day. However, it can sense the presence of foes even while it is sleeping. In such a situation, this Pokémon immediately teleports to safety.",
  "attack": 100,
  "defense": 100,
  "height": 0.9,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("5783d10cdc6eb212ff9808ee"),
  "name": "Farfetch'd",
  "description": "Farfetch'd is always seen with a stalk from a plant of some sort. Apparently, there are good stalks and bad stalks. This Pokémon has been known to fight with others over stalks.",
  "attack": 300,
  "defense": 300,
  "height": 0.8,
  "moves": [
    "Desvio"
  ]
}
Fetched 8 record(s) in 3ms
`

###Pesquisar todos os pokemons que não são do tipo elétrico###
`
iMac-de-Leonardo(mongod-3.2.7) be-mean-pokemons> var query= {type: /electric/i}
iMac-de-Leonardo(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5783d060dc6eb212ff9808e7"),
  "name": "Pikachu",
  "description": "Pikachu is an Electric type Pokémon introduced in Generation 1. It is known as the Mouse Pokémon",
  "attack": 229,
  "defense": 196,
  "height": 0.4,
  "type": "ELECTRIC",
  "moves": [
    "Desvio",
    "Investida"
  ]
}
Fetched 1 record(s) in 1ms
```

###Pesquisar todos pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49###
```
be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
iMac-de-Leonardo(mongod-3.2.7) be-mean-pokemons> var query = {
...   $and: [
...     {
...       moves: {$in: ['investida']}
...     },
...     {
...       defense: {$not: {$lte: 49}}
...     }
...   ]
... }
iMac-de-Leonardo(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```

###Remova todos os pokemons do tipo água e com attack menor que 50###
```
be-mean-pokemons> var query = {$and: [ {type: "water"}], attack:{$lt:50}}
iMac-de-Leonardo(mongod-3.2.7) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 0ms
WriteResult({
  "nRemoved": 1
})
```