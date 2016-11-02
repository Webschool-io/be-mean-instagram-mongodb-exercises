# MongoDB - Aula 04 - Exercício
autor: Tiago Amaral

## Exercício

1. **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

	```
	var query = {$or:[{name:/pikachu/i},{name:/bulbassauro/i},{name:/squirtle/i},{name:/charmander/i}]}
	var attacks = ['esquiva','concentrar']
	var options = {multi:true}
	var mod = {$pushAll:{moves:attacks}}
	
	db.pokemons.update(query,mod,options)
	
	Updated 5 existing record(s) in 5ms
	WriteResult({
	  "nMatched": 5,
	  "nUpserted": 0,
	  "nModified": 5
	})

	```


2. **Adicionar** 1 movimento em todos os pokemons: `desvio`.
	```
	var options = {multi:true}
	var mod = {$push:{moves:'desvio'}}
	db.pokemons.update({},mod,options)
	
	Updated 15 existing record(s) in 4ms
	WriteResult({
	  "nMatched": 15,
	  "nUpserted": 0,
	  "nModified": 15
	})

	```

3. **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".
	```
	var query = {name:/AindaNaoExisteMon/i}
	var mod = {
		$set:{active:true},
		$setOnInsert: {name: 'AindaNaoExisteMon',attack: null,defense: null,height: null,description: "Sem maiores informações"}
	}
	var options = {upsert:true}

	db.pokemons.update(query,mod,options)

	Updated 1 new record(s) in 3ms
	WriteResult({
	  "nMatched": 0,
	  "nUpserted": 1,
	  "nModified": 0,
	  "_id": ObjectId("58154d3501f1e1e26e9e2d2a")
	})

	```


4. Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.
	```
	var attacks = {$or:[{moves: {$in:['investida']}},{name:/sandshrew/i}]}
	db.pokemons.find(attacks)

	{
	  "_id": ObjectId("580961ba3ec41a29daaf3198"),
	  "name": "Charmander",
	  "description": "Esse é o cão chupando manga de fofinho",
	  "type": "fogo",
	  "attack": 52,
	  "height": 0.6,
	  "active": false,
	  "moves": [
	    "investida",
	    "esquiva",
	    "concentrar",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("580965e23ec41a29daaf3199"),
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
	  "_id": ObjectId("580965fc3ec41a29daaf319a"),
	  "name": "Caterpie",
	  "description": "Larva lutadora",
	  "type": "inseto",
	  "attack": 30,
	  "height": 0.3,
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("581297bfa30814a771543a89"),
	  "name": "Sandshrew",
	  "description": "tatu lutador",
	  "attack": 40,
	  "defense": 40,
	  "height": 0.6,
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("581297c7a30814a771543a8a"),
	  "name": "Clefairy",
	  "description": "fada lutadora",
	  "attack": 20,
	  "defense": 20,
	  "height": 0.6,
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("581297d5a30814a771543a8b"),
	  "name": "Clefairy",
	  "description": "fada lutadora",
	  "attack": 20,
	  "defense": 20,
	  "height": 0.6,
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("581297dea30814a771543a8c"),
	  "name": "Abra",
	  "description": "dorminhoco teletransportador",
	  "attack": 10,
	  "defense": 10,
	  "height": 0.9,
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("581297e9a30814a771543a8d"),
	  "name": "Tentacool",
	  "description": "polvo lutador",
	  "attack": 20,
	  "defense": 20,
	  "height": 0.9,
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("58129fee93b6d544ef2d3fc1"),
	  "description": "Pokemon de teste",
	  "name": "Testemon",
	  "attack": 8091,
	  "defense": 8000,
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("5813f39bec94d0b964a48807"),
	  "active": false,
	  "name": "NaoExisteMon",
	  "attack": null,
	  "defense": null,
	  "height": null,
	  "description": "Sem maiores informações",
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("5813f198ec94d0b964a48805"),
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("580961423ec41a29daaf3195"),
	  "name": "Pikachu",
	  "description": "Rato elétrico bem fofinho",
	  "type": "electric",
	  "attack": 55,
	  "height": 0.4,
	  "moves": [
	    "investida",
	    "choque do trovão",
	    "esquiva",
	    "concentrar",
	    "desvio"
	  ],
	  "active": false
	}
	{
	  "_id": ObjectId("580961923ec41a29daaf3196"),
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
	    "concentrar",
	    "esquiva",
	    "concentrar",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("580961a73ec41a29daaf3197"),
	  "name": "Charmander",
	  "description": "Esse é o cão chupando manga de fofinho",
	  "type": "fogo",
	  "attack": 52,
	  "height": 0.6,
	  "active": false,
	  "moves": [
	    "investida",
	    "lança-chamas",
	    "esquiva",
	    "concentrar",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("5813f29d3c98249f27d4b39a"),
	  "name": "Squirtle",
	  "description": "Ejeta água que passarinho não bebe",
	  "type": "água",
	  "attack": 48,
	  "height": 0.5,
	  "active": false,
	  "moves": [
	    "investida",
	    "hidro bomba",
	    "esquiva",
	    "concentrar",
	    "desvio"
	  ]
	}
	Fetched 15 record(s) in 12ms

	```

5. Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.
	```
	var attacks = {moves: {$all:['esquiva','concentrar']}} 
	db.pokemons.find(query)
	{
	  "_id": ObjectId("580961ba3ec41a29daaf3198"),
	  "name": "Charmander",
	  "description": "Esse é o cão chupando manga de fofinho",
	  "type": "fogo",
	  "attack": 52,
	  "height": 0.6,
	  "active": false,
	  "moves": [
	    "investida",
	    "esquiva",
	    "concentrar",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("580961423ec41a29daaf3195"),
	  "name": "Pikachu",
	  "description": "Rato elétrico bem fofinho",
	  "type": "electric",
	  "attack": 55,
	  "height": 0.4,
	  "moves": [
	    "investida",
	    "choque do trovão",
	    "esquiva",
	    "concentrar",
	    "desvio"
	  ],
	  "active": false
	}
	{
	  "_id": ObjectId("580961923ec41a29daaf3196"),
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
	    "concentrar",
	    "esquiva",
	    "concentrar",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("580961a73ec41a29daaf3197"),
	  "name": "Charmander",
	  "description": "Esse é o cão chupando manga de fofinho",
	  "type": "fogo",
	  "attack": 52,
	  "height": 0.6,
	  "active": false,
	  "moves": [
	    "investida",
	    "lança-chamas",
	    "esquiva",
	    "concentrar",
	    "desvio"
	  ]
	}
	Fetched 4 record(s) in 5ms
	```

6. Pesquisar **todos** os pokemons que não são do tipo `elétrico`.
	```
	var query = {type:{$ne:'electric'}}
	db.pokemons.find(query)

	{
	  "_id": ObjectId("580961ba3ec41a29daaf3198"),
	  "name": "Charmander",
	  "description": "Esse é o cão chupando manga de fofinho",
	  "type": "fogo",
	  "attack": 52,
	  "height": 0.6,
	  "active": false,
	  "moves": [
	    "investida",
	    "esquiva",
	    "concentrar",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("580965e23ec41a29daaf3199"),
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
	  "_id": ObjectId("580965fc3ec41a29daaf319a"),
	  "name": "Caterpie",
	  "description": "Larva lutadora",
	  "type": "inseto",
	  "attack": 30,
	  "height": 0.3,
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("581297bfa30814a771543a89"),
	  "name": "Sandshrew",
	  "description": "tatu lutador",
	  "attack": 40,
	  "defense": 40,
	  "height": 0.6,
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("581297c7a30814a771543a8a"),
	  "name": "Clefairy",
	  "description": "fada lutadora",
	  "attack": 20,
	  "defense": 20,
	  "height": 0.6,
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("581297d5a30814a771543a8b"),
	  "name": "Clefairy",
	  "description": "fada lutadora",
	  "attack": 20,
	  "defense": 20,
	  "height": 0.6,
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("581297dea30814a771543a8c"),
	  "name": "Abra",
	  "description": "dorminhoco teletransportador",
	  "attack": 10,
	  "defense": 10,
	  "height": 0.9,
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("581297e9a30814a771543a8d"),
	  "name": "Tentacool",
	  "description": "polvo lutador",
	  "attack": 20,
	  "defense": 20,
	  "height": 0.9,
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("58129fee93b6d544ef2d3fc1"),
	  "description": "Pokemon de teste",
	  "name": "Testemon",
	  "attack": 8091,
	  "defense": 8000,
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("5813f39bec94d0b964a48807"),
	  "active": false,
	  "name": "NaoExisteMon",
	  "attack": null,
	  "defense": null,
	  "height": null,
	  "description": "Sem maiores informações",
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("5813f198ec94d0b964a48805"),
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("580961923ec41a29daaf3196"),
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
	    "concentrar",
	    "esquiva",
	    "concentrar",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("580961a73ec41a29daaf3197"),
	  "name": "Charmander",
	  "description": "Esse é o cão chupando manga de fofinho",
	  "type": "fogo",
	  "attack": 52,
	  "height": 0.6,
	  "active": false,
	  "moves": [
	    "investida",
	    "lança-chamas",
	    "esquiva",
	    "concentrar",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("5813f29d3c98249f27d4b39a"),
	  "name": "Squirtle",
	  "description": "Ejeta água que passarinho não bebe",
	  "type": "água",
	  "attack": 48,
	  "height": 0.5,
	  "active": false,
	  "moves": [
	    "investida",
	    "hidro bomba",
	    "esquiva",
	    "concentrar",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("58154d3501f1e1e26e9e2d2a"),
	  "active": true,
	  "name": "AindaNaoExisteMon",
	  "attack": null,
	  "defense": null,
	  "height": null,
	  "description": "Sem maiores informações"
	}
	Fetched 15 record(s) in 8ms


	```

7. Pesquisar **todos** pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.
	```
	var query1 = {moves:{$in:['investida']}}
	var query2 = {attack:{$not:{$lte: 49}}}
	var q1q2 = {$and:[query1,query2]}

	db.pokemons.find(q1q2)

	{
	  "_id": ObjectId("580961ba3ec41a29daaf3198"),
	  "name": "Charmander",
	  "description": "Esse é o cão chupando manga de fofinho",
	  "type": "fogo",
	  "attack": 52,
	  "height": 0.6,
	  "active": false,
	  "moves": [
	    "investida",
	    "esquiva",
	    "concentrar",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("58129fee93b6d544ef2d3fc1"),
	  "description": "Pokemon de teste",
	  "name": "Testemon",
	  "attack": 8091,
	  "defense": 8000,
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("5813f39bec94d0b964a48807"),
	  "active": false,
	  "name": "NaoExisteMon",
	  "attack": null,
	  "defense": null,
	  "height": null,
	  "description": "Sem maiores informações",
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("5813f198ec94d0b964a48805"),
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("580961423ec41a29daaf3195"),
	  "name": "Pikachu",
	  "description": "Rato elétrico bem fofinho",
	  "type": "electric",
	  "attack": 55,
	  "height": 0.4,
	  "moves": [
	    "investida",
	    "choque do trovão",
	    "esquiva",
	    "concentrar",
	    "desvio"
	  ],
	  "active": false
	}
	{
	  "_id": ObjectId("580961a73ec41a29daaf3197"),
	  "name": "Charmander",
	  "description": "Esse é o cão chupando manga de fofinho",
	  "type": "fogo",
	  "attack": 52,
	  "height": 0.6,
	  "active": false,
	  "moves": [
	    "investida",
	    "lança-chamas",
	    "esquiva",
	    "concentrar",
	    "desvio"
	  ]
	}
	Fetched 6 record(s) in 4ms
	```

8. Remova **todos** os pokemons do tipo água e com attack menor que 50.

	```
	var query1 = {type:'água'}
	var query2 = {attack: {$lte: 50}}
	var q1q2 = {$and:[query1,query2]}
	db.pokemons.remove(q1q2)

	Removed 1 record(s) in 4ms
	WriteResult({
	  "nRemoved": 1
	})

	```

9. Diferença entre os operadores ***$ne*** e ***$not***
	```
	$not: É o "não" lógico, aceita regex e retorna os documentos que não tenham esse valor (inclusive os que não tem o campo especificado).

	$ne: Retorna os documentos em que o valor 'não é igual' ao buscado, não aceita regex e retorna os documentos que não tenham esse valor (inclusive os que não tem o campo especificado).
	```