# MongoDB - Aula 04 - Exercício
autor: RAFAEL CARDOSO COELHO

## 1. **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander
```js
var query = {name: /pikachu/i}
var mod = {$pushAll: {moves: ['choque do trovão', 'esfera elétrica']}}
db.pokemons.update(query, mod)

Updated 1 existing record(s) in 3ms
WriteResult({
    "nMatched": 1,
    "nUpserted": 0,
    "nModified": 1
})

var query = {name: /squirtle/i}
var mod = {$pushAll: {moves: ['raio de gelo', 'giro rápido']}}
db.pokemons.update(query, mod)

Updated 1 existing record(s) in 1ms
WriteResult({
    "nMatched": 1,
    "nUpserted": 0,
    "nModified": 1
})

var query = {name: /bulbassauro/i}
var mod = {$pushAll: {moves: ['raio solar', 'dança de pétalas']}}
db.pokemons.update(query, mod)

Updated 1 existing record(s) in 1ms
WriteResult({
    "nMatched": 1,
    "nUpserted": 0,
    "nModified": 1
})

var query = {name: /charmander/i}
var mod = {$pushAll: {moves: ['lança chamas', 'encarar']}}
db.pokemons.update(query, mod)

Updated 1 existing record(s) in 1ms
WriteResult({
    "nMatched": 1,
    "nUpserted": 0,
    "nModified": 1
})
```

## 2. **Adicionar** 1 movimento em todos os pokemons: `desvio`
```js
var query = {}
var mod = {$push: {moves: 'desvio'}}
var options = {multi: true}
db.pokemons.update(query, mod, options)

Updated 5 existing record(s) in 77ms
WriteResult({
    "nMatched": 5,
    "nUpserted": 0,
    "nModified": 5
})
```

## 3. **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações"
```js
var query = {name: /AindaNaoExisteMon/i}
var mod = {setOnInsert: {name: 'AindaNaoExisteMon', description: 'Sem mais informações', type: null, attack: null, height: null}}
var options = {upsert: true}
db.pokemons.update(query, mod, options)
```

## 4. Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito
```js
var query = {moves: {$in: [/investida/i, /lança chamas/i]}}
db.pokemons.find(query)

{
    "_id": ObjectId("567d868e2e0ccbf23142f362"),
    "name": "Charmander",
    "description": "Esse é o cão chupando manga de fofinho",
    "type": "fogo",
    "attack": 52,
    "height": 0.6,
    "moves": [
        "lança chamas",
        "encarar",
        "desvio"
    ]
}
Fetched 1 record(s) in 2ms
```

## 5. Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito
```js
var query = {moves: {$all: [/encarar/i, /lança chamas/i]}}
db.pokemons.find(query)

{
    "_id": ObjectId("567d868e2e0ccbf23142f362"),
    "name": "Charmander",
    "description": "Esse é o cão chupando manga de fofinho",
    "type": "fogo",
    "attack": 52,
    "height": 0.6,
    "moves": [
        "lança chamas",
        "encarar",
        "desvio"
    ]
}
Fetched 1 record(s) in 2ms
```

## 6. Pesquisar **todos** os pokemons que não são do tipo `elétrico`
```js
var query = {type: {$not: /elétrico/i}}
db.pokemons.find(query)

{
    "_id": ObjectId("567d86682e0ccbf23142f361"),
    "name": "Bulbassauro",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 49,
    "height": 0.4,
    "moves": [
        "raio solar",
        "dança de pétalas",
        "desvio"
    ]
}
{
    "_id": ObjectId("567d868e2e0ccbf23142f362"),
    "name": "Charmander",
    "description": "Esse é o cão chupando manga de fofinho",
    "type": "fogo",
    "attack": 52,
    "height": 0.6,
    "moves": [
        "lança chamas",
        "encarar",
        "desvio"
    ]
}
{
    "_id": ObjectId("567d86ae2e0ccbf23142f363"),
    "name": "Squirtle",
    "description": "Ejeta água que passarinho não bebe",
    "type": "água",
    "attack": 48,
    "height": 0.5,
    "moves": [
        "raio de gelo",
        "giro rápido",
        "desvio"
    ]
}
{
    "_id": ObjectId("567d8f1cdc3c391d5ec3769a"),
    "name": "Cartepie",
    "description": "Larva lutadora",
    "type": "inseto",
    "attack": 30,
    "height": 0.3,
    "defense": 35,
    "moves": [
        "desvio"
    ]
}
Fetched 4 record(s) in 4ms
```

## 7. Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49

**Se você não tiver Pokemons com valores de `defense` então faça a query para o campo `attack`, como feito abaixo:**
```js
var query = {$and: [{moves: {$in: ['investida']}}, {attack: {$not: {$lte: 49}}}]}
db.pokemons.find(query)

Fetched 0 record(s) in 1ms
```

## 8. Remova **todos** os pokemons do tipo água E com attack menor que 50
```js
var query = {$and: [{type: /água/i}, {attack: {$lt: 50}}]}
db.pokemons.remove(query)

Removed 1 record(s) in 2ms
WriteResult({
    "nRemoved": 1
})
```