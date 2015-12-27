# MongoDB - Aula 04 - Exercício
autor: Victor Igor

##Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```	
var query   = {$or:[{name:/Pikachu/i},{name:/Squirtle/i},{name:/Bulbassauro/i},{name:/Charmander/i}]}
var attacks = ['cabeçada', 'patada']
var mod 	=  {$pushAll: {moves: attacks}} 
var options = {multi: true}
db.pokemons.update(query, mod, options)

WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})

```
##Adicionar 1 movimento em todos os pokemons: desvio.

```
var query   = {}
var options = {multi: true}
var mod     = {$push: {moves:'desvio'}}
db.pokemons.update(query, mod, options)

WriteResult({
  "nMatched": 14,
  "nUpserted": 0,
  "nModified": 14
})

```

##Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".

```	
var query   = {name: 'AindaNaoExisteMon'}
var mod     =  {$setOnInsert: {
	attack: null,
	defense: null,
	height: null, 
	description: "Sem maiores informações"	
	}
}
var options = {upsert: true}
db.pokemons.update(query, mod, options)

Updated 1 new record(s) in 71ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("567e318b8c9d5a59c75d1503")
})

```
##Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.

```
	var query = {moves:{$in:[/investida/i,/folha navalha/i,]}}
	db.pokemons.find(query)

{
  "_id": ObjectId("564da193ab81d6513c255cab"),
  "name": "Psyduck",
  "description": "Psyduck uses a mysterious power. When it does so, this Pokémon generates brain waves that are supposedly only seen in sleepers.",
  "type": "Water",
  "attack": 30,
  "defence": 20,
  "height": 0.8,
  "moves": [
    "investida",
    "lança chamas",
    "desvio"
  ]
}
{
  "_id": ObjectId("564da193ab81d6513c255cb1"),
  "name": "modifique Persian",
  "description": "mudei aqui pq sou doido",
  "type": "Normal",
  "attack": 40,
  "defence": 30,
  "height": 1,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("567df96b8c9d5a59c75d1501"),
  "name": "esse campo nao existe",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("567dffac8c9d5a59c75d1502"),
  "name": "naoexiste",
  "moves": [
    "investida",
    "desvio"
  ],
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
{
  "_id": ObjectId("564da193ab81d6513c255caa"),
  "name": "Raichu",
  "description": "if the electrical sacs become excessively charged, Raichu plants its tail in the ground and discharges.",
  "type": "electric",
  "attack": 50,
  "defence": 30,
  "height": 0.8,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564da193ab81d6513c255cac"),
  "name": "Arcanine",
  "description": "Arcanine is known for its high speed. It is said to be capable of running over 6,200 miles in a single day and night.",
  "type": "Fire",
  "attack": 60,
  "defence": 40,
  "height": 1.9,
  "moves": [
    "investida",
    "veloz demais",
    "desvio"
  ]
}
{
  "_id": ObjectId("564da193ab81d6513c255cad"),
  "name": "Poliwrath",
  "description": "Poliwraths highly developed, brawny muscles never grow fatigued, however much it exercises.",
  "type": "Water-Flying",
  "attack": 50,
  "defence": 40,
  "height": 1.3,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564da193ab81d6513c255cb0"),
  "name": "Golbat",
  "description": "Golbat loves to drink the blood of living things. It is particularly active in the pitch black of night.",
  "type": "Poison-Flying",
  "attack": 40,
  "defence": 30,
  "height": 1.6,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564da193ab81d6513c255cae"),
  "name": "Metapod",
  "description": "The shell covering this Pokémons body is as hard as an iron slab.",
  "type": "Bug",
  "attack": 10,
  "defence": 30,
  "height": 0.7,
  "moves": [
    "investida",
    "folha navalha",
    "desvio"
  ]
}
{
  "_id": ObjectId("564da193ab81d6513c255caf"),
  "name": "Arbok",
  "description": "This Pokemon is terrifically strong in order to constrict things with its body.",
  "type": "Poison",
  "attack": 40,
  "defence": 30,
  "height": 3.5,
  "moves": [
    "investida",
    "desvio"
  ]
}
Fetched 10 record(s) in 4ms

```
##Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```
	var attack = [
		"investida",
	    "folha navalha",
	    "desvio"
	]
	var query = {moves: {$all: attack}}
	db.pokemons.find(query)
{
  "_id": ObjectId("564da193ab81d6513c255cae"),
  "name": "Metapod",
  "description": "The shell covering this Pokémons body is as hard as an iron slab.",
  "type": "Bug",
  "attack": 10,
  "defence": 30,
  "height": 0.7,
  "moves": [
    "investida",
    "folha navalha",
    "desvio"
  ]
}
Fetched 1 record(s) in 2ms

```
##Pesquisar todos os pokemons que não são do tipo elétrico


```
	var query = {type:{$not:/electric/i}}
	db.pokemons.find(query)

	{
  "_id": ObjectId("564da193ab81d6513c255cab"),
  "name": "Psyduck",
  "description": "Psyduck uses a mysterious power. When it does so, this Pokémon generates brain waves that are supposedly only seen in sleepers.",
  "type": "Water",
  "attack": 30,
  "defence": 20,
  "height": 0.8,
  "moves": [
    "investida",
    "lança chamas",
    "desvio"
  ]
}
{
  "_id": ObjectId("564da193ab81d6513c255cb1"),
  "name": "modifique Persian",
  "description": "mudei aqui pq sou doido",
  "type": "Normal",
  "attack": 40,
  "defence": 30,
  "height": 1,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("567df96b8c9d5a59c75d1501"),
  "name": "esse campo nao existe",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("567dffac8c9d5a59c75d1502"),
  "name": "naoexiste",
  "moves": [
    "investida",
    "desvio"
  ],
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
{
  "_id": ObjectId("564da193ab81d6513c255cac"),
  "name": "Arcanine",
  "description": "Arcanine is known for its high speed. It is said to be capable of running over 6,200 miles in a single day and night.",
  "type": "Fire",
  "attack": 60,
  "defence": 40,
  "height": 1.9,
  "moves": [
    "investida",
    "veloz demais",
    "desvio"
  ]
}
{
  "_id": ObjectId("564da193ab81d6513c255cad"),
  "name": "Poliwrath",
  "description": "Poliwraths highly developed, brawny muscles never grow fatigued, however much it exercises.",
  "type": "Water-Flying",
  "attack": 50,
  "defence": 40,
  "height": 1.3,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564da193ab81d6513c255cb0"),
  "name": "Golbat",
  "description": "Golbat loves to drink the blood of living things. It is particularly active in the pitch black of night.",
  "type": "Poison-Flying",
  "attack": 40,
  "defence": 30,
  "height": 1.6,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("567e254b4cf834992eaec784"),
  "name": "squirtle",
  "description": "muito lesado",
  "type": " Water",
  "attack": 48,
  "defence": 65,
  "height": 1.8,
  "moves": [
    "cabeçada",
    "patada",
    "desvio"
  ]
}
{
  "_id": ObjectId("567e25b84cf834992eaec785"),
  "name": "Bulbassauro",
  "description": "gordo demais",
  "type": " Grass",
  "attack": 49,
  "defence": 49,
  "height": 2.4,
  "moves": [
    "cabeçada",
    "patada",
    "desvio"
  ]
}
{
  "_id": ObjectId("567e268d4cf834992eaec786"),
  "name": "Charmander",
  "description": "dino tocha",
  "type": "fire",
  "attack": 53,
  "defence": 43,
  "height": 2,
  "moves": [
    "cabeçada",
    "patada",
    "desvio"
  ]
}
{
  "_id": ObjectId("564da193ab81d6513c255cae"),
  "name": "Metapod",
  "description": "The shell covering this Pokémons body is as hard as an iron slab.",
  "type": "Bug",
  "attack": 10,
  "defence": 30,
  "height": 0.7,
  "moves": [
    "investida",
    "folha navalha",
    "desvio"
  ]
}
{
  "_id": ObjectId("564da193ab81d6513c255caf"),
  "name": "Arbok",
  "description": "This Pokemon is terrifically strong in order to constrict things with its body.",
  "type": "Poison",
  "attack": 40,
  "defence": 30,
  "height": 3.5,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("567e318b8c9d5a59c75d1503"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 13 record(s) in 3ms

```
##Pesquisar todos os pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49

```
var query = {
	$and:[{moves  :{$in :[/investida/i]}}, 
		  {defense:{$lte:49       }}
	]	
}

db.pokemons.find(query)
Fetched 0 record(s) in 0ms

```
##Remova todos os pokemons do tipo água e com attack menor que 50.

```
var query = {
	$and: [{type:/water/i},
		   {attack:{$lt:50}}
	]
}
db.pokemons.remove(query)

Removed 2 record(s) in 2ms
WriteResult({
  "nRemoved": 2
})

```