# MongoDB - Aula 04- Exercício
autor: Renan Roger Ferreira da silva

## 1º Adicionar 2 ataques ao mesmo tempo nos pokemons pikachu,squitler,bulbasauro e charmander.
```
  var query = {$or:[{name:/pikachu/i},{name:/charmander/i},{name:/charlizard/i}]}
  renan-pc(mongod-3.4.3) be-mean-pokemon> var attacks = ['investida','recuar','ultimate']
  renan-pc(mongod-3.4.3) be-mean-pokemon> var mod = {$pushAll:{moves:attacks}}
  renan-pc(mongod-3.4.3) be-mean-pokemon> var options={multi:true}
  renan-pc(mongod-3.4.3) be-mean-pokemon> db.pokemons.update(query,mod,options)
  Updated 3 existing record(s) in 2ms
WriteResult({
  "nMatched": 3,
  "nUpserted": 0,
  "nModified": 3
})


```
## 2º adicionar 1 movimento ```desvio```a todos os pokemons.
```
renan-pc(mongod-3.4.3) be-mean-pokemon> var query = {}
renan-pc(mongod-3.4.3) be-mean-pokemon> var options = {multi:true}
renan-pc(mongod-3.4.3) be-mean-pokemon> var mod = {$push:{moves:"recuar"}}
renan-pc(mongod-3.4.3) be-mean-pokemon> db.pokemons.update(query,mod,options)
Updated 6 existing record(s) in 2ms
WriteResult({
  "nMatched": 6,
  "nUpserted": 0,
  "nModified": 6
})

```
## 3ª adicionar o pokemon `AindaNaoExisteMon` caso ele não exista, todos os dados devem ser `null` e a descrição: "sem informações".
```
 renan-pc(mongod-3.4.3) be-mean-pokemon> var query = {name:"AindaNaoExisteMon"}
renan-pc(mongod-3.4.3) be-mean-pokemon> var mod = {$set:{active:true},$setOnInsert:{name:"AindaNaoExisteMon",description:null,type:null,atack:null,height:null}}
renan-pc(mongod-3.4.3) be-mean-pokemon> var option = {upsert:true}
renan-pc(mongod-3.4.3) be-mean-pokemon> db.pokemons.update(query,mod,option)
Updated 1 new record(s) in 42ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("590b4a6890846fa3ecb0919c")
})

``` 
## 4º pesquisar todos os pokemons que  possuam o ataque `invesitda` e mais um que vc adicionou, escolha seu pokemon favorito.
``` 
  var query = {moves:{$in:["investida","choque do trovao"]}}
  db.pokemons.find(query);
  {
  "_id": ObjectId("5903895dc663a59d8b11b95d"),
  "name": "Pikachu",
  "description": "Raio eletrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "choque do trovao",
    "investida",
    "recuar",
    "ultimate",
    "investida",
    "recuar",
    "ultimate",
    "investida",
    "recuar",
    "ultimate",
    "recuar"
  ]
}
{
  "_id": ObjectId("5903895dc663a59d8b11b95e"),
  "name": "charmander",
  "description": "Raio cabuloso de fogo",
  "type": "fire",
  "attack": 60,
  "height": 0.5,
  "moves": [
    "investida",
    "recuar",
    "ultimate",
    "recuar"
  ]
}
{
  "_id": ObjectId("5903895dc663a59d8b11b95f"),
  "name": "charlizard",
  "description": "Dragon modafoka",
  "type": "fire",
  "attack": 99,
  "height": 1.2,
  "moves": [
    "investida",
    "recuar",
    "ultimate",
    "recuar"
  ]
}


```
## 5º escolha todos os pokemons que possuam os ataques que voce adicionou, escolha seu pokemon favorito.

```
var query = {moves:{$in:["choque do trovao"]}}
  db.pokemons.find(query);
   "_id": ObjectId("5903895dc663a59d8b11b95d"),
  "name": "Pikachu",
  "description": "Raio eletrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "choque do trovao",
    "investida",
    "recuar",
    "ultimate",
    "investida",
    "recuar",
    "ultimate",
    "investida",
    "recuar",
    "ultimate",
    "recuar"
  ]

```

## 6 pesquise todos os pokemons que não são do tipo `eletrico`.
```
renan-pc(mongod-3.4.3) be-mean-pokemon> var query = {type:{$nin:[/eletric/i]}}
renan-pc(mongod-3.4.3) be-mean-pokemon> db.pokemons.find(query)
{
  "_id": ObjectId("5903895dc663a59d8b11b95e"),
  "name": "charmander",
  "description": "Raio cabuloso de fogo",
  "type": "fire",
  "attack": 60,
  "height": 0.5,
  "moves": [
    "investida",
    "recuar",
    "ultimate",
    "recuar"
  ]
}
{
  "_id": ObjectId("5903895dc663a59d8b11b95f"),
  "name": "charlizard",
  "description": "Dragon modafoka",
  "type": "fire",
  "attack": 99,
  "height": 1.2,
  "moves": [
    "investida",
    "recuar",
    "ultimate",
    "recuar"
  ]
}
{
  "_id": ObjectId("5903895dc663a59d8b11b960"),
  "name": "Blastoise",
  "description": "Mega tartaruga bolada",
  "type": "water",
  "attack": 99,
  "height": 1.5,
  "moves": [
    "recuar"
  ]
}
{
  "_id": ObjectId("5903895dc663a59d8b11b961"),
  "name": "gree-ninja",
  "description": "ninjao trevoso",
  "type": "ninja",
  "attack": 85,
  "height": 1.2,
  "moves": [
    "recuar"
  ]
}
{
  "_id": ObjectId("5908985fd9f11889e5b0abf2"),
  "name": "Testemon",
  "attack": 8000,
  "defence": 8000,
  "height": 2.1,
  "description": "Pokemon de teste",
  "moves": [
    "recuar"
  ]
}
{
  "_id": ObjectId("590b4a6890846fa3ecb0919c"),
  "name": "AindaNaoExisteMon",
  "active": true,
  "description": null,
  "type": null,
  "atack": null,
  "height": null
}
Fetched 6 record(s) in 11ms

```
## 8º pesquisar todos os pokemons que tenahm atack `investida` e defesa não menor ou igual a 49.

```
renan-pc(mongod-3.4.3) be-mean-pokemon> var query ={$and:[{moves:{$in:["investida"]}},{defence:{$not:{$lte:49}}}]}
renan-pc(mongod-3.4.3) be-mean-pokemon> db.pokemons.find(query)
{
  "_id": ObjectId("5903895dc663a59d8b11b95d"),
  "name": "Pikachu",
  "description": "Raio eletrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "choque do trovao",
    "investida",
    "recuar",
    "ultimate",
    "investida",
    "recuar",
    "ultimate",
    "investida",
    "recuar",
    "ultimate",
    "recuar"
  ]
}
{
  "_id": ObjectId("5903895dc663a59d8b11b95e"),
  "name": "charmander",
  "description": "Raio cabuloso de fogo",
  "type": "fire",
  "attack": 60,
  "height": 0.5,
  "moves": [
    "investida",
    "recuar",
    "ultimate",
    "recuar"
  ]
}
{
  "_id": ObjectId("5903895dc663a59d8b11b95f"),
  "name": "charlizard",
  "description": "Dragon modafoka",
  "type": "fire",
  "attack": 99,
  "height": 1.2,
  "moves": [
    "investida",
    "recuar",
    "ultimate",
    "recuar"
  ]
}
Fetched 3 record(s) in 3ms


```
## 8º Remova **todos** os pokemons do tipo água e com atack menor que 50
```
renan-pc(mongod-3.4.3) be-mean-pokemon> var query = {$and:[{type:"água"},{attack:{$lt:50}}]}
renan-pc(mongod-3.4.3) be-mean-pokemon> db.pokemons.remove(query)
Removed 0 record(s) in 5ms
WriteResult({
  "nRemoved": 0
})

```
