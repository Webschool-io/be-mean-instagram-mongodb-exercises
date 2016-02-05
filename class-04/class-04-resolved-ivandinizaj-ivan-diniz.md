# MongoDB - Aula 04 - Exercício
autor: Ivan Diniz

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```javascript
$ var query = { $or : [
	{name: /pikachu/i},
	{name: /squirtle/i}, 
	{name: /bulbassauro/i},
	{name: /charmander/i}
	] 
}
$ var mod = {$set: {moves: ["esquiva", "investida"]} }
$ var opts = { multi: true }
$ db.pokemons.update(query, mod, opts)
```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```javascript
$ var query = {}
$ var mod = {$push: {moves: "desvio"}}
$ var opts = {multi: true}
$ db.pokemons.update(query, mod, opts)
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```javascript
$ var query = {name: /AindaNaoExisteMon/i}
$ var mod = {$setOnInsert: {
	name: "AindaNaoExisteMon",
	description: "Sem maiores informações",
	type: null,
	attack: 0,
	height: 0,
	moves: []
}}
$ var opts = {upsert: true}
$ db.pokemons.update(query, mod, opts)

WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("567f31acff718b8fad23aa8d")
})

```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```javascript
$ var query = {moves: {$in: [/investida/i, /choque do trovão/i]} }
$ db.pokemons.find(query)
{
  "_id": ObjectId("5675fff4c095c1d582e7932c"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "esquiva",
    "investida",
    "desvio",
    "choque do trovão"
  ]
}
{
  "_id": ObjectId("567600cfc095c1d582e7932d"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "esquiva",
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5676012ac095c1d582e7932e"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "esquiva",
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5676018bc095c1d582e7932f"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "esquiva",
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("567609fac095c1d582e79330"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "moves": [
    "esquiva",
    "investida",
    "desvio"
  ]
}
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```javascript
$ var query = {moves: {$in: [/choque do trovão/i]}}
$ db.pokemons.find(query)

{
  "_id": ObjectId("5675fff4c095c1d582e7932c"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "esquiva",
    "investida",
    "desvio",
    "choque do trovão"
  ]
}
```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```javascript
$ var query = {$nor : [{type: "eletric"}] }
$ db.pokemons.find(query)

{
  "_id": ObjectId("567600cfc095c1d582e7932d"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "esquiva",
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5676012ac095c1d582e7932e"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "esquiva",
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5676018bc095c1d582e7932f"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "esquiva",
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("567609fac095c1d582e79330"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "moves": [
    "esquiva",
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("567f31acff718b8fad23aa8d"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "type": null,
  "attack": 0,
  "height": 0,
  "moves": [ ]
}

```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **menor ou igual** a 49.##
```javascript
$ var query = {$and : [
	{moves: {$in: [/investida/i]} },
	{defense: {$lte: 49} }
]}
$ db.pokemons.find(query)

{
  "_id": ObjectId("567609fac095c1d582e79330"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "moves": [
    "esquiva",
    "investida",
    "desvio"
  ]
}

```

## Remova **todos** os pokemons do tipo água e com attack **menor que** 50.
```javascript
$ var query = {$and :[ 
	{type: /água/i},
	{attack: {$lt: 50} }
]}
db.pokemons.remove(query)

WriteResult({
  "nRemoved": 1
})	
```
