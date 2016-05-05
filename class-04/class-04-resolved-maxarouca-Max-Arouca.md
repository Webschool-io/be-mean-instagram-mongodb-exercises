# MongoDB - Aula 04 - Exercício
autor: **Max Arouca**

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

````javascript
var query = {$or: [{name: /pikachu/i}, {name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbassauro/i}, {name: /charmander/i}]}

var mod = {$set: {moves: ['Bater', 'controlar psiquico']}}

var options = { multi: true }

db.pokemons.update(query, mod)

Updated 4 existing record(s) in 3ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})


````

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

````javascript

var query = {}

var mod = {$push: {moves: 'desvio'}}

var options = {multi: true}

db.pokemons.update(query, mod, options)

Updated 11 existing record(s) in 30ms
WriteResult({
  "nMatched": 11,
  "nUpserted": 0,
  "nModified": 11
})

````


## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

````javascript

var poke = {name: "AindaNaoExisteMon", attack: null, defense: null, height: null, description: "Sem maiores informações"}

db.pokemons.save(poke)

Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})

````

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

````javascript

var query = {moves:{$in:[/investida/i, /bater/i]}}
db.pokemons.find(query)


````


## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

````javascript

var query = {moves:{$in:[/bater/i,/controlar psiquico/i]}}
db.pokemons.find(query)

````


## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

````javascript

var query = {type: /eletrico/i}
db.pokemons.find(query)

````


## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

````javascript

var query = {$and: [{moves: /investida/i}, { "defense" : { $lt: 49 } }]}
db.pokemons.find(query)

````

## Remova **todos** os pokemons do tipo água e com attack menor que 50.

````javascript

var query = {$and: [{"type": "água"}, { "attack" : { $lt: 50 } }]}
db.pokemons.remove(query)
