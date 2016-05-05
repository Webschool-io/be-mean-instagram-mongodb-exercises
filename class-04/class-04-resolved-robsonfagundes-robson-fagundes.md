# MongoDB - Aula 04 - Exercício
autor: Robson Fagundes

## 1. **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```js

	var query = {name: /Pikachu/i}
	var mod = {$pushAll: {movesAttack: ['eletric ball', 'thunder invested']}}
	db.pokemons.update(query, mod)

	var query = {name: /Squirtle/i}
	var mod = {$pushAll: {movesAttack: ['swim at high speeds', 'resistance in water']}}
	db.pokemons.update(query, mod)

	var query = {name: /Bulbasaur/i}
	var mod = {$pushAll: {movesAttack: ['progressively larger', "sun's rays"]}}
	db.pokemons.update(query, mod)

	var query = {name: /Charmander/i}
	var mod = {$pushAll: {movesAttack: ['tail fire', 'burns fiercely']}}
	db.pokemons.update(query, mod)

```
```
Dell-3500(mongod-3.0.7) be-mean-pokemons> var query = {name: /Pikachu/i}
Dell-3500(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll: {movesAttack: ['eletric ball', 'thunder invested']}}
Dell-3500(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 4ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```



## 2. **Adicionar** 1 movimento em todos os pokemons: `desvio`.

```js

	var query = {}
	var mod = {$push: {moves: 'desvio'}}
	var options = {multi: true}
	db.pokemons.update(query, mod, options)

```
```
Updated 7 existing record(s) in 4ms
WriteResult({
  "nMatched": 7,
  "nUpserted": 0,
  "nModified": 7
})
```

## 3. **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".

```js

	var query = {name: /AindaNaoExisteMon/i}
	var mod = {$setOnInsert:
	    {
	      name: 'AindaNaoExisteMon',
	      type: null,
	      attack: null,
	      defense: null,
	      height: null,
	      description: 'Sem maiores informações'
	    }
	}
	var options = {upsert: true}
	db.pokemons.update(query, mod, options) 

```
```
Updated 1 new record(s) in 18ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564fb69caf5fd078eb5d40fb")
})
```

## 4. Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.

```js

	var query = {movesAttack: {$in: [/investida/i, /eletric ball/i]}}
	db.pokemons.find(query)

	var query = {movesAttack: {$in: [/burns fiercely/i, /eletric ball/i]}}
	db.pokemons.find(query)

```
{
  "_id": ObjectId("56427fedb892b212ddd6ec90"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "movesAttack": [
    "eletric ball",
    "thunder invested"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564285dd576657b5d00592c8"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions.",
  "type": "Fire",
  "attack": 60,
  "height": 0.2,
  "movesAttack": [
    "tail fire",
    "burns fiercely"
  ],
  "moves": [
    "desvio"
  ]
}
Fetched 2 record(s) in 6ms
```

```

## 5. Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```js
	
	var query = {movesAttack: {$all: [/burns fiercely/i, /tail fire/i]}}
	db.pokemons.find(query)

```
```
{
  "_id": ObjectId("564285dd576657b5d00592c8"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions.",
  "type": "Fire",
  "attack": 60,
  "height": 0.2,
  "movesAttack": [
    "tail fire",
    "burns fiercely"
  ],
  "moves": [
    "desvio"
  ]
}
Fetched 1 record(s) in 2ms
```

## 6. Pesquisar **todos** os pokemons que não são do tipo `elétrico`.

```js

	var query = {type: {$not: /electric/i}}
	db.pokemons.find(query)

```
```
Fetched 7 record(s) in 6ms
```

## 7. Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.

```js

	var query = {$and: [ {movesAttack: {$in: ['tail fire']}}, {attack: {$not: {$lte: 49}}} ]}
	db.pokemons.find(query)

```
```
{
  "_id": ObjectId("564285dd576657b5d00592c8"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions.",
  "type": "Fire",
  "attack": 60,
  "height": 0.2,
  "movesAttack": [
    "tail fire",
    "burns fiercely"
  ],
  "moves": [
    "desvio"
  ]
}
Fetched 1 record(s) in 2ms

```

## 8. Remova **todos** os pokemons do tipo água E com attack menor que 50.

```js

	var query = {$and: [ {type: /água/i}, {attack: {$lt: 50}} ]}
	db.pokemons.remove(query)

	var query = {$and: [ {type: /Water/i}, {attack: {$lt: 50}} ]}
	db.pokemons.remove(query)


```
```
Updated 7 existing record(s) in 4ms
WriteResult({
  "nMatched": 7,
  "nUpserted": 0,
  "nModified": 7
})
```

