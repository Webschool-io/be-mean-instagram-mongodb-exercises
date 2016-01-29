# MongoDB - Aula 04 - Exercício
autor: Wellington Fernandes

## Passo 1

    ```
	var query = {$or: [{name: "Scyther"}, { "name": "Mareep"},  {"name": "Metapod"}]}
	var mod = {$inc: {attack: 2}}
	var options = {multi: true}
	db.pokemons.update(query, mod, options)
	
    ```	

## Passo 2

    ```
    var query = {}
	var mod = {$push: {moves: "desvio"}}
	var options = {multi: true}
	db.pokemons.update(query, mod, options)

    ```

## Passo 3

    ```
    var query = {name: /NaoExisteMon/i}
	var mod = {$set: {active: true}, $setOnInsert: {name: "NaoExisteMon", attack: null, defense: null, height: null, description: "Sem maiores informacoes", moves: []}}
	var options = {upsert: true}
	db.pokemons.update(query, mod, options)

    ```

## Passo 4

    ```
    var query = {moves: {$all: ["investida", "Chute"]}}
	db.pokemons.find(query)
	{
	    "_id": ObjectId("5642a9f7fbf2aa7ab2c4a037"),
	    "name": "Scyther",
	    "description": "Louva Deus lutador de Muay Thai",
	    "type": terra,
	    "attack": 92,
	    "defense": 50,
	    "height": 0.3,
	    "active": false,
	    "moves": [
	        "investida",
	        "Chute",
	        "desvio"
	    ]
	}


    ```

## Passo 5

    ```    
    var query = {moves: {$in: ["investida", "Chute", "Pedrada na cabeça", "desvio"]}}
	db.pokemons.find(query)

    ```

## Passo 6

	```    
    var query = {type: {$nin: ["eletrico"]}}
	db.pokemons.find(query)

    ```

## Passo 7

	```    
    var query = {$and: [{moves: /investida/i}, {defense: {$gte: 49}}]}
	db.pokemons.find(query)

    ```

## Passo 7

	```    
    var query = {$and: [{type: "agua"}, {attack: {$lt: 49}}]}
	db.pokemons.find(query)

    ```