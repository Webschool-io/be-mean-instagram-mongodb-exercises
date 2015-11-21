# MongoDB - Aula 04 - Exercício
autor: Wanderval Carvalho

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```js
var query = {name: /Pikachu/i}  
var mod = {$pushAll: {moves: ['Encarar', 'Agilidade']}}
db.pokemons.update(query, mod)

var query = {name: /Squirtle/i}
var mod = {$pushAll: {moves: ['raio de gelo', 'Retirada']}}
db.pokemons.update(query, mod)

var query = {name: /Bulbasaur/i}
var mod = {$pushAll: {moves: ['Semente Sanguesuga', 'Pó do sono']}}
db.pokemons.update(query, mod)

var query = {name: /Charmander/i}
var mod = {$pushAll: {moves: ['Explosão de chamas', 'Quebra Crânio']}}
db.pokemons.update(query, mod)

//results
db.pokemons.find(query)
{
  "_id": ObjectId("5643a20a2f04f7b0b63ff1fe"),
  "name": "Pikachu",
  "description": "Bichinho folgado amarelo, imitador do blanka do street fighter e ainda traveco usa maquiagem na cara dura",
  "attack": 3,
  "defense": 2,
  "height": 0.4,
  "type": "Eletrico",
  "moves": [
    "investida",
    "Encarar",
    "Agilidade"
  ]
}
db.pokemons.find(query)
{
  "_id": ObjectId("564fc794d457dd17d144f104"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": true,
  "moves": [
    "investida",
    "raio de gelo",
    "Retirada"
  ]
}
db.pokemons.find(query)
{
  "_id": ObjectId("5643fe519e5485fb04160902"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "attack": 3,
  "defense": 2,
  "height": 0.7,
  "type": "Grama",
  "moves": [
    "investida",
    "Semente Sanguesuga",
    "Pó do sono"
  ]
}
db.pokemons.find(query)
{
  "_id": ObjectId("564fd535d457dd17d144f105"),
  "name": "Charmander",
  "description": "Esse é o zangado da branca de neve",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "Explosão de chamas",
    "Quebra Crânio"
  ]
}

```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.

```js
var query = {}
var mod = {$push: {moves: 'desvio'}}
var options = {multi:true}
db.pokemons.update(query, mod,options)
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".

```js
var query = {name:/AindaNaoExisteMon/i}
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
var options = {upsert:true}
db.pokemons.update(query,mod,options)
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.

```js
var query = {moves: {$in: [/investida/i, /arremesso sísmico/i]}}
db.pokemons.find(query)
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```js
var query = {moves: {$in: [/arremesso sísmico/i]}}
db.pokemons.find(query)
```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.

```js
var query = {type:{$not: /eletrico/i}}
db.pokemons.find(query)

```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.

**Se você não tiver Pokemons com valores de `defense` então faça a query para o campo `attack`, como feito abaixo:**

```js
var query = {$and:[{moves:{$in:['investida']}}, {defense:{$not:{$lte:49}}}]}
db.pokemons.find(query)
```

## Remova **todos** os pokemons do tipo água E com attack menor que 50.

```js
var query = {$and:[{type:/água/i},{attack: {$lt:50}}]}
db.pokemons.remove(query)
```

