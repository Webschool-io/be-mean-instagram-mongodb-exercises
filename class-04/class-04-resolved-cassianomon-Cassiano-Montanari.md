# MongoDB - Aula 04 - Exercício
autor: Cassiano Montanari

## Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

	```
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> var query = {name: /pikachu/i}
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> var mod = {$pushAll:{moves:["estrela elétrica", "recarregar bateria"]}}
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> db.pokemons.update(query, mod)
	Updated 1 existing record(s) in 6ms
	WriteResult({
	  "nMatched": 1,
	  "nUpserted": 0,
	  "nModified": 1
	})

	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> var query = {name: /squirtle/i}
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> var mod = {$pushAll:{moves:["marreta de agua", "tartaruga giratoria"]}}
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> db.pokemons.update(query, mod)

	Updated 1 existing record(s) in 1ms
	WriteResult({
	  "nMatched": 1,
	  "nUpserted": 0,
	  "nModified": 1
	})

	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> var query = {name: /bulbassauro/i}
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> var mod = {$pushAll:{moves:["cipo infernal", "chicotada da zuera"]}}
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> db.pokemons.update(query, mod)

	Updated 1 existing record(s) in 1ms
	WriteResult({
	  "nMatched": 1,
	  "nUpserted": 0,
	  "nModified": 1
	})

	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> var query = {name: /charmander/i}
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> var mod = {$pushAll:{moves:["fogo fogoso", "fogo da zuera"]}}
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> db.pokemons.update(query, mod)

	Updated 1 existing record(s) in 2ms
	WriteResult({
	  "nMatched": 1,
	  "nUpserted": 0,
	  "nModified": 1
	})
	```

## Adicionar 1 movimento em todos os pokemons: `desvio`.##

	```
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> var query = {}
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> var mod = {$push:{moves: "desvio"}}
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> var opt = {multi: true}
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> db.pokemons.update(query, mod, opt)
	Updated 10 existing record(s) in 2ms
	WriteResult({
	  "nMatched": 10,
	  "nUpserted": 0,
	  "nModified": 10
	})
	```

## Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".

	```
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> var mod = {$setOnInsert: {name:"AindaNaoExisteMon", type: null, attack: null, defense: null, height: null, description: "Sem maiores informações"} }
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> var opt = {upsert: true}
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> db.pokemons.update(query, mod, opt)
	Updated 1 new record(s) in 1ms
	WriteResult({
	  "nMatched": 0,
	  "nUpserted": 1,
	  "nModified": 0,
	  "_id": ObjectId("575386717d2f955ffc32c9a3")
	})

	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> db.pokemons.find({"_id": ObjectId("575386717d2f955ffc32c9a3")})
	{
	  "_id": ObjectId("575386717d2f955ffc32c9a3"),
	  "name": "AindaNaoExisteMon",
	  "type": null,
	  "attack": null,
	  "defense": null,
	  "height": null,
	  "description": "Sem maiores informações"
	}
	Fetched 1 record(s) in 4ms
	```

## Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.;

	```
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> var query = {moves: {$in: [/investida/i, /tartaruga giratoria/i]}}
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("574e30544f5147bc1c639fbc"),
	  "name": "Cyndaquil",
	  "description": "Raposa humildona que tem fogo nas costas",
	  "type": "fire",
	  "attack": 30,
	  "height": 1.08,
	  "defense": 20,
	  "active": false,
	  "moves": [
	    "investida",
	    "rabada flamejante",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("574e30544f5147bc1c639fbd"),
	  "name": "Magnemite",
	  "description": "Imã maneiro",
	  "type": "Magnet",
	  "attack": 20,
	  "height": 1,
	  "defense": 30,
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("574e30544f5147bc1c639fbe"),
	  "name": "Chicorita",
	  "description": "Planta zueira",
	  "type": "plant",
	  "attack": 15,
	  "height": 1.4,
	  "defense": 20,
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("574e30544f5147bc1c639fbf"),
	  "name": "Squirtle",
	  "description": "Tartaruga ninja da agua",
	  "type": "water",
	  "attack": 25,
	  "height": 0.8,
	  "defense": 20,
	  "moves": [
	    "investida",
	    "marreta de agua",
	    "tartaruga giratoria",
	    "desvio"
	  ],
	  "active": false
	}
	{
	  "_id": ObjectId("574e30544f5147bc1c639fc0"),
	  "name": "Tortoise",
	  "description": "Tartaruga ninja da agua evoluída",
	  "type": "water",
	  "attack": 35,
	  "height": 1.4,
	  "defense": 40,
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("574f6990f15671948a439f25"),
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
	  "_id": ObjectId("5750e35af142efad454dff39"),
	  "active": false,
	  "name": "Monail",
	  "attack": null,
	  "defense": null,
	  "height": null,
	  "description": "Sem informações",
	  "moves": [
	    "investida",
	    "choque do trovão",
	    "desvio"
	  ]
	}
	Fetched 7 record(s) in 37ms
	```

## Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

	```
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> var query = {moves: {$all: [/choque do trovão/i, /investida/i]}}
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("5750e35af142efad454dff39"),
	  "active": false,
	  "name": "Monail",
	  "attack": null,
	  "defense": null,
	  "height": null,
	  "description": "Sem informações",
	  "moves": [
	    "investida",
	    "choque do trovão",
	    "desvio"
	  ]
	}
	Fetched 1 record(s) in 5ms
	```
## Pesquisar todos os pokemons que não são do tipo elétrico.

	```
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> var query = {type: {$not: /eletric/i}}
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("574e30544f5147bc1c639fbc"),
	  "name": "Cyndaquil",
	  "description": "Raposa humildona que tem fogo nas costas",
	  "type": "fire",
	  "attack": 30,
	  "height": 1.08,
	  "defense": 20,
	  "active": false,
	  "moves": [
	    "investida",
	    "rabada flamejante",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("574e30544f5147bc1c639fbd"),
	  "name": "Magnemite",
	  "description": "Imã maneiro",
	  "type": "Magnet",
	  "attack": 20,
	  "height": 1,
	  "defense": 30,
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("574e30544f5147bc1c639fbe"),
	  "name": "Chicorita",
	  "description": "Planta zueira",
	  "type": "plant",
	  "attack": 15,
	  "height": 1.4,
	  "defense": 20,
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("574e30544f5147bc1c639fbf"),
	  "name": "Squirtle",
	  "description": "Tartaruga ninja da agua",
	  "type": "water",
	  "attack": 25,
	  "height": 0.8,
	  "defense": 20,
	  "moves": [
	    "investida",
	    "marreta de agua",
	    "tartaruga giratoria",
	    "desvio"
	  ],
	  "active": false
	}
	{
	  "_id": ObjectId("574e30544f5147bc1c639fc0"),
	  "name": "Tortoise",
	  "description": "Tartaruga ninja da agua evoluída",
	  "type": "water",
	  "attack": 35,
	  "height": 1.4,
	  "defense": 40,
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("574f6990f15671948a439f25"),
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
	  "_id": ObjectId("5750e35af142efad454dff39"),
	  "active": false,
	  "name": "Monail",
	  "attack": null,
	  "defense": null,
	  "height": null,
	  "description": "Sem informações",
	  "moves": [
	    "investida",
	    "choque do trovão",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("5753799c86840e2346768370"),
	  "name": "Charmander",
	  "Description": "Dragão de fogo foderoso",
	  "attack": 65,
	  "defense": 34,
	  "height": 1.7,
	  "type": "fire",
	  "moves": [
	    "fogo fogoso",
	    "fogo da zuera",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("575379d086840e2346768371"),
	  "name": "Bulbassauro",
	  "Description": "Tartarugão gigante de agua",
	  "attack": 55,
	  "defense": 66,
	  "height": 1.8,
	  "type": "water",
	  "moves": [
	    "cipo infernal",
	    "chicotada da zuera",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("575386717d2f955ffc32c9a3"),
	  "name": "AindaNaoExisteMon",
	  "type": null,
	  "attack": null,
	  "defense": null,
	  "height": null,
	  "description": "Sem maiores informações"
	}
	Fetched 10 record(s) in 51ms
	```

## Pesquisar todos pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49.

	```
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> var query = {$and: [{moves: {$in:['investida']}}, {defense:{$not: {$lte:49}}}]}
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("574f6990f15671948a439f25"),
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
	  "_id": ObjectId("5750e35af142efad454dff39"),
	  "active": false,
	  "name": "Monail",
	  "attack": null,
	  "defense": null,
	  "height": null,
	  "description": "Sem informações",
	  "moves": [
	    "investida",
	    "choque do trovão",
	    "desvio"
	  ]
	}
	Fetched 2 record(s) in 10ms
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons>
	```

## Remova todos os pokemons do tipo água e com attack menor que 50.

	```
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> var query = {$and: [{type: /water/i}, {attack: {$lt: 50}}]}
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> db.pokemons.remove(query)
	Removed 2 record(s) in 2ms
	WriteResult({
	  "nRemoved": 2
	})
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> var query = {$and: [{type: /water/i}, {attack: {$lt: 50}}]}
	VOSTRO(C:\MongoDB\bin\mongod.exe-3.2.6) be-mean-pokemons> db.pokemons.find(query)
	Fetched 0 record(s) in 1ms
	```

## Qual a diferença entre os operadores $ne e $not

	```
	$ne = not equal, ou seja, que não é igual, ao utilizar este operador ele irá trazer todas os objetos que não correspondem com a query em que o $ne está sendo utilizado.

	$not = que não é como se fosse o contrário do que estará pedindo, por exemplo:
	$ query = (quero sorvete)
	$ eu.query = (Eu quero sorvete);

	$ query = $not(quero sorvete)
	$ eu.query = (Eu não quero sorvete);
	```