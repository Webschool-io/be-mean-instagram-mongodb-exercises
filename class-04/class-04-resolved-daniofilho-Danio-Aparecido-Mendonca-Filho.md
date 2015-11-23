# MongoDB - Aula 04 - Exercício
autor: Dânio Filho

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
var query = { $or: [{ name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbassauro/i}, {name: /charmander/i }] }
var atks = ['Raio Poderoso', 'Chute matador', 'Paralisia Mental']
var mod = { $pushAll: {moves: atks}}
var options = {multi: true}
db.pokemons.update(query, mod, options)

Updated 5 existing record(s) in 35ms
WriteResult({
  "nMatched": 5,
  "nUpserted": 0,
  "nModified": 5
})
```


## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

```
var query = {}
var atks = ['Desvio']
var mod = { $pushAll: {moves: atks} }
var options = {multi: true}
db.pokemons.update(query, mod, options)

Updated 6 existing record(s) in 4ms
WriteResult({
  "nMatched": 6,
  "nUpserted": 0,
  "nModified": 6
})

```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

```
var query = {name: /AindaNaoExisteMon/i}
var mod = {
  $setOnInsert: {
	name: "NaoExisteMon",
	type: null, 
	attack: null, 
	height: null, 
	moves: [],
	description: "Sem maiores informações"
  }
}
var options = {upsert: true}
db.pokemons.update(query, mod, options)

Updated 1 new record(s) in 5ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564cf66112860e1d346d30f8")
})
```


## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

```
var query = { moves: { $all: [/investida/i, /paralisia mental/i] }}
db.pokemons.find(query)

{
  "_id": ObjectId("56426ef47625928590e6919e"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "Investida",
    "choque do trovão",
    "Raio Poderoso",
    "Chute matador",
    "Paralisia Mental",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564270717625928590e6919f"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "Investida",
    "folha navalha",
    "Raio Poderoso",
    "Chute matador",
    "Paralisia Mental",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564270717625928590e691a0"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "Investida",
    "lança-chamas",
    "Raio Poderoso",
    "Chute matador",
    "Paralisia Mental",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564270737625928590e691a1"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "Investida",
    "Raio Poderoso",
    "Chute matador",
    "Paralisia Mental",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564271587625928590e691a2"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "Investida",
    "hidro bomba",
    "Raio Poderoso",
    "Chute matador",
    "Paralisia Mental",
    "Desvio"
  ]
}
Fetched 5 record(s) in 6ms
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

```
var query = { moves: { $all: [/desvio/i, /raio poderoso/i, /chute matador/i, /paralisia mental/i] }}
db.pokemons.find(query)

{
  "_id": ObjectId("56426ef47625928590e6919e"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "Investida",
    "choque do trovão",
    "Raio Poderoso",
    "Chute matador",
    "Paralisia Mental",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564270717625928590e6919f"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "Investida",
    "folha navalha",
    "Raio Poderoso",
    "Chute matador",
    "Paralisia Mental",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564270717625928590e691a0"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "Investida",
    "lança-chamas",
    "Raio Poderoso",
    "Chute matador",
    "Paralisia Mental",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564270737625928590e691a1"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "Investida",
    "Raio Poderoso",
    "Chute matador",
    "Paralisia Mental",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564271587625928590e691a2"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "Investida",
    "hidro bomba",
    "Raio Poderoso",
    "Chute matador",
    "Paralisia Mental",
    "Desvio"
  ]
}
Fetched 5 record(s) in 3ms

```


## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

```
var query = { type: { $ne: 'electric'} }
db.pokemons.find(query)

{
  "_id": ObjectId("564272a87625928590e691a3"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "moves": [
    "Investida",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564270717625928590e6919f"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "Investida",
    "folha navalha",
    "Raio Poderoso",
    "Chute matador",
    "Paralisia Mental",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564270717625928590e691a0"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "Investida",
    "lança-chamas",
    "Raio Poderoso",
    "Chute matador",
    "Paralisia Mental",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564270737625928590e691a1"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "Investida",
    "Raio Poderoso",
    "Chute matador",
    "Paralisia Mental",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564271587625928590e691a2"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "Investida",
    "hidro bomba",
    "Raio Poderoso",
    "Chute matador",
    "Paralisia Mental",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564cf66112860e1d346d30f8"),
  "name": "NaoExisteMon",
  "type": null,
  "attack": null,
  "height": null,
  "moves": [ ],
  "description": "Sem maiores informações"
}
Fetched 6 record(s) in 5ms
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

```
var query =  {
  $and: [
    {
      moves: {
        $in: [
          /investida/i
        ]
      }
    },
    {
      attack: {
        $not: {
          $lte: 49
        }
      }
    }
  ]
}
db.pokemons.find(query)

{
  "_id": ObjectId("56426ef47625928590e6919e"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "Investida",
    "choque do trovão",
    "Raio Poderoso",
    "Chute matador",
    "Paralisia Mental",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564270717625928590e691a0"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "Investida",
    "lança-chamas",
    "Raio Poderoso",
    "Chute matador",
    "Paralisia Mental",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564270737625928590e691a1"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "Investida",
    "Raio Poderoso",
    "Chute matador",
    "Paralisia Mental",
    "Desvio"
  ]
}
Fetched 3 record(s) in 2ms
```


## Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
var query = {
	$and: [
		{ attack: { $lt: 50 } },
    	{ type: 'água'}
	]
}
db.pokemons.find(query)

{
  "_id": ObjectId("564271587625928590e691a2"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "Investida",
    "hidro bomba",
    "Raio Poderoso",
    "Chute matador",
    "Paralisia Mental",
    "Desvio"
  ]
}
Fetched 1 record(s) in 0ms

db.pokemons.remove(query)

Removed 1 record(s) in 5ms
WriteResult({
  "nRemoved": 1
})

db.pokemons.find(query)

Fetched 0 record(s) in 1ms

```
