# MongoDB - Aula 04 - Exercício
autor: Mauriene Firmino

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
mauriene-J1800NH(mongod-2.6.10) pokemons> var query = { name:{ $in:["Pikachu","Squirtle","Bulbassauro","Charmander"] } }
mauriene-J1800NH(mongod-2.6.10) pokemons> var mod = {$pushAll:{moves:["Mov 1","Mov 2"]}}
mauriene-J1800NH(mongod-2.6.10) pokemons> var options = {multi:true}
mauriene-J1800NH(mongod-2.6.10) pokemons> db.pokemons.update(query,mod,options)
Updated 3 existing record(s) in 43ms
WriteResult({
  "nMatched": 3,
  "nUpserted": 0,
  "nModified": 3
})

```
## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

``` 
mauriene-J1800NH(mongod-2.6.10) pokemons> var query = {}
mauriene-J1800NH(mongod-2.6.10) pokemons> var mod = {$push:{moves:["desvio"]}}
mauriene-J1800NH(mongod-2.6.10) pokemons> var options = {multi:true}
mauriene-J1800NH(mongod-2.6.10) pokemons> db.pokemons.update(query,mod,options)
Updated 620 existing record(s) in 27ms
WriteResult({
  "nMatched": 620,
  "nUpserted": 0,
  "nModified": 620
})

```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

``` 
mauriene-J1800NH(mongod-2.6.10) pokemons> var query = {name:/AindaNaoExisteMon/i}
mauriene-J1800NH(mongod-2.6.10) pokemons> var mod = {
... $setOnInsert:{
... name: "AindaNaoExisteMon",
... attack: null,
... defense:null,
... height:null,
... description: "Sem maiores informações"
... }
... }
mauriene-J1800NH(mongod-2.6.10) pokemons> var options = {
... upsert: true
... }
mauriene-J1800NH(mongod-2.6.10) pokemons> db.pokemons.update(query,mod,options)
Updated 1 new record(s) in 14ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("57c6cba8ef4fa1543fac479a")
})

```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

``` 
mauriene-J1800NH(mongod-2.6.10) pokemons> var query = {moves:{$in:["investida","Mov 1"]}}
mauriene-J1800NH(mongod-2.6.10) pokemons> db.pokemons.find(query)

```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

``` 
mauriene-J1800NH(mongod-2.6.10) pokemons> var query = {moves:{$in:["Mov 1","Mov 2"]}}
mauriene-J1800NH(mongod-2.6.10) pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564a7c362c153ed825a6905a"),
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
    "Mov 1",
    "Mov 2",
    [
      "desvio"
    ]
  ]
}
{
  "_id": ObjectId("564a7c452c153ed825a690e1"),
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
    "Mov 1",
    "Mov 2",
    [
      "desvio"
    ]
  ]
}
{
  "_id": ObjectId("564a7c4c2c153ed825a6911d"),
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
    "Mov 1",
    "Mov 2",
    [
      "desvio"
    ]
  ]
}
Fetched 3 record(s) in 3ms

```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

``` 
mauriene-J1800NH(mongod-2.6.10) pokemons> var query = {moves:{$in:["Mov 1","Mov 2"]}}
mauriene-J1800NH(mongod-2.6.10) pokemons> db.pokemons.find(query)

```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

``` 
var query = { $and:[ { moves: { $in: [/investida/i]} }, { defense: { $gte: 50 } } ]};

```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.

``` 
mauriene-J1800NH(mongod-2.6.10) pokemons> var query = { $and:[ {types:"aqua"}, {attack:{$lt:50}} ] }
mauriene-J1800NH(mongod-2.6.10) pokemons> db.pokemons.remove(query)

```
