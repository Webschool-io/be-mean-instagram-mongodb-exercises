## MongoDb - Aula 4 - Exercício
autor: Victor Gomes Baby

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander

MacBook-Pro-de-Victor(mongod-3.0.7) be-mean-pokemon> var query = {$or: [{name:/pikachu/i},{name:/squirtle/i}, {name:/bulbasauro/i}, {name:/charmander/i}]}
MacBook-Pro-de-Victor(mongod-3.0.7) be-mean-pokemon> var mod = {$push:{moves:['ataque rápido', 'rugido']}}
MacBook-Pro-de-Victor(mongod-3.0.7) be-mean-pokemon> var options = {multi:true}
MacBook-Pro-de-Victor(mongod-3.0.7) be-mean-pokemon> db.pokemons.update(query, mod, options)
Updated 3 existing record(s) in 160ms
WriteResult({
  "nMatched": 3,
  "nUpserted": 0,
  "nModified": 3
})
MacBook-Pro-de-Victor(mongod-3.0.7) be-mean-pokemon> db.pokemons.find(query)
{
  "_id": ObjectId("564b80055ec9c44174cd0e18"),
  "name": "Pikachu",
  "type": "eletric",
  "attack": 100,
  "defense": 100,
  "height": 0.4,
  "description": "Rato eletrico bem fofinho",
  "moves": [
    "investida",
    "choque do trovão",
    [
      "ataque rápido",
      "rugido"
    ]
  ],
  "active": false
}
{
  "_id": ObjectId("564d27cb1f2c64c09f9129ea"),
  "active": false,
  "name": "Squirtle",
  "attack": 80,
  "defense": 100,
  "height": 0.8,
  "description": "Tartaruga cospe água",
  "moves": [
    "investida",
    [
      "ataque rápido",
      "rugido"
    ]
  ]
}
{
  "_id": ObjectId("564d295a1f2c64c09f9129ec"),
  "active": false,
  "name": "Charmander",
  "attack": 666,
  "defense": 666,
  "height": 0.8,
  "description": "Bixo do capeta",
  "moves": [
    "investida",
    [
      "ataque rápido",
      "rugido"
    ]
  ]
}
Fetched 3 record(s) in 136ms

## **Adicionar** 1 movimento em todos os pokemons: 'desvio'

MacBook-Pro-de-Victor(mongod-3.0.7) be-mean-pokemon> var query = {}
MacBook-Pro-de-Victor(mongod-3.0.7) be-mean-pokemon> var mod = {$set:{moves:['desvio']}}
MacBook-Pro-de-Victor(mongod-3.0.7) be-mean-pokemon> var options = {multi:true}
MacBook-Pro-de-Victor(mongod-3.0.7) be-mean-pokemon> db.pokemons.update(query, mod, options)
Updated 12 existing record(s) in 33ms
WriteResult({
  "nMatched": 12,
  "nUpserted": 0,
  "nModified": 12
})
MacBook-Pro-de-Victor(mongod-3.0.7) be-mean-pokemon> db.pokemons.find()
{
  "_id": ObjectId("564292e2cb1c07093682ea93"),
  "name": "Geodude",
  "description": "The longer a Geodude lives, the more its edges are chipped and worn away, making it more rounded in appearance. However, this Pokémon heart will remain hard, craggy, and rough always.",
  "type": "rock",
  "attack": 65,
  "defense": 40,
  "height": 0.4,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564292e2cb1c07093682ea94"),
  "name": "Zubat",
  "description": "Zubat remains quietly unmoving in a dark spot during the bright daylight hours. It does so because prolonged exposure to the sun causes its body to become slightly burned.",
  "type": "poison",
  "attack": 30,
  "defense": 30,
  "height": 0.8,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564292e2cb1c07093682ea95"),
  "name": "Lapras",
  "description": "People have driven Lapras almost to the point of extinction. In the evenings, this Pokémon is said to sing plaintively as it seeks what few others of its kind still remain.",
  "type": "water",
  "attack": 40,
  "defense": 40,
  "height": 2.5,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564292e2cb1c07093682ea96"),
  "name": "Sandshrew",
  "description": "Sandshrews body is configured to absorb water without waste, enabling it to survive in an arid desert. This Pokémon curls up to protect itself from its enemies.",
  "type": "ground",
  "attack": 45,
  "defense": 45,
  "height": 0.6,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564292e2cb1c07093682ea97"),
  "name": "Pidgey",
  "description": "Passarinho foda para karaleo",
  "type": "flying",
  "attack": 30,
  "defense": 30,
  "height": 0.3,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564b77ca5ec9c44174cd0e17"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "moves": [
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("564b80055ec9c44174cd0e18"),
  "name": "Pikachu",
  "type": "eletric",
  "attack": 100,
  "defense": 100,
  "height": 0.4,
  "description": "Rato eletrico bem fofinho",
  "moves": [
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("564d12585fff1457894bb17e"),
  "active": false,
  "name": "NaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564d0e7f5fff1457894bb17d"),
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564d27cb1f2c64c09f9129ea"),
  "active": false,
  "name": "Squirtle",
  "attack": 80,
  "defense": 100,
  "height": 0.8,
  "description": "Tartaruga cospe água",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564d28b41f2c64c09f9129eb"),
  "active": false,
  "name": "Bulbassauro",
  "attack": 90,
  "defense": 90,
  "height": 0.7,
  "description": "Squirtle o krlh",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564d295a1f2c64c09f9129ec"),
  "active": false,
  "name": "Charmander",
  "attack": 666,
  "defense": 666,
  "height": 0.8,
  "description": "Bixo do capeta",
  "moves": [
    "desvio"
  ]
}
Fetched 12 record(s) in 43ms

## **Adicionar** o pokemon 'AindaNaoExisteMon' caso ele não exista com todos os dados com o valor 'null' e a descrição : 'Sem maiores informações'

MacBook-Pro-de-Victor(mongod-3.0.7) be-mean-pokemon> var query = {name:/AindaNaoExisteMon/i}
MacBook-Pro-de-Victor(mongod-3.0.7) be-mean-pokemon> var mod = {$set:{active:true}, $setOnInsert:{name:'AindaNaoExisteMon', attack: null, defense:null, height:null, description:'Sem maiores informações', moves:[null]}}
MacBook-Pro-de-Victor(mongod-3.0.7) be-mean-pokemon> var options = {upsert:true}
MacBook-Pro-de-Victor(mongod-3.0.7) be-mean-pokemon> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 105ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564d357b5fff1457894bb17f")
})
MacBook-Pro-de-Victor(mongod-3.0.7) be-mean-pokemon> db.pokemons.find(query)
{
  "_id": ObjectId("564d357b5fff1457894bb17f"),
  "active": true,
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações",
  "moves": [
    null
  ]
}
Fetched 1 record(s) in 23ms

## Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito

MacBook-Pro-de-Victor(mongod-3.0.7) be-mean-pokemon> var query = {moves:{$in:['rugido','ataque rapido', 'desvio']}}
MacBook-Pro-de-Victor(mongod-3.0.7) be-mean-pokemon> db.pokemons.find(query)
{
  "_id": ObjectId("564292e2cb1c07093682ea93"),
  "name": "Geodude",
  "description": "The longer a Geodude lives, the more its edges are chipped and worn away, making it more rounded in appearance. However, this Pokémon heart will remain hard, craggy, and rough always.",
  "type": "rock",
  "attack": 65,
  "defense": 40,
  "height": 0.4,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564292e2cb1c07093682ea94"),
  "name": "Zubat",
  "description": "Zubat remains quietly unmoving in a dark spot during the bright daylight hours. It does so because prolonged exposure to the sun causes its body to become slightly burned.",
  "type": "poison",
  "attack": 30,
  "defense": 30,
  "height": 0.8,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564292e2cb1c07093682ea95"),
  "name": "Lapras",
  "description": "People have driven Lapras almost to the point of extinction. In the evenings, this Pokémon is said to sing plaintively as it seeks what few others of its kind still remain.",
  "type": "water",
  "attack": 40,
  "defense": 40,
  "height": 2.5,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564292e2cb1c07093682ea96"),
  "name": "Sandshrew",
  "description": "Sandshrews body is configured to absorb water without waste, enabling it to survive in an arid desert. This Pokémon curls up to protect itself from its enemies.",
  "type": "ground",
  "attack": 45,
  "defense": 45,
  "height": 0.6,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564292e2cb1c07093682ea97"),
  "name": "Pidgey",
  "description": "Passarinho foda para karaleo",
  "type": "flying",
  "attack": 30,
  "defense": 30,
  "height": 0.3,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564b77ca5ec9c44174cd0e17"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "moves": [
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("564d12585fff1457894bb17e"),
  "active": false,
  "name": "NaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564d0e7f5fff1457894bb17d"),
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564d3b531f2c64c09f9129ed"),
  "active": false,
  "name": "Charmander",
  "attack": 666,
  "defense": 666,
  "height": 0.8,
  "description": "Bixo do capeta",
  "moves": [
    "investida",
    "rugido",
    "ataque rapido"
  ]
}
{
  "_id": ObjectId("564d3b741f2c64c09f9129ef"),
  "active": false,
  "name": "Squirtle",
  "attack": 80,
  "defense": 100,
  "height": 0.8,
  "description": "Tartaruga cospe água",
  "moves": [
    "investida",
    "rugido",
    "ataque rapido"
  ]
}
{
  "_id": ObjectId("564d3bc61f2c64c09f9129f0"),
  "active": false,
  "name": "Pikachu",
  "attack": 100,
  "defense": 100,
  "height": 0.8,
  "description": "Ratinho elétrico fofinho",
  "type": "eletric",
  "moves": [
    "investida",
    "choque do trovão",
    "rugido",
    "ataque rapido"
  ]
}
Fetched 11 record(s) in 7ms

## Pesquisar **todos** os pokemons que não são do tipo 'elétrico'

MacBook-Pro-de-Victor(mongod-3.0.7) be-mean-pokemon> var query = {type:{$ne:'eletric'}}
MacBook-Pro-de-Victor(mongod-3.0.7) be-mean-pokemon> db.pokemons.find(query)
{
  "_id": ObjectId("564292e2cb1c07093682ea93"),
  "name": "Geodude",
  "description": "The longer a Geodude lives, the more its edges are chipped and worn away, making it more rounded in appearance. However, this Pokémon heart will remain hard, craggy, and rough always.",
  "type": "rock",
  "attack": 65,
  "defense": 40,
  "height": 0.4,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564292e2cb1c07093682ea94"),
  "name": "Zubat",
  "description": "Zubat remains quietly unmoving in a dark spot during the bright daylight hours. It does so because prolonged exposure to the sun causes its body to become slightly burned.",
  "type": "poison",
  "attack": 30,
  "defense": 30,
  "height": 0.8,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564292e2cb1c07093682ea95"),
  "name": "Lapras",
  "description": "People have driven Lapras almost to the point of extinction. In the evenings, this Pokémon is said to sing plaintively as it seeks what few others of its kind still remain.",
  "type": "water",
  "attack": 40,
  "defense": 40,
  "height": 2.5,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564292e2cb1c07093682ea96"),
  "name": "Sandshrew",
  "description": "Sandshrews body is configured to absorb water without waste, enabling it to survive in an arid desert. This Pokémon curls up to protect itself from its enemies.",
  "type": "ground",
  "attack": 45,
  "defense": 45,
  "height": 0.6,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564292e2cb1c07093682ea97"),
  "name": "Pidgey",
  "description": "Passarinho foda para karaleo",
  "type": "flying",
  "attack": 30,
  "defense": 30,
  "height": 0.3,
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564b77ca5ec9c44174cd0e17"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "moves": [
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("564d12585fff1457894bb17e"),
  "active": false,
  "name": "NaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564d0e7f5fff1457894bb17d"),
  "active": false,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564d357b5fff1457894bb17f"),
  "active": true,
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações",
  "moves": [
    null
  ]
}
{
  "_id": ObjectId("564d3b531f2c64c09f9129ed"),
  "active": false,
  "name": "Charmander",
  "attack": 666,
  "defense": 666,
  "height": 0.8,
  "description": "Bixo do capeta",
  "moves": [
    "investida",
    "rugido",
    "ataque rapido"
  ]
}
{
  "_id": ObjectId("564d3b631f2c64c09f9129ee"),
  "active": false,
  "name": "Bulbassauro",
  "attack": 90,
  "defense": 90,
  "height": 0.7,
  "description": "Squirtle o krlh",
  "moves": [
    "investida"
  ]
}
{
  "_id": ObjectId("564d3b741f2c64c09f9129ef"),
  "active": false,
  "name": "Squirtle",
  "attack": 80,
  "defense": 100,
  "height": 0.8,
  "description": "Tartaruga cospe água",
  "moves": [
    "investida",
    "rugido",
    "ataque rapido"
  ]
}
Fetched 12 record(s) in 13ms

## Pesquisar **todos** os pokemons que tenham o ataque 'investida' **e** tenham a defesa **não menor ou igual** a 49

MacBook-Pro-de-Victor(mongod-3.0.7) be-mean-pokemon> var query1 = {moves:{$all:['investida']}} 
MacBook-Pro-de-Victor(mongod-3.0.7) be-mean-pokemon> var query2 = {defense:{$not:{$lte:49}}}
MacBook-Pro-de-Victor(mongod-3.0.7) be-mean-pokemon> var query1 = {moves:{$in:['investida']}}
MacBook-Pro-de-Victor(mongod-3.0.7) be-mean-pokemon> var query = {$and:[query1, query2]}
MacBook-Pro-de-Victor(mongod-3.0.7) be-mean-pokemon> db.pokemons.find(query)
{
  "_id": ObjectId("564d3b531f2c64c09f9129ed"),
  "active": false,
  "name": "Charmander",
  "attack": 666,
  "defense": 666,
  "height": 0.8,
  "description": "Bixo do capeta",
  "moves": [
    "investida",
    "rugido",
    "ataque rapido"
  ]
}
{
  "_id": ObjectId("564d3b631f2c64c09f9129ee"),
  "active": false,
  "name": "Bulbassauro",
  "attack": 90,
  "defense": 90,
  "height": 0.7,
  "description": "Squirtle o krlh",
  "moves": [
    "investida"
  ]
}
{
  "_id": ObjectId("564d3b741f2c64c09f9129ef"),
  "active": false,
  "name": "Squirtle",
  "attack": 80,
  "defense": 100,
  "height": 0.8,
  "description": "Tartaruga cospe água",
  "moves": [
    "investida",
    "rugido",
    "ataque rapido"
  ]
}
{
  "_id": ObjectId("564d3bc61f2c64c09f9129f0"),
  "active": false,
  "name": "Pikachu",
  "attack": 100,
  "defense": 100,
  "height": 0.8,
  "description": "Ratinho elétrico fofinho",
  "type": "eletric",
  "moves": [
    "investida",
    "choque do trovão",
    "rugido",
    "ataque rapido"
  ]
}

## Remova **todos** os pokemons do tipo água e com attack menor que 50.

MacBook-Pro-de-Victor(mongod-3.0.7) be-mean-pokemon> var query = {$and:[{type:'água'},{attack:{$lt:50}}]}
MacBook-Pro-de-Victor(mongod-3.0.7) be-mean-pokemon> db.pokemons.remove(query)
Removed 0 record(s) in 3ms
WriteResult({
  "nRemoved": 0
})
MacBook-Pro-de-Victor(mongod-3.0.7) be-mean-pokemon> 