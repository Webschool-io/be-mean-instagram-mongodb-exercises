# MongoDB - Aula 04 - Exercício
autor: Matheus Torres Pereira

## 1. Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbasauro e Charmander

```
ubuntu(mongod-3.2.12) be-mean-pokemons> var query = {name: {$in: ['Pikachu', 'Squirtle', 'Bulbasaur', 'Charmander']}}

ubuntu(mongod-3.2.12) be-mean-pokemons> var mod = {$pushAll:{attacks: ['investida', 'cabeçada']}}

ubuntu(mongod-3.2.12) be-mean-pokemons> mod
{
  "$pushAll": {
    "attacks": [
      "investida",
      "cabeçada"
    ]
  }
}


ubuntu(mongod-3.2.12) be-mean-pokemons> db.pokemons.update(query, mod, {multi:true})
Updated 4 existing record(s) in 4ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
va
ubuntu(mongod-3.2.12) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("58af1bee57d2d3ebfdb8a689"),
  "name": "Bulbasaur",
  "description": "Pokemon com uma planta nas costas",
  "attack": 49,
  "defense": 49,
  "height": 0.71,
  "type": "grama",
  "attacks": [
    "investida",
    "cabeçada"
  ]
}
{
  "_id": ObjectId("58af1bee57d2d3ebfdb8a68a"),
  "name": "Charmander",
  "description": "Pokemon com fogo no rabo",
  "attack": 52,
  "defense": 43,
  "height": 0.61,
  "type": "fogo",
  "attacks": [
    "investida",
    "cabeçada"
  ]
}
{
  "_id": ObjectId("58af1bee57d2d3ebfdb8a68b"),
  "name": "Squirtle",
  "description": "Tartaruga cuspidora de água",
  "attack": 48,
  "defense": 65,
  "height": 0.51,
  "type": "água",
  "attacks": [
    "investida",
    "cabeçada"
  ]
}
{
  "_id": ObjectId("58af1bee57d2d3ebfdb8a68d"),
  "name": "Pikachu",
  "description": "Pokemon rato amarelo que solta raio pela bochecha",
  "attack": 55,
  "defense": 40,
  "height": 0.41,
  "type": "raio",
  "attacks": [
    "investida",
    "cabeçada"
  ]
}
Fetched 4 record(s) in 3ms
```

## 2. Adicionar 1 movimento em todos os pokemons: 'desvio'

```
ubuntu(mongod-3.2.12) be-mean-pokemons> var mod = {$pushAll: {moves: ['desvio']}}
ubuntu(mongod-3.2.12) be-mean-pokemons> db.pokemons.update({}, mod, {multi:true})
Updated 5 existing record(s) in 2ms
WriteResult({
  "nMatched": 5,
  "nUpserted": 0,
  "nModified": 5
})
ubuntu(mongod-3.2.12) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("58af1bee57d2d3ebfdb8a689"),
  "name": "Bulbasaur",
  "description": "Pokemon com uma planta nas costas",
  "attack": 49,
  "defense": 49,
  "height": 0.71,
  "type": "grama",
  "attacks": [
    "investida",
    "cabeçada"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("58af1bee57d2d3ebfdb8a68a"),
  "name": "Charmander",
  "description": "Pokemon com fogo no rabo",
  "attack": 52,
  "defense": 43,
  "height": 0.61,
  "type": "fogo",
  "attacks": [
    "investida",
    "cabeçada"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("58af1bee57d2d3ebfdb8a68b"),
  "name": "Squirtle",
  "description": "Tartaruga cuspidora de água",
  "attack": 48,
  "defense": 65,
  "height": 0.51,
  "type": "água",
  "attacks": [
    "investida",
    "cabeçada"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("58af1bee57d2d3ebfdb8a68c"),
  "name": "Pidgey",
  "description": "Pokemon pomba",
  "attack": 45,
  "defense": 40,
  "height": 0.3,
  "type": "normal",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("58af1bee57d2d3ebfdb8a68d"),
  "name": "Pikachu",
  "description": "Pokemon rato amarelo que solta raio pela bochecha",
  "attack": 55,
  "defense": 40,
  "height": 0.41,
  "type": "raio",
  "attacks": [
    "investida",
    "cabeçada"
  ],
  "moves": [
    "desvio"
  ]
}
Fetched 5 record(s) in 3ms
```

## 3. Adicionar o pokemon 'AindaNaoExisteMon' caso ele não exista com todos os dados com o valor 'null' e a descrição: "Sem maiores informações"

```
ubuntu(mongod-3.2.12) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}
ubuntu(mongod-3.2.12) be-mean-pokemons> var mod = {$set : {name: 'AindaNaoExisteMon', attack: null, defense: null, height: null, description: 'Sem maiores informações'}}
ubuntu(mongod-3.2.12) be-mean-pokemons> db.pokemons.update(query, mod, {upsert: true} )
Updated 1 new record(s) in 5ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("58af3c7d1f8fab2f017c87b2")
})

ubuntu(mongod-3.2.12) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("58af3c7d1f8fab2f017c87b2"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 1 record(s) in 1ms

```

## 4. Pesquisar todos os pokemons que possuam o ataque 'investida' e mais um que você adicionou, escolha seu pokemon favorito

```
ubuntu(mongod-3.2.12) be-mean-pokemons> var query = {attacks: {$in : ['investida', 'furacao']}}
ubuntu(mongod-3.2.12) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("58af1bee57d2d3ebfdb8a689"),
  "name": "Bulbasaur",
  "description": "Pokemon com uma planta nas costas",
  "attack": 49,
  "defense": 49,
  "height": 0.71,
  "type": "grama",
  "attacks": [
    "investida",
    "cabeçada"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("58af1bee57d2d3ebfdb8a68a"),
  "name": "Charmander",
  "description": "Pokemon com fogo no rabo",
  "attack": 52,
  "defense": 43,
  "height": 0.61,
  "type": "fogo",
  "attacks": [
    "investida",
    "cabeçada"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("58af1bee57d2d3ebfdb8a68b"),
  "name": "Squirtle",
  "description": "Tartaruga cuspidora de água",
  "attack": 48,
  "defense": 65,
  "height": 0.51,
  "type": "água",
  "attacks": [
    "investida",
    "cabeçada"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("58af1bee57d2d3ebfdb8a68d"),
  "name": "Pikachu",
  "description": "Pokemon rato amarelo que solta raio pela bochecha",
  "attack": 55,
  "defense": 40,
  "height": 0.41,
  "type": "raio",
  "attacks": [
    "investida",
    "cabeçada"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("58af3d7ca75478d7122b6951"),
  "name": "Pidgey",
  "description": "Pokemon pomba",
  "attack": 45,
  "defense": 40,
  "height": 0.3,
  "attacks": [
    "furacao"
  ]
}
Fetched 5 record(s) in 4ms
```

## 5. Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito

```
ubuntu(mongod-3.2.12) be-mean-pokemons> var query = {attacks: {$in : ['furacao', 'investida', 'cabecada', 'choque do trovao', 'lança chamas']}}
ubuntu(mongod-3.2.12) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("58af1bee57d2d3ebfdb8a689"),
  "name": "Bulbasaur",
  "description": "Pokemon com uma planta nas costas",
  "attack": 49,
  "defense": 49,
  "height": 0.71,
  "type": "grama",
  "attacks": [
    "investida",
    "cabeçada"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("58af1bee57d2d3ebfdb8a68a"),
  "name": "Charmander",
  "description": "Pokemon com fogo no rabo",
  "attack": 52,
  "defense": 43,
  "height": 0.61,
  "type": "fogo",
  "attacks": [
    "investida",
    "cabeçada",
    "lança chamas"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("58af1bee57d2d3ebfdb8a68b"),
  "name": "Squirtle",
  "description": "Tartaruga cuspidora de água",
  "attack": 48,
  "defense": 65,
  "height": 0.51,
  "type": "água",
  "attacks": [
    "investida",
    "cabeçada"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("58af1bee57d2d3ebfdb8a68d"),
  "name": "Pikachu",
  "description": "Pokemon rato amarelo que solta raio pela bochecha",
  "attack": 55,
  "defense": 40,
  "height": 0.41,
  "type": "raio",
  "attacks": [
    "investida",
    "cabeçada",
    "choque do trovao"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("58af3d7ca75478d7122b6951"),
  "name": "Pidgey",
  "description": "Pokemon pomba",
  "attack": 45,
  "defense": 40,
  "height": 0.3,
  "attacks": [
    "furacao"
  ]
}
Fetched 5 record(s) in 4ms
```

## 6. Pesquisar todos os pokemons que não são do tipo 'raio'

```
ubuntu(mongod-3.2.12) be-mean-pokemons> db.pokemons.find({type: {$ne: 'raio'}})
{
  "_id": ObjectId("58af1bee57d2d3ebfdb8a689"),
  "name": "Bulbasaur",
  "description": "Pokemon com uma planta nas costas",
  "attack": 49,
  "defense": 49,
  "height": 0.71,
  "type": "grama",
  "attacks": [
    "investida",
    "cabeçada"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("58af1bee57d2d3ebfdb8a68a"),
  "name": "Charmander",
  "description": "Pokemon com fogo no rabo",
  "attack": 52,
  "defense": 43,
  "height": 0.61,
  "type": "fogo",
  "attacks": [
    "investida",
    "cabeçada",
    "lança chamas"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("58af1bee57d2d3ebfdb8a68b"),
  "name": "Squirtle",
  "description": "Tartaruga cuspidora de água",
  "attack": 48,
  "defense": 65,
  "height": 0.51,
  "type": "água",
  "attacks": [
    "investida",
    "cabeçada"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("58af3c7d1f8fab2f017c87b2"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
{
  "_id": ObjectId("58af3d7ca75478d7122b6951"),
  "name": "Pidgey",
  "description": "Pokemon pomba",
  "attack": 45,
  "defense": 40,
  "height": 0.3,
  "attacks": [
    "furacao"
  ]
}

```

## 7. Pesquisar todos os pokemons que tenham o ataque 'investida' e tenham defesa não menor ou igual a 49

```
ubuntu(mongod-3.2.12) be-mean-pokemons> db.pokemons.find({$and: [{attacks: 'investida'},{defense: {$gt:49}}]})
{
  "_id": ObjectId("58af1bee57d2d3ebfdb8a68b"),
  "name": "Squirtle",
  "description": "Tartaruga cuspidora de água",
  "attack": 48,
  "defense": 65,
  "height": 0.51,
  "type": "água",
  "attacks": [
    "investida",
    "cabeçada"
  ],
  "moves": [
    "desvio"
  ]
}
Fetched 1 record(s) in 2ms
```

## 8. Remova todos os pokemons do tipo água com attack menor que 50.

```
ubuntu(mongod-3.2.12) be-mean-pokemons> var query = {$and: [{type: 'água'}, {attack: {$lt:50}}]}
ubuntu(mongod-3.2.12) be-mean-pokemons> db.pokemons.remove(query, {multi:true})
Removed 1 record(s) in 2ms
WriteResult({
  "nRemoved": 1
})

```