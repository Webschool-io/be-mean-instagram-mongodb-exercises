# MongoDB - Aula 04 - Exercício
autor: João Paulo Effting

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
``` 
var query = {name: /pikachu/i}
var mod = {$pushAll:{moves:['Choque do trovão', 'investida']}}
db.pokemons.find(query)
{
  "_id": ObjectId("564b1db125337263280d04a7"),
  "attack": 55,
  "created": "2013-11-03T15:05:41.317235",
  "defense": 40,
  "height": "4",
  "hp": 35,
  "name": "Pikachu",
  "speed": 90,
  "types": [
    "electric"
  ],
  "moves": [
    "Choque do trovão",
    "investida"
  ]
}
Fetched 1 record(s) in 2ms


var query = {name: /squirtle/i}
var mod = {$pushAll:{moves:['Hidro bomba', 'investida']}}
db.pokemons.find(query)
{
  "_id": ObjectId("564b1db425337263280d04b6"),
  "attack": 48,
  "created": "2013-11-03T15:05:41.278310",
  "defense": 65,
  "height": "5",
  "hp": 44,
  "name": "Squirtle",
  "speed": 43,
  "types": [
    "water"
  ],
  "moves": [
    "Hidro bomba",
    "investida"
  ]
}
Fetched 1 record(s) in 2ms


var query = {name: /bulbasaur/i}
var mod = {$pushAll:{moves:['Folhas navalhas', 'investida']}}
db.pokemons.find(query)
{
  "_id": ObjectId("564b1de325337263280d068c"),
  "attack": 49,
  "created": "2013-11-03T15:05:41.260678",
  "defense": 49,
  "height": "7",
  "hp": 45,
  "name": "Bulbasaur",
  "speed": 45,
  "types": [
    "poison",
    "grass"
  ],
  "moves": [
    "Folhas navalhas",
    "investida"
  ]
}
Fetched 1 record(s) in 2ms


var query = {name: /charmander/i}
var mod = {$pushAll:{moves:['Lança chamas', 'investida']}}
db.pokemons.find(query)
{
  "_id": ObjectId("564b1dad25337263280d047a"),
  "attack": 52,
  "created": "2013-11-03T15:05:41.271082",
  "defense": 43,
  "height": "6",
  "hp": 39,
  "name": "Charmander",
  "speed": 65,
  "types": [
    "fire"
  ],
  "moves": [
    "Lança chamas",
    "investida"
  ]


```

## **Adicionar** 1 movimento em todos os pokémons : `desvio`##
```
var query = {}
var mod = {$pushAll:{moves:['Desvio']}}
var options = {multi:true}
db.pokemons.update(query,mod,options)
Updated 610 existing record(s) in 26ms
WriteResult({
  "nMatched": 610,
  "nUpserted": 0,
  "nModified": 610
})

db.pokemons.find().limit(5)
{
  "_id": ObjectId("564b1dad25337263280d0479"),
  "attack": 56,
  "created": "2013-11-03T15:05:41.305777",
  "defense": 35,
  "height": "3",
  "hp": 30,
  "name": "Rattata",
  "speed": 72,
  "types": [
    "normal"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d047b"),
  "attack": 64,
  "created": "2013-11-03T15:05:41.273462",
  "defense": 58,
  "height": "11",
  "hp": 58,
  "name": "Charmeleon",
  "speed": 80,
  "types": [
    "fire"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d047c"),
  "attack": 63,
  "created": "2013-11-03T15:05:41.280718",
  "defense": 80,
  "height": "10",
  "hp": 59,
  "name": "Wartortle",
  "speed": 58,
  "types": [
    "water"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d047d"),
  "attack": 83,
  "created": "2013-11-03T15:05:41.282985",
  "defense": 100,
  "height": "16",
  "hp": 79,
  "name": "Blastoise",
  "speed": 78,
  "types": [
    "water"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d047e"),
  "attack": 30,
  "created": "2013-11-03T15:05:41.285736",
  "defense": 35,
  "height": "3",
  "hp": 45,
  "name": "Caterpie",
  "speed": 45,
  "types": [
    "bug"
  ],
  "moves": [
    "Desvio"
  ]
}
Fetched 5 record(s) in 3ms



```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
``` 
var query = {name: 'AindaNaoExisteMon'}
var mod = {$setOnInsert:{attack: null,created: null,defense:null,height:null,hp:null,speed:null,types:null,moves:null,description:'Sem maiores informações'}}
var options = {upsert: true}
db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 9ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("570c41f513b4b71e0c762e8e")
})
var query = {"_id": ObjectId("570c41f513b4b71e0c762e8e")}
db.pokemons.find(query)
{
  "_id": ObjectId("570c41f513b4b71e0c762e8e"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "created": null,
  "defense": null,
  "height": null,
  "hp": null,
  "speed": null,
  "types": null,
  "moves": null,
  "description": "Sem maiores informações"
}
Fetched 1 record(s) in 1ms
joaopaulo(mongod-2.6.3) be-mean-pokemon> 

```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
var query = {moves: {$in:[/investida/i,/choque do trovão/i]}}
db.pokemons.find(query)
{
  "_id": ObjectId("564b1dad25337263280d047a"),
  "attack": 52,
  "created": "2013-11-03T15:05:41.271082",
  "defense": 43,
  "height": "6",
  "hp": 39,
  "name": "Charmander",
  "speed": 65,
  "types": [
    "fire"
  ],
  "moves": [
    "Lança chamas",
    "investida",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1db125337263280d04a7"),
  "attack": 55,
  "created": "2013-11-03T15:05:41.317235",
  "defense": 40,
  "height": "4",
  "hp": 35,
  "name": "Pikachu",
  "speed": 90,
  "types": [
    "electric"
  ],
  "moves": [
    "Choque do trovão",
    "investida",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1db425337263280d04b6"),
  "attack": 48,
  "created": "2013-11-03T15:05:41.278310",
  "defense": 65,
  "height": "5",
  "hp": 44,
  "name": "Squirtle",
  "speed": 43,
  "types": [
    "water"
  ],
  "moves": [
    "Hidro bomba",
    "investida",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1de325337263280d068c"),
  "attack": 49,
  "created": "2013-11-03T15:05:41.260678",
  "defense": 49,
  "height": "7",
  "hp": 45,
  "name": "Bulbasaur",
  "speed": 45,
  "types": [
    "poison",
    "grass"
  ],
  "moves": [
    "Folhas navalhas",
    "investida",
    "Desvio"
  ]
}
Fetched 4 record(s) in 4ms

```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```
var query = {moves: {$in:[/choque do trovão/i,/Hidro bomba/i,/folhas navalhas/i,/Lança chamas/i]}}
db.pokemons.find(query)
{
  "_id": ObjectId("564b1dad25337263280d047a"),
  "attack": 52,
  "created": "2013-11-03T15:05:41.271082",
  "defense": 43,
  "height": "6",
  "hp": 39,
  "name": "Charmander",
  "speed": 65,
  "types": [
    "fire"
  ],
  "moves": [
    "Lança chamas",
    "investida",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1db125337263280d04a7"),
  "attack": 55,
  "created": "2013-11-03T15:05:41.317235",
  "defense": 40,
  "height": "4",
  "hp": 35,
  "name": "Pikachu",
  "speed": 90,
  "types": [
    "electric"
  ],
  "moves": [
    "Choque do trovão",
    "investida",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1db425337263280d04b6"),
  "attack": 48,
  "created": "2013-11-03T15:05:41.278310",
  "defense": 65,
  "height": "5",
  "hp": 44,
  "name": "Squirtle",
  "speed": 43,
  "types": [
    "water"
  ],
  "moves": [
    "Hidro bomba",
    "investida",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1de325337263280d068c"),
  "attack": 49,
  "created": "2013-11-03T15:05:41.260678",
  "defense": 49,
  "height": "7",
  "hp": 45,
  "name": "Bulbasaur",
  "speed": 45,
  "types": [
    "poison",
    "grass"
  ],
  "moves": [
    "Folhas navalhas",
    "investida",
    "Desvio"
  ]
}
Fetched 4 record(s) in 3ms

```
## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```
var query = {types:{$nin:[/electric/]}}
db.pokemons.find(query).limit(3)
{
  "_id": ObjectId("564b1dad25337263280d0479"),
  "attack": 56,
  "created": "2013-11-03T15:05:41.305777",
  "defense": 35,
  "height": "3",
  "hp": 30,
  "name": "Rattata",
  "speed": 72,
  "types": [
    "normal"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d047b"),
  "attack": 64,
  "created": "2013-11-03T15:05:41.273462",
  "defense": 58,
  "height": "11",
  "hp": 58,
  "name": "Charmeleon",
  "speed": 80,
  "types": [
    "fire"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d047c"),
  "attack": 63,
  "created": "2013-11-03T15:05:41.280718",
  "defense": 80,
  "height": "10",
  "hp": 59,
  "name": "Wartortle",
  "speed": 58,
  "types": [
    "water"
  ],
  "moves": [
    "Desvio"
  ]
}
Fetched 3 record(s) in 5ms

todos os pokémons:
db.pokemons.count()
610

sem os elétricos: 
db.pokemons.find(query).length()
570


```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
``` 
var query = {$and:[{moves:{$in:[/investida/i]}},{defense:{$not:{$lte:49}}}]}
joaopaulo(mongod-2.6.3) be-mean-pokemon> db.pokemons.find(query)
{
  "_id": ObjectId("564b1db425337263280d04b6"),
  "attack": 48,
  "created": "2013-11-03T15:05:41.278310",
  "defense": 65,
  "height": "5",
  "hp": 44,
  "name": "Squirtle",
  "speed": 43,
  "types": [
    "water"
  ],
  "moves": [
    "Hidro bomba",
    "investida",
    "Desvio"
  ]
}
Fetched 1 record(s) in 3ms

joaopaulo(mongod-2.6.3) be-mean-pokemon> db.pokemons.find(query)
{
  "_id": ObjectId("564b1db425337263280d04b6"),
  "attack": 48,
  "created": "2013-11-03T15:05:41.278310",
  "defense": 65,
  "height": "5",
  "hp": 44,
  "name": "Squirtle",
  "speed": 43,
  "types": [
    "water"
  ],
  "moves": [
    "Hidro bomba",
    "investida",
    "Desvio"
  ]
}
Fetched 1 record(s) in 2ms

```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
``` 
var query = {$and:[{types:{$in:[/water/i]}},{attack:{$lt:50}}]}
joaopaulo(mongod-2.6.3) be-mean-pokemon> db.pokemons.remove(query)
Removed 21 record(s) in 9ms
WriteResult({
  "nRemoved": 21
})


```
