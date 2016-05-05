# MongoDB - Aula 04 - Exercício
autor: Jefferson Lima

## Exercício

### 1) Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
var query = {name:/pikachu/i}
var mod = {$pushAll:{moves:['bola elétrica','choque elétrico']}}
db.pokemons.update(query, mod)

Updated 1 existing record(s) in 3ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

var query = {name:/squirtle/i}
var mod = {$pushAll:{moves:['Jato dagua','Canhão dagua']}}
db.pokemons.update(query, mod)

WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

var query = {name:/bulbassauro/i}
var mod = {$pushAll:{moves:['folha lâmina','Cipoada']}}
db.pokemons.update(query, mod)

WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})


### 2) Adicionar 1 movimento em todos os pokemons: desvio.
var query = {}
var mod = {$push:{moves:'desvio'}}
var option = {multi:true}
db.pokemons.update(query, mod, option)

### 3) Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".

var query = {name: /AindaNaoExisteMon/i}
var mod = {$setOnInsert:{name: 'AindaNaoExisteMon',type: null,attack: null,defense: null,height: null,description: 'Sem maiores informações'}}
var options = {upsert: true}
db.pokemons.update(query, mod, options)

### 4) Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.

var query = {moves:{$in:[/investida/i, /Cipoada/i]}}
db.pokemons.find(query)

### 5) Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.
var query = {moves:{$in:[/folha lâmina/i, /cipoada/i]}}
db.pokemons.find(query)

### 6) Pesquisar todos os pokemons que não são do tipo elétrico.
var query = {type:{$not:/electric/i}}
db.pokemons.find(query)

### 7) Pesquisar todos pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49.
var query = {$and:[{moves:{$in:['investida']}}, {attack:{$gte:49}} ]}
db.pokemons.find(query)

### 8) Remova todos os pokemons do tipo água e com attack menor que 50.
var query = {$and:[{type:/água/i}, {attack:{$lt:50}} ] }
db.pokemons.remove(query)