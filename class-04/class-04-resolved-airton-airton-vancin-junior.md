# MongoDB - Aula 04 - Exercício
autor: Airton Vancin Junior


## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
var query = {name: /Pikachu/i}
var mod = {$pushAll: {moves: ['esfera elétrica', 'investida trovão']}, $setOnInsert:{name: "Pikachu", description: "Sem maiores informações", type: null, attack: null, height: null} }
var options = {upsert: true}
db.pokemons.update(query, mod, options)

var query = {name: /Squirtle/i}
var mod = {$pushAll: {moves: ['esfera elétrica', 'investida trovão']}, $setOnInsert:{name: "Squirtle", description: "Sem maiores informações", type: null, attack: null, height: null} }
var options = {upsert: true}
db.pokemons.update(query, mod, options)

var query = {name: /Bulbassauro/i}
var mod = {$pushAll: {moves: ['esfera elétrica', 'investida trovão']}, $setOnInsert:{name: "Bulbassauro", description: "Sem maiores informações", type: null, attack: null, height: null} }
var options = {upsert: true}
db.pokemons.update(query, mod, options)

var query = {name: /Charmander/i}
var mod = {$pushAll: {moves: ['esfera elétrica', 'investida trovão']}, $setOnInsert:{name: "Charmander", description: "Sem maiores informações", type: null, attack: null, height: null} }
var options = {upsert: true}
db.pokemons.update(query, mod, options)

```


## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

```
linux(mongod-2.6.10) be-mean-pokemons> var query = {}
linux(mongod-2.6.10) be-mean-pokemons> var mod = {$push: {moves: 'desvio'}}
linux(mongod-2.6.10) be-mean-pokemons> var options = {multi: true}
linux(mongod-2.6.10) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 9 existing record(s) in 3ms
WriteResult({
  "nMatched": 9,
  "nUpserted": 0,
  "nModified": 9
})
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

```
linux(mongod-2.6.10) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}
linux(mongod-2.6.10) be-mean-pokemons> var mod = {$setOnInsert:{name: "Pikachu", description: "Sem maiores informações", type: null, attack: null, height: null} }
linux(mongod-2.6.10) be-mean-pokemons> var options = {upsert: true}
linux(mongod-2.6.10) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 7ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("56510c1fe1741eb3a5f76ce4")
})

```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

```
linux(mongod-2.6.10) be-mean-pokemons> var query = {moves: {$in: [/investida trovão/i, /desvio/i]}}
linux(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643fbcdcba869323ecad2a4"),
  "name": "Arbok",
  "description": "Este Pokémon é terrivelmente forte, a fim de contrair coisas com seu corpo",
  "type": "Poison",
  "attack": 65,
  "height": 3.5,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5643fc5bcba869323ecad2a5"),
  "name": "Raicu",
  "description": "Raichu plantas a cauda no chão e descargas",
  "type": "Electric",
  "attack": 55,
  "height": 0.8,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5643fd05cba869323ecad2a6"),
  "name": "Zigzagoon",
  "description": "Inquieto vagueia em todos os lugares em todos os momentos",
  "type": "Normal",
  "attack": 45,
  "height": 0.4,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5643fd57cba869323ecad2a7"),
  "name": "Wurmple",
  "description": "Descasca a casca das árvores e se alimenta de seiva que escorre para fora",
  "type": "Bug",
  "attack": 35,
  "height": 0.3,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5643fdaccba869323ecad2a8"),
  "name": "Blastoise",
  "description": "Blastoise tem bicas de água que se projetam de sua concha. Os bicos de água são muito precisos. Eles podem disparar balas de água com precisão suficiente para atacar latas vazias de uma distância de mais de 160 pés.",
  "type": "Water",
  "attack": 75,
  "height": 1.6,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("565105b7e1741eb3a5f76cdd"),
  "moves": [
    "esfera elétrica",
    "investida trovão",
    "desvio"
  ],
  "name": "Pikachu",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null
}
{
  "_id": ObjectId("565107abe1741eb3a5f76ce1"),
  "moves": [
    "esfera elétrica",
    "investida trovão",
    "desvio"
  ],
  "name": "Squirtle",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null
}
{
  "_id": ObjectId("565107b0e1741eb3a5f76ce2"),
  "moves": [
    "esfera elétrica",
    "investida trovão",
    "desvio"
  ],
  "name": "Bulbassauro",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null
}
{
  "_id": ObjectId("565107b5e1741eb3a5f76ce3"),
  "moves": [
    "esfera elétrica",
    "investida trovão",
    "desvio"
  ],
  "name": "Charmander",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null
}
Fetched 9 record(s) in 6ms

```


## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

```
linux(mongod-2.6.10) be-mean-pokemons> var query = {moves: {$all: [/investida trovão/i, /esfera elétrica/i]}}
linux(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("565105b7e1741eb3a5f76cdd"),
  "moves": [
    "esfera elétrica",
    "investida trovão",
    "desvio"
  ],
  "name": "Pikachu",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null
}
{
  "_id": ObjectId("565107abe1741eb3a5f76ce1"),
  "moves": [
    "esfera elétrica",
    "investida trovão",
    "desvio"
  ],
  "name": "Squirtle",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null
}
{
  "_id": ObjectId("565107b0e1741eb3a5f76ce2"),
  "moves": [
    "esfera elétrica",
    "investida trovão",
    "desvio"
  ],
  "name": "Bulbassauro",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null
}
{
  "_id": ObjectId("565107b5e1741eb3a5f76ce3"),
  "moves": [
    "esfera elétrica",
    "investida trovão",
    "desvio"
  ],
  "name": "Charmander",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null
}
Fetched 4 record(s) in 3ms

```


## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

```
linux(mongod-2.6.10) be-mean-pokemons> var query = {type: {$not: /electric/i}}
linux(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643fbcdcba869323ecad2a4"),
  "name": "Arbok",
  "description": "Este Pokémon é terrivelmente forte, a fim de contrair coisas com seu corpo",
  "type": "Poison",
  "attack": 65,
  "height": 3.5,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5643fd05cba869323ecad2a6"),
  "name": "Zigzagoon",
  "description": "Inquieto vagueia em todos os lugares em todos os momentos",
  "type": "Normal",
  "attack": 45,
  "height": 0.4,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5643fd57cba869323ecad2a7"),
  "name": "Wurmple",
  "description": "Descasca a casca das árvores e se alimenta de seiva que escorre para fora",
  "type": "Bug",
  "attack": 35,
  "height": 0.3,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5643fdaccba869323ecad2a8"),
  "name": "Blastoise",
  "description": "Blastoise tem bicas de água que se projetam de sua concha. Os bicos de água são muito precisos. Eles podem disparar balas de água com precisão suficiente para atacar latas vazias de uma distância de mais de 160 pés.",
  "type": "Water",
  "attack": 75,
  "height": 1.6,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("565105b7e1741eb3a5f76cdd"),
  "moves": [
    "esfera elétrica",
    "investida trovão",
    "desvio"
  ],
  "name": "Pikachu",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null
}
{
  "_id": ObjectId("565107abe1741eb3a5f76ce1"),
  "moves": [
    "esfera elétrica",
    "investida trovão",
    "desvio"
  ],
  "name": "Squirtle",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null
}
{
  "_id": ObjectId("565107b0e1741eb3a5f76ce2"),
  "moves": [
    "esfera elétrica",
    "investida trovão",
    "desvio"
  ],
  "name": "Bulbassauro",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null
}
{
  "_id": ObjectId("565107b5e1741eb3a5f76ce3"),
  "moves": [
    "esfera elétrica",
    "investida trovão",
    "desvio"
  ],
  "name": "Charmander",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null
}
{
  "_id": ObjectId("56510c1fe1741eb3a5f76ce4"),
  "name": "Pikachu",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null
}
Fetched 9 record(s) in 7ms
```


## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

```
linux(mongod-2.6.10) be-mean-pokemons> var query = {$and: [ {moves: {$in: [/investida/i]}}, {attack: {$not: {$lte: 49}}} ]}
    linux(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("565105b7e1741eb3a5f76cdd"),
  "moves": [
    "esfera elétrica",
    "investida trovão",
    "desvio"
  ],
  "name": "Pikachu",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null
}
{
  "_id": ObjectId("565107abe1741eb3a5f76ce1"),
  "moves": [
    "esfera elétrica",
    "investida trovão",
    "desvio"
  ],
  "name": "Squirtle",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null
}
{
  "_id": ObjectId("565107b0e1741eb3a5f76ce2"),
  "moves": [
    "esfera elétrica",
    "investida trovão",
    "desvio"
  ],
  "name": "Bulbassauro",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null
}
{
  "_id": ObjectId("565107b5e1741eb3a5f76ce3"),
  "moves": [
    "esfera elétrica",
    "investida trovão",
    "desvio"
  ],
  "name": "Charmander",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null
}
Fetched 4 record(s) in 7ms

```


## Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
linux(mongod-2.6.10) be-mean-pokemons> var query = {$and: [{type: /water/i}, {attack: {$lt: 50}} ]}
linux(mongod-2.6.10) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 2ms
WriteResult({
  "nRemoved": 1
})
```