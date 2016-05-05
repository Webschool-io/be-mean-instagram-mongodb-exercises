# MongoDB - Aula 04 - Exercício

autor: Matheus Costa de Paiva

## 1. **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
	levelho(mongod-3.0.7) be-mean-pokemons> var query = {name: /pikachu/i}
	levelho(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll: {moves:['esfera elétrica','trovãozada']}}
	levelho(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod)
	Updated 1 existing record(s) in 45ms
	WriteResult({
	  "nMatched": 1,
	  "nUpserted": 0,
	  "nModified": 1
	})
	levelho(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("566aeca93e6ceca410aa3152"),
	  "name": "Pikachu",
	  "description": "Rato elétrico",
	  "type": "electric",
	  "attack": 100,
	  "height": 0.4,
	  "active": false,
	  "moves": [
	    "esfera elétrica",
	    "trovãozada"
	  ]
	}
	Fetched 1 record(s) in 3ms
	levelho(mongod-3.0.7) be-mean-pokemons> var query = {name: /squirtle/i}
	levelho(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll: {moves:['aguinha do mal','aguinha do bem']}}
	levelho(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod)
	Updated 1 existing record(s) in 3ms
	WriteResult({
	  "nMatched": 1,
	  "nUpserted": 0,
	  "nModified": 1
	})
	levelho(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("566aed283e6ceca410aa3153"),
	  "name": "Squirtle",
	  "description": "Ejeta água que passarinho não bebe",
	  "type": "água",
	  "attack": 48,
	  "height": 0.5,
	  "active": false,
	  "moves": [
	    "aguinha do mal",
	    "aguinha do bem"
	  ]
	}
	Fetched 1 record(s) in 2ms
	levelho(mongod-3.0.7) be-mean-pokemons> var query = {name: /bulbassauro/i}
	levelho(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll: {moves:['boboataque','ataque de bulbice']}}
	levelho(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod)
	Updated 1 existing record(s) in 8ms
	WriteResult({
	  "nMatched": 1,
	  "nUpserted": 0,
	  "nModified": 1
	})
	levelho(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("566aed7a3e6ceca410aa3154"),
	  "name": "Bulbassauro",
	  "description": "Chicote de trepadeira",
	  "type": "grama",
	  "attack": 49,
	  "height": 0.4,
	  "active": false,
	  "moves": [
	    "boboataque",
	    "ataque de bulbice"
	  ]
	}
	Fetched 1 record(s) in 1ms
	levelho(mongod-3.0.7) be-mean-pokemons> var query = {name: /charmander/i}
	levelho(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll: {moves:['fogo no rabo','rosca queimada']}}
	levelho(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod)
	Updated 1 existing record(s) in 3ms
	WriteResult({
	  "nMatched": 1,
	  "nUpserted": 0,
	  "nModified": 1
	})
	levelho(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("566aedde3e6ceca410aa3155"),
	  "name": "Charmander",
	  "description": "cão chupando manga fofinho",
	  "type": "fogo",
	  "attack": 52,
	  "height": 0.6,
	  "active": false,
	  "moves": [
	    "fogo no rabo",
	    "rosca queimada"
	  ]
	}
	Fetched 1 record(s) in 5ms
```

## 2. **Adicionar** 1 movimento em todos os pokemons: `desvio`.
```
	levelho(mongod-3.0.7) be-mean-pokemons> var mod = {$push: {moves:"desvio"}}
	levelho(mongod-3.0.7) be-mean-pokemons> var options = {multi: true}
	levelho(mongod-3.0.7) be-mean-pokemons> db.pokemons.update({}, mod, options)
	Updated 9 existing record(s) in 7ms
	WriteResult({
	  "nMatched": 9,
	  "nUpserted": 0,
	  "nModified": 9
	})

```

## 3. **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".
```
	levelho(mongod-3.0.7) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}
	levelho(mongod-3.0.7) be-mean-pokemons> var mod = {$setOnInsert:{ name:'AindaNaoExistemon', type: null, attack: null, defense: null, heigth: null, description: 'sem maiores informações.' }}
	levelho(mongod-3.0.7) be-mean-pokemons> var options = {upsert: true}
	levelho(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
	Updated 1 new record(s) in 4ms
	WriteResult({
	  "nMatched": 0,
	  "nUpserted": 1,
	  "nModified": 0,
	  "_id": ObjectId("566af4d945736df61898c757")
	})
	levelho(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("566af4d945736df61898c757"),
	  "name": "AindaNaoExistemon",
	  "type": null,
	  "attack": null,
	  "defense": null,
	  "heigth": null,
	  "description": "sem maiores informações."
	}
	Fetched 1 record(s) in 1ms
```

## 4. Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.
```
	levelho(mongod-3.0.7) be-mean-pokemons> var query = {moves:{$in:[/investida/i, /boboataque/i]}}
	levelho(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("566aed7a3e6ceca410aa3154"),
	  "name": "Bulbassauro",
	  "description": "Chicote de trepadeira",
	  "type": "grama",
	  "attack": 49,
	  "height": 0.4,
	  "active": false,
	  "moves": [
	    "boboataque",
	    "ataque de bulbice",
	    "desvio"
	  ]
	}
	Fetched 1 record(s) in 1ms
```

## 5. Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.
```
	levelho(mongod-3.0.7) be-mean-pokemons> var query = {moves:{$all:[/fogo no rabo/i, /rosca queimada/i]}}
	levelho(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("566aedde3e6ceca410aa3155"),
	  "name": "Charmander",
	  "description": "cão chupando manga fofinho",
	  "type": "fogo",
	  "attack": 52,
	  "height": 0.6,
	  "active": false,
	  "moves": [
	    "fogo no rabo",
	    "rosca queimada",
	    "desvio"
	  ]
	}
	Fetched 1 record(s) in 2ms
```

## 6. Pesquisar **todos** os pokemons que não são do tipo `elétrico`.
```
	levelho(mongod-3.0.7) be-mean-pokemons> var query = {type:{$not: /electric/i}}
	levelho(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("566a1c25f16b47e8550adb43"),
	  "name": "Mongomon",
	  "description": "Um pokemon não-relacional",
	  "type": "bedeomon",
	  "attack": 42,
	  "defense": 42,
	  "height": 42,
	  "moves": [
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("566a1c25f16b47e8550adb44"),
	  "name": "Mateomon",
	  "description": "Um pokemon que passarinho não bebe",
	  "type": "bebeomon",
	  "attack": 69,
	  "defense": 96,
	  "height": 12,
	  "moves": [
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("566a1c25f16b47e8550adb45"),
	  "name": "Sabedomon",
	  "description": "Um pokemon que sabe das coisas.",
	  "type": "cebeomon",
	  "attack": 55,
	  "defense": 77,
	  "height": 66,
	  "moves": [
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("566a1c25f16b47e8550adb46"),
	  "name": "Criativomon",
	  "description": "Um pokemon que pensa ser publicitário",
	  "type": "pepeomon",
	  "attack": 3,
	  "defense": 1,
	  "height": 100,
	  "moves": [
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("566a1c25f16b47e8550adb47"),
	  "name": "Facebokomon",
	  "description": "Um pokemon social",
	  "type": "redomon",
	  "attack": 77,
	  "defense": 33,
	  "height": 124,
	  "moves": [
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("566aed283e6ceca410aa3153"),
	  "name": "Squirtle",
	  "description": "Ejeta água que passarinho não bebe",
	  "type": "água",
	  "attack": 48,
	  "height": 0.5,
	  "active": false,
	  "moves": [
	    "aguinha do mal",
	    "aguinha do bem",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("566aed7a3e6ceca410aa3154"),
	  "name": "Bulbassauro",
	  "description": "Chicote de trepadeira",
	  "type": "grama",
	  "attack": 49,
	  "height": 0.4,
	  "active": false,
	  "moves": [
	    "boboataque",
	    "ataque de bulbice",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("566aedde3e6ceca410aa3155"),
	  "name": "Charmander",
	  "description": "cão chupando manga fofinho",
	  "type": "fogo",
	  "attack": 52,
	  "height": 0.6,
	  "active": false,
	  "moves": [
	    "fogo no rabo",
	    "rosca queimada",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("566af4d945736df61898c757"),
	  "name": "AindaNaoExistemon",
	  "type": null,
	  "attack": null,
	  "defense": null,
	  "heigth": null,
	  "description": "sem maiores informações."
	}
	Fetched 9 record(s) in 3ms
```

## 7. Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.
```
	levelho(mongod-3.0.7) be-mean-pokemons> var query = {$and: [ {moves:{$in:[/investida/i]}} , {attack: {$not: {$lte:49}}} ]}
	levelho(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
	Fetched 0 record(s) in 0ms
```

## 8. Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
	levelho(mongod-3.0.7) be-mean-pokemons> var query = {$and: [ {type: 'água'} , {attack: {$lt:50}} ]}
	levelho(mongod-3.0.7) be-mean-pokemons> db.pokemons.remove(query)
	Removed 1 record(s) in 3ms
	WriteResult({
	  "nRemoved": 1
	})
```

## 9. Demonstre a diferença entre os operadores `$ne` e `$not`.
```
	Na demonstração abaixo, vê-se que a query feita com $not nos devolve o valor esperado: pokemons cuja altura não seja menor ou igual a 100. Porém, quando se usa o $ne em seu lugar, são retornados todos os pokemons. Isso acontece porque o $ne busca por um valor literal. Por esse mesmo motivo, não é possível usar Regex no $ne.

	levelho(mongod-3.0.7) be-mean-pokemons> var query = {height: {$not:{$lte:100}}}
	levelho(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("566a1c25f16b47e8550adb47"),
	  "name": "Facebokomon",
	  "description": "Um pokemon social",
	  "type": "redomon",
	  "attack": 77,
	  "defense": 33,
	  "height": 124,
	  "moves": [
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("566af4d945736df61898c757"),
	  "name": "AindaNaoExistemon",
	  "type": null,
	  "attack": null,
	  "defense": null,
	  "heigth": null,
	  "description": "sem maiores informações."
	}
	Fetched 2 record(s) in 3ms
	levelho(mongod-3.0.7) be-mean-pokemons> var query = {height: {$ne:{$lte:100}}}
	levelho(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("566a1c25f16b47e8550adb43"),
	  "name": "Mongomon",
	  "description": "Um pokemon não-relacional",
	  "type": "bedeomon",
	  "attack": 42,
	  "defense": 42,
	  "height": 42,
	  "moves": [
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("566a1c25f16b47e8550adb44"),
	  "name": "Mateomon",
	  "description": "Um pokemon que passarinho não bebe",
	  "type": "bebeomon",
	  "attack": 69,
	  "defense": 96,
	  "height": 12,
	  "moves": [
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("566a1c25f16b47e8550adb45"),
	  "name": "Sabedomon",
	  "description": "Um pokemon que sabe das coisas.",
	  "type": "cebeomon",
	  "attack": 55,
	  "defense": 77,
	  "height": 66,
	  "moves": [
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("566a1c25f16b47e8550adb46"),
	  "name": "Criativomon",
	  "description": "Um pokemon que pensa ser publicitário",
	  "type": "pepeomon",
	  "attack": 3,
	  "defense": 1,
	  "height": 100,
	  "moves": [
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("566a1c25f16b47e8550adb47"),
	  "name": "Facebokomon",
	  "description": "Um pokemon social",
	  "type": "redomon",
	  "attack": 77,
	  "defense": 33,
	  "height": 124,
	  "moves": [
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("566aeca93e6ceca410aa3152"),
	  "name": "Pikachu",
	  "description": "Rato elétrico",
	  "type": "electric",
	  "attack": 100,
	  "height": 0.4,
	  "active": false,
	  "moves": [
	    "esfera elétrica",
	    "trovãozada",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("566aed7a3e6ceca410aa3154"),
	  "name": "Bulbassauro",
	  "description": "Chicote de trepadeira",
	  "type": "grama",
	  "attack": 49,
	  "height": 0.4,
	  "active": false,
	  "moves": [
	    "boboataque",
	    "ataque de bulbice",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("566aedde3e6ceca410aa3155"),
	  "name": "Charmander",
	  "description": "cão chupando manga fofinho",
	  "type": "fogo",
	  "attack": 52,
	  "height": 0.6,
	  "active": false,
	  "moves": [
	    "fogo no rabo",
	    "rosca queimada",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("566af4d945736df61898c757"),
	  "name": "AindaNaoExistemon",
	  "type": null,
	  "attack": null,
	  "defense": null,
	  "heigth": null,
	  "description": "sem maiores informações."
	}
	Fetched 9 record(s) in 9ms
```
