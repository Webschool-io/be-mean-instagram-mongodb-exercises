# MongoDB - Aula 04 - Exercício
autor: **Sergio Diniz Correia**

# 1- Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```javascript
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> var query = {name : {$in : [/pikachu/i, /bulbasaur/i, /squirtle/i, /charmander/i]}}
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll : {moves: ['Investida', 'Ataque Rapido']}}
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> var options = {multi:true}
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 10ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
```

# 2- Adicionar 1 movimento em todos os pokemons: desvio.
```javascript
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> var mod = {$push: {moves: 'Desvio'}}
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> var options = {multi:true}
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.update({}, mod, options)
Updated 9 existing record(s) in 3ms
WriteResult({
  "nMatched": 9,
  "nUpserted": 0,
  "nModified": 9
})


```

# 3- Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".
```javascript
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> var query = {name : /AindaNaoExisteMon/i}
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> var mod = {$setOnInsert : {"active": false, "nome": "AindaNaoExisteMon", "attack": null, "defense": null, "height": null, "description": "Sem maiores informações"}}
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> var options = {upsert:true}
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 3ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("56520bde6aa1bd8e4e977623")
})


```

# 4- Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.
```javascript
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$all : ['Investida', 'Ateque Unico']}}
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("565208a26a1fac10dd6f860e"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge.",
  "type": "Electric",
  "attack": 30,
  "height": 0.4,
  "moves": [
    "Investida",
    "Ataque Rapido",
    "Desvio",
    "Ateque Unico"
  ]
}
Fetched 1 record(s) in 2ms

```

# 5- Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.
```javascript
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$all : ['Investida', 'Ataque Rapido']}}
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("565208a26a1fac10dd6f860e"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge.",
  "type": "Electric",
  "attack": 30,
  "height": 0.4,
  "moves": [
    "Investida",
    "Ataque Rapido",
    "Desvio",
    "Ateque Unico"
  ]
}
{
  "_id": ObjectId("565208c26a1fac10dd6f860f"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "type": "Grass",
  "attack": 30,
  "height": 0.7,
  "moves": [
    "Investida",
    "Ataque Rapido",
    "Desvio"
  ]
}
{
  "_id": ObjectId("565208d16a1fac10dd6f8610"),
  "name": "Squirtle",
  "description": "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
  "type": "Water",
  "attack": 30,
  "height": 0.5,
  "moves": [
    "Investida",
    "Ataque Rapido",
    "Desvio"
  ]
}
{
  "_id": ObjectId("565208d96a1fac10dd6f8611"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
  "type": "Fire",
  "attack": 30,
  "height": 0.6,
  "moves": [
    "Investida",
    "Ataque Rapido",
    "Desvio"
  ]
}
Fetched 4 record(s) in 6ms


```

# 6- Pesquisar todos os pokemons que não são do tipo elétrico.
```javascript
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> var query = {type: {$ne : '/Electric/i'}}
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564b2cc2de86e4e06dfe93b3"),
  "name": "Krabby",
  "description": "Krabby live on beaches, burrowed inside holes dug into the sand. On sandy beaches with little in the way of food, these Pokémon can be seen squabbling with each other over territory.",
  "type": "Water",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b2d18de86e4e06dfe93b4"),
  "name": "Kingler",
  "description": "Kingler has an enormous, oversized claw. It waves this huge claw in the air to communicate with others. However, because the claw is so heavy, the Pokémon quickly tires.",
  "type": "Water",
  "attack": 55,
  "height": 1.3,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b2d42de86e4e06dfe93b5"),
  "name": "Voltorb",
  "description": "nova descricao :)",
  "type": "Water",
  "attack": 55,
  "height": 0.5,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b2d66de86e4e06dfe93b6"),
  "name": "Electrode",
  "description": "Electrode eats electricity in the atmosphere. On days when lightning strikes, you can see this Pokémon exploding all over the place from eating too much electricity.",
  "type": "Water",
  "attack": 55,
  "height": 1.2,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b2d8cde86e4e06dfe93b7"),
  "name": "Exeggcute",
  "description": "This Pokémon consists of six eggs that form a closely knit cluster. The six eggs attract each other and spin around. When cracks increasingly appear on the eggs, Exeggcute is close to evolution.",
  "type": "Water",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("565208a26a1fac10dd6f860e"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge.",
  "type": "Electric",
  "attack": 30,
  "height": 0.4,
  "moves": [
    "Investida",
    "Ataque Rapido",
    "Desvio"
  ]
}
{
  "_id": ObjectId("565208c26a1fac10dd6f860f"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "type": "Grass",
  "attack": 30,
  "height": 0.7,
  "moves": [
    "Investida",
    "Ataque Rapido",
    "Desvio"
  ]
}
{
  "_id": ObjectId("565208d16a1fac10dd6f8610"),
  "name": "Squirtle",
  "description": "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
  "type": "Water",
  "attack": 30,
  "height": 0.5,
  "moves": [
    "Investida",
    "Ataque Rapido",
    "Desvio"
  ]
}
{
  "_id": ObjectId("565208d96a1fac10dd6f8611"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
  "type": "Fire",
  "attack": 30,
  "height": 0.6,
  "moves": [
    "Investida",
    "Ataque Rapido",
    "Desvio"
  ]
}
{
  "_id": ObjectId("56520bde6aa1bd8e4e977623"),
  "active": false,
  "nome": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 10 record(s) in 6ms

```

# 7- Pesquisar todos pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49.
```javascript
be-mean-pokemons> var query = {$and : [{moves: "Investida"}, {attack : {$gt : 49}}]}
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms

```

# 8- Remova todos os pokemons do tipo água e com attack menor que 50.
```javascript
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> var query = {$and : [{type: "Water"}, {attack : {$lt: 50}}]}
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 4ms
WriteResult({
  "nRemoved": 1
})

```
