# MongoDB - Aula 04 - Exercício

User: [nicholasinatel](https://github.com/nicholasinatel)

Autor: Nicholas Fernandes de Almeida Paolillo

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
var query = { name : /pikachu/i}
var mod = {$pushAll: {moves: ["esfera elétrica","investida trovão"]}}
db.pokemons.update(query, mod)

var query = { name : /squirtle/i}
var mod = {$pushAll: {moves: ["raio de gelo","giro rápido"]}}
db.pokemons.update(query, mod)

var query = { name : /bulbassauro/i}
var mod = {$pushAll: {moves: ["raio solar","dança de pétalas"]}}
db.pokemons.update(query, mod)

var query = { name : /charmander/i}
var mod = {$pushAll: {moves: ["brasas","encarar"]}}
db.pokemons.update(query, mod)
```

## **Adicionar** 1 movimento em todos os pokemons: desvio.

```
var query = {}
var mod = {$push: {moves: "desvio"}}
var options = {multi: true}
db.pokemons.update(query, mod, options)
```

## **Adicionar** o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".

```
var query = {name: /AindaNaoExisteMon/i}
var mod = {   $set: {active: true},   $setOnInsert: {name: "AindaNaoExisteMon", attack: null, defense: null, height: null, description: "Sem maiores informações"} }
var options = {upsert: true}
db.pokemons.update(query, mod, options)

```

## Pesquisar **todos** o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.

```
var query = { moves : {$in:[/investida/i,/esfera elétrica/i]}}
db.pokemons.find(query)
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```
var query = { moves : {$all:[/investida/i,/esfera elétrica/i]}}
db.pokemons.find(query)

```

## Pesquisar **todos** os pokemons que não são do tipo elétrico.

```
var query = { type : { $not :  /eletrico/i  } }
db.pokemons.find(query)

```

## Pesquisar **todos** pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49.

```
var query = { $and: [ { moves: {$in:["investida"]}}, { defense : { $not : { $lte : 49 } } } ] }
db.pokemons.find(query)
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
var query = {$and: [{type: /agua/i},{attack: {$lt: 50}}]}
db.pokemons.remove(query)

```
