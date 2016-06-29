# MongoDB - 04 - Exercicio
autor: William Dias Vargas


## 1 **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
HP(mongod-3.0.7) be-mean-teste> 

var query = { $or: [ {name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbassauro/i}, {name: /charmander/i} ]};

HP(mongod-3.0.7) be-mean-teste> 
var mod = { $pushAll: { moves: ['esquiva','corrida']}};
HP(mongod-3.0.7) be-mean-teste> var options = { multi: true };

HP(mongod-3.0.7) be-mean-teste> 
db.pokemons.update(query, mod, options);
Updated 4 existing record(s) in 381ms
WriteResult({
"nMatched": 4,
"nUpserted": 0,
"nModified": 4
})

```
## 2 **Adicionar** 1 movimento em todos os pokemons: `desvio`.
```
HP(mongod-3.0.7) be-mean-teste> 
var query = {};
HP(mongod-3.0.7) be-mean-teste> 
var mod = { $push: { moves: "desvio"}}
HP(mongod-3.0.7) be-mean-teste> 
var options = { multi: true }
HP(mongod-3.0.7) be-mean-teste> 
db.pokemons.update(query, mod, options)
Updated 7 existing record(s) in 30ms
WriteResult({
"nMatched": 7,
"nUpserted": 0,
"nModified": 7
})

```
##  3 **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".
```
HP(mongod-3.0.7) be-mean-teste> var mod = { $setOnInsert: {
...     name: "AindaNaoExisteMon"
...   , attack: null
...   , height: null
...   , defense: null
...   , moves: []
...   , description: "Sem maiores informações"
... }}
HP(mongod-3.0.7) be-mean-teste> var options = { upsert: true }
HP(mongod-3.0.7) be-mean-teste> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 26ms
WriteResult({
"nMatched": 0,
"nUpserted": 1,
"nModified": 0,
"_id": ObjectId("564fb88bf66b738212d7b6cc")
})

```
## 4 Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.
```
HP(mongod-3.0.7) be-mean-teste> var query = { moves: { $all: ['investida', /choque do trovao/i] }}
HP(mongod-3.0.7) be-mean-teste> db.pokemons.find(query)
{
	"_id": ObjectId("564627af9d7d4c6893325509"),
	"name": "Pikachu",
	"description": "Rato eletrico bem fofinho",
	"type": "electric",
	"attack": 55,
	"height": 0.4,
	"active": false,
	"moves": [
	"investida",
	"choque do trovao",
	"esquiva",
	"corrida",
	"desvio"
	]
}
Fetched 1 record(s) in 2ms

```
## 5 Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.
```
HP(mongod-3.0.7) be-mean-teste> var query = { moves: { $in: [/esquiva/i] }}
HP(mongod-3.0.7) be-mean-teste> db.pokemons.find(query)
{
	"_id": ObjectId("564627af9d7d4c6893325509"),
	"name": "Pikachu",
	"description": "Rato eletrico bem fofinho",
	"type": "electric",
	"attack": 55,
	"height": 0.4,
	"active": false,
	"moves": [
	"investida",
	"choque do trovao",
	"esquiva",
	"corrida",
	"desvio"
	]
}
{
	"_id": ObjectId("5646285b9d7d4c689332550a"),
	"name": "Bulbassauro",
	"description": "Chicote de trepadeira",
	"type": "grama",
	"attack": 49,
	"height": 0.4,
	"active": false,
	"moves": [
	"investida",
	"folha navalha",
	"esquiva",
	"corrida",
	"desvio"
	]
}
{
	"_id": ObjectId("564629129d7d4c689332550b"),
	"name": "Charmander",
	"description": "Fogo no rabo",
	"type": "fogo",
	"attack": 52,
	"height": 0.6,
	"active": false,
	"moves": [
	"investida",
	"lanca-chamas",
	"esquiva",
	"corrida",
	"desvio"
	]
}
{
	"_id": ObjectId("5646291e9d7d4c689332550c"),
	"name": "Squirtle",
	"description": "Ejeta agua que passarinho nao bebe",
	"type": "agua",
	"attack": 48,
	"height": 0.5,
	"active": false,
	"moves": [
	"investida",
	"hidro bomba",
	"esquiva",
	"corrida",
	"desvio"
	]
}
Fetched 4 record(s) in 54ms

```
## 6 Pesquisar **todos** os pokemons que não são do tipo `elétrico`.
```
HP(mongod-3.0.7) be-mean-teste> var query = { type: { $ne: "eletrico" }};
HP(mongod-3.0.7) be-mean-teste> db.pokemons.find(query)
{
	"_id": ObjectId("564627af9d7d4c6893325509"),
	"name": "Pikachu",
	"description": "Rato eletrico bem fofinho",
	"type": "electric",
	"attack": 55,
	"height": 0.4,
	"active": false,
	"moves": [
	"investida",
	"choque do trovao",
	"esquiva",
	"corrida",
	"desvio"
	]
}
{
	"_id": ObjectId("5646285b9d7d4c689332550a"),
	"name": "Bulbassauro",
	"description": "Chicote de trepadeira",
	"type": "grama",
	"attack": 49,
	"height": 0.4,
	"active": false,
	"moves": [
	"investida",
	"folha navalha",
	"esquiva",
	"corrida",
	"desvio"
	]
}
{
	"_id": ObjectId("564629129d7d4c689332550b"),
	"name": "Charmander",
	"description": "Fogo no rabo",
	"type": "fogo",
	"attack": 52,
	"height": 0.6,
	"active": false,
	"moves": [
	"investida",
	"lanca-chamas",
	"esquiva",
	"corrida",
	"desvio"
	]
}
{
	"_id": ObjectId("56462bd3ca279a3a8da49767"),
	"name": "Caterpie",
	"description": "Larva lutadora",
	"type": "inset",
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
	"_id": ObjectId("564f95b7f66b738212d7b6c9"),
	"active": false,
	"moves": [
	"investida",
	"desvio"
	]
}
{
	"_id": ObjectId("564f9682f66b738212d7b6ca"),
	"active": false,
	"moves": [
	"investida",
	"desvio"
	]
}
{
	"_id": ObjectId("5646291e9d7d4c689332550c"),
	"name": "Squirtle",
	"description": "Ejeta agua que passarinho nao bebe",
	"type": "agua",
	"attack": 48,
	"height": 0.5,
	"active": false,
	"moves": [
	"investida",
	"hidro bomba",
	"esquiva",
	"corrida",
	"desvio"
	]
}
{
	"_id": ObjectId("564fb88bf66b738212d7b6cc"),
	"name": "AindaNaoExisteMon",
	"attack": null,
	"height": null,
	"defense": null,
	"moves": [ ],
	"description": "Sem maiores informações"
}
Fetched 8 record(s) in 2ms

```
## 7 Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.
```
HP(mongod-3.0.7) be-mean-teste> 
HP(mongod-3.0.7) be-mean-teste> var query = { $and:[ { moves: { $in: [/investida/i]} }, { defense: { $gt: 49 } } ]}
HP(mongod-3.0.7) be-mean-teste> db.pokemons.find(query)
Fetched 0 record(s) in 1ms

```
## 8 Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
HP(mongod-3.0.7) be-mean-teste> var query = { $and:[ { type: "agua" }, { attack: { $lt: 50 }} ]}
HP(mongod-3.0.7) be-mean-teste> db.pokemons.remove(query)
Removed 1 record(s) in 3ms
WriteResult({
"nRemoved": 1
})
HP(mongod-3.0.7) be-mean-teste> 

```
