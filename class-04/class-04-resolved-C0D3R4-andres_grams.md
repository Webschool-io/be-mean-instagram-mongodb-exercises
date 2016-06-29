# MongoDB - Aula 04 - Exercício
autor: C0D3R4

Insert Keys = query,mod, opt, poke ;

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: `Pikachu, Squirtle, Bulbassauro e Charmander`.
```JavaScript

var query = {
$or: [
	{name: /Pikachu/i},
	{name: /Squirtle/i},
	{name: /Bulbasaur/i},
	{name: /Charmander/i}
    ]
};

var mod = {$set: {
	moves: ['Meta', 'Dobra Meta']
}};

var opt = {
	multi: true
};

db.pokemons.update(query, mod, opt)
Updated 4 existing record(s) in 24ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})

```
## LISTAR POKEMONS MODIFICADOS COM NOVO ATAQUE `META`

```JavaScript

var Meta = {"moves":"Meta"};

be-mean-pokemons> db.pokemons.find(Meta)
{
  "_id": ObjectId("5645142fe649ecb17651a01d"),
  "name": "Bulbasaur",
  "description": "Dragão Comodo cabulozooo",
  "type": "Dragao Comodo",
  "weaknesses": "Ice",
  "attack": 10,
  "defense": 20,
  "height": 0.2,
  "weight": 199.5,
  "moves": [
    "Meta",
    "Dobra Meta"
  ]
}
{
  "_id": ObjectId("5645142fe649ecb17651a01e"),
  "name": "Pikachu",
  "description": "Ratinho com rabo de raio cabulozooo",
  "type": "Rato",
  "weaknesses": "Water",
  "attack": 15,
  "defense": 15,
  "height": 0.4,
  "weight": 13.2,
  "moves": [
    "Meta",
    "Dobra Meta"
  ]
}
{
  "_id": ObjectId("565dcd20b9365ef65d4a50da"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "Meta",
    "Dobra Meta"
  ]
}
{
  "_id": ObjectId("565dcf18b9365ef65d4a50db"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "Meta",
    "Dobra Meta"
  ]
}
```

## **Adicionar** 1 movimento em todos os pokemons: 'desvio'.

```JavaScript

var mod = {$push: {moves:'agachamento'}}

var opt = {multi: true}

db.pokemons.update({}, mod, opt)

```

# Adicionar o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: `"Sem maiores informações"`.

```JavaScript

var query = {name:'dirceumon'}
var mod = {$setOnInsert: {
  name: 'dirceumon',
  attack: 100,
  defense: 80,
  heigth: 180,
  speed: 1000,
  types: 'corrupto',
  description: 'Presidente da Camara tem o poder de passar o impeachment segurou até dia 02-12 pois o PT o estava apoiando agora deixou a casa caiusa'
}}
var opt = {upsert: true}
db.pokemons.update(query, mod, opt)


```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.

```JavaScript
var query = {moves:{$in:['investida', 'mensalao']}}
db.pokemons.find(query)

db.pokemons.find({moves:"mensalao"})
{
  "_id": ObjectId("565f7b7023c0000c36c5182b"),
  "name": "dirceumon",
  "attack": 100,
  "defense": 80,
  "heigth": 180,
  "speed": 1000,
  "types": "corrupto",
  "description": "Presidente da Camara tem o poder de passar o impeachment segurou até dia 02-12 pois o PT o estava apoiando agora deixou a casa caiusa",
  "moves": [
    "mensalao"
  ]
}


```
# Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```JavaScript
var query ={attack:{$lte:5}}

mongo < mc.js 
MongoDB shell version: 2.6.3
connecting to: test
Mongo-Hacker 0.0.9
switched to db be-mean-pokemons
{
  "_id": ObjectId("5645142fe649ecb17651a01b"),
  "name": "Blastoise",
  "description": "Tartaruga Ninja cabulozaaa",
  "type": "Turtle",
  "weaknesses": "Grass",
  "attack": 5,
  "defense": 10,
  "height": 0.5,
  "weight": 188.5,
  "moves": [
    "desvio",
    "agachamento"
  ]
}
{
  "_id": ObjectId("5645142fe649ecb17651a01c"),
  "name": "Charizard",
  "description": "Dragao cabulozooo",
  "type": "Dragao",
  "weaknesses": "Water",
  "attack": 5,
  "defense": 10,
  "height": 1.05,
  "weight": 199.5,
  "moves": [
    "desvio",
    "agachamento"
  ]
}

db.pokemons.find(query)

```

# Pesquisar todos os pokemons que não são do tipo elétrico.

```JavaScript
use be-mean-pokemons
db.pokemons.find({type:{$ne:['eletrico']}})

```

# Pesquisar todos pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49.

```JavaScript
use be-mean-pokemons
db.pokemons.find({
	$and:[
	{moves: {$in: ['investida']}},
	{defense: {$not:{$lte: 0.49}}}
	]
  }
)

```
# Remova todos os pokemons do tipo água e com attack menor que 50.


```JavaScript
use be-mean-pokemons
db.pokemons.remove({
	$and:[
	{types: {$in: ['water','agua']}},
	{attack: {$lt: 50}}
	]
  }
)

```