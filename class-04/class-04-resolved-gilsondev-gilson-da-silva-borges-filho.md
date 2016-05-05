# MongoDB - Aula 04 - Exercício

Autor: Gilson Filho

## 1. Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Bulbassauro e Charmander.

```bash
be-mean-pokemons> var query = {name: /pikachu/i}
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564b1db125337263280d04a7"),
  "attack": 55,
  "created": "2013-11-03T15:05:41.317235",
  "defense": 40,
  "height": "4",
  "hp": 35,
  "name": "Pikachu",
  "speed": 90,
  "types": [
    "electric"
  ],
  "moves": [
    "attack1",
    "attack2"
  ]
}
Fetched 1 record(s) in 1ms
be-mean-pokemons> var mod = {$pushAll: {moves: ["attack1", "attack2"]}}
be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 10ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564b1db125337263280d04a7"),
  "attack": 55,
  "created": "2013-11-03T15:05:41.317235",
  "defense": 40,
  "height": "4",
  "hp": 35,
  "name": "Pikachu",
  "speed": 90,
  "types": [
    "electric"
  ],
  "moves": [
    "attack1",
    "attack2"
  ]
}
Fetched 1 record(s) in 1ms
```

```bash
be-mean-pokemons> var query = {name: /squirtle/i}
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564b1db425337263280d04b6"),
  "attack": 48,
  "created": "2013-11-03T15:05:41.278310",
  "defense": 65,
  "height": "5",
  "hp": 44,
  "name": "Squirtle",
  "speed": 43,
  "types": [
    "water"
  ]
}
Fetched 1 record(s) in 1ms
be-mean-pokemons> var mod = {$pushAll: {moves: ["attack1", "attack2"]}}
be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 4ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564b1db425337263280d04b6"),
  "attack": 48,
  "created": "2013-11-03T15:05:41.278310",
  "defense": 65,
  "height": "5",
  "hp": 44,
  "name": "Squirtle",
  "speed": 43,
  "types": [
    "water"
  ],
  "moves": [
    "attack1",
    "attack2"
  ]
}
Fetched 1 record(s) in 1ms
```

```bash
be-mean-pokemons> var query = {name: /bulbasaur/i}
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564b1de325337263280d068c"),
  "attack": 49,
  "created": "2013-11-03T15:05:41.260678",
  "defense": 49,
  "height": "7",
  "hp": 45,
  "name": "Bulbasaur",
  "speed": 45,
  "types": [
    "poison",
    "grass"
  ]
}
Fetched 1 record(s) in 2ms
be-mean-pokemons> var mod = {$pushAll: {moves: ["attack1", "attack2"]}}
be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564b1de325337263280d068c"),
  "attack": 49,
  "created": "2013-11-03T15:05:41.260678",
  "defense": 49,
  "height": "7",
  "hp": 45,
  "name": "Bulbasaur",
  "speed": 45,
  "types": [
    "poison",
    "grass"
  ],
  "moves": [
    "attack1",
    "attack2"
  ]
}
Fetched 1 record(s) in 1ms
```

```bash
be-mean-pokemons> var query = {name: /charmander/i}
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564b1dad25337263280d047a"),
  "attack": 52,
  "created": "2013-11-03T15:05:41.271082",
  "defense": 43,
  "height": "6",
  "hp": 39,
  "name": "Charmander",
  "speed": 65,
  "types": [
    "fire"
  ]
}
Fetched 1 record(s) in 1ms
be-mean-pokemons> var mod = {$pushAll: {moves: ["attack1", "attack2"]}}
be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564b1dad25337263280d047a"),
  "attack": 52,
  "created": "2013-11-03T15:05:41.271082",
  "defense": 43,
  "height": "6",
  "hp": 39,
  "name": "Charmander",
  "speed": 65,
  "types": [
    "fire"
  ],
  "moves": [
    "attack1",
    "attack2"
  ]
}
Fetched 1 record(s) in 1ms
```

## 2. Adicionar 1 movimento em todos os pokemons: `desvio`

```bash
be-mean-pokemons> var query = {}
be-mean-pokemons> var mod = {$push: {moves: ["desvio"]}}
be-mean-pokemons> var options = {multi: true}
be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 610 existing record(s) in 11ms
WriteResult({
  "nMatched": 610,
  "nUpserted": 0,
  "nModified": 610
})
```

## 3. Adicionar o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações"

```bash
be-mean-pokemons> var query = {name: /notexists/i}
be-mean-pokemons> var mod = {
	$set: {description: "Sem maiores informações"},
	$setOnInsert: {
		name: "AindaNaoExisteMon",
		attack: null,
		defense: null,
		height: null,
		hp: null,
		speed: null,
		types: null,
		moves: null
	}
}
be-mean-pokemons> var options = {upsert: true}
be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 2ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("5658f574d96ec5053b0e1498")
})
be-mean-pokemons> db.pokemons.find({"_id": ObjectId("5658f574d96ec5053b0e1498")})
{
  "_id": ObjectId("5658f574d96ec5053b0e1498"),
  "description": "Sem maiores informações",
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "hp": null,
  "speed": null,
  "types": null,
  "moves": null
}
Fetched 1 record(s) in 1ms
```

## 4. Pesquisar todos os pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.

```bash
be-mean-pokemons> var query = {moves: {$in: ["investida", "attack3"]}}
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564b1daf25337263280d0493"),
  "attack": 100,
  "created": "2013-11-03T15:05:41.404294",
  "defense": 70,
  "height": "15",
  "hp": 80,
  "name": "Machoke",
  "speed": 45,
  "types": [
    "fighting"
  ],
  "moves": [
    "investida",
    "attack3"
  ]
}
{
  "_id": ObjectId("564b1daf25337263280d0494"),
  "attack": 130,
  "created": "2013-11-03T15:05:41.406521",
  "defense": 80,
  "height": "16",
  "hp": 90,
  "name": "Machamp",
  "speed": 55,
  "types": [
    "fighting"
  ],
  "moves": [
    "investida",
    "attack3"
  ]
}
Fetched 2 record(s) in 1ms
```

## 5. Pesquisar todos os pokemons que possuem os ataques que você adicionou, escolha o seu pokemon favorito.

```bash
be-mean-pokemons> var query = {moves: {$in: ["attack1", "attack2"]}}
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564b1de325337263280d068c"),
  "attack": 49,
  "created": "2013-11-03T15:05:41.260678",
  "defense": 49,
  "height": "7",
  "hp": 45,
  "name": "Bulbasaur",
  "speed": 45,
  "types": [
    "poison",
    "grass"
  ],
  "moves": [
    "attack1",
    "attack2",
    [
      "desvio"
    ]
  ]
}
```

## 6. Pesquisar todos que não são do tipo eletrico

```bash
be-mean-pokemons> var query = {types: {$nin: ["eletric"]}}
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564b1dae25337263280d048b"),
  "attack": 95,
  "created": "2013-11-03T15:05:41.456387",
  "defense": 180,
  "height": "15",
  "hp": 50,
  "name": "Cloyster",
  "speed": 70,
  "types": [
    "water",
    "ice"
  ],
  "moves": [
    [
      "desvio"
    ]
  ]
}
```

## 7. Pesquisar todos pokemons que tenham o ataque `investida` E que tenham a defesa não menor ou igual a 49

```bash
be-mean-pokemons> var query = {$and: [{moves: {$in: ["investida"]}}, {attack: {$not: {$lte: 49}}}]}
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564b1daf25337263280d0493"),
  "attack": 100,
  "created": "2013-11-03T15:05:41.404294",
  "defense": 70,
  "height": "15",
  "hp": 80,
  "name": "Machoke",
  "speed": 45,
  "types": [
    "fighting"
  ],
  "moves": [
    "investida",
    "attack3"
  ]
}
{
  "_id": ObjectId("564b1daf25337263280d0494"),
  "attack": 130,
  "created": "2013-11-03T15:05:41.406521",
  "defense": 80,
  "height": "16",
  "hp": 90,
  "name": "Machamp",
  "speed": 55,
  "types": [
    "fighting"
  ],
  "moves": [
    "investida",
    "attack3"
  ]
}
```

## 8. Remova todos os pokemons do tipo agua e com attack menor que 50

```bash
be-mean-pokemons> var query = {$and: [{types: {$in: ["water"]}}, {attack: {$lt: 50}}]}
be-mean-pokemons> var options = {multi: true}
be-mean-pokemons> db.pokemons.remove(query, options)
WriteResult({
  "nRemoved": 21
})
```
