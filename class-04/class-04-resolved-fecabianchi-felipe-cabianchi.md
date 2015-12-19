# MongoDB - Aula 04 - Exercício
autor: Felipe Cabianchi de Oliveira

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

	```js
		var query = {name : {$in : poke}}
		var poke = [/pikachu/i, /bulbasaur/i, /squirtle/i, /charmander/i]
		var attacks = ['investida', 'desvio']
		var mod = {$pushAll : {moves : attacks}}
		var opt = {multi : true}

		Updated 4 existing record(s) in 10ms
		WriteResult({
			"nMatched": 4,
			"nUpserted": 0,
			"nModified": 4
		})

		{
		  "_id": ObjectId("5653dca1415e21582441090e"),
		  "name": "Pikachu",
		  "description": "Ratinho",
		  "type": "eletric",
		  "attack": 55,
		  "height": 4,
		  "moves": [
		    "investida",
		    "desvio"
		  ]
		}
		{
		  "_id": ObjectId("5653dca6415e21582441090f"),
		  "name": "Squirtle",
		  "description": "aguinha",
		  "type": "water",
		  "attack": 48,
		  "height": 5,
		  "moves": [
		    "investida",
		    "desvio"
		  ]
		}
		{
		  "_id": ObjectId("5653dcaa415e215824410910"),
		  "name": "Bulbasaur",
		  "description": "Chicote",
		  "type": "grass",
		  "attack": 49,
		  "height": 7,
		  "moves": [
		    "investida",
		    "desvio"
		  ]
		}
		{
		  "_id": ObjectId("5654b3a5f2014feb151bc27e"),
		  "name": "Charmander",
		  "description": "Sou eu bola de fogo",
		  "type": "fire",
		  "attack": 123,
		  "height": 0.5,
		  "moves": [
		    "investida",
		    "desvio"
		  ]
		}

	```


## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
	```js
		var query = {}
		var mod = {$push : {moves : 'desvio'}}
		var opt = {multi : true}

		db.pokemons.update(query, mod, opt)

		Updated 9 existing record(s) in 2ms
		WriteResult({
			"nMatched": 9,
			"nUpserted": 0,
			"nModified": 9
		})
	```


## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
	```js
		var query = {name : /AindaNaoExisteMon/i}
		var mod = {$setOnInsert : {
	 		 'name' : 'AindaNaoExisteMon'
			,'description' : 'Sem maiores informações'
			,'type' : null
			,'attack' : null
			,'height' : null
			,'moves'  : []
		}}
		var opt = {upsert : true}

		db.pokemons.update(query, mod, opt)
		
		WriteResult({
			"nMatched": 0,
			"nUpserted": 1,
			"nModified": 0,
			"_id": ObjectId("5654c11710c42b67840bd89d")
		})	

		{
			"_id": ObjectId("5654c11710c42b67840bd89d"),
			"name": "AindaNaoExisteMon",
			"description": "Sem maiores informações",
			"type": null,
			"attack": null,
			"height": null,
			"moves": [ ]
		}

	```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
	```js
		var query = {moves : {$in : [/investida/i, /bola de fogo/i]}}

		db.pokemons.find(query)

		{
		  "_id": ObjectId("5643f4dd403adc69105a1ed2"),
		  "name": "Charizard",
		  "description": "fogo++",
		  "type": "fire",
		  "attack": 84,
		  "height": 17,
		  "moves": [
		    "desvio",
		    "bola de fogo"
		  ]
		}
		{
		  "_id": ObjectId("5653dca1415e21582441090e"),
		  "name": "Pikachu",
		  "description": "Ratinho",
		  "type": "eletric",
		  "attack": 55,
		  "height": 4,
		  "moves": [
		    "investida",
		    "desvio",
		    "choque do trovao"
		  ]
		}
		{
		  "_id": ObjectId("5653dca6415e21582441090f"),
		  "name": "Squirtle",
		  "description": "aguinha",
		  "type": "water",
		  "attack": 48,
		  "height": 5,
		  "moves": [
		    "investida",
		    "desvio"
		  ]
		}
		{
		  "_id": ObjectId("5653dcaa415e215824410910"),
		  "name": "Bulbasaur",
		  "description": "Chicote",
		  "type": "grass",
		  "attack": 49,
		  "height": 7,
		  "moves": [
		    "investida",
		    "desvio"
		  ]
		}
		{
		  "_id": ObjectId("5654b3a5f2014feb151bc27e"),
		  "name": "Charmander",
		  "description": "Sou eu bola de fogo",
		  "type": "fire",
		  "attack": 123,
		  "height": 0.5,
		  "moves": [
		    "investida",
		    "desvio"
		  ]
		}
	```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
	```js
		var query = {moves : {$all : [/investida/i, /choque do trovao/i]}}

		db.pokemons.find(query)

		{
		  "_id": ObjectId("5653dca1415e21582441090e"),
		  "name": "Pikachu",
		  "description": "Ratinho",
		  "type": "eletric",
		  "attack": 55,
		  "height": 4,
		  "moves": [
		    "investida",
		    "desvio",
		    "choque do trovao"
		  ]
		}
	```
	
## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
	```js
		var query = {type : {$not : /eletric/i}}

		db.pokemons.find(query)

		{
		  "_id": ObjectId("5643f4dd403adc69105a1ed2"),
		  "name": "Charizard",
		  "description": "fogo++",
		  "type": "fire",
		  "attack": 84,
		  "height": 17,
		  "moves": [
		    "desvio",
		    "bola de fogo"
		  ],
		  "defense": 15
		}
		{
		  "_id": ObjectId("5643f54a403adc69105a1ed3"),
		  "name": "Charmeleon",
		  "description": "sorta -fogo",
		  "type": "fire",
		  "attack": 64,
		  "height": 11,
		  "moves": [
		    "desvio"
		  ],
		  "defense": 40
		}
		{
		  "_id": ObjectId("5643f5ac403adc69105a1ed4"),
		  "name": "Pidgeot",
		  "description": "nois q voa",
		  "type": "normal",
		  "attack": 80,
		  "height": 15,
		  "moves": [
		    "desvio"
		  ],
		  "defense": 28
		}
		{
		  "_id": ObjectId("5643f631403adc69105a1ed6"),
		  "name": "Kakuna",
		  "description": "Pele de pedra",
		  "type": "Bug",
		  "attack": 25,
		  "height": 6,
		  "moves": [
		    "desvio"
		  ],
		  "defense": 28
		}
		{
		  "_id": ObjectId("5653dca6415e21582441090f"),
		  "name": "Squirtle",
		  "description": "aguinha",
		  "type": "water",
		  "attack": 48,
		  "height": 5,
		  "moves": [
		    "investida",
		    "desvio"
		  ],
		  "defense": 61
		}
		{
		  "_id": ObjectId("5653dcaa415e215824410910"),
		  "name": "Bulbasaur",
		  "description": "Chicote",
		  "type": "grass",
		  "attack": 49,
		  "height": 7,
		  "moves": [
		    "investida",
		    "desvio"
		  ],
		  "defense": 15
		}
		{
		  "_id": ObjectId("5654b3a5f2014feb151bc27e"),
		  "name": "Charmander",
		  "description": "Sou eu bola de fogo",
		  "type": "fire",
		  "attack": 123,
		  "height": 0.5,
		  "moves": [
		    "investida",
		    "desvio"
		  ],
		  "defense": 41
		}
		{
		  "_id": ObjectId("5643f600403adc69105a1ed5"),
		  "name": "Meowth",
		  "description": "Mia",
		  "type": "normal",
		  "attack": 45,
		  "height": 4,
		  "moves": [
		    "desvio"
		  ],
		  "defense": 40
		}
		{
		  "_id": ObjectId("5654c11710c42b67840bd89d"),
		  "name": "AindaNaoExisteMon",
		  "description": "Sem maiores informações",
		  "type": null,
		  "attack": null,
		  "height": null,
		  "moves": [ ],
		  "defense": 66
		}
	```


## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
	```js
		var query = {$and : [{moves : {$in : [/investida/i]}}, {defense : {$not : {$lte : 49}}}]}

		db.pokemons.find(query)

		{
		  "_id": ObjectId("5653dca6415e21582441090f"),
		  "name": "Squirtle",
		  "description": "aguinha",
		  "type": "water",
		  "attack": 48,
		  "height": 5,
		  "moves": [
		    "investida",
		    "desvio"
		  ],
		  "defense": 61
		}
	```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
	```js
		var query = {$and : [{type : /water/i}, {attack : {$lt : 50}}]}

		WriteResult({
			"nRemoved": 1
		})
	```

## Diferença entre **$ne** e **$not**.
	
	```
		$not : faz um não logico para uma operação expecifica e seleciona os documentos que não combina com a expressão

		Exemplo

		db.pokemons.find({height: { $not : {$lt : 5}}})

		A query vai selecionar os pokemons aonde a altura é maior que 5.
	```
	```
		$ne : seleciona os documentos aonde o valor do campo é diferente de um valor expecifico.
		
		Exemplo
		
		db.pokemons.find({attack : {$ne : 30}})
		
		A query vai listar todos pokemons no qual o attack não é igual a 30.
	```