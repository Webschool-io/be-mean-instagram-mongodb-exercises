# MongoDB - Aula 04 - Exercício
autor: **Pablo Zaniolo**

## 1. Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
var query = {name: {$in: [/pikachu/i, /squirtle/i, /bulbassauro/i, /charmander/i]}}
var mod = {$pushAll : {moves:['pseudo power','bolha de ar']}}
var options = {multi: true}
db.pokemons.update(query, mod, options)
```

## 2. **Adicionar** 1 movimento em todos os pokemons: desvio.

```
var query = {}
var mod = {$pushAll: {moves: ['desvio']}}
var options = {multi: true}
db.pokemons.update(query, mod, options)
```

## 3. **Adicionar** o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".

```
var query = {name: /AindaNaoExisteMon/i}
var mod = {
	$setOnInsert: {
		name: "AindaNaoExisteMon",
		attack: null,
		defense: null,
		height: null,
		description: "Sem maiores informações"}
}
var options = {upsert: true}
```

## 4. Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.

```
var query = {name: {$in: [/pikachu/i, /bulbassauro/i]}}
db.pokemons.find(query)
```

## 5. Pesquisar todos os pokemons que possuam os movimentos que você adicionou, escolha seu pokemon favorito.

```
var query = {moves: {$in: [/pseudo power/i, /bolha de ar/i]}}
db.pokemons.find(query)
```

## 6. Pesquisar todos os pokemons que não são do tipo elétrico.

```
var query = {type: {$ne: 'elétrico'}} 
db.pokemons.find(query)
```

## 7. Pesquisar todos pokemons que tenham o movimento investida E tenham a defesa não menor ou igual a 49.

```
var query = {$and: [{moves: /investida/i}, {defense: {$gt: 49}}]}
db.pokemons.find(query)
```

## 8. Remova todos os pokemons do tipo água e com attack menor que 50.

```
var query = {$and: [{type: /agua/i}, {attack: {$lt: 50}}]}
db.pokemons.remove(query)
```