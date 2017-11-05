# MongoDB - Aula 04 - Exercício
autor: Alex Sandro Souza

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
gigantus(mongod-3.2.17) be-mean-instagram> var query = {$or:[{name:/pikachu/i},{name:/squirtle/i},{name:/bulbassauro/i},{name:/charmander/i}]}
gigantus(mongod-3.2.17) be-mean-instagram> var mod = {$set:{moves:['soco inglês','ataque furia']}}
gigantus(mongod-3.2.17) be-mean-instagram> var opt = {multi:true}
gigantus(mongod-3.2.17) be-mean-instagram> db.pokemons.update(query,mod,opt)
Updated 4 existing record(s) in 2ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})

```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

```
gigantus(mongod-3.2.17) be-mean-instagram> var query = {}
gigantus(mongod-3.2.17) be-mean-instagram> var mod = {$push:{moves:'desvio'}}
gigantus(mongod-3.2.17) be-mean-instagram> var opt = {multi:true}
gigantus(mongod-3.2.17) be-mean-instagram> db.pokemons.update(query,mod,opt)
Updated 7 existing record(s) in 2ms
WriteResult({
  "nMatched": 7,
  "nUpserted": 0,
  "nModified": 7
})

```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

```
gigantus(mongod-3.2.17) be-mean-instagram> var query = {name:/AindaNaoExisteMon/i}
gigantus(mongod-3.2.17) be-mean-instagram> var mod = {$setOnInsert:{name:'AindaNaoExisteMon',description:'Sem maiores informações',type:null,attack:null,height:null,defense:null,moves:[]}}
gigantus(mongod-3.2.17) be-mean-instagram> var opt = {upsert:true}
gigantus(mongod-3.2.17) be-mean-instagram> db.pokemons.update(query,mod,opt)
Updated 1 new record(s) in 4ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("59fef3f7f9869bf02555489a")
})

```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
gigantus(mongod-3.2.17) be-mean-instagram> var query = {moves:{$in:[/investida/i,/soco inglês/i]}}
gigantus(mongod-3.2.17) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("59f906a1241d4eb872e7e217"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "soco inglês",
    "ataque furia",
    "desvio"
  ]
}
{
  "_id": ObjectId("59f906b6241d4eb872e7e218"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "soco inglês",
    "ataque furia",
    "desvio"
  ]
}
{
  "_id": ObjectId("59f906be241d4eb872e7e219"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 18,
  "height": 0.5,
  "active": false,
  "moves": [
    "soco inglês",
    "ataque furia",
    "desvio"
  ]
}
{
  "_id": ObjectId("59f90898b754920f4ff31def"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("59fb7d5a8848a88e64108846"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("59fe20e0b116716e80d9626f"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("59fee287fef87f09dbdf3978"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "elétrico",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "soco inglês",
    "ataque furia",
    "desvio"
  ],
  "active": false
}
Fetched 7 record(s) in 5ms

```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

```
gigantus(mongod-3.2.17) be-mean-instagram> var query = {moves:{$in:[/soco inglês/i]}}
gigantus(mongod-3.2.17) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("59f906a1241d4eb872e7e217"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "soco inglês",
    "ataque furia",
    "desvio"
  ]
}
{
  "_id": ObjectId("59f906b6241d4eb872e7e218"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "soco inglês",
    "ataque furia",
    "desvio"
  ]
}
{
  "_id": ObjectId("59f906be241d4eb872e7e219"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 18,
  "height": 0.5,
  "active": false,
  "moves": [
    "soco inglês",
    "ataque furia",
    "desvio"
  ]
}
{
  "_id": ObjectId("59fee287fef87f09dbdf3978"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "elétrico",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "soco inglês",
    "ataque furia",
    "desvio"
  ],
  "active": false
}
Fetched 4 record(s) in 5ms
```
## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

```
gigantus(mongod-3.2.17) be-mean-instagram> var query = {type:{$ne:'elétrico'}}
gigantus(mongod-3.2.17) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("59f906a1241d4eb872e7e217"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "soco inglês",
    "ataque furia",
    "desvio"
  ]
}
{
  "_id": ObjectId("59f906b6241d4eb872e7e218"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "soco inglês",
    "ataque furia",
    "desvio"
  ]
}
{
  "_id": ObjectId("59f906be241d4eb872e7e219"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 18,
  "height": 0.5,
  "active": false,
  "moves": [
    "soco inglês",
    "ataque furia",
    "desvio"
  ]
}
{
  "_id": ObjectId("59f90898b754920f4ff31def"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("59fb7d5a8848a88e64108846"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("59fe20e0b116716e80d9626f"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("59fef3f7f9869bf02555489a"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null,
  "defense": null,
  "moves": [ ]
}
Fetched 7 record(s) in 6ms

```
## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```
gigantus(mongod-3.2.17) be-mean-instagram> var query = {$and: [{moves: {$in: [/desvio/i]}}, {attack: {$not: {$lte: 49} } }]}
gigantus(mongod-3.2.17) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("59f906b6241d4eb872e7e218"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "soco inglês",
    "ataque furia",
    "desvio"
  ]
}
{
  "_id": ObjectId("59fb7d5a8848a88e64108846"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("59fe20e0b116716e80d9626f"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("59fee287fef87f09dbdf3978"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "elétrico",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "soco inglês",
    "ataque furia",
    "desvio"
  ],
  "active": false
}
Fetched 4 record(s) in 3ms


```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
gigantus(mongod-3.2.17) be-mean-instagram> var query = {$and:[{type:'água'},{attack:{$lt:50}}]}
gigantus(mongod-3.2.17) be-mean-instagram> db.pokemons.remove(query)
Removed 1 record(s) in 2ms
WriteResult({
  "nRemoved": 1
})

```
