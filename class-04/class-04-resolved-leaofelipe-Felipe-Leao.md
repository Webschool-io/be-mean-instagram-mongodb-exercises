# MongoDB - Aula 04 - Exercício
autor: Felipe Leão

## Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander
```
> var query = {$or: [{name: /pikachu/i}, {name: /bulbassauro/i}, {name: /squirtle/i}, {name: /charmander/i}]}
> var mod = {$pushAll: {moves: ["Investida", "Defesa Suprema"]}}
> var options = {multi: true}
> db.pokemons.update(query, mod, options)
```

## Adicionar 1 movimento em todos os pokemons: desvio
```
> var query = {}
> var mod = {$push: {moves: "Desvio"}}
> var options = {multi: true}
> db.pokemons.update(query, mod, options)
```

## Adicionar o pokemon "AindaNaoExisteMon" caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".
```
> var query = {name: "AindaNaoExisteMon"}
> var mod = {$set: {description: "Sem maiores informações"}}
> var options = {upsert: true}
> db.pokemons.update(query, mod, options)
```

## Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.
```
> var query = {moves : {$in : [/investida/i, /defesa suprema/i]}}
> db.pokemons.find(query)
```

## Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.
```
> var query = {moves : {$in : [/investida/i, /defesa suprema/i, /desvio/i]}}
> db.pokemons.find(query)
```

## Pesquisar todos os pokemons que não são do tipo elétrico.
```
> var query = {type: {$ne: "elétrico"}}
> db.pokemons.find(query)
```

## Pesquisar todos pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49.
```
> var query = {$and: [{moves: {$in : [/investida/i]}}, {defense : {$not : {$lte: 49}}}]}
> db.pokemons.find(query)
```

## Remova todos os pokemons do tipo água e com attack menor que 50.
```
> var query = {$and : [{type: /água/i},{attack: {$lt : 50}}]}
> db.pokemons.remove(query)
```
