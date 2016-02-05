# MongoDB - Aula 04 - Exercício

autor: Amanda Vilela

## 1. Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
amanda-Inspiron-7520(mongod-2.4.9) be-mean> var attacks = ['retirada, dança']

amanda-Inspiron-7520(mongod-2.4.9) be-mean> var mod = {$pushAll: {moves: attacks}}

amanda-Inspiron-7520(mongod-2.4.9) be-mean> var options = {multi: true}

amanda-Inspiron-7520(mongod-2.4.9) be-mean> var query = {name: {$in: ['Pikachu', 'Squirtle', 'Bulbassauro', 'Charmander']}}

amanda-Inspiron-7520(mongod-2.4.9) be-mean> db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 0ms

```

## 2. Adicionar 1 movimento em todos os pokemons: desvio.

```

amanda-Inspiron-7520(mongod-2.4.9) be-mean> var options = {multi: true}

amanda-Inspiron-7520(mongod-2.4.9) be-mean> var query = {}

amanda-Inspiron-7520(mongod-2.4.9) be-mean> var mod = {$push: {moves: 'desvio'}}

amanda-Inspiron-7520(mongod-2.4.9) be-mean> db.pokemons.update(query, mod, options)
Updated 7 existing record(s) in 1ms


```

## 3. Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".

```
amanda-Inspiron-7520(mongod-2.4.9) be-mean> var query = {name: 'NaoExisteMon'}

amanda-Inspiron-7520(mongod-2.4.9) be-mean> var mod = {$set: {active: true}, $setOnInsert:{description: "Sem maiores infomações"}}

amanda-Inspiron-7520(mongod-2.4.9) be-mean> var options = {upsert : true}

amanda-Inspiron-7520(mongod-2.4.9) be-mean> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 1ms

```
## 4. Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.

```
amanda-Inspiron-7520(mongod-2.4.9) be-mean> var query = {moves: {$in: ['investida', 'retirada']}}
amanda-Inspiron-7520(mongod-2.4.9) be-mean> db.pokemons.find(query)
{
  "_id": ObjectId("565bb3c2fbda50ab00fc33ba"),
  "active": false,
  "attack": 8000,
  "defense": 8000,
  "description": "Pokemon de teste",
  "moves": [
    "investida",
    "desvio"
  ],
  "name": "Testemon"
}
{
  "_id": ObjectId("5651f44e2b465aac30102fef"),
  "active": false,
  "attack": 30,
  "defense": 35,
  "description": "Larva lutadora",
  "height": 0.3,
  "moves": [
    "investida",
    "desvio"
  ],
  "name": "Caterpie",
  "type": "inseto"
}
{
  "_id": ObjectId("5651f3132b465aac30102feb"),
  "active": false,
  "attack": 49,
  "description": "Chicote de trepadeira",
  "height": 0.4,
  "moves": [
    "investida",
    "folha navalha",
    "retirada",
    "dança",
    "desvio"
  ],
  "name": "Bulbassauro",
  "type": "grama"
}

{
  "_id": ObjectId("5651f3912b465aac30102fee"),
  "active": false,
  "attack": 48,
  "description": "Ejeta água que passarinho não bebe",
  "height": 0.5,
  "moves": [
    "investida",
    "hidro bomba",
    "retirada",
    "dança",
    "desvio"
  ],
  "name": "Squirtle",
  "type": "água"
}

{
  "_id": ObjectId("569fd0e22658bca3f7ef8e93"),
  "active": false,
  "attack": null,
  "defense": null,
  "description": "Sem maiores informações",
  "height": null,
  "moves": [
    "investida",
    "desvio"
  ],
  "name": "Nao ExisteMon"
}
{
  "_id": ObjectId("5651f21e2b465aac30102fea"),
  "active": false,
  "attack": 55,
  "description": "Rato elétrico bem fofinho",
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "retirada",
    "dança",
    "desvio"
  ],
  "name": "Pikachu",
  "type": "eletric"
}
{
  "_id": ObjectId("5651f3592b465aac30102fed"),
  "active": false,
  "attack": 52,
  "description": "Esse é o cão chupando manga de fofinho",
  "height": 0.6,
  "moves": [
    "investida",
    "lança-chamas",
    "retirada",
    "dança",
    "desvio"
  ],
  "name": "Charmander",
  "type": "fogo"
}
Fetched 7 record(s) in 3ms

```

## 5. Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```
amanda-Inspiron-7520(mongod-2.4.9) be-mean> var query = {moves: {$all: ['dança', 'retirada', 'lança-chamas']}}

amanda-Inspiron-7520(mongod-2.4.9) be-mean> db.pokemons.find(query)
{
  "_id": ObjectId("5651f3592b465aac30102fed"),
  "active": false,
  "attack": 52,
  "description": "Esse é o cão chupando manga de fofinho",
  "height": 0.6,
  "moves": [
    "investida",
    "lança-chamas",
    "retirada, dança",
    "retirada",
    "dança",
    "desvio"
  ],
  "name": "Charmander",
  "type": "fogo"
}
Fetched 1 record(s) in 1ms

```

## 6. Pesquisar todos os pokemons que não são do tipo elétrico.

```

amanda-Inspiron-7520(mongod-2.4.9) be-mean> var query = {moves: {$nin: ['eletrico']}}
amanda-Inspiron-7520(mongod-2.4.9) be-mean> db.pokemons.find(query)
{
  "_id": ObjectId("565bb3c2fbda50ab00fc33ba"),
  "active": false,
  "attack": 8000,
  "defense": 8000,
  "description": "Pokemon de teste",
  "moves": [
    "investida",
    "desvio"
  ],
  "name": "Testemon"
}
{
  "_id": ObjectId("5651f44e2b465aac30102fef"),
  "active": false,
  "attack": 30,
  "defense": 35,
  "description": "Larva lutadora",
  "height": 0.3,
  "moves": [
    "investida",
    "desvio"
  ],
  "name": "Caterpie",
  "type": "inseto"
}
{
  "_id": ObjectId("5651f3132b465aac30102feb"),
  "active": false,
  "attack": 49,
  "description": "Chicote de trepadeira",
  "height": 0.4,
  "moves": [
    "investida",
    "folha navalha",
    "retirada, dança",
    "retirada",
    "dança",
    "desvio"
  ],
  "name": "Bulbassauro",
  "type": "grama"
}
{
  "_id": ObjectId("5651f3912b465aac30102fee"),
  "active": false,
  "attack": 48,
  "description": "Ejeta água que passarinho não bebe",
  "height": 0.5,
  "moves": [
    "investida",
    "hidro bomba",
    "retirada, dança",
    "retirada",
    "dança",
    "desvio"
  ],
  "name": "Squirtle",
  "type": "água"
}
{
  "_id": ObjectId("5651f3592b465aac30102fed"),
  "active": false,
  "attack": 52,
  "description": "Esse é o cão chupando manga de fofinho",
  "height": 0.6,
  "moves": [
    "investida",
    "lança-chamas",
    "retirada, dança",
    "retirada",
    "dança",
    "desvio"
  ],
  "name": "Charmander",
  "type": "fogo"
}
{
  "_id": ObjectId("569ff30c2658bca3f7ef8e94"),
  "active": true,
  "description": "Sem maiores infomações",
  "name": "NaoExisteMon"
}
Fetched 6 record(s) in 2ms

```

## 7. Pesquisar todos os pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49.

```
amanda-Inspiron-7520(mongod-2.4.9) be-mean> var query = {$and: [{defense: {$gt:50}}, {moves: 'investida'}]}

amanda-Inspiron-7520(mongod-2.4.9) be-mean> db.pokemons.find(query)
{
  "_id": ObjectId("565bb3c2fbda50ab00fc33ba"),
  "active": false,
  "attack": 8000,
  "defense": 8000,
  "description": "Pokemon de teste",
  "moves": [
    "investida",
    "desvio"
  ],
  "name": "Testemon"
}
Fetched 1 record(s) in 1ms

```

## 8. Remova todos os pokemons do tipo água e com attack menor que 50.

```
amanda-Inspiron-7520(mongod-2.4.9) be-mean> var query = {$and: [{attack: {$lt:50}}, {type: 'água'}]}

amanda-Inspiron-7520(mongod-2.4.9) be-mean> db.pokemons.remove(query)
Removed 1 record(s) in 1ms

```
