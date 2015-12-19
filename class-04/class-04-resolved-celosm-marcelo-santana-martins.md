# MongoDB - Aula 04 - Exercício
autor: Marcelo Santana Martins

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> var query = { $or: [ {name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbassauro/i}, {name: /charmander/i} ]};
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> var mod = { $pushAll: { moves: ['chutar', 'voar']}};
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> var opts = { multi: true };
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, opts);
Updated 3 existing record(s) in 1ms
WriteResult({
  "nMatched": 3,
  "nUpserted": 0,
  "nModified": 3
})
```


## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> var query = {}
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> var mod = { $push: { moves: "desvio"}}
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> var opts = { multi: true }
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, opts)
Updated 8 existing record(s) in 2ms
WriteResult({
  "nMatched": 8,
  "nUpserted": 0,
  "nModified": 8
})

```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> var query = { name: /AindaNaoExisteMon/i }
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> var mod = { $setOnInsert: { name: "AindaNaoExisteMon", attack: null, height: null, defense: null, moves: [], description: "Sem maiores informações" }};
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> var opts = { upsert: true }
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query,mod,opts)
Updated 1 new record(s) in 1ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564d2609a3ef98ef7fbc24c4")
})
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$in : ['investida', 'voar']}}
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5647cacc7d97c6b63eab93be"),
  "name": "Togetic",
  "description": "Togetic is said to be a Pokémon that brings good fortune.",
  "attack": 20,
  "defense": 40,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564a663b7745546576d26a3c"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "moves": [
    "investida",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("564d0f38a3ef98ef7fbc24c3"),
  "active": false,
  "name": "NaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5647cacc7d97c6b63eab93bb"),
  "name": "Charmander",
  "description": "Chinchou lets loose positive and negative electrical charges from its two antennas to make its prey faint.",
  "attack": 20,
  "defense": 20,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "chutar",
    "voar",
    "desvio"
  ]
}
{
  "_id": ObjectId("5647cacc7d97c6b63eab93bc"),
  "name": "Pichu",
  "description": "Pichu charges itself with electricity more easily on days with thunderclouds or when the air is very dry.",
  "attack": 20,
  "defense": 10,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5647cacc7d97c6b63eab93bd"),
  "name": "Bulbassauro",
  "description": "As its energy, Togepi uses the positive emotions of compassion and pleasure exuded by people and Pokémon",
  "attack": 10,
  "defense": 30,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "chutar",
    "voar",
    "desvio"
  ]
}
{
  "_id": ObjectId("564d0d75a3ef98ef7fbc24c2"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5647cacc7d97c6b63eab93ba"),
  "name": "Squirtle",
  "description": "Squirtles shell is not merely used for protection.",
  "attack": 30,
  "defense": 30,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "chutar",
    "voar",
    "desvio"
  ]
}
Fetched 8 record(s) in 1ms
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> 
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> 
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> 
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> cls

marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$in : ['investida', 'voar']}}
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5647cacc7d97c6b63eab93be"),
  "name": "Togetic",
  "description": "Togetic is said to be a Pokémon that brings good fortune.",
  "attack": 20,
  "defense": 40,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564a663b7745546576d26a3c"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "moves": [
    "investida",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("564d0f38a3ef98ef7fbc24c3"),
  "active": false,
  "name": "NaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5647cacc7d97c6b63eab93bb"),
  "name": "Charmander",
  "description": "Chinchou lets loose positive and negative electrical charges from its two antennas to make its prey faint.",
  "attack": 20,
  "defense": 20,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "chutar",
    "voar",
    "desvio"
  ]
}
{
  "_id": ObjectId("5647cacc7d97c6b63eab93bc"),
  "name": "Pichu",
  "description": "Pichu charges itself with electricity more easily on days with thunderclouds or when the air is very dry.",
  "attack": 20,
  "defense": 10,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5647cacc7d97c6b63eab93bd"),
  "name": "Bulbassauro",
  "description": "As its energy, Togepi uses the positive emotions of compassion and pleasure exuded by people and Pokémon",
  "attack": 10,
  "defense": 30,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "chutar",
    "voar",
    "desvio"
  ]
}
{
  "_id": ObjectId("564d0d75a3ef98ef7fbc24c2"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5647cacc7d97c6b63eab93ba"),
  "name": "Squirtle",
  "description": "Squirtles shell is not merely used for protection.",
  "attack": 30,
  "defense": 30,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "chutar",
    "voar",
    "desvio"
  ]
}
Fetched 8 record(s) in 1ms
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$in: ['voar']}}
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5647cacc7d97c6b63eab93bb"),
  "name": "Charmander",
  "description": "Chinchou lets loose positive and negative electrical charges from its two antennas to make its prey faint.",
  "attack": 20,
  "defense": 20,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "chutar",
    "voar",
    "desvio"
  ]
}
{
  "_id": ObjectId("5647cacc7d97c6b63eab93bd"),
  "name": "Bulbassauro",
  "description": "As its energy, Togepi uses the positive emotions of compassion and pleasure exuded by people and Pokémon",
  "attack": 10,
  "defense": 30,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "chutar",
    "voar",
    "desvio"
  ]
}
{
  "_id": ObjectId("5647cacc7d97c6b63eab93ba"),
  "name": "Squirtle",
  "description": "Squirtles shell is not merely used for protection.",
  "attack": 30,
  "defense": 30,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "chutar",
    "voar",
    "desvio"
  ]
}
Fetched 3 record(s) in 1ms
```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> var query = { moves: {$nin : ['eletrico']}}
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5647cacc7d97c6b63eab93be"),
  "name": "Togetic",
  "description": "Togetic is said to be a Pokémon that brings good fortune.",
  "attack": 20,
  "defense": 40,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564a663b7745546576d26a3c"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "moves": [
    "investida",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("564d0f38a3ef98ef7fbc24c3"),
  "active": false,
  "name": "NaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5647cacc7d97c6b63eab93bb"),
  "name": "Charmander",
  "description": "Chinchou lets loose positive and negative electrical charges from its two antennas to make its prey faint.",
  "attack": 20,
  "defense": 20,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "chutar",
    "voar",
    "desvio"
  ]
}
{
  "_id": ObjectId("5647cacc7d97c6b63eab93bc"),
  "name": "Pichu",
  "description": "Pichu charges itself with electricity more easily on days with thunderclouds or when the air is very dry.",
  "attack": 20,
  "defense": 10,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5647cacc7d97c6b63eab93bd"),
  "name": "Bulbassauro",
  "description": "As its energy, Togepi uses the positive emotions of compassion and pleasure exuded by people and Pokémon",
  "attack": 10,
  "defense": 30,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "chutar",
    "voar",
    "desvio"
  ]
}
{
  "_id": ObjectId("564d0d75a3ef98ef7fbc24c2"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5647cacc7d97c6b63eab93ba"),
  "name": "Squirtle",
  "description": "Squirtles shell is not merely used for protection.",
  "attack": 30,
  "defense": 30,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "chutar",
    "voar",
    "desvio"
  ]
}
{
  "_id": ObjectId("564d2609a3ef98ef7fbc24c4"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "height": null,
  "defense": null,
  "moves": [ ],
  "description": "Sem maiores informações"
}
Fetched 9 record(s) in 1ms
```


## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> var query = { $and: [{ moves: { $in: [/investida/i] }}, { defense: { $not: { $lte: 49 } } }]}
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564a663b7745546576d26a3c"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "moves": [
    "investida",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("564d0f38a3ef98ef7fbc24c3"),
  "active": false,
  "name": "NaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564d0d75a3ef98ef7fbc24c2"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
Fetched 3 record(s) in 0ms
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{attack: {$lt: 50}}, {type: /água/i}]}
marcelo-VirtualBox(mongod-3.0.7) be-mean-pokemons> db.pokemons.remove(query)
Removed 0 record(s) in 1ms
WriteResult({
  "nRemoved": 0
})
```