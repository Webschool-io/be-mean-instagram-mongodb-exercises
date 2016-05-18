# MongoDB - Aula 04 - Exercício
autor: Jackson Ricardo Schroeder


# Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
macminixereda(mongod-3.2.0) be-mean-teste> var query = { $or: [ { name: /pikachu/i }, { name: /squirtle/i }, { name: /bulbassauro/i }, { name: /charmander/i } ] };
macminixereda(mongod-3.2.0) be-mean-teste> var mod = { $pushAll: { moves: [ "gospe leite", "gospe iogurte" ] } };
macminixereda(mongod-3.2.0) be-mean-teste> var options = { multi: true };
macminixereda(mongod-3.2.0) be-mean-teste> db.pokemons.update(query, mod, options);
Updated 4 existing record(s) in 1ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
macminixereda(mongod-3.2.0) be-mean-teste> db.pokemons.find(query);
{
  "_id": ObjectId("573a8a5324450f724f323f15"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "gospe leite",
    "gospe iogurte"
  ],
  "active": false
}
{
  "_id": ObjectId("573a8bbd24450f724f323f16"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "gospe leite",
    "gospe iogurte"
  ]
}
{
  "_id": ObjectId("573a8c0524450f724f323f17"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança chamas",
    "gospe leite",
    "gospe iogurte"
  ]
}
{
  "_id": ObjectId("573a8c6524450f724f323f18"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "gospe leite",
    "gospe iogurte"
  ]
}
Fetched 4 record(s) in 2ms
macminixereda(mongod-3.2.0) be-mean-teste>
```

# Adicionar 1 movimento em todos os pokemons: desvio.

```
macminixereda(mongod-3.2.0) be-mean-teste> var query = {};
macminixereda(mongod-3.2.0) be-mean-teste> var mod = { $push: { moves: "desvio" } };
macminixereda(mongod-3.2.0) be-mean-teste> db.pokemons.update(query, mod, options);
Updated 7 existing record(s) in 1ms
WriteResult({
  "nMatched": 7,
  "nUpserted": 0,
  "nModified": 7
})
```

# Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".

```
macminixereda(mongod-3.2.0) be-mean-teste> var query = { name: /aindanaoexistemon/i };
macminixereda(mongod-3.2.0) be-mean-teste> var mod = { $set: { description: "Sem mais informações" }, $setOnInsert: { name: "AindaNaoExisteMon", type: null, attack: null, defense: null, height: null } };
macminixereda(mongod-3.2.0) be-mean-teste> var options = { upsert: true };
macminixereda(mongod-3.2.0) be-mean-teste> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 2ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("573c17226769febfa5a37278")
})
macminixereda(mongod-3.2.0) be-mean-teste> db.pokemons.find(query);
{
  "_id": ObjectId("573c17226769febfa5a37278"),
  "description": "Sem mais informações",
  "name": "AindaNaoExisteMon",
  "type": null,
  "attack": null,
  "defense": null,
  "height": null
}
Fetched 1 record(s) in 1ms
```

# Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.

```
macminixereda(mongod-3.2.0) be-mean-teste> var query = { moves: { $all: [ /investida/i, /gospe leite/i ] } };
macminixereda(mongod-3.2.0) be-mean-teste> db.pokemons.find(query);
{
  "_id": ObjectId("573a8a5324450f724f323f15"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "gospe leite",
    "gospe iogurte",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("573a8bbd24450f724f323f16"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "gospe leite",
    "gospe iogurte",
    "desvio"
  ]
}
{
  "_id": ObjectId("573a8c0524450f724f323f17"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança chamas",
    "gospe leite",
    "gospe iogurte",
    "desvio"
  ]
}
{
  "_id": ObjectId("573a8c6524450f724f323f18"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "gospe leite",
    "gospe iogurte",
    "desvio"
  ]
}
Fetched 4 record(s) in 2ms
```

# Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```
macminixereda(mongod-3.2.0) be-mean-teste> var query = { moves: { $all: [ /gospe iogurte/i, /gospe leite/i ] } };
macminixereda(mongod-3.2.0) be-mean-teste> db.pokemons.find(query);
```

# Pesquisar todos os pokemons que não são do tipo elétrico.

```
macminixereda(mongod-3.2.0) be-mean-teste> var query = { type: {$ne: "eletric" } };
macminixereda(mongod-3.2.0) be-mean-teste> db.pokemons.find(query);
```

# Pesquisar todos os pokemons que tenham o movimento investida E tenham o defesa não menor ou igual a 49.

```
macminixereda(mongod-3.2.0) be-mean-teste> var query = { $and: [ { moves: {$in: ["investida"] } }, { defense: { $not: { $lte: 49 } } } ] };
macminixereda(mongod-3.2.0) be-mean-teste> query
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
macminixereda(mongod-3.2.0) be-mean-teste> db.pokemons.find(query);
```

# Remova todos os pokemons do tipo água E com attack menor que 50.

```
macminixereda(mongod-3.2.0) be-mean-teste> var query = { $and: [ { type: /Água/i }, { attack: { $lte: 50 } } ] };
macminixereda(mongod-3.2.0) be-mean-teste> db.pokemons.find(query);
{
  "_id": ObjectId("573a8c6524450f724f323f18"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "gospe leite",
    "gospe iogurte",
    "desvio"
  ]
}
Fetched 1 record(s) in 1ms
macminixereda(mongod-3.2.0) be-mean-teste> db.pokemons.remove(query);
Removed 1 record(s) in 1ms
WriteResult({
  "nRemoved": 1
})
macminixereda(mongod-3.2.0) be-mean-teste> db.pokemons.find(query);
Fetched 0 record(s) in 1ms
```
