# MongoDB - Aula 03 - Exercício
    autor: Thiago Santos de Amorim

#Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

var attacks = ['move rápido', 'raio de fogo']

linux-atsn(mongod-3.2.1) be-mean-instagram> attacks
[
  "move rápido",
  "raio de fogo"
]


var query = {$or: [{nome: 'Pikachu'}, {nome: 'Squirtle'}, {nome: 'Bulbassauro'}, {nome: 'Charmander'}]}

linux-atsn(mongod-3.2.1) be-mean-instagram> query
{
  "$or": [
    {
      "nome": "Pikachu"
    },
    {
      "nome": "Squirtle"
    },
    {
      "nome": "Bulbassauro"
    },
    {
      "nome": "Charmander"
    }
  ]
}

var mod = {$pushAll: {moves: attacks}}

linux-atsn(mongod-3.2.1) be-mean-instagram> mod
{
  "$pushAll": {
    "moves": [
      "move rápido",
      "raio de fogo"
    ]
  }
}

var options = {multi: true}

linux-atsn(mongod-3.2.1) be-mean-instagram> db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 3ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})



# Adicionar 1 movimento em todos os pokemons: desvio.

linux-atsn(mongod-3.2.1) be-mean-instagram> var query = {}
linux-atsn(mongod-3.2.1) be-mean-instagram> var mod = {$push: {moves: 'bulmerangue de vento'}}
linux-atsn(mongod-3.2.1) be-mean-instagram> var options = {multi: true}
linux-atsn(mongod-3.2.1) be-mean-instagram> db.pokemons.update(query, mod, options)
Updated 7 existing record(s) in 3ms
WriteResult({
  "nMatched": 7,
  "nUpserted": 0,
  "nModified": 7
})


# Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".

linux-atsn(mongod-3.2.1) be-mean-instagram> var mod = {$set: {active: true}, $setOnInsert: {nome: "AindaNãoExisteMon", attack: null, defense: null, height: null, description: "Sem maiores informações"}}

# Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.

linux-atsn(mongod-3.2.1) be-mean-instagram> var query = {moves: {$in: [/investida/i, /bulmerangue/]}}
linux-atsn(mongod-3.2.1) be-mean-instagram> db.pokemons.find(query)


# Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

linux-atsn(mongod-3.2.1) be-mean-instagram> var query = {moves: {$in: [/move rapido/i, /bulmerangue/]}}
linux-atsn(mongod-3.2.1) be-mean-instagram> db.pokemons.find(query)


# Pesquisar todos os pokemons que não são do tipo elétrico.

linux-atsn(mongod-3.2.1) be-mean-instagram> var query = {type: {$not: /eletric/i}}
linux-atsn(mongod-3.2.1) be-mean-instagram> db.pokemons.find(query)


# Pesquisar todos pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49.

linux-atsn(mongod-3.2.1) be-mean-instagram> var query = {$and: [{moves: {$in: [/investida/i]}}, {defense:{$not: {$lte: 49}}}]}
linux-atsn(mongod-3.2.1) be-mean-instagram> db.pokemons.find(query)


# Remova todos os pokemons do tipo água e com attack menor que 50.

linux-atsn(mongod-3.2.1) be-mean-instagram> var query = {$and: [{type: /agua/i}, {attack: {$lt: 50}}]}
linux-atsn(mongod-3.2.1) be-mean-instagram> db.pokemons.remove(query)
