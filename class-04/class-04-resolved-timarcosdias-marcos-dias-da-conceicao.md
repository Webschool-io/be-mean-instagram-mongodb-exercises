# MongoDB - Aula 04 - Exercício
autor: Marcos Dias da Conceição

## 1. **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
var query = {name : {$in : ['Pikachu', 'Squirtle', 'Bulbassauro', 'Charmander']}}
var mod = {$pushAll : {moves: ['soco',  'chute']}}
var options = {multi: true}
db.pokemons.update(query, mod, options)

Updated 4 existing record(s) in 8ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
```

## 2. **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```
var query = {}
var mod = {$push : {moves: 'desvio'}}
var options = {multi: true}
db.pokemons.update(query, mod, options)

Updated 12 existing record(s) in 1ms
WriteResult({
  "nMatched": 12,
  "nUpserted": 0,
  "nModified": 12
})
```

## 3. **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
var query = {name : 'AindaNaoExisteMon'}
var mod = {
	$setOnInsert: {
		name: 'AindaNaoExisteMon',
    type: null,
    attack: null,
		defense: null,
		height: null,
		description : 'Sem maiores informações'
	}
}
var options = {upsert: true}
db.pokemons.update(query, mod, options)

Updated 1 new record(s) in 1ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("56b6637e82de0eab2521e431")
})
```

## 4. Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
var query = {moves : {$in : [/investida/i, /soco/i]}}
db.pokemons.find(query)
```

## 5. Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```
var query = {moves : {$all : [/chute/i, /soco/i]}}
db.pokemons.find(query)
```

## 6. Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```
var query = {type : {$ne : 'elétrico'}}
db.pokemons.find(query)
```

## 7. Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```
var query = {moves : {$in : ['investida']}, defense : {$gt: 49}}
db.pokemons.find(query)

//ou

var query = {$and: [ {moves: {$in : ['investida']}} , {defense : {$gt: 49}} ]}
db.pokemons.find(query)

//ou

var query = {$and: [ {moves : {$in : ['investida']}}, {attack : {$not: {$lte: 49}}} ]}
db.pokemons.find(query)
```

## 8. Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
var query = {type: 'água', attack : {$lt: 50}}
db.pokemons.remove(query)

//ou

var query = {$and: [{type: 'água'}, {attack : {$lt: 50}} ]}
db.pokemons.remove(query)
```
