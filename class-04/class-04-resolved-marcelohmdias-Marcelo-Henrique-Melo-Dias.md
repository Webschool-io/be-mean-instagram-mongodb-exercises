# MongoDB - Aula 04 - Exercício

**autor**: Marcelo H M Dias

## 1. Adicionar dois ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```bash
MH-Note(mongod-3.0.7) pokemons> var query = {$or: [{name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbassauro/i}, {name: /charmander/i}]}
MH-Note(mongod-3.0.7) pokemons> var mod = {$pushAll: {moves: ["Ataque rápido", "Investida"]}}
MH-Note(mongod-3.0.7) pokemons> var opt = {multi: true}
MH-Note(mongod-3.0.7) pokemons> db.pokemons.update(query, mod, opt)
Updated 4 existing record(s) in 4ms
	WriteResult({
		"nMatched": 4,
		"nUpserted": 0,
		"nModified": 4
	})
MH-Note(mongod-3.0.7) pokemons> 
```

## 2. Adicionar um movimento em todos os pokemons: 'Desvio'.

```bash
MH-Note(mongod-3.0.7) pokemons> var query = {}
MH-Note(mongod-3.0.7) pokemons> var mod = {$push: {moves: "Desvio"}}
MH-Note(mongod-3.0.7) pokemons> var opt = {multi: true}
MH-Note(mongod-3.0.7) pokemons> db.pokemons.update(query, mod, opt)
Updated 5 existing record(s) in 0ms
WriteResult({
  "nMatched": 5,
  "nUpserted": 0,
  "nModified": 5
})
MH-Note(mongod-3.0.7) pokemons>
```

## 3. Adicionar o pokemon 'AindaNaoExisteMon', caso ele ainda não exista com todos os dados com o valor `null` e a descrição `"Sem maiores informações"`.

```bash
MH-Note(mongod-3.0.7) pokemons> var query = {name: /AindaNaoExisteMon/i}
MH-Note(mongod-3.0.7) pokemons> var mod = {$setOnInsert: {name: "AindaNaoExisteMon", attack: null, height: null, defense: null, moves: [], description: "Sem maiores informações"}}
MH-Note(mongod-3.0.7) pokemons> var opt = {upsert: true}
MH-Note(mongod-3.0.7) pokemons> db.pokemons.update(query, mod, opt)
Updated 1 new record(s) in 1ms
	WriteResult({
		"nMatched": 0,
		"nUpserted": 1,
		"nModified": 0,
		"_id": ObjectId("5652322cf6382d18e1522297")
	})
MH-Note(mongod-3.0.7) pokemons>
```

## 4. Pesquisar todos os pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.

```bash
MH-Note(mongod-3.0.7) pokemons> var query = {moves: {$in: ["Investida", "Folha Navalha"]}}
MH-Note(mongod-3.0.7) pokemons> db.pokemons.find(query)
	{
		"_id": ObjectId("56522ee2b77e99268925b1b4"),
		"name": "Pikachu",
		"description": "Rato elétrico bem fofinho",
		"type": "electric",
		"attack": 55,
		"height": 0.4,
		"moves": [
			"Ataque rápido",
			"Investida",
			"Desvio"
		]
	}
	{
		"_id": ObjectId("56522ee2b77e99268925b1b6"),
		"name": "Charmander",
		"description": "Esse é o cão chupando manga de fofinho",
		"type": "fogo",
		"attack": 52,
		"height": 0.6,
		"moves": [
			"Ataque rápido",
			"Investida",
			"Desvio"
		]
	}
	{
		"_id": ObjectId("56522ee2b77e99268925b1b7"),
		"name": "Squirtle",
		"description": "Ejeta água que passarinho não bebe",
		"type": "água",
		"attack": 48,
		"height": 0.5,
		"moves": [
			"Ataque rápido",
			"Investida",
			"Desvio"
		]
	}
	{
		"_id": ObjectId("56522ee2b77e99268925b1b5"),
		"name": "Bulbassauro",
		"description": "Chicote de trepadeira",
		"type": "grama",
		"attack": 49,
		"height": 0.4,
		"moves": [
			"Ataque rápido",
			"Investida",
			"Desvio",
			"Chicote de cipó",
			"Folha Navalha"
		]
	}
Fetched 4 record(s) in 1ms
MH-Note(mongod-3.0.7) pokemons>
```

## 5. Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha se pokemon favorito.

```bash
MH-Note(mongod-3.0.7) pokemons> var query = {moves: {$in: ["Folha Navalha"]}}
MH-Note(mongod-3.0.7) pokemons> db.pokemons.find(query)
	{
		"_id": ObjectId("56522ee2b77e99268925b1b5"),
		"name": "Bulbassauro",
		"description": "Chicote de trepadeira",
		"type": "grama",
		"attack": 49,
		"height": 0.4,
		"moves": [
			"Ataque rápido",
			"Investida",
			"Desvio",
			"Chicote de cipó",
			"Folha Navalha"
		]
	}
Fetched 1 record(s) in 1ms
MH-Note(mongod-3.0.7) pokemons>
```

## 6. Pesquisar todos os pokemons que não são do tipo 'elétrico'.

```bash
MH-Note(mongod-3.0.7) pokemons> var query = {type: {$nin: [/electric/i]}}
MH-Note(mongod-3.0.7) pokemons> db.pokemons.find(query)
	{
		"_id": ObjectId("56522ee2b77e99268925b1b6"),
		"name": "Charmander",
		"description": "Esse é o cão chupando manga de fofinho",
		"type": "fogo",
		"attack": 52,
		"height": 0.6,
		"moves": [
			"Ataque rápido",
			"Investida",
			"Desvio"
		]
	}
	{
		"_id": ObjectId("56522ee2b77e99268925b1b7"),
		"name": "Squirtle",
		"description": "Ejeta água que passarinho não bebe",
		"type": "água",
		"attack": 48,
		"height": 0.5,
		"moves": [
			"Ataque rápido",
			"Investida",
			"Desvio"
		]
	}
	{
		"_id": ObjectId("56522f1bb77e99268925b1b9"),
		"name": "Caterpie",
		"description": "Larva lutadora",
		"type": "inseto",
		"attack": 30,
		"height": 0.3,
		"moves": [
			"Desvio"
		]
	}
	{
		"_id": ObjectId("5652322cf6382d18e1522297"),
		"name": "AindaNaoExisteMon",
		"attack": null,
		"height": null,
		"defense": null,
		"moves": [ ],
		"description": "Sem maiores informações"
	}
	{
		"_id": ObjectId("56522ee2b77e99268925b1b5"),
		"name": "Bulbassauro",
		"description": "Chicote de trepadeira",
		"type": "grama",
		"attack": 49,
		"height": 0.4,
		"moves": [
			"Ataque rápido",
			"Investida",
			"Desvio",
			"Chicote de cipó",
			"Folha Navalha"
		]
	}
	Fetched 5 record(s) in 2ms
MH-Note(mongod-3.0.7) pokemons> 
```

## 7. Pesquisar todos os pokemons que tenham o ataque `investida` e tenham defesa não menor ou igual a 49.

```bash
MH-Note(mongod-3.0.7) pokemons> var valueOne = {moves: {$in: [/investida/i]}}
MH-Note(mongod-3.0.7) pokemons> var valueTwo = {defense: {$not: {$lte: 49}}}
MH-Note(mongod-3.0.7) pokemons> var query = {$and: [valueOne, valueTwo]}
MH-Note(mongod-3.0.7) pokemons> db.pokemons.find(query)
	{
		"_id": ObjectId("56522ee2b77e99268925b1b4"),
		"name": "Pikachu",
		"description": "Rato elétrico bem fofinho",
		"type": "electric",
		"attack": 55,
		"height": 0.4,
		"moves": [
			"Ataque rápido",
			"Investida",
			"Desvio"
		]
	}
	{
		"_id": ObjectId("56522ee2b77e99268925b1b6"),
		"name": "Charmander",
		"description": "Esse é o cão chupando manga de fofinho",
		"type": "fogo",
		"attack": 52,
		"height": 0.6,
		"moves": [
			"Ataque rápido",
			"Investida",
			"Desvio"
		]
	}
	{
		"_id": ObjectId("56522ee2b77e99268925b1b7"),
		"name": "Squirtle",
		"description": "Ejeta água que passarinho não bebe",
		"type": "água",
		"attack": 48,
		"height": 0.5,
		"moves": [
			"Ataque rápido",
			"Investida",
			"Desvio"
		]
	}
	{
		"_id": ObjectId("56522ee2b77e99268925b1b5"),
		"name": "Bulbassauro",
		"description": "Chicote de trepadeira",
		"type": "grama",
		"attack": 49,
		"height": 0.4,
		"moves": [
			"Ataque rápido",
			"Investida",
			"Desvio",
			"Chicote de cipó",
			"Folha Navalha"
		]
	}
	Fetched 4 record(s) in 1ms
MH-Note(mongod-3.0.7) pokemons>
```

## 8. Remova todos os pokemons do tipo `água` e com attack menor que 50.

```bash
MH-Note(mongod-3.0.7) pokemons> var valueOne = {type: "água"}
MH-Note(mongod-3.0.7) pokemons> var valueTwo = {attack: {$lt: 50}}
MH-Note(mongod-3.0.7) pokemons> var query = {$and: [valueOne, valueTwo]}
MH-Note(mongod-3.0.7) pokemons> db.pokemons.remove(query)
	Removed 1 record(s) in 2ms
	WriteResult({
		"nRemoved": 1
	})
MH-Note(mongod-3.0.7) pokemons>
```