# MongoDB - Aula 04 - Exercício
autor: Laurindo Ferreira Lucio Junior

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```javascript
// Selecionando o database
show dbs
use be-mean-pokemons
show collecions

var query = {name: /Pikachu/i}
var mod = {$pushAll: {moves: ['investida', 'agilidade extrema']}}
db.pokemons.update(query, mod)
/*
	Updated 1 existing record(s) in 3ms
	WriteResult({
	    "nMatched": 1,
	    "nUpserted": 0,
	    "nModified": 1
	})
*/
db.pokemons.find(query)
/*
	{
	    "_id": 25,
	    "name": "Pikachu",
	    "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge.",
	    "type": "eletric",
	    "attack": 55,
	    "height": 0.4,
	    "moves": [
	        "investida",
	        "choque do trovão",
	        "investida",
	        "agilidade extrema"
	    ],
	    "active": false
	}
*/

var query = {name: /Squirtle/i}
var mod = {$pushAll: {moves: ['hidrante atômico', 'láminas aquáticas']}}
db.pokemons.update(query, mod)
/*
	Updated 1 existing record(s) in 6ms
	WriteResult({
	    "nMatched": 1,
	    "nUpserted": 0,
	    "nModified": 1
	})
*/
db.pokemons.find(query)
/*
	{
	    "_id": 7,
	    "name": "Squirtle",
	    "description": "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
	    "type": "water",
	    "attack": 48,
	    "height": 0.5,
	    "active": false,
	    "moves": [
	        "investida",
	        "hidro bomba",
	        "hidrante atômico",
	        "láminas aquáticas"
	    ]
	}
*/

var query = {name: /Bulbasaur/i}
var mod = {$pushAll: {moves: ['Pântano das Raízes','Espinhos Sufocantes']}}
db.pokemons.update(query, mod)
/*
	Updated 1 existing record(s) in 4ms
	WriteResult({
	    "nMatched": 1,
	    "nUpserted": 0,
	    "nModified": 1
	})
*/
db.pokemons.find(query)
/*
	{
	    "_id": 1,
	    "name": "Bulbasaur",
	    "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
	    "type": "grass",
	    "attack": 49,
	    "height": 0.7,
	    "active": false,
	    "moves": [
	        "investida",
	        "folha navalha",
	        "Pântano das Raízes",
	        "Espinhos Sufocantes"
	    ]
	}
*/

var query = {name: /Charmander/i}
var mod = {$pushAll: {moves: ['Pilar de Chamas', 'Piroclasma']}}
db.pokemons.update(query, mod)
/*
	Updated 1 existing record(s) in 3ms
	WriteResult({
	    "nMatched": 1,
	    "nUpserted": 0,
	    "nModified": 1
	})
*/
db.pokemons.find(query)
/*
	{
	    "_id": 4,
	    "name": "Charmander",
	    "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
	    "type": "fire",
	    "attack": 52,
	    "height": 0.6,
	    "active": false,
	    "moves": [
	        "investida",
	        "lança-chamas",
	        "Pilar de Chamas",
	        "Piroclasma"
	    ]
	}
*/

```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

```javascript
var query = {}
var mod = {$push: {moves: 'desvio'}}
var options = {multi: true}
db.pokemons.update(query, mod, options)
/*
	Updated 12 existing record(s) in 3ms
	WriteResult({
	    "nMatched": 12,
	    "nUpserted": 0,
	    "nModified": 12
	})
*/
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

```javascript
var query = {name: /AindaNaoExisteMon/i}
var mod = {
	$setOnInsert: {
		name: 'AindaNaoExisteMon',
		attack: null,
		defensse: null,
		height: null,
		type: null,
		description: "Sem maiores informações"
	}
}
var options = {upsert: true}
db.pokemons.update(query, mod, options)
/*
	WriteResult({
	    "nMatched": 0,
	    "nUpserted": 1,
	    "nModified": 0,
	    "_id": ObjectId("56a3b5d6e25fcf7a54036c61")
	})

	{
	    "_id": ObjectId("56a3b5d6e25fcf7a54036c61"),
	    "name": "AindaNaoExisteMon",
	    "attack": null,
	    "defensse": null,
	    "height": null,
	    "type": null,
	    "description": "Sem maiores informações"
	}
	Fetched 1 record(s) in 15ms
*/
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

```javascript
var query = {moves: {$in: [ /investida/i , /Pântano das Raízes/i ]}}
db.pokemons.find(query)
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

```javascript
var query = {moves: {$all: [ /Pântano das Raízes/i, /Espinhos Sufocantes/i ]}}
db.pokemons.find(query)
```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

```javascript
var query = {type: {$not: /eletric/i }}
db.pokemons.find(query)
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

```javascript
/* Não tenho pokemons com defesa, então fiz com o atributo 'attack' */
var query = {$and: [{moves: {$in: ['investida']}}, {attack: {$not: {$lte: 49}}} ]}
db.pokemons.find(query)
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.

```javascript
var query = {$and: [{type: /water/i}, {attack: {$lt: 50}}]}
db.pokemons.remove(query)
/*
	Removed 1 record(s) in 4ms
	WriteResult({
	    "nRemoved": 1
	})
*/
```