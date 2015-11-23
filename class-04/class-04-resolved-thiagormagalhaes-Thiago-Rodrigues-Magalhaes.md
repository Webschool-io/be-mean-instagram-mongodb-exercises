# MongoDB - Aula 04 - Exercício
autor: Thiago Rodrigues Magalhães


## 1. **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
thiago(mongod-3.0.7) be-mean-pokemons> var query = {$or: [{name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbassauro/i}, {name: /charmander/i}]}

thiago(mongod-3.0.7) be-mean-pokemons> query
{
  "$or": [
    {
      "name": /pikachu/i
    },
    {
      "name": /squirtle/i
    },
    {
      "name": /bulbassauro/i
    },
    {
      "name": /charmander/i
    }
  ]
}

thiago(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll: {moves: ['investida', 'soco']}}
thiago(mongod-3.0.7) be-mean-pokemons> mod
{
  "$pushAll": {
    "moves": [
      "investida",
      "soco"
    ]
  }
}

thiago(mongod-3.0.7) be-mean-pokemons> var options = {multi: true}
thiago(mongod-3.0.7) be-mean-pokemons> options
{
  "multi": true
}

thiago(mongod-3.0.7) be-mean-pokemons> db.pokemon.update(query, mod, options)
Updated 3 existing record(s) in 7ms
WriteResult({
  "nMatched": 3,
  "nUpserted": 0,
  "nModified": 3
})

thiago(mongod-3.0.7) be-mean-pokemons> db.pokemon.find(query)
{
  "_id": ObjectId("564cde3cbf53d2e2a1796b56"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokemon becomes enraged, the flame burns fiercely.",
  "attack": 3,
  "defense": 2,
  "height": 0.6,
  "moves": [
    "investida",
    "soco"
  ]
}
{
  "_id": ObjectId("564cde4fbf53d2e2a1796b58"),
  "name": "Squirtle",
  "description": "Squirtle shell is not merely used for protection. The shells rounded shape and the grooves on its superface help minimize resistance in water, enabling this Pokemon to swim at hght speeds.",
  "attack": 3,
  "defense": 3,
  "height": 0.5,
  "moves": [
    "investida",
    "soco"
  ]
}
{
  "_id": ObjectId("564cde79bf53d2e2a1796b59"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, its evidence that this Pokemon mistook the intensity of its charge.",
  "attack": 3,
  "defense": 2,
  "height": 0.4,
  "moves": [
    "investida",
    "soco"
  ]
}
Fetched 3 record(s) in 3ms
```

## 2. **Adicionar** 1 movimento em todos os pokemons: desvio.

```
thiago(mongod-3.0.7) be-mean-pokemons> var query = {}
thiago(mongod-3.0.7) be-mean-pokemons> query
{
  
}

thiago(mongod-3.0.7) be-mean-pokemons> var mod = {$push: {moves: 'desvio'}}
thiago(mongod-3.0.7) be-mean-pokemons> mod
{
  "$push": {
    "moves": "desvio"
  }
}

thiago(mongod-3.0.7) be-mean-pokemons> var options = {multi: true}
thiago(mongod-3.0.7) be-mean-pokemons> options
{
  "multi": true
}

thiago(mongod-3.0.7) be-mean-pokemons> db.pokemon.update(query, mod, options)
Updated 5 existing record(s) in 50ms
WriteResult({
  "nMatched": 5,
  "nUpserted": 0,
  "nModified": 5
})

thiago(mongod-3.0.7) be-mean-pokemons> db.pokemon.find(query)
{
  "_id": ObjectId("564cde3cbf53d2e2a1796b56"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokemon becomes enraged, the flame burns fiercely.",
  "attack": 3,
  "defense": 2,
  "height": 0.6,
  "moves": [
    "investida",
    "soco",
    "desvio"
  ]
}
{
  "_id": ObjectId("564cde44bf53d2e2a1796b57"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the suns rays, the seed grows progressively larger.",
  "attack": 3,
  "defense": 2,
  "height": 0.7,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564cde4fbf53d2e2a1796b58"),
  "name": "Squirtle",
  "description": "Squirtle shell is not merely used for protection. The shells rounded shape and the grooves on its superface help minimize resistance in water, enabling this Pokemon to swim at hght speeds.",
  "attack": 3,
  "defense": 3,
  "height": 0.5,
  "moves": [
    "investida",
    "soco",
    "desvio"
  ]
}
{
  "_id": ObjectId("564cde79bf53d2e2a1796b59"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, its evidence that this Pokemon mistook the intensity of its charge.",
  "attack": 3,
  "defense": 2,
  "height": 0.4,
  "moves": [
    "investida",
    "soco",
    "desvio"
  ]
}
{
  "_id": ObjectId("564cde34bf53d2e2a1796b55"),
  "name": "Yveltal",
  "description": "When this legendary Pokemon wings and tail feathers spread wide and glow red, it absorbs the life force of living creatures",
  "attack": 7,
  "defense": 4,
  "height": 5.8,
  "moves": [
    "desvio"
  ]
}
Fetched 5 record(s) in 10ms
```

## 3. **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".

```
thiago(mongod-3.0.7) be-mean-pokemons> var query = {name: 'AindaNaoExisteMon'}

thiago(mongod-3.0.7) be-mean-pokemons> query
{
  "name": "AindaNaoExisteMon"
}

thiago(mongod-3.0.7) be-mean-pokemons> var mod = {$set: {description: 'Sem maiores informações'}, $setOnInsert: {name: 'AindaNaoExisteMon', attack: null, defense: null, height: null, moves: null}}
thiago(mongod-3.0.7) be-mean-pokemons> mod
{
  "$set": {
    "description": "Sem maiores informações"
  },
  "$setOnInsert": {
    "name": "AindaNaoExisteMon",
    "attack": null,
    "defense": null,
    "height": null,
    "moves": null
  }
}

thiago(mongod-3.0.7) be-mean-pokemons> var options = {upsert: true}
thiago(mongod-3.0.7) be-mean-pokemons> options
{
  "upsert": true
}

thiago(mongod-3.0.7) be-mean-pokemons> db.pokemon.update(query, mod, options)
Updated 1 new record(s) in 19ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564ce4cb9639555cc8d2d10c")
})

thiago(mongod-3.0.7) be-mean-pokemons> db.pokemon.find(query)
{
  "_id": ObjectId("564ce4cb9639555cc8d2d10c"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "attack": null,
  "defense": null,
  "height": null,
  "moves": null
}
Fetched 1 record(s) in 1ms
```

## 4. Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.

```
thiago(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$all: ['soco', 'desvio']}}

thiago(mongod-3.0.7) be-mean-pokemons> query
{
  "moves": {
    "$all": [
      "soco",
      "desvio"
    ]
  }
}

thiago(mongod-3.0.7) be-mean-pokemons> db.pokemon.find(query)
{
  "_id": ObjectId("564cde3cbf53d2e2a1796b56"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokemon becomes enraged, the flame burns fiercely.",
  "attack": 3,
  "defense": 2,
  "height": 0.6,
  "moves": [
    "soco",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("564cde4fbf53d2e2a1796b58"),
  "name": "Squirtle",
  "description": "Squirtle shell is not merely used for protection. The shells rounded shape and the grooves on its superface help minimize resistance in water, enabling this Pokemon to swim at hght speeds.",
  "attack": 3,
  "defense": 3,
  "height": 0.5,
  "moves": [
    "soco",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("564cde79bf53d2e2a1796b59"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, its evidence that this Pokemon mistook the intensity of its charge.",
  "attack": 3,
  "defense": 2,
  "height": 0.4,
  "moves": [
    "soco",
    "desvio",
    "investida"
  ]
}
Fetched 3 record(s) in 3ms
```

## 5. Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```
thiago(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$in: ['soco', 'desvio', 'investida']}}

thiago(mongod-3.0.7) be-mean-pokemons> query
{
  "moves": {
    "$in": [
      "soco",
      "desvio",
      "investida"
    ]
  }
}

thiago(mongod-3.0.7) be-mean-pokemons> db.pokemon.find(query)
{
  "_id": ObjectId("564cde3cbf53d2e2a1796b56"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokemon becomes enraged, the flame burns fiercely.",
  "attack": 3,
  "defense": 2,
  "height": 0.6,
  "moves": [
    "soco",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("564cde44bf53d2e2a1796b57"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the suns rays, the seed grows progressively larger.",
  "attack": 3,
  "defense": 2,
  "height": 0.7,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564cde4fbf53d2e2a1796b58"),
  "name": "Squirtle",
  "description": "Squirtle shell is not merely used for protection. The shells rounded shape and the grooves on its superface help minimize resistance in water, enabling this Pokemon to swim at hght speeds.",
  "attack": 3,
  "defense": 3,
  "height": 0.5,
  "moves": [
    "soco",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("564cde79bf53d2e2a1796b59"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, its evidence that this Pokemon mistook the intensity of its charge.",
  "attack": 3,
  "defense": 2,
  "height": 0.4,
  "moves": [
    "soco",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("564cde34bf53d2e2a1796b55"),
  "name": "Yveltal",
  "description": "When this legendary Pokemon wings and tail feathers spread wide and glow red, it absorbs the life force of living creatures",
  "attack": 7,
  "defense": 4,
  "height": 5.8,
  "moves": [
    "desvio"
  ]
}
Fetched 5 record(s) in 4ms
```

## 6. Pesquisar **todos** os pokemons que não são do tipo `elétrico`.
```
thiago(mongod-3.0.7) be-mean-pokemons> var query = {type: 'elétrico'}

thiago(mongod-3.0.7) be-mean-pokemons> query
{
  "type": "elétrico"
}

thiago(mongod-3.0.7) be-mean-pokemons> db.pokemon.find(query)
Fetched 0 record(s) in 0ms

```

## 7. Pesquisar **todos** pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.

```
thiago(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{moves: {$in: ['investida']}}, {defense: {$not: {$lte: 49}}}]}

thiago(mongod-3.0.7) be-mean-pokemons> query
{
  "$and": [
    {
      "moves": {
        "$in": [
          "investida"
        ]
      }
    },
    {
      "defense": {
        "$not": {
          "$lte": 49
        }
      }
    }
  ]
}

thiago(mongod-3.0.7) be-mean-pokemons> db.pokemon.find(query)
Fetched 0 record(s) in 1ms
```

## 8. Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
thiago(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{type: 'water'}, {attack: {$lt: 50}}]}

thiago(mongod-3.0.7) be-mean-pokemons> query
{
  "$and": [
    {
      "type": "water"
    },
    {
      "attack": {
        "$lt": 50
      }
    }
  ]
}

thiago(mongod-3.0.7) be-mean-pokemons> db.pokemon.remove(query)
Removed 0 record(s) in 37ms
WriteResult({
  "nRemoved": 0
})

```