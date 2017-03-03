# MongoDB - Aula 04 - Exercício
autor: Samuel Desconsi - Underzzoo

## 1. Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbasaur e Charmander.

```
var query = {$or: 
  [
    {name: /Pikachu/i},
    {name: /Squirtle/i},
    {name: /Bulbasaur/i},
    {name: /Charmander/i}
  ]
}

var mod = {$set:{
moves:['Atacar','Defender']
}}

var options = {multi: true}

db.pokemons.update(query, mod, options)

WriteResult({ "nMatched" : 4, "nUpserted" : 0, "nModified" : 4 })
> db.pokemons.find().pretty()
{
	"_id" : ObjectId("5811fa2b2cc158a2d2134b83"),
	"name" : "Bulbasaur",
	"description" : "Couve-Flor",
	"type" : "Grass",
	"attack" : 30,
	"height" : 0.7,
	"moves" : [
		"Atacar",
		"Defender"
	]
}
{
	"_id" : ObjectId("5811fa2b2cc158a2d2134b84"),
	"name" : "Charmander",
	"description" : "Dragãozinho",
	"type" : "Fire",
	"attack" : 30,
	"height" : 0.6,
	"moves" : [
		"Atacar",
		"Defender"
	]
}
{
	"_id" : ObjectId("5811fa2b2cc158a2d2134b85"),
	"name" : "Squirtle",
	"description" : "Tartaruguinha",
	"type" : "Water",
	"attack" : 30,
	"height" : 0.5,
	"moves" : [
		"Atacar",
		"Defender"
	]
}
{
	"_id" : ObjectId("5811fa2b2cc158a2d2134b86"),
	"name" : "Caterpie",
	"description" : "Corózinho",
	"type" : "Bug",
	"attack" : 20,
	"height" : 0.3
}
{
	"_id" : ObjectId("5811fa2b2cc158a2d2134b87"),
	"name" : "Butterfree",
	"description" : "Corózinho Evoluido pra brabuleta",
	"type" : "Bug",
	"attack" : 20,
	"height" : 1.1
}
{
	"_id" : ObjectId("581202422cc158a2d2134b88"),
	"name" : "Pikachu",
	"description" : "Rato Elétrico",
	"type" : "Thunder",
	"attack" : 45,
	"height" : 0.4,
	"moves" : [
		"Atacar",
		"Defender"
	]
}

```

## 2. Adicionar um movimento em todos os pokemons: 'Desvio'

```
> var query = {}

> var mod = {$push: {moves: 'desvio'}}

> var options = {multi: true}

> db.pokemons.update(query, mod, options)

WriteResult({ "nMatched" : 6, "nUpserted" : 0, "nModified" : 6 })

> db.pokemons.find().pretty()
{
	"_id" : ObjectId("5811fa2b2cc158a2d2134b83"),
	"name" : "Bulbasaur",
	"description" : "Couve-Flor",
	"type" : "Grass",
	"attack" : 30,
	"height" : 0.7,
	"moves" : [
		"Atacar",
		"Defender",
		"desvio"
	]
}
{
	"_id" : ObjectId("5811fa2b2cc158a2d2134b84"),
	"name" : "Charmander",
	"description" : "Dragãozinho",
	"type" : "Fire",
	"attack" : 30,
	"height" : 0.6,
	"moves" : [
		"Atacar",
		"Defender",
		"desvio"
	]
}
{
	"_id" : ObjectId("5811fa2b2cc158a2d2134b85"),
	"name" : "Squirtle",
	"description" : "Tartaruguinha",
	"type" : "Water",
	"attack" : 30,
	"height" : 0.5,
	"moves" : [
		"Atacar",
		"Defender",
		"desvio"
	]
}
{
	"_id" : ObjectId("5811fa2b2cc158a2d2134b86"),
	"name" : "Caterpie",
	"description" : "Corózinho",
	"type" : "Bug",
	"attack" : 20,
	"height" : 0.3,
	"moves" : [
		"desvio"
	]
}
{
	"_id" : ObjectId("5811fa2b2cc158a2d2134b87"),
	"name" : "Butterfree",
	"description" : "Corózinho Evoluido pra brabuleta",
	"type" : "Bug",
	"attack" : 20,
	"height" : 1.1,
	"moves" : [
		"desvio"
	]
}
{
	"_id" : ObjectId("581202422cc158a2d2134b88"),
	"name" : "Pikachu",
	"description" : "Rato Elétrico",
	"type" : "Thunder",
	"attack" : 45,
	"height" : 0.4,
	"moves" : [
		"Atacar",
		"Defender",
		"desvio"
	]
}

```

## 3. Adicionar o pokemons AindaNaoExistemon, caso ele não exista com todos os dados com valor 'null' e a descrição: "Sem maiores informações"

```
var query = {name: 'AindaNaoExistemon'}

var mod = {$setOnInsert: {
	name: 'AindaNaoExistemon',
	description: 'Sem maiores informações',
	type: null,
	attack: null,
	height: null,
	moves: {}

}}

var options = {upsert: true}

> db.pokemons.update(query, mod, options)
WriteResult({
	"nMatched" : 0,
	"nUpserted" : 1,
	"nModified" : 0,
	"_id" : ObjectId("581244109c7b202dc753f7ad")
})

> db.pokemons.find({name: /AindaNao/i}).pretty()
{
	"_id" : ObjectId("581244109c7b202dc753f7ad"),
	"name" : "AindaNaoExistemon",
	"description" : "Sem maiores informações",
	"type" : null,
	"attack" : null,
	"height" : null,
	"moves" : {
		
	}
}

```

## 4. Listagem Pokemons com ataque investida e mais um ataque

```
var query = {moves:{$in:['Investida', 'Defesa']}}
db.pokemons.find(query).pretty()
[Sem resultados]

> var query = {moves:{$in:[/Def/i]}}
> db.pokemons.find(query).pretty()
{
	"_id" : ObjectId("5811fa2b2cc158a2d2134b83"),
	"name" : "Bulbasaur",
	"description" : "Couve-Flor",
	"type" : "Grass",
	"attack" : 30,
	"height" : 0.7,
	"moves" : [
		"Atacar",
		"Defender",
		"desvio"
	]
}
{
	"_id" : ObjectId("5811fa2b2cc158a2d2134b84"),
	"name" : "Charmander",
	"description" : "Dragãozinho",
	"type" : "Fire",
	"attack" : 30,
	"height" : 0.6,
	"moves" : [
		"Atacar",
		"Defender",
		"desvio"
	]
}
{
	"_id" : ObjectId("5811fa2b2cc158a2d2134b85"),
	"name" : "Squirtle",
	"description" : "Tartaruguinha",
	"type" : "Water",
	"attack" : 30,
	"height" : 0.5,
	"moves" : [
		"Atacar",
		"Defender",
		"desvio"
	]
}
{
	"_id" : ObjectId("581202422cc158a2d2134b88"),
	"name" : "Pikachu",
	"description" : "Rato Elétrico",
	"type" : "Thunder",
	"attack" : 45,
	"height" : 0.4,
	"moves" : [
		"Atacar",
		"Defender",
		"desvio"
	]
}

[Não gosto de pokemons, nenhum é meu favorito, logo só quero aprender.]

```

## 5. Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```
var query ={attack:{$gt:30}}
db.pokemons.find(query)

> var query ={attack:{$gt:30}}
> db.pokemons.find(query).pretty()
{
	"_id" : ObjectId("581202422cc158a2d2134b88"),
	"name" : "Pikachu",
	"description" : "Rato Elétrico",
	"type" : "Thunder",
	"attack" : 45,
	"height" : 0.4,
	"moves" : [
		"Atacar",
		"Defender",
		"desvio"
	]
}

[Eu não gosto de pokemon, mas o Pikachu ta ownando a galera em AP. :D]
[É para ser o valor do ataque, ou os moves que foram adicionados?]

> var query = {name: /Pik/i}
> var mod = {$push: {moves: 'Choque do Trovão'}}
> var options = {multi: false}
> db.pokemons.update(query, mod, options)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.pokemons.find(query).pretty()
{
	"_id" : ObjectId("581202422cc158a2d2134b88"),
	"name" : "Pikachu",
	"description" : "Rato Elétrico",
	"type" : "Thunder",
	"attack" : 45,
	"height" : 0.4,
	"moves" : [
		"Atacar",
		"Defender",
		"desvio",
		"Choque do Trovão"
	]
}

```
## 6. Pesquisar todos que não são do tipo 'elétrico'

```
> var query = {type: {$ne: "Thunder" } }
> db.pokemons.find(query).pretty()
{
	"_id" : ObjectId("5811fa2b2cc158a2d2134b83"),
	"name" : "Bulbasaur",
	"description" : "Couve-Flor",
	"type" : "Grass",
	"attack" : 30,
	"height" : 0.7,
	"moves" : [
		"Atacar",
		"Defender",
		"desvio"
	]
}
{
	"_id" : ObjectId("5811fa2b2cc158a2d2134b84"),
	"name" : "Charmander",
	"description" : "Dragãozinho",
	"type" : "Fire",
	"attack" : 30,
	"height" : 0.6,
	"moves" : [
		"Atacar",
		"Defender",
		"desvio"
	]
}
{
	"_id" : ObjectId("5811fa2b2cc158a2d2134b85"),
	"name" : "Squirtle",
	"description" : "Tartaruguinha",
	"type" : "Water",
	"attack" : 30,
	"height" : 0.5,
	"moves" : [
		"Atacar",
		"Defender",
		"desvio"
	]
}
{
	"_id" : ObjectId("5811fa2b2cc158a2d2134b86"),
	"name" : "Caterpie",
	"description" : "Corózinho",
	"type" : "Bug",
	"attack" : 20,
	"height" : 0.3,
	"moves" : [
		"desvio"
	]
}
{
	"_id" : ObjectId("5811fa2b2cc158a2d2134b87"),
	"name" : "Butterfree",
	"description" : "Corózinho Evoluido pra brabuleta",
	"type" : "Bug",
	"attack" : 20,
	"height" : 1.1,
	"moves" : [
		"desvio"
	]
}
{
	"_id" : ObjectId("581244109c7b202dc753f7ad"),
	"name" : "AindaNaoExistemon",
	"description" : "Sem maiores informações",
	"type" : null,
	"attack" : null,
	"height" : null,
	"moves" : {
		
	}
}




```

## 7. Pesquisar todos pokemons que tenham o ataque 'investida' && tenham a defesa 'não menor ou igual a 49'.

```
var query = {}
var mod = {$set: {defense: 50}}
var options = {multi: true}
> db.pokemons.update(query, mod, options)
WriteResult({ "nMatched" : 7, "nUpserted" : 0, "nModified" : 7 })

var query = {$or: [{name: /Pika/i}, {name: /Bulb/i }]}
var mod = {$push: {moves: 'Investida'}}
var options = {multi: true}
> db.pokemons.update(query, mod, options)
WriteResult({ "nMatched" : 2, "nUpserted" : 0, "nModified" : 2 })

> db.pokemons.find({$and:[{moves: {$in: [/investida/i]}}, {defense: {$not:{$lte: 49}}}]}).pretty()

{
	"_id" : ObjectId("5811fa2b2cc158a2d2134b83"),
	"name" : "Bulbasaur",
	"description" : "Couve-Flor",
	"type" : "Grass",
	"attack" : 30,
	"height" : 0.7,
	"moves" : [
		"Atacar",
		"Defender",
		"desvio",
		"Investida"
	],
	"defense" : 50
}
{
	"_id" : ObjectId("581202422cc158a2d2134b88"),
	"name" : "Pikachu",
	"description" : "Rato Elétrico",
	"type" : "Thunder",
	"attack" : 45,
	"height" : 0.4,
	"moves" : [
		"Atacar",
		"Defender",
		"desvio",
		"Choque do Trovão",
		"Investida"
	],
	"defense" : 50
}
> 


```

## 8. Remova todos os pokemons do tipo água e com ataque menor que 50

```
var query = {$and:[ {types: /water/i}, {attack: {$lt: 50}} ]}
db.pokemons.remove(query)
WriteResult({ "nRemoved" : 0 }

```

 
