# MongoDB - Aula 04 - Exercício
autor: **Alex Morgado Pereira**

1. Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
2. Adicionar 1 movimento em todos os pokemons: 'desvio'
3. Adicionar o pokemons 'AindaNãoExisteMon' caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações"
4. Pesquisar todos os pokemons que possuam o ataque 'investida' e mais um que você adicionou, escolha seu pokemon favorito.
5. Pesquisar todos os pokemons que possuam ataques que você adicionou, escolha seu pokemon favorito.
6. Pesquisar todos que não são do tipo 'elétrico'
7. Pesquisar todos pokemons que tenham ataque 'investida' e tenham a defesa não menor ou igual a 49
8. Remova todos os pokemons do tipo água e com attack menor que 50.

##Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
var query = {
$or:[
{name: /Pikachu/i},
{name: /Squirtle/i},
{name: /Bulbassauro/i},
{name: /Charmander/i}
]
}

var mod = {$set:{
moves:['Agilidade','Atacar']
}}

var options = {multi: true}

db.pokemons.update(query, mod, options)

Updated 3 existing record(s) in 8ms
WriteResult({
"nMatched": 3,
"nUpserted": 0,
"nModified": 3
})
```
##Adicionar 1 movimento em todos os pokemons: 'desvio'
```
var query = {}

var mod = {$push:{
moves:"desvio"
}}

var options = {multi: true}

db.pokemons.update(query, mod, options)

Updated 12 existing record(s) in 1ms
WriteResult({
"nMatched": 12,
"nUpserted": 0,
"nModified": 12
})
```
##Adicionar o pokemons 'AindaNãoExisteMon' caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações"
```
var query = {name: /AindaNãoExisteMon/i}

var mod = {
$set: {
name: "AindaNãoExisteMon",
},
$setOnInsert: {
atack: null,
defense: null,
height: null,
description: "Sem maiores informações",
}
}

var opt = {upsert: true}
db.pokemons.update(query, mod, opt)

Updated 1 new record(s) in 9ms
WriteResult({
"nMatched": 0,
"nUpserted": 1,
"nModified": 0,
"_id": ObjectId("57c23bac60b7cb5a626cc666")
})

db.pokemons.find(query)
{
  "_id": ObjectId("57c23bac60b7cb5a626cc666"),
  "name": "AindaNãoExisteMon",
  "atack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 1 record(s) in 6ms

```
##Pesquisar todos os pokemons que possuam o ataque 'investida' e mais um que você adicionou, escolha seu pokemon favorito.
```
var query = { $or : [ { moves : 'investida' } , { name : /squirtle/i } ] }
db.pokemons.find(query)
{
  "_id": ObjectId("57acae523368e1cdf5510837"),
  "name": "Pikachu",
  "descricao": "Rato elétrico bem fofinho",
  "tipo": "eletric",
  "ataque": "55",
  "height": "0.4",
  "moves": [
  "Agilidade",
  "Atacar",
  "desvio",
  "desvio",
  "investida"
  ]
}
{
  "_id": ObjectId("57bcc908f2973de1aff68642"),
  "name": "squirtle",
  "descricao": "é um Pokémon tipo água. Ele evolui para Wartortle quando chega no nivel 16 e depois para Blastoise quando chega no nivel 36.",
  "tipo": "água",
  "height": 0.5,
  "ataque": "85",
  "moves": [
  "Agilidade",
  "Atacar",
  "desvio",
  "desvio"
  ]
}
Fetched 2 record(s) in 3ms
```

##Pesquisar todos os pokemons que possuam ataques que você adicionou, escolha seu pokemon favorito.
```
var query = {moves: {$in: ["Ataque de Bolhas", "Agilidade"]}} 
db.pokemons.find(query)
{
  "_id": ObjectId("57acae523368e1cdf5510837"),
  "name": "Pikachu",
  "descricao": "Rato elétrico bem fofinho",
  "tipo": "eletric",
  "ataque": "55",
  "height": "0.4",
  "moves": [
  "Agilidade",
  "Atacar",
  "desvio",
  "desvio",
  "investida"
  ]
}
{
  "_id": ObjectId("57bcc908f2973de1aff68642"),
  "name": "squirtle",
  "descricao": "é um Pokémon tipo água. Ele evolui para Wartortle quando chega no nivel 16 e depois para Blastoise quando chega no nivel 36.",
  "tipo": "água",
  "height": 0.5,
  "ataque": "85",
  "moves": [
  "Agilidade",
  "Atacar",
  "desvio",
  "desvio"
  ]
}
{
  "_id": ObjectId("57bcc9fcf2973de1aff68643"),
  "name": "Charmander",
  "descricao": "Charmander é um Pokémon tipo fogo introduzido na Geração 1. É conhecido como o lagarto Pokémon.",
  "tipo": "Fogo",
  "height": 0.6,
  "ataque": "52",
  "moves": [
  "Agilidade",
  "Atacar",
  "desvio",
  "desvio"
  ]
}
{
  "_id": ObjectId("57a550301f8da2cc48912f28"),
  "name": "Goodra",
  "tipo": "Dragão",
  "hp": 90,
  "ataque": 100,
  "defesa": 70,
  "ataqueEspecial": 110,
  "defesaEspecial": 150,
  "velocidade": 80,
  "total": 600,
  "height": 0.6,
  "moves": [
  "desvio",
  "Ataque de Bolhas"
  ]
}
Fetched 4 record(s) in 1ms
```
##Pesquisar todos que não são do tipo 'elétrico'
var query = { moves : { $ne : 'elétrico'} }
db.pokemons.find(query)
```
{
  "_id": ObjectId("57a550c61f8da2cc48912f2a"),
  "name": "Garchomp",
  "tipo": "Dragão/Terra",
  "hp": 108,
  "ataque": 170,
  "defesa": 115,
  "ataqueEspecial": 120,
  "defesaEspecial": 95,
  "velocidade": 92,
  "total": 700,
  "descricao": "Ele voa com uma velocidade igual a de um jato. Ele nunca permite que sua presa escape.",
  "height": 0.2,
  "moves": [
  "desvio"
  ]
}
{
  "_id": ObjectId("57b1f393735cbdd1bce7a0ee"),
  "descricao": "pokemon de teste",
  "name": "Testemon",
  "ataque": 8100,
  "defesa": 8000,
  "height": 2.1,
  "moves": [
  "desvio"
  ]
}
{
  "_id": ObjectId("57bcc908f2973de1aff68642"),
  "name": "squirtle",
  "descricao": "é um Pokémon tipo água. Ele evolui para Wartortle quando chega no nivel 16 e depois para Blastoise quando chega no nivel 36.",
  "tipo": "água",
  "height": 0.5,
  "ataque": "85",
  "moves": [
  "Agilidade",
  "Atacar",
  "desvio",
  "desvio"
  ]
}
{
  "_id": ObjectId("57bcca7df2973de1aff68644"),
  "name": "Bulbasaur",
  "descricao": "Bulbasaur é um Pokémon do tipo Grama / veneno introduzido na Geração 1. É conhecida como a Semente Pokémon.",
  "tipo": [
  "grama",
  "veneno"
  ],
  "height": 0.4,
  "ataque": "49",
  "moves": [
  "desvio"
  ]
}
{
  "_id": ObjectId("57bcc9fcf2973de1aff68643"),
  "name": "Charmander",
  "descricao": "Charmander é um Pokémon tipo fogo introduzido na Geração 1. É conhecido como o lagarto Pokémon.",
  "tipo": "Fogo",
  "height": 0.6,
  "ataque": "52",
  "moves": [
  "Agilidade",
  "Atacar",
  "desvio",
  "desvio"
  ]
}
{
  "_id": ObjectId("57a54fee1f8da2cc48912f27"),
  "name": "Archeops",
  "tipo": "Rocha / Voador",
  "hp": 75,
  "ataque": 140,
  "defesa": 65,
  "ataqueEspecial": 112,
  "defesaEspecial": 65,
  "velocidade": 110,
  "total": 567,
  "height": 0.3,
  "moves": [
  "desvio"
  ]
}
{
  "_id": ObjectId("57a550301f8da2cc48912f28"),
  "name": "Goodra",
  "tipo": "Dragão",
  "hp": 90,
  "ataque": 100,
  "defesa": 70,
  "ataqueEspecial": 110,
  "defesaEspecial": 150,
  "velocidade": 80,
  "total": 600,
  "height": 0.6,
  "moves": [
  "desvio",
  "Ataque de Bolhas"
  ]
}
{
  "_id": ObjectId("57a550771f8da2cc48912f29"),
  "name": "Hydreigon",
  "tipo": "Noturno/Dragão",
  "hp": 92,
  "ataque": 105,
  "defesa": 90,
  "ataqueEspecial": 125,
  "defesaEspecial": 90,
  "velocidade": 98,
  "total": 600,
  "height": 1,
  "moves": [
  "desvio"
  ]
}
{
  "_id": ObjectId("57aca7da2db883de63fc4720"),
  "name": "Venusaur",
  "tipo": "grama",
  "hp": 78,
  "ataque": 90,
  "defesa": 90,
  "ataqueEspecial": 100,
  "defesaEspecial": 90,
  "velocidade": 90,
  "height": 0.5,
  "total": 450,
  "moves": [
  "desvio"
  ]
}
{
  "_id": ObjectId("57aca7e72db883de63fc4721"),
  "name": "Venusaur",
  "tipo": "grama",
  "hp": 78,
  "ataque": 90,
  "defesa": 90,
  "ataqueEspecial": 100,
  "defesaEspecial": 90,
  "velocidade": 90,
  "height": 2,
  "total": 450,
  "moves": [
  "desvio"
  ]
}
{
  "_id": ObjectId("57c23bac60b7cb5a626cc666"),
  "name": "AindaNãoExisteMon",
  "atack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 12 record(s) in 5ms
```
##Pesquisar todos pokemons que tenham ataque 'investida' e tenham a defesa não menor ou igual a 49
```
var query = { $and: [ { moves: 'investida' }, { defense: { $lte: 49 } } ] }
db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```

##Remova todos os pokemons do tipo água e com attack menor que 50.
var query = {
$and: [
{tipo: 'água'},
{ataque: {$lt: 49}}
]
}
db.pokemons.remove(query)
Removed 0 record(s) in 8ms
WriteResult({
"nRemoved": 0
})