#MongoDB - Aula 04 - Exercício
Autor: Sadraque Santos

## 1 - **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Psyduck, Caterpie e Blastoise
```js
var query = {$or:[{name: /pikachu/i},
             {name: /psyduck/i},
             {name: /caterpie/i},
             {name: /blastoise/i}]}
var mod = {$pushAll: {moves: ["Defesa", "Esquiva"]}}
var options = {multi: true}

db.pokemons.update(query, mod, options)
// Updated 4 existing record(s) in 1ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
```

## 2 - **Adicionar** o movimento `desvio` a todos os pokemons.
```js
var query = {}
var mod = {$push: {moves: "Desvio"}}
var options = {multi:true}
db.pokemons.update(query, mod, options)
// Updated 6 existing record(s) in 1ms
WriteResult({
  "nMatched": 6,
  "nUpserted": 0,
  "nModified": 6
})
```

## 3 - **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".
```js
var query = {name: /AindaNaoExisteMon/i}
var mod = {
  $setOnInsert: {
    name: "AindaNaoExisteMon",
    attack: null,
    defense: null,
    height: null,
    description: "Sem maiores informações"
  }
}
var options = {upsert: true}
db.pokemons.update(query, mod, options)
// Updated 1 new record(s) in 59ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("579893bffa33c97ac0397cec")
})
```

## 4 - Pesquisar todos os pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha o seu pokemon favorito.
```js
var query = {moves: {$all: [/investida/i, /defesa/i]}}
db.pokemons.find(query)
{
  "_id": ObjectId("57988dc503faffc347b7d693"),
  "name": "Blastoise",
  "description": "They can shoot bullets of water with enough accuracy to strike",
  "attack": 150,
  "defense": 300,
  "height": 1.6,
  "moves": [
    "Defesa",
    "Esquiva",
    "Desvio",
    "Investida"
  ]
}
{
  "_id": ObjectId("57988dc503faffc347b7d694"),
  "name": "Caterpie",
  "description": "Caterpie has a voracious appetite. It can devour leaves bigger than its body right before your eyes. From its antenna, this Pokémon releases a terrifically strong odor",
  "type": "grama",
  "attack": 25,
  "defense": 60,
  "height": 0.3,
  "moves": [
    "Defesa",
    "Esquiva",
    "Desvio",
    "Investida"
  ]
}
{
  "_id": ObjectId("57988dc503faffc347b7d696"),
  "name": "Psyduck",
  "description": "Psyduck uses a mysterious power. When it does so, this Pokémon generates brain waves that are supposedly only seen in sleepers",
  "attack": 175,
  "defense": 80,
  "height": 0.8,
  "moves": [
    "Defesa",
    "Esquiva",
    "Desvio",
    "Investida"
  ]
}
{
  "_id": ObjectId("57988dc503faffc347b7d697"),
  "name": "Pikachu",
  "description": "Rato que fala pornografia",
  "attack": 55,
  "defense": 70,
  "height": 0.4,
  "moves": [
    "Defesa",
    "Esquiva",
    "Desvio",
    "Investida"
  ]
}
// Fetched 4 record(s) in 2ms
```

## 5 - Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha o seu pokemon favorito.
```js
var query = {moves: {$in: [/defesa/i]}};
db.pokemons.find(query)
{
  "_id": ObjectId("57988dc503faffc347b7d693"),
  "name": "Blastoise",
  "description": "They can shoot bullets of water with enough accuracy to strike",
  "attack": 150,
  "defense": 300,
  "height": 1.6,
  "moves": [
    "Defesa",
    "Esquiva",
    "Desvio",
    "Investida"
  ]
}
{
  "_id": ObjectId("57988dc503faffc347b7d694"),
  "name": "Caterpie",
  "description": "Caterpie has a voracious appetite. It can devour leaves bigger than its body right before your eyes. From its antenna, this Pokémon releases a terrifically strong odor",
  "type": "grama",
  "attack": 25,
  "defense": 60,
  "height": 0.3,
  "moves": [
    "Defesa",
    "Esquiva",
    "Desvio",
    "Investida"
  ]
}
{
  "_id": ObjectId("57988dc503faffc347b7d696"),
  "name": "Psyduck",
  "description": "Psyduck uses a mysterious power. When it does so, this Pokémon generates brain waves that are supposedly only seen in sleepers",
  "attack": 175,
  "defense": 80,
  "height": 0.8,
  "moves": [
    "Defesa",
    "Esquiva",
    "Desvio",
    "Investida"
  ]
}
{
  "_id": ObjectId("57988dc503faffc347b7d697"),
  "name": "Pikachu",
  "description": "Rato que fala pornografia",
  "attack": 55,
  "defense": 70,
  "height": 0.4,
  "moves": [
    "Defesa",
    "Esquiva",
    "Desvio",
    "Investida"
  ]
}
// Fetched 4 record(s) in 2ms
```

## 6 - Pesquisar **todos** os pokemons que não são do tipo `elétrico`.
```js
var query = {type: {$not: /elétrico/i}}
db.pokemons.find(query)
{
  "_id": ObjectId("57988dc503faffc347b7d692"),
  "name": "Charmander",
  "description": "The roof is on fire",
  "attack": 200,
  "defense": 80,
  "height": 0.6,
  "moves": [
    "Desvio",
    "Investida"
  ]
}
{
  "_id": ObjectId("57988dc503faffc347b7d693"),
  "name": "Blastoise",
  "description": "They can shoot bullets of water with enough accuracy to strike",
  "attack": 150,
  "defense": 300,
  "height": 1.6,
  "moves": [
    "Defesa",
    "Esquiva",
    "Desvio",
    "Investida"
  ]
}
{
  "_id": ObjectId("57988dc503faffc347b7d694"),
  "name": "Caterpie",
  "description": "Caterpie has a voracious appetite. It can devour leaves bigger than its body right before your eyes. From its antenna, this Pokémon releases a terrifically strong odor",
  "type": "grama",
  "attack": 25,
  "defense": 60,
  "height": 0.3,
  "moves": [
    "Defesa",
    "Esquiva",
    "Desvio",
    "Investida"
  ]
}
{
  "_id": ObjectId("57988dc503faffc347b7d695"),
  "name": "Jigglypuff",
  "description": "Jigglypuff\"s vocal cords can freely adjust the wavelength of its voice.",
  "attack": 20,
  "defense": 120,
  "height": 0.5,
  "moves": [
    "Desvio",
    "Investida"
  ]
}
{
  "_id": ObjectId("57988dc503faffc347b7d696"),
  "name": "Psyduck",
  "description": "Psyduck uses a mysterious power. When it does so, this Pokémon generates brain waves that are supposedly only seen in sleepers",
  "attack": 175,
  "defense": 80,
  "height": 0.8,
  "moves": [
    "Defesa",
    "Esquiva",
    "Desvio",
    "Investida"
  ]
}
{
  "_id": ObjectId("579893bffa33c97ac0397cec"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações",
  "moves": [
    "Investida"
  ]
}
// Fetched 6 record(s) in 2ms
```

## 7 - Pesquisar **todos** os pokemons que tenham o ataque `investida` **e** tenham a defesa **não menor ou igual** a 49.
```js
var query = {$and:[
              {moves: {$in: [/investida/i]}},
              {defense: {$gte: 49}}
            ]}
db.pokemons.find(query)
{
  "_id": ObjectId("57988dc503faffc347b7d692"),
  "name": "Charmander",
  "description": "The roof is on fire",
  "attack": 200,
  "defense": 80,
  "height": 0.6,
  "moves": [
    "Desvio",
    "Investida"
  ]
}
{
  "_id": ObjectId("57988dc503faffc347b7d693"),
  "name": "Blastoise",
  "description": "They can shoot bullets of water with enough accuracy to strike",
  "attack": 150,
  "defense": 300,
  "height": 1.6,
  "moves": [
    "Defesa",
    "Esquiva",
    "Desvio",
    "Investida"
  ]
}
{
  "_id": ObjectId("57988dc503faffc347b7d694"),
  "name": "Caterpie",
  "description": "Caterpie has a voracious appetite. It can devour leaves bigger than its body right before your eyes. From its antenna, this Pokémon releases a terrifically strong odor",
  "type": "grama",
  "attack": 25,
  "defense": 60,
  "height": 0.3,
  "moves": [
    "Defesa",
    "Esquiva",
    "Desvio",
    "Investida"
  ]
}
{
  "_id": ObjectId("57988dc503faffc347b7d695"),
  "name": "Jigglypuff",
  "description": "Jigglypuff\"s vocal cords can freely adjust the wavelength of its voice.",
  "attack": 20,
  "defense": 120,
  "height": 0.5,
  "moves": [
    "Desvio",
    "Investida"
  ]
}
{
  "_id": ObjectId("57988dc503faffc347b7d696"),
  "name": "Psyduck",
  "description": "Psyduck uses a mysterious power. When it does so, this Pokémon generates brain waves that are supposedly only seen in sleepers",
  "attack": 175,
  "defense": 80,
  "height": 0.8,
  "moves": [
    "Defesa",
    "Esquiva",
    "Desvio",
    "Investida"
  ]
}
{
  "_id": ObjectId("57988dc503faffc347b7d697"),
  "name": "Pikachu",
  "description": "Rato que fala pornografia",
  "attack": 55,
  "defense": 70,
  "height": 0.4,
  "moves": [
    "Defesa",
    "Esquiva",
    "Desvio",
    "Investida"
  ],
  "type": "Elétrico"
}
// Fetched 6 record(s) in 2ms
```

## 8 - Remova **todos** os pokemons do tipo água e com ataque menor que 50.
```js
var query = { $and:[ { type: /água/i }, { attack: { $lt: 50 }} ]}
db.pokemons.remove(query)
// Removed 1 record(s) in 2ms
WriteResult({
  "nRemoved": 1
})
```
