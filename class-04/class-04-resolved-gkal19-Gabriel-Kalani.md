# MongoDB - Aula 04 - Exercício  
Autor: Gabriel Kalani

1 - Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro, Charmander


```json  
  be-mean-pokemons> var query = {$or: [{name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbassauro/i}, {name: /charmander/i}]}  
  be-mean-pokemons> var mod = {$set: {moves: ['Sabe programar em JS', 'investida']}}  
  be-mean-pokemons> var options = {multi: true}  
  be-mean-pokemons> db.pokemons.update(query, mod, options)
  Updated 0 record(s) in 23ms
  WriteResult({
    "nMatched": 0,
    "nUpserted": 0,
    "nModified": 0
})
```


2- Adicionar 1 movimento em todos os pokemons: 'desvio'

```json  
  be-mean-pokemons> var query = {}  
  be-mean-pokemons> var mod = { $push: { moves: "desvio"}} 
  be-mean-pokemons> var options = { multi: true } 
  be-mean-pokemons> db.pokemons.update(query, mod, options)
  Updated 0 record(s) in 1ms
  WriteResult({
    "nMatched": 0,
    "nUpserted": 0,
    "nModified": 0
})
```


3- Adicionar o pokemon 'AindaNaoExisteMon' caso ele não exista com todos os dados com o valor 'null' e a descrição 'Sem maiores informações'


```json  
  be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}  
  be-mean-pokemons> var mod = {$setOnInsert: {name: 'AindaNaoExisteMom', attack: null, height: null, defense: null, moves: [], description: 'Sem maiores informações'}}  
  be-mean-pokemons> var options = {upsert: true}  
  be-mean-pokemons> db.pokemons.update(query, mod, options) 
  Updated 1 new record(s) in 2ms
  WriteResult({
    "nMatched": 0,
    "nUpserted": 1,
    "nModified": 0,
    "_id": ObjectId("56a95b568ba44e85fe2da0c3")
})
  be-mean-pokemons> var query = {"_id": ObjectId("56a95b568ba44e85fe2da0c3")}  
  be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56a95b568ba44e85fe2da0c3"),
  "name": "AindaNaoExisteMom",
  "attack": null,
  "height": null,
  "defense": null,
  "moves": [ ],
  "description": "Sem maiores informações"
}
Fetched 1 record(s) in 1ms 
```


4 - Pesquisar todos o pokemons que possuam o ataque 'investida' e mais um que você adicionou, escolha seu pokemon favorito

```json
  be-mean-pokemons> var query = {moves: {$in: ['investida', 'Sabe programar em JS']}}  
  be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56a90674529091c469c87fec"),
  "name": "Pikachu",
  "description": "Um hamster/rato bem fofo e foda",
  "type": "raio",
  "attack": 58,
  "height": 0.9,
  "moves": [
    "Sabe programar em JS",
    "Respira de baixo da água",
    "desvio"
  ]
}
{
  "_id": ObjectId("56a907fd529091c469c87fef"),
  "name": "Suissa",
  "description": "Esse pokemon tem ideias fodas \"bagarai\" que vão trazer muito dinheiro e acabar com o capitalismo",
  "type": "fodao",
  "attack": 100,
  "height": 2,
  "moves": [
    "Espanca o CoffeScript",
    "Faz nego hater chorar",
    "desvio",
    "investida"
  ]
}
  Fetched 12 record(s) in 6ms 
```


5 - Pesquisar 'todos' o pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito

```json  
  be-mean-pokemons> var query = {moves: {$in: ['investida', 'Sabe programar em JS', 'desvio', 'Respira de baixo da água']}}
  be-mean-pokemons> db.pokemons.find(query)
  {
    "_id": ObjectId("56a907fd529091c469c87fef"),
    "name": "Suissa",
    "description": "Esse pokemon tem ideias fodas \"bagarai\" que vão trazer muito dinheiro e acabar com o capitalismo",
    "type": "fodao",
    "attack": 100,
    "height": 2,
    "moves": [
      "Espanca o CoffeScript",
      "Faz nego hater chorar",
      "desvio",
      "investida"
    ]
  }
  Fetched 1 record(s) in 1ms
  gkal19-aula-bemean-2468380(mongod-2.6.11) be-mean-pokemons> db.pokemons.find()
  {
    "_id": ObjectId("56a90483529091c469c87feb"),
    "name": "Metagross",
    "description": "Esse cara é tão esperto quanto o mizeravi",
    "type": "esperto",
    "attack": 135,
    "defense": 130,
    "height": 1.6,
    "moves": [
      "desvio"
    ]
  }
  {
    "_id": ObjectId("56a90674529091c469c87fec"),
    "name": "Pikachu",
    "description": "Um hamster/rato bem fofo e foda",
    "type": "raio",
    "attack": 58,
    "height": 0.9,
    "moves": [
      "Sabe programar em JS",
      "Respira de baixo da água",
      "desvio"
    ]
  }
  {
    "_id": ObjectId("56a906fe529091c469c87fed"),
    "name": "Mewtwo",
    "description": "Uma \"cobaia de laboratório\" hahah ",
    "type": "fdp",
    "attack": 78,
    "height": 1,
    "moves": [
      "desvio"
    ]
  }
  {
    "_id": ObjectId("56a907dd529091c469c87fee"),
    "description": "Pokémon preguiçoso que nem treina",
    "name": "Fracomon",
    "attack": 20,
    "defense": 20,
    "moves": [
      "desvio"
    ]
  }
  {
    "_id": ObjectId("56a941ba69035bd75828d284"),
    "name": "Kakaroto",
    "description": "Esse pokémon tem um ataque e defesa com um número mais de 8000",
    "attack": 8000,
    "defense": 8000,
    "height": 2.1,
    "moves": [
      "desvio"
    ]
  }
  {
    "_id": ObjectId("56a9425769035bd75828d285"),
    "name": "Kakaroto",
    "attack": 8000,
    "defense": 8000,
    "height": 2.1,
    "description": "Esse pokémon tem um ataque e defesa com um número mais de 8000",
    "moves": [
      "desvio"
    ]
  }
  {
    "_id": ObjectId("56a94450c98b6e230c03bdce"),
    "name": "Muk",
    "description": "Esse cara cospe em você um ácido que te deixa malucão",
    "type": "crackudo",
    "attack": 135,
    "defense": 130,
    "height": 1.2,
    "moves": [
      "desvio"
    ]
  }
  {
    "_id": ObjectId("56a907fd529091c469c87fef"),
    "name": "Suissa",
    "description": "Esse pokemon tem ideias fodas \"bagarai\" que vão trazer muito dinheiro e acabar com o capitalismo",
    "type": "fodao",
    "attack": 100,
    "height": 2,
    "moves": [
      "Espanca o CoffeScript",
      "Faz nego hater chorar",
      "desvio",
      "investida"
    ]
  }
  {
    "_id": ObjectId("56a959bec98b6e230c03bdd0"),
    "name": "Bulbasauro",
    "description": "Bulbasauro, assim como Pikachu decide não evoluir por vontade própria.",
    "attack": 300,
    "defense": 200,
    "height": 0.7,
    "moves": [
      "desvio"
    ]
  }
  {
    "_id": ObjectId("56a908fc529091c469c87ff0"),
    "name": "Charmander",
    "description": "Pra quem procura fazer um churrasco no final de semana, o Charmander é uma boa opção",
    "type": "fogo",
    "attack": 46,
    "height": 0.9,
    "moves": [
      "Sabe programar em JS",
      "Respira de baixo da água",
      "desvio"
    ]
  }
  {
    "_id": ObjectId("56a959abc98b6e230c03bdcf"),
    "name": "Squirtle",
    "description": "Quando um Squirtle nasce, sua primeira ação é entrar no casco.",
    "attack": 300,
    "defense": 200,
    "height": 0.7,
    "moves": [
      "Sabe programar em JS",
      "Respira de baixo da água",
      "desvio"
    ]
  }
  {
    "_id": ObjectId("56a95b568ba44e85fe2da0c3"),
    "name": "AindaNaoExisteMom",
    "attack": null,
    "height": null,
    "defense": null,
    "moves": [ ],
    "description": "Sem maiores informações"
  }
  Fetched 12 record(s) in 5ms
  gkal19-aula-bemean-2468380(mongod-2.6.11) be-mean-pokemons> var query = {moves: {$in: ['investida', 'Choque do Trovão', 'desvio', 'Sabe programar em JS', 'Respira de baixo da água']}}
  gkal19-aula-bemean-2468380(mongod-2.6.11) be-mean-pokemons> db.pokemons.find(query)
  {
    "_id": ObjectId("56a90483529091c469c87feb"),
    "name": "Metagross",
    "description": "Esse cara é tão esperto quanto o mizeravi",
    "type": "esperto",
    "attack": 135,
    "defense": 130,
    "height": 1.6,
    "moves": [
      "desvio"
    ]
  }
  {
    "_id": ObjectId("56a90674529091c469c87fec"),
    "name": "Pikachu",
    "description": "Um hamster/rato bem fofo e foda",
    "type": "raio",
    "attack": 58,
    "height": 0.9,
    "moves": [
      "Sabe programar em JS",
      "Respira de baixo da água",
      "desvio"
    ]
  }
  {
    "_id": ObjectId("56a906fe529091c469c87fed"),
    "name": "Mewtwo",
    "description": "Uma \"cobaia de laboratório\" hahah ",
    "type": "fdp",
    "attack": 78,
    "height": 1,
    "moves": [
      "desvio"
    ]
  }
  {
    "_id": ObjectId("56a907dd529091c469c87fee"),
    "description": "Pokémon preguiçoso que nem treina",
    "name": "Fracomon",
    "attack": 20,
    "defense": 20,
    "moves": [
      "desvio"
    ]
  }
  {
    "_id": ObjectId("56a941ba69035bd75828d284"),
    "name": "Kakaroto",
    "description": "Esse pokémon tem um ataque e defesa com um número mais de 8000",
    "attack": 8000,
    "defense": 8000,
    "height": 2.1,
    "moves": [
      "desvio"
    ]
  }
  {
    "_id": ObjectId("56a9425769035bd75828d285"),
    "name": "Kakaroto",
    "attack": 8000,
    "defense": 8000,
    "height": 2.1,
    "description": "Esse pokémon tem um ataque e defesa com um número mais de 8000",
    "moves": [
      "desvio"
    ]
  }
  {
    "_id": ObjectId("56a94450c98b6e230c03bdce"),
    "name": "Muk",
    "description": "Esse cara cospe em você um ácido que te deixa malucão",
    "type": "crackudo",
    "attack": 135,
    "defense": 130,
    "height": 1.2,
    "moves": [
      "desvio"
    ]
  }
  {
    "_id": ObjectId("56a907fd529091c469c87fef"),
    "name": "Suissa",
    "description": "Esse pokemon tem ideias fodas \"bagarai\" que vão trazer muito dinheiro e acabar com o capitalismo",
    "type": "fodao",
    "attack": 100,
    "height": 2,
    "moves": [
      "Espanca o CoffeScript",
      "Faz nego hater chorar",
      "desvio",
      "investida"
    ]
  }
  {
    "_id": ObjectId("56a959bec98b6e230c03bdd0"),
    "name": "Bulbasauro",
    "description": "Bulbasauro, assim como Pikachu decide não evoluir por vontade própria.",
    "attack": 300,
    "defense": 200,
    "height": 0.7,
    "moves": [
      "desvio"
    ]
  }
  {
    "_id": ObjectId("56a908fc529091c469c87ff0"),
    "name": "Charmander",
    "description": "Pra quem procura fazer um churrasco no final de semana, o Charmander é uma boa opção",
    "type": "fogo",
    "attack": 46,
    "height": 0.9,
    "moves": [
      "Sabe programar em JS",
      "Respira de baixo da água",
      "desvio"
    ]
  }
  {
    "_id": ObjectId("56a959abc98b6e230c03bdcf"),
    "name": "Squirtle",
    "description": "Quando um Squirtle nasce, sua primeira ação é entrar no casco.",
    "attack": 300,
    "defense": 200,
    "height": 0.7,
    "moves": [
      "Sabe programar em JS",
      "Respira de baixo da água",
      "desvio"
    ]
  }
  Fetched 11 record(s) in 172ms  
```


6 - Pesquisar todos os pokemons que não são do tipo `elétrico`

```json
  be-mean-pokemons> var query = {type: {$ne: 'elétrico'}}  
  be-mean-pokemons> db.pokemons.find(query)  
  {
    "_id": ObjectId("56a90483529091c469c87feb"),
    "name": "Metagross",
    "description": "Esse cara é tão esperto quanto o mizeravi",
    "type": "esperto",
    "attack": 135,
    "defense": 130,
    "height": 1.6,
    "moves": [
      "desvio"
    ]
  }
  {
    "_id": ObjectId("56a90674529091c469c87fec"),
    "name": "Pikachu",
    "description": "Um hamster/rato bem fofo e foda",
    "type": "raio",
    "attack": 58,
    "height": 0.9,
    "moves": [
      "Sabe programar em JS",
      "Respira de baixo da água",
      "desvio"
    ]
  }
  {
    "_id": ObjectId("56a906fe529091c469c87fed"),
    "name": "Mewtwo",
    "description": "Uma \"cobaia de laboratório\" hahah ",
    "type": "fdp",
    "attack": 78,
    "height": 1,
    "moves": [
      "desvio"
    ]
  }
  {
    "_id": ObjectId("56a907dd529091c469c87fee"),
    "description": "Pokémon preguiçoso que nem treina",
    "name": "Fracomon",
    "attack": 20,
    "defense": 20,
    "moves": [
      "desvio"
    ]
  }
  {
    "_id": ObjectId("56a941ba69035bd75828d284"),
    "name": "Kakaroto",
    "description": "Esse pokémon tem um ataque e defesa com um número mais de 8000",
    "attack": 8000,
    "defense": 8000,
    "height": 2.1,
    "moves": [
      "desvio"
    ]
  }
  {
    "_id": ObjectId("56a9425769035bd75828d285"),
    "name": "Kakaroto",
    "attack": 8000,
    "defense": 8000,
    "height": 2.1,
    "description": "Esse pokémon tem um ataque e defesa com um número mais de 8000",
    "moves": [
      "desvio"
    ]
  }
  {
    "_id": ObjectId("56a94450c98b6e230c03bdce"),
    "name": "Muk",
    "description": "Esse cara cospe em você um ácido que te deixa malucão",
    "type": "crackudo",
    "attack": 135,
    "defense": 130,
    "height": 1.2,
    "moves": [
      "desvio"
    ]
  }
  {
    "_id": ObjectId("56a907fd529091c469c87fef"),
    "name": "Suissa",
    "description": "Esse pokemon tem ideias fodas \"bagarai\" que vão trazer muito dinheiro e acabar com o capitalismo",
    "type": "fodao",
    "attack": 100,
    "height": 2,
    "moves": [
      "Espanca o CoffeScript",
      "Faz nego hater chorar",
      "desvio",
      "investida"
    ]
  }
  {
    "_id": ObjectId("56a959bec98b6e230c03bdd0"),
    "name": "Bulbasauro",
    "description": "Bulbasauro, assim como Pikachu decide não evoluir por vontade própria.",
    "attack": 300,
    "defense": 200,
    "height": 0.7,
    "moves": [
      "desvio"
    ]
  }
  {
    "_id": ObjectId("56a908fc529091c469c87ff0"),
    "name": "Charmander",
    "description": "Pra quem procura fazer um churrasco no final de semana, o Charmander é uma boa opção",
    "type": "fogo",
    "attack": 46,
    "height": 0.9,
    "moves": [
      "Sabe programar em JS",
      "Respira de baixo da água",
      "desvio"
    ]
  }
  {
    "_id": ObjectId("56a959abc98b6e230c03bdcf"),
    "name": "Squirtle",
    "description": "Quando um Squirtle nasce, sua primeira ação é entrar no casco.",
    "attack": 300,
    "defense": 200,
    "height": 0.7,
    "moves": [
      "Sabe programar em JS",
      "Respira de baixo da água",
      "desvio"
    ]
  }
  {
    "_id": ObjectId("56a95b568ba44e85fe2da0c3"),
    "name": "AindaNaoExisteMom",
    "attack": null,
    "height": null,
    "defense": null,
    "moves": [ ],
    "description": "Sem maiores informações"
  }
  Fetched 12 record(s) in 179ms
```


7 - Pesquisar 'todos' pokemons que tenham o ataque 'investida' E tenham a defesa 'não menor ou igual' a 49


```json
  be-mean-pokemons> var query = {$and: [{moves: {$in: ['investida']}}, {defense: {$lte: 49}}]}  
  be-mean-pokemons> db.pokemons.find(query)
  Fetched 0 record(s) in 0ms  
```

8 - Remova 'todos' os pokemons do tipo água E com attack menor que 50

```json
  be-mean-pokemons> var query = { $and:[ { type: "água" }, { attack: { $lt: 50 }} ]}; 
  be-mean-pokemons> be-mean-pokemons> db.pokemons.remove(query);
  Removed 0 record(s) in 8ms
  WriteResult({
    "nRemoved": 0
  })
  be-mean-pokemons> db.pokemons.remove(query)
  Removed 0 record(s) in 2ms
  WriteResult({
    "nRemoved": 0
  })
  be-mean-pokemons> db.pokemons.find(query)
  Fetched 0 record(s) in 0ms 
```
