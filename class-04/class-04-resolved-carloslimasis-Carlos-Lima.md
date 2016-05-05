## 1. Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> var query = {$or: [{name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbassauro/i}, {name: /charmander/i}]}
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> query
	{
	  "$or": [
	    {
	      "name": /pikachu/i
	    },
	    {
	      "name": /squirtle/i
	    },
	    {
	      "name": /bulbassauro/i
	    },
	    {
	      "name": /charmander/i
	    }
	  ]
	}
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> var mod = {$pushAll: {moves: ['absorver', 'contra-ataque']}}
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> mod
	{
	  "$pushAll": {
	    "moves": [
	      "absorver",
	      "contra-ataque"
	    ]
	  }
	}
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> var options = {multi: true}
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> options
	{
	  "multi": true
	}
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> db.pokemons.update(query, mod, options)
	Updated 4 existing record(s) in 80ms
	WriteResult({
	  "nMatched": 4,
	  "nUpserted": 0,
	  "nModified": 4
	})
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> db.pokemons.find(query)
	{
	  "_id": ObjectId("5651dd01892990c38151dcbf"),
	  "name": "Charmander",
	  "description": "Dragão de fogo",
	  "type": "fire",
	  "attack": 39,
	  "height": 0.9,
	  "defense": 31,
	  "moves": [
	    "lança chamas",
	    "investida",
	    "absorver",
	    "contra-ataque"
	  ]
	}
	{
	  "_id": ObjectId("56509f78d99344afbbfaae77"),
	  "name": "Bulbassauro",
	  "description": "Dinossauro muito louco",
	  "type": "grama",
	  "attack": 0.5,
	  "height": 0.3,
	  "defense": 25,
	  "active": false,
	  "moves": [
	    "folha navalha",
	    "investida",
	    "absorver",
	    "contra-ataque"
	  ]
	}
	{
	  "_id": ObjectId("5651d578892990c38151dcbd"),
	  "name": "Pikachu",
	  "description": "Carinha que da choque",
	  "type": "eletric",
	  "attack": 40,
	  "height": 0.8,
	  "defense": 35,
	  "active": false,
	  "moves": [
	    "choque do trovão",
	    "investida",
	    "absorver",
	    "contra-ataque"
	  ]
	}
	{
	  "_id": ObjectId("5651d5ce892990c38151dcbe"),
	  "name": "Squirtle",
	  "description": "Tartaruguinha da hora",
	  "type": "aquatic",
	  "attack": 38,
	  "height": 0.8,
	  "defense": 30,
	  "active": false,
	  "moves": [
	    "hidro bomba",
	    "investida",
	    "absorver",
	    "contra-ataque"
	  ]
	}
	Fetched 4 record(s) in 122ms
```

## 2. Adicionar 1 movimento em todos os pokemons: desvio.
```
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> var query = {}
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> query
	{
	  
	}
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> var mod = {$push: {moves: "desvio"}}
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> mod
	{
	  "$push": {
	    "moves": "desvio"
	  }
	}
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> var options = {multi: true}
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> options
	{
	  "multi": true
	}
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> db.pokemons.update(query, mod, options)
	Updated 11 existing record(s) in 62ms
	WriteResult({
	  "nMatched": 11,
	  "nUpserted": 0,
	  "nModified": 11
	})
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> db.pokemons.find(query)
	{
	  "_id": ObjectId("564524fe6f18e1ae072759f5"),
	  "name": "Rattata",
	  "description": "Roedor pequeno mas cabuloso",
	  "type": "Roedor",
	  "attack": 25,
	  "height": 0.3,
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("564525c96f18e1ae072759f6"),
	  "name": "Oddish",
	  "description": "Plantinha engraçada",
	  "type": "Planta",
	  "attack": 30,
	  "height": 0.5,
	  "defense": 10,
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("564526226f18e1ae072759f7"),
	  "name": "Meowth",
	  "description": "Gato feioso",
	  "type": "Animal",
	  "attack": 20,
	  "height": 0.4,
	  "defense": 20,
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("564526536f18e1ae072759f8"),
	  "name": "Psyduck",
	  "description": "Pato meio louco",
	  "type": "Pato",
	  "attack": 30,
	  "height": 0.8,
	  "defense": 20,
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("564526986f18e1ae072759f9"),
	  "name": "Arcanine",
	  "description": "Cachorro ficou calminho",
	  "type": "Cachorro de fogo",
	  "attack": 60,
	  "height": 1.9,
	  "defense": 40,
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("56510357d99344afbbfaae78"),
	  "description": "Pokemon de teste",
	  "name": "Testemon",
	  "attack": 8001,
	  "defense": 8000,
	  "moves": [
	    "investida",
	    "desvio"
	  ],
	  "active": false
	}
	{
	  "_id": ObjectId("5651d6aefce9e122256ddeb0"),
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("56509f78d99344afbbfaae77"),
	  "name": "Bulbassauro",
	  "description": "Dinossauro muito louco",
	  "type": "grama",
	  "attack": 0.5,
	  "height": 0.3,
	  "defense": 25,
	  "active": false,
	  "moves": [
	    "folha navalha",
	    "investida",
	    "absorver",
	    "contra-ataque",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("5651d578892990c38151dcbd"),
	  "name": "Pikachu",
	  "description": "Carinha que da choque",
	  "type": "eletric",
	  "attack": 40,
	  "height": 0.8,
	  "defense": 35,
	  "active": false,
	  "moves": [
	    "choque do trovão",
	    "investida",
	    "absorver",
	    "contra-ataque",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("5651d5ce892990c38151dcbe"),
	  "name": "Squirtle",
	  "description": "Tartaruguinha da hora",
	  "type": "aquatic",
	  "attack": 38,
	  "height": 0.8,
	  "defense": 30,
	  "active": false,
	  "moves": [
	    "hidro bomba",
	    "investida",
	    "absorver",
	    "contra-ataque",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("5651dd01892990c38151dcbf"),
	  "name": "Charmander",
	  "description": "Dragão de fogo",
	  "type": "fire",
	  "attack": 39,
	  "height": 0.9,
	  "defense": 31,
	  "moves": [
	    "lança chamas",
	    "investida",
	    "absorver",
	    "contra-ataque",
	    "desvio"
	  ]
	}
	Fetched 11 record(s) in 9ms
```

## 3. Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".
```
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> var query = {name: /AindaNaoExisteMon/i}
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> query
	{
	  "name": /AindaNaoExisteMon/i
	}
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> var mod = {$set: { "name": "AindaNaoExisteMon", "description": "Sem maiores informações", "type": null, "attack": null, "height": null, "active": null, "moves": null}}
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> mod
	{
	  "$set": {
	    "name": "AindaNaoExisteMon",
	    "description": "Sem maiores informações",
	    "type": null,
	    "attack": null,
	    "height": null,
	    "active": null,
	    "moves": null
	  }
	}
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> var options = {upsert: true}
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> options
	{
	  "upsert": true
	}
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> db.pokemons.update(query, mod, options)
	Updated 1 new record(s) in 540ms
	WriteResult({
	  "nMatched": 0,
	  "nUpserted": 1,
	  "nModified": 0,
	  "_id": ObjectId("5651f658fce9e122256ddeb2")
	})
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> db.pokemons.find(query)
	{
	  "_id": ObjectId("5651f658fce9e122256ddeb2"),
	  "name": "AindaNaoExisteMon",
	  "description": "Sem maiores informações",
	  "type": null,
	  "attack": null,
	  "height": null,
	  "active": null,
	  "moves": null
	}
	Fetched 1 record(s) in 46ms
```

## 4. Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.

```
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> var query = {moves: {$in: [/investida/i, /absorver/i]}, name: /charmander/i}
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> query
	{
	  "moves": {
	    "$in": [
	      /investida/i,
	      /absorver/i
	    ]
	  },
	  "name": /charmander/i
	}
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> db.pokemons.find(query)
	{
	  "_id": ObjectId("5651dd01892990c38151dcbf"),
	  "name": "Charmander",
	  "description": "Dragão de fogo",
	  "type": "fire",
	  "attack": 39,
	  "height": 0.9,
	  "defense": 31,
	  "moves": [
	    "lança chamas",
	    "investida",
	    "absorver",
	    "contra-ataque",
	    "desvio"
	  ]
	}
	Fetched 1 record(s) in 1ms
```

## 5. Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> var query = {moves: {$in: [/contra-ataque/i, /absorver/i]}, name: /charmander/i}
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> query
	{
	  "moves": {
	    "$in": [
	      /contra-ataque/i,
	      /absorver/i
	    ]
	  },
	  "name": /charmander/i
	}
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> db.pokemons.find(query)
	{
	  "_id": ObjectId("5651dd01892990c38151dcbf"),
	  "name": "Charmander",
	  "description": "Dragão de fogo",
	  "type": "fire",
	  "attack": 39,
	  "height": 0.9,
	  "defense": 31,
	  "moves": [
	    "lança chamas",
	    "investida",
	    "absorver",
	    "contra-ataque",
	    "desvio"
	  ]
	}
	Fetched 1 record(s) in 3ms
```

## 6. Pesquisar todos os pokemons que não são do tipo elétrico.

```
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> var query = {type: /eletric/i}
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> query
	{
	  "type": /eletric/i
	}
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> db.pokemons.find(query)
	{
	  "_id": ObjectId("5651d578892990c38151dcbd"),
	  "name": "Pikachu",
	  "description": "Carinha que da choque",
	  "type": "eletric",
	  "attack": 40,
	  "height": 0.8,
	  "defense": 35,
	  "active": false,
	  "moves": [
	    "choque do trovão",
	    "investida",
	    "absorver",
	    "contra-ataque",
	    "desvio"
	  ]
	}
	Fetched 1 record(s) in 2ms
```

## 7. Pesquisar todos os pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49.

```
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> var query = {moves: {$in: [/investida/i]},  defense: {$not: {$lte: 49}}}
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> query
	{
	  "moves": {
	    "$in": [
	      /investida/i
	    ]
	  },
	  "defense": {
	    "$not": {
	      "$lte": 49
	    }
	  }
	}
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> db.pokemons.find(query)
	{
	  "_id": ObjectId("564524fe6f18e1ae072759f5"),
	  "name": "Rattata",
	  "description": "Roedor pequeno mas cabuloso",
	  "type": "Roedor",
	  "attack": 25,
	  "height": 0.3,
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("56510357d99344afbbfaae78"),
	  "description": "Pokemon de teste",
	  "name": "Testemon",
	  "attack": 8001,
	  "defense": 8000,
	  "moves": [
	    "investida",
	    "desvio"
	  ],
	  "active": false
	}
	{
	  "_id": ObjectId("5651d6aefce9e122256ddeb0"),
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	Fetched 3 record(s) in 2ms
```

## 8. Remova todos os pokemons do tipo água e com attack menor que 50.

```
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> var query = {$and: [{type: /aquatic/i}, {attack: {$lt: 50}}]}
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> query
	{
	  "$and": [
	    {
	      "type": /aquatic/i
	    },
	    {
	      "attack": {
	        "$lt": 50
	      }
	    }
	  ]
	}
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> db.pokemons.find(query)
	{
	  "_id": ObjectId("5651d5ce892990c38151dcbe"),
	  "name": "Squirtle",
	  "description": "Tartaruguinha da hora",
	  "type": "aquatic",
	  "attack": 38,
	  "height": 0.8,
	  "defense": 30,
	  "active": false,
	  "moves": [
	    "hidro bomba",
	    "investida",
	    "absorver",
	    "contra-ataque",
	    "desvio"
	  ]
	}
	Fetched 1 record(s) in 29ms
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> db.pokemons.remove(query)
	Removed 1 record(s) in 367ms
	WriteResult({
	  "nRemoved": 1
	})
	MacBook-de-Carlos(mongod-3.0.5) be-mean-pokemon> db.pokemons.find(query)
	Fetched 0 record(s) in 1ms
```

## 9. Esse item não está no vídeo e se você fizer significa que você lê as coisas, nesse exercício demonstre qual a diferença entre os operadores $ne e $not.

```
	Quando utilizamos o valor $ne em um query recebemos como resultado somente registros que possuem
	o campo que está sendo validado na query.

	Quanto ao operador $not quando utilizado em uma query recebemos como resultado tanto os registros 
	que possuem o campo validado quanto os registros que não o possuem.