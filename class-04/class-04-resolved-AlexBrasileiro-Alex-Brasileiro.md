1. Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
2. Adicionar 1 movimento em todos os pokemons: 'desvio'
3. Adicionar o pokemons 'AindaNãoExisteMon' caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações"
4. Pesquisar todos os pokemons que possuam o ataque 'investida' e mais um que você adicionou, escolha seu pokemon favorito.
5. Pesquisar todos os pokemons que possuam ataques que você adicionou, escolha seu pokemon favorito.
6. Pesquisar todos que não são do tipo 'elétrico'
7. Pesquisar todos pokemons que tenham ataque 'investida' e tenham a defesa não menor ou igual a 49
8. Remova todos os pokemons do tipo água e com attack menor que 50.


1. Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Ivysaur, Kakuna, Blastoise e Testemon.

```
	
	var query = {
		$or: [ 
			{name: 'Ivysaur'},
			{name: 'Kakuna'},
			{name: 'Blastoise'},
			{name: 'Testemon'}
		]
	}
	var attacks = ['ataque rápido', 'bola elétrica']
	var mod = {
			$pushAll: {
			attacks : attacks 
		}
	}
	var opt = {
		multi: true
	}
	
	db.pokemons.update(query, mod, opt)
	
	Updated 4 existing record(s) in 4ms
	
	WriteResult({
	  "nMatched": 4,
	  "nUpserted": 0,
	  "nModified": 4
	})
	
	db.pokemons.find(query)
	
	{
	  "_id": ObjectId("567afa81021db0d38f00da03"),
	  "description": "Pokemon de teste",
	  "name": "Testemon",
	  "attack": 8000,
	  "defense": 8000,
	  "active": false,
	  "moves": [
	    "investida"
	  ],
	  "attacks": [
	    "ataque rápido",
	    "bola elétrica"
	  ]
	}
	{
	  "_id": ObjectId("5679ed9f021db0d38f00d9fe"),
	  "name": "Ivysaur",
	  "description": "Ivysaur's legs and trunk grow thick and strong",
	  "attack": 4,
	  "defense": 3,
	  "height": 1,
	  "active": false,
	  "moves": [
	    "investida"
	  ],
	  "attacks": [
	    "ataque rápido",
	    "bola elétrica"
	  ]
	}
	{
	  "_id": ObjectId("5679ed9f021db0d38f00da00"),
	  "name": "Kakuna",
	  "description": "Descrição Modificada - Ele é feinho que dói!",
	  "attack": 1,
	  "defense": 2,
	  "height": 0.6,
	  "active": false,
	  "moves": [
	    "investida",
	    "lança-chamas"
	  ],
	  "attacks": [
	    "ataque rápido",
	    "bola elétrica"
	  ]
	}
	{
	  "_id": ObjectId("5679ed9f021db0d38f00da01"),
	  "name": "Blastoise",
	  "description": "Blastoise has water spouts that protrude from its shell",
	  "attack": 4,
	  "defense": 4,
	  "height": 1.6,
	  "active": false,
	  "moves": [
	    "investida",
	    "hidro bomba"
	  ],
	  "attacks": [
	    "ataque rápido",
	    "bola elétrica"
	  ]
	}
	
	Fetched 4 record(s) in 4ms


```

2. Adicionar 1 movimento em todos os pokemons: 'desvio'

```
	
	var query = {}
	var mod = {
		$push: {
			moves : 'desvio' 
		}
	}
	var opt = {
		multi: true
	}
	
	db.pokemons.update(query, mod, opt)
	
	Updated 7 existing record(s) in 2ms
	
	WriteResult({
	  "nMatched": 7,
	  "nUpserted": 0,
	  "nModified": 7
	})
	
	db.pokemons.find(query)
	
	{
	  "_id": ObjectId("5679ed9f021db0d38f00d9ff"),
	  "name": "Wartortle",
	  "description": "Its tail is large and covered with a rich, thick fur",
	  "attack": 80,
	  "defense": 4,
	  "height": 1,
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("567afa81021db0d38f00da03"),
	  "description": "Pokemon de teste",
	  "name": "Testemon",
	  "attack": 8000,
	  "defense": 8000,
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ],
	  "attacks": [
	    "ataque rápido",
	    "bola elétrica"
	  ]
	}
	{
	  "_id": ObjectId("5679ed9f021db0d38f00da02"),
	  "name": "Sandshrew",
	  "description": "Sandshrew's body is configured to absorb water without waste, enabling it to survive in an arid desert",
	  "attack": 4,
	  "defense": 4,
	  "height": 0.6,
	  "active": false,
	  "moves": [
	    "investida",
	    "choque do trovão",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("567c12c6ee7b4a0557f914ea"),
	  "active": false,
	  "name": "Squirtle",
	  "atack": null,
	  "defense": null,
	  "height": null,
	  "description": "Sem informações",
	  "moves": [
	    "investida",
	    "folha navalha",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("5679ed9f021db0d38f00d9fe"),
	  "name": "Ivysaur",
	  "description": "Ivysaur's legs and trunk grow thick and strong",
	  "attack": 4,
	  "defense": 3,
	  "height": 1,
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ],
	  "attacks": [
	    "ataque rápido",
	    "bola elétrica"
	  ]
	}
	{
	  "_id": ObjectId("5679ed9f021db0d38f00da00"),
	  "name": "Kakuna",
	  "description": "Descrição Modificada - Ele é feinho que dói!",
	  "attack": 1,
	  "defense": 2,
	  "height": 0.6,
	  "active": false,
	  "moves": [
	    "investida",
	    "lança-chamas",
	    "desvio"
	  ],
	  "attacks": [
	    "ataque rápido",
	    "bola elétrica"
	  ]
	}
	{
	  "_id": ObjectId("5679ed9f021db0d38f00da01"),
	  "name": "Blastoise",
	  "description": "Blastoise has water spouts that protrude from its shell",
	  "attack": 4,
	  "defense": 4,
	  "height": 1.6,
	  "active": false,
	  "moves": [
	    "investida",
	    "hidro bomba",
	    "desvio"
	  ],
	  "attacks": [
	    "ataque rápido",
	    "bola elétrica"
	  ]
	}
	
	Fetched 7 record(s) in 4ms
	

```

3. Adicionar o pokemons 'AindaNãoExisteMon' caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações"

```
	
	var query = {name : /AindaNãoExisteMon/i}
	var mod = {
		$set: {
			name: "AindaNãoExisteMon",
		},
		$setOnInsert: {
			atack: null,
			defense: null,
			height: null,
			description: "Sem maiores informações",
		}
	}
	var opt = {upsert: true}
	db.pokemons.update(query, mod, opt)
	
	Updated 1 new record(s) in 2ms
	
	WriteResult({
	  "nMatched": 0,
	  "nUpserted": 1,
	  "nModified": 0,
	  "_id": ObjectId("567c3be4ee7b4a0557f914eb")
	})
	
	db.pokemons.find(query)
	
	{
	  "_id": ObjectId("567c3be4ee7b4a0557f914eb"),
	  "name": "AindaNãoExisteMon",
	  "atack": null,
	  "defense": null,
	  "height": null,
	  "description": "Sem maiores informações"
	}
	
	Fetched 1 record(s) in 1ms


```

4. Pesquisar todos os pokemons que possuam o ataque 'investida' e mais um que você adicionou, escolha seu pokemon favorito.

```
	
	var query = {moves : {$in : ['investida' , 'folha navalha']}}
	
	db.pokemons.find(query)
	
	{
	  "_id": ObjectId("5679ed9f021db0d38f00d9ff"),
	  "name": "Wartortle",
	  "description": "Its tail is large and covered with a rich, thick fur",
	  "attack": 80,
	  "defense": 4,
	  "height": 1,
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("567afa81021db0d38f00da03"),
	  "description": "Pokemon de teste",
	  "name": "Testemon",
	  "attack": 8000,
	  "defense": 8000,
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ],
	  "attacks": [
	    "ataque rápido",
	    "bola elétrica"
	  ]
	}
	{
	  "_id": ObjectId("5679ed9f021db0d38f00da02"),
	  "name": "Sandshrew",
	  "description": "Sandshrew's body is configured to absorb water without waste, enabling it to survive in an arid desert",
	  "attack": 4,
	  "defense": 4,
	  "height": 0.6,
	  "active": false,
	  "moves": [
	    "investida",
	    "choque do trovão",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("567c12c6ee7b4a0557f914ea"),
	  "active": false,
	  "name": "Squirtle",
	  "atack": null,
	  "defense": null,
	  "height": null,
	  "description": "Sem informações",
	  "moves": [
	    "investida",
	    "folha navalha",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("5679ed9f021db0d38f00d9fe"),
	  "name": "Ivysaur",
	  "description": "Ivysaur's legs and trunk grow thick and strong",
	  "attack": 4,
	  "defense": 3,
	  "height": 1,
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ],
	  "attacks": [
	    "ataque rápido",
	    "bola elétrica"
	  ]
	}
	{
	  "_id": ObjectId("5679ed9f021db0d38f00da00"),
	  "name": "Kakuna",
	  "description": "Descrição Modificada - Ele é feinho que dói!",
	  "attack": 1,
	  "defense": 2,
	  "height": 0.6,
	  "active": false,
	  "moves": [
	    "investida",
	    "lança-chamas",
	    "desvio"
	  ],
	  "attacks": [
	    "ataque rápido",
	    "bola elétrica"
	  ]
	}
	{
	  "_id": ObjectId("5679ed9f021db0d38f00da01"),
	  "name": "Blastoise",
	  "description": "Blastoise has water spouts that protrude from its shell",
	  "attack": 4,
	  "defense": 4,
	  "height": 1.6,
	  "active": false,
	  "moves": [
	    "investida",
	    "hidro bomba",
	    "desvio"
	  ],
	  "attacks": [
	    "ataque rápido",
	    "bola elétrica"
	  ]
	}
	
	Fetched 7 record(s) in 3ms

```

5. Pesquisar todos os pokemons que possuam ataques que você adicionou, escolha seu pokemon favorito.

```

	var query = {moves : {$in : ['choque do trovão' , 'folha navalha' , 'lança-chamas' , 'hidro bomba']}}
	
	db.pokemons.find(query)
	
	{
	  "_id": ObjectId("5679ed9f021db0d38f00da02"),
	  "name": "Sandshrew",
	  "description": "Sandshrew's body is configured to absorb water without waste, enabling it to survive in an arid desert",
	  "attack": 4,
	  "defense": 4,
	  "height": 0.6,
	  "active": false,
	  "moves": [
	    "investida",
	    "choque do trovão",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("567c12c6ee7b4a0557f914ea"),
	  "active": false,
	  "name": "Squirtle",
	  "atack": null,
	  "defense": null,
	  "height": null,
	  "description": "Sem informações",
	  "moves": [
	    "investida",
	    "folha navalha",
	    "desvio"
	  ]
	}
	{
	  "_id": ObjectId("5679ed9f021db0d38f00da00"),
	  "name": "Kakuna",
	  "description": "Descrição Modificada - Ele é feinho que dói!",
	  "attack": 1,
	  "defense": 2,
	  "height": 0.6,
	  "active": false,
	  "moves": [
	    "investida",
	    "lança-chamas",
	    "desvio"
	  ],
	  "attacks": [
	    "ataque rápido",
	    "bola elétrica"
	  ]
	}
	{
	  "_id": ObjectId("5679ed9f021db0d38f00da01"),
	  "name": "Blastoise",
	  "description": "Blastoise has water spouts that protrude from its shell",
	  "attack": 4,
	  "defense": 4,
	  "height": 1.6,
	  "active": false,
	  "moves": [
	    "investida",
	    "hidro bomba",
	    "desvio"
	  ],
	  "attacks": [
	    "ataque rápido",
	    "bola elétrica"
	  ]
	}
	
	Fetched 4 record(s) in 3ms

```

6. Pesquisar todos que não são do tipo 'elétrico'

```

	var query = {type : /elétrico/i}
	
	db.pokemons.find(query)
	
	{
	  "_id": ObjectId("5679ed9f021db0d38f00da02"),
	  "name": "Sandshrew",
	  "description": "Sandshrew's body is configured to absorb water without waste, enabling it to survive in an arid desert",
	  "attack": 4,
	  "defense": 4,
	  "height": 0.6,
	  "active": false,
	  "moves": [
	    "investida",
	    "choque do trovão",
	    "desvio"
	  ],
	  "type": "elétrico"
	}

	Fetched 1 record(s) in 0ms

```

7. Pesquisar todos pokemons que tenham ataque 'investida' e tenham a defesa não menor ou igual a 49

```
	
	var query = {
		$and: [
			{moves: /investida/i},
			{defense: { $gte: 49 }}
			]
		}
	db.pokemons.find(query)
	
	{
	  "_id": ObjectId("567afa81021db0d38f00da03"),
	  "description": "Pokemon de teste",
	  "name": "Testemon",
	  "attack": 8000,
	  "defense": 8000,
	  "active": false,
	  "moves": [
	    "investida",
	    "desvio"
	  ],
	  "attacks": [
	    "ataque rápido",
	    "bola elétrica"
	  ]
	}

	Fetched 1 record(s) in 2ms
	
```

8. Remova todos os pokemons do tipo água e com attack menor que 50.

```
	
	var query = {
		$and: [
			{type: /elétrico/i},
			{attack: { $gt: 3 }}
		]
	}
	
	db.pokemons.remove(query)
	
	Removed 1 record(s) in 2ms
	
	WriteResult({
	  "nRemoved": 1
	})	

```