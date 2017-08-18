# MongoDB - Aula 04 - Exercício
autor: Carlos Henrique Ribeiro

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.


```js
var query = {name: /Pikachu/i}
var mod = {$pushAll: {moves: ['Pancada de Raio', 'Descarga']}}
db.pokemons.update(query, mod)

var query = {name: /Squirtle/i}
var mod = {$pushAll: {moves: ['Bolhas', 'Aqua Míssil']}}
db.pokemons.update(query, mod)

var query = {name: /Bulbassauro/i}
var mod = {$pushAll: {moves: ['Absorver', 'Planta Mortal']}}
db.pokemons.update(query, mod)

var query = {name: /Charmander/i}
var mod = {$pushAll: {moves: ['Explosão Incineradora', 'Promessa de Fogo']}}
db.pokemons.update(query, mod)

```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

```js
var query = {}
var mod = {$push: {moves: 'desvio'}}
var options = {multi: true}
db.pokemons.update(query, mod, options)

```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

```js
var query = {name: /AindaNaoExisteMon/i}
var mod = {
    $setOnInsert:
    {
      name: 'AindaNaoExisteMon',
      type: null,
      attack: null,
      defense: null,
      height: null,
      description: 'Sem maiores informações'
    }
}
var options = {
    upsert: true
}
db.pokemons.update(query, mod, options)
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

```js
var query = {
    moves: {
        $in: [/investida/i, /bolhas/i]
        }
    }
db.pokemons.find(query)
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

```js
var query = {moves: {

    $all: [/Pancada de Raio/i, /Descarga/i]

    }
}
db.pokemons.find(query)

```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

```js
var query = {type: {$not: /elétrico/i}}
db.pokemons.find(query)
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

```js
var query = {$and: [ {moves: {$in: ['investida']}}, {attack: {$not: {$lte: 49}}} ]}
db.pokemons.find(query)
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```js
var query = {$and: [ {type: /água/i}, {attack: {$lt: 50}} ]}
db.pokemons.remove(query)
```
