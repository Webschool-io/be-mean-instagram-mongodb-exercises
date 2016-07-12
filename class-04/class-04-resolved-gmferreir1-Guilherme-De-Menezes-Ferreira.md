# MongoDB - Aula 04 - Exercício
autor: Guilherme de Menezes Ferrira

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
(mongod-3.2.1) be-mean-pokemons> var query = {name:/pikachu/i}
(mongod-3.2.1) be-mean-pokemons> var mod  = {$pushAll:{moves:['Choque do trovão', 'esfera elétrica']}}
(mongod-3.2.1) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 3ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

(mongod-3.2.1) be-mean-pokemons> var query = {name:/bulbassauro/i}
be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 4ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

(mongod-3.2.1) be-mean-pokemons> var query = {name:/charmander/i}
(mongod-3.2.1) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 4ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

(mongod-3.2.1) be-mean-pokemons> var query = {name:/squirtle/i}
(mongod-3.2.1) be-mean-pokemons> var mod = {$pushAll:{moves:['Caralho de cana', 'Foda metalica']}}
(mongod-3.2.1) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 4ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```
(mongod-3.2.1) be-mean-pokemons> var mod = {$push:{moves:'desvio'}}
(mongod-3.2.1) be-mean-pokemons> var options = {multi:true}
(mongod-3.2.1) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 7 existing record(s) in 3ms
WriteResult({
  "nMatched": 7,
  "nUpserted": 0,
  "nModified": 7
})
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
(mongod-3.2.1) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}
(mongod-3.2.1) be-mean-pokemons> var mod = {$setOnInsert: {name: 'AindaNaoExisteMon', type: null, attack: null, defense: null, height: null, descrption: 'Sem maiores informações'}}
(mongod-3.2.1) be-mean-pokemons> var options = {upsert: true}
(mongod-3.2.1) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 4ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("56bf78be688fd09b42c420fa")
})
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
(mongod-3.2.1) be-mean-pokemons> var query = {moves: {$in: [/investida/i, /foda metalica/i]}}
(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56bdb4c87ee78537f807d683"),
  "name": "Squirtle",
  "description": "Descrição alterada",
  "attack": 300,
  "defense": 300,
  "height": 0.5,
  "moves": [
    "Caralho de cana",
    "Foda metalica",
    "desvio",
    "desvio"
  ]
}
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```
(mongod-3.2.1) be-mean-pokemons> var query = {moves: {$in: [ /caralho de cana/i]}}
(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56bdb4c87ee78537f807d683"),
  "name": "Squirtle",
  "description": "Descrição alterada",
  "attack": 300,
  "defense": 300,
  "height": 0.5,
  "moves": [
    "Caralho de cana",
    "Foda metalica",
    "desvio",
    "desvio"
  ]
}
```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```
Megazord(mongod-3.0.7) be-mean> var query = {type: {$not: /eletric/i}}

(mongod-3.2.1) be-mean-pokemons> var query = {type: {$not: /eletric/i}}
(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56bdb4c87ee78537f807d681"),
  "name": "bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the suns rays, the seed grows progressively larger",
  "attack": 30,
  "defense": 20,
  "height": 7,
  "moves": [
    "desvio",
    "desvio"
  ]
}
{
  "_id": ObjectId("56bdb4c87ee78537f807d682"),
  "name": "ivysaur",
  "description": "There is a bud on this Pokémon's back. To support its weight, Ivysaur's legs and trunk grow thick and strong. If it starts spending more time lying in the sunlight, it's a sign that the bud will bloom into a large flower soon.",
  "attack": 30,
  "defense": 30,
  "height": 10,
  "moves": [
    "desvio",
    "desvio"
  ]
}
{
  "_id": ObjectId("56bdb4c87ee78537f807d683"),
  "name": "Squirtle",
  "description": "Descrição alterada",
  "attack": 300,
  "defense": 300,
  "height": 0.5,
  "moves": [
    "Caralho de cana",
    "Foda metalica",
    "desvio",
    "desvio"
  ]
}
{
  "_id": ObjectId("56bdb4c87ee78537f807d684"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
  "attack": 300,
  "defense": 200,
  "height": 0.6,
  "moves": [
    "Choque do trovão",
    "esfera elétrica",
    "desvio",
    "desvio"
  ]
}
{
  "_id": ObjectId("56bdb4c87ee78537f807d685"),
  "name": "Farfetch'd",
  "description": "Farfetch'd is always seen with a stalk from a plant of some sort. Apparently, there are good stalks and bad stalks. This Pokémon has been known to fight with others over stalks.",
  "attack": 300,
  "defense": 300,
  "height": 0.8,
  "moves": [
    "desvio",
    "desvio"
  ]
}
{
  "_id": ObjectId("56bf74cba994abb464630c10"),
  "name": "Pikachu",
  "description": "Descrição do pikachu",
  "attack": 2,
  "defense": 21,
  "height": 0.5,
  "moves": [
    "Choque do trovão",
    "esfera elétrica",
    "desvio",
    "desvio"
  ]
}
{
  "_id": ObjectId("56bf74ffa994abb464630c11"),
  "name": "Bulbassauro",
  "description": "Descrição do Bulbassauro",
  "attack": 3,
  "defense": 11,
  "height": 1.5,
  "moves": [
    "Choque do trovão",
    "esfera elétrica",
    "desvio",
    "desvio"
  ]
}
{
  "_id": ObjectId("56bf78be688fd09b42c420fa"),
  "name": "AindaNaoExisteMon",
  "type": null,
  "attack": null,
  "defense": null,
  "height": null,
  "descrption": "Sem maiores informações"
}
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```
(mongod-3.2.1) be-mean-pokemons> var query1 = {moves: {$in: [/investida/i]}}
(mongod-3.2.1) be-mean-pokemons> var query2 = {defense: {$not: {$lte: 49}}}
(mongod-3.2.1) be-mean-pokemons> var query3 = {$and: [query1, query2]}
(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query3)
Fetched 0 record(s) in 0ms
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
(mongod-3.2.1) be-mean-pokemons> var query1 = {type:/water/i}
(mongod-3.2.1) be-mean-pokemons> var query2 = {attack: {$lt: 50}}
(mongod-3.2.1) be-mean-pokemons> var query3 = {$and: [query1, query2]}
(mongod-3.2.1) be-mean-pokemons> db.pokemons.remove(query3)
Removed 0 record(s) in 5ms
WriteResult({
  "nRemoved": 0
})
```