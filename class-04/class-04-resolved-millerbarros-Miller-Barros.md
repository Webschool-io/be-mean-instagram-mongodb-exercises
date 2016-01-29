# MongoDB - Aula 04 - Exercício
autor: Miller Barros

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Raichu, Bulbasaur e Nidoran.
```
miller-nt(mongod-3.0.7) be-mean-pokemons> var query = {name: {$in: [/pikachu/i, /raichu/i, /bulbasaur/i, /nidoran/i]}}
miller-nt(mongod-3.0.7) be-mean-pokemons> var mod = {$set: {attacks: ['investida', 'voadora']}}
miller-nt(mongod-3.0.7) be-mean-pokemons> var opts = {multi: true}
miller-nt(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, opts)
Updated 4 existing record(s) in 1ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
miller-nt(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643fcd754d8612c0d6f4c28"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "attack": 30,
  "defense": 20,
  "height": 0.7,
  "attacks": [
    "investida",
    "voadora"
  ]
}
{
  "_id": ObjectId("5643fcd754d8612c0d6f4c29"),
  "name": "Pikachu",
  "description": "O pokemon do Ash",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "attacks": [
    "investida",
    "voadora"
  ]
}
{
  "_id": ObjectId("5643fcd754d8612c0d6f4c2a"),
  "name": "Raichu",
  "description": "If the electrical sacs become excessively charged, Raichu plants its tail in the ground and discharges. Scorched patches of ground will be found near this Pokémon's nest.",
  "attack": 50,
  "defense": 30,
  "height": 0.8,
  "attacks": [
    "investida",
    "voadora"
  ]
}
{
  "_id": ObjectId("5643fcd754d8612c0d6f4c2b"),
  "name": "Nidoran",
  "description": "Nidoran? has barbs that secrete a powerful poison. They are thought to have developed as protection for this small-bodied Pokémon. When enraged, it releases a horrible toxin from its horn.",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "attacks": [
    "investida",
    "voadora"
  ]
}
Fetched 4 record(s) in 2ms
```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.
```
miller-nt(mongod-3.0.7) be-mean-pokemons> var query = {}
miller-nt(mongod-3.0.7) be-mean-pokemons> var mod = {$push: {moves: "desvio"}}
miller-nt(mongod-3.0.7) be-mean-pokemons> var opts = {multi: true}
miller-nt(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, opts)
Updated 5 existing record(s) in 1ms
WriteResult({
  "nMatched": 5,
  "nUpserted": 0,
  "nModified": 5
})
miller-nt(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643fcd754d8612c0d6f4c28"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "attack": 30,
  "defense": 20,
  "height": 0.7,
  "attacks": [
    "investida",
    "voadora"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5643fcd754d8612c0d6f4c29"),
  "name": "Pikachu",
  "description": "O pokemon do Ash",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "attacks": [
    "investida",
    "voadora"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5643fcd754d8612c0d6f4c2a"),
  "name": "Raichu",
  "description": "If the electrical sacs become excessively charged, Raichu plants its tail in the ground and discharges. Scorched patches of ground will be found near this Pokémon's nest.",
  "attack": 50,
  "defense": 30,
  "height": 0.8,
  "attacks": [
    "investida",
    "voadora"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5643fcd754d8612c0d6f4c2b"),
  "name": "Nidoran",
  "description": "Nidoran? has barbs that secrete a powerful poison. They are thought to have developed as protection for this small-bodied Pokémon. When enraged, it releases a horrible toxin from its horn.",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "attacks": [
    "investida",
    "voadora"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5643fcd754d8612c0d6f4c2c"),
  "name": "Nidoqueen",
  "description": "Nidoqueen's body is encased in extremely hard scales. It is adept at sending foes flying with harsh tackles. This Pokémon is at its strongest when it is defending its young.",
  "attack": 50,
  "defense": 40,
  "height": 1.3,
  "moves": [
    "desvio"
  ]
}
Fetched 5 record(s) in 3ms
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".
```
miller-nt(mongod-3.0.7) be-mean-pokemons> var query = {name: 'AindaNaoExisteMon'}
miller-nt(mongod-3.0.7) be-mean-pokemons> var mod = {$set: {description: 'Sem maiores informações'}, $setOnInsert: {name: 'AindaNaoExisteMon', attack: null, defense: null, height: null}}
miller-nt(mongod-3.0.7) be-mean-pokemons> var opts = {upsert: true}
miller-nt(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, opts)
Updated 1 new record(s) in 3ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("565679ca56581f73436aff07")
})
miller-nt(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({name: /aindanaoexistemon/i})
{
  "_id": ObjectId("565679ca56581f73436aff07"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "attack": null,
  "defense": null,
  "height": null
}
Fetched 1 record(s) in 1ms
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.
```
miller-nt(mongod-3.0.7) be-mean-pokemons> var query = {$or: [{attacks: {$in: [/investida/i]}}, {name: /nidoran/i}]}
miller-nt(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643fcd754d8612c0d6f4c28"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "attack": 30,
  "defense": 20,
  "height": 0.7,
  "attacks": [
    "investida",
    "voadora"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5643fcd754d8612c0d6f4c29"),
  "name": "Pikachu",
  "description": "O pokemon do Ash",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "attacks": [
    "investida",
    "voadora"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5643fcd754d8612c0d6f4c2a"),
  "name": "Raichu",
  "description": "If the electrical sacs become excessively charged, Raichu plants its tail in the ground and discharges. Scorched patches of ground will be found near this Pokémon's nest.",
  "attack": 50,
  "defense": 30,
  "height": 0.8,
  "attacks": [
    "investida",
    "voadora"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5643fcd754d8612c0d6f4c2b"),
  "name": "Nidoran",
  "description": "Nidoran? has barbs that secrete a powerful poison. They are thought to have developed as protection for this small-bodied Pokémon. When enraged, it releases a horrible toxin from its horn.",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "attacks": [
    "investida",
    "voadora"
  ],
  "moves": [
    "desvio"
  ]
}
Fetched 4 record(s) in 2ms
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.
```
miller-nt(mongod-3.0.7) be-mean-pokemons> var query = {$or: [{attacks: {$in: [/investida/i, /voadora/i]}}, {name: /nidoran/i}]}
miller-nt(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643fcd754d8612c0d6f4c28"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "attack": 30,
  "defense": 20,
  "height": 0.7,
  "attacks": [
    "investida",
    "voadora"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5643fcd754d8612c0d6f4c29"),
  "name": "Pikachu",
  "description": "O pokemon do Ash",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "attacks": [
    "investida",
    "voadora"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5643fcd754d8612c0d6f4c2a"),
  "name": "Raichu",
  "description": "If the electrical sacs become excessively charged, Raichu plants its tail in the ground and discharges. Scorched patches of ground will be found near this Pokémon's nest.",
  "attack": 50,
  "defense": 30,
  "height": 0.8,
  "attacks": [
    "investida",
    "voadora"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5643fcd754d8612c0d6f4c2b"),
  "name": "Nidoran",
  "description": "Nidoran? has barbs that secrete a powerful poison. They are thought to have developed as protection for this small-bodied Pokémon. When enraged, it releases a horrible toxin from its horn.",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "attacks": [
    "investida",
    "voadora"
  ],
  "moves": [
    "desvio"
  ]
}
Fetched 4 record(s) in 3ms
```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.
```
miller-nt(mongod-3.0.7) be-mean-pokemons> var query = {type: {$nin: [/elétrico/i]}}
miller-nt(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643fcd754d8612c0d6f4c28"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "attack": 30,
  "defense": 20,
  "height": 0.7,
  "attacks": [
    "investida",
    "voadora"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5643fcd754d8612c0d6f4c29"),
  "name": "Pikachu",
  "description": "O pokemon do Ash",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "attacks": [
    "investida",
    "voadora"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5643fcd754d8612c0d6f4c2a"),
  "name": "Raichu",
  "description": "If the electrical sacs become excessively charged, Raichu plants its tail in the ground and discharges. Scorched patches of ground will be found near this Pokémon's nest.",
  "attack": 50,
  "defense": 30,
  "height": 0.8,
  "attacks": [
    "investida",
    "voadora"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5643fcd754d8612c0d6f4c2b"),
  "name": "Nidoran",
  "description": "Nidoran? has barbs that secrete a powerful poison. They are thought to have developed as protection for this small-bodied Pokémon. When enraged, it releases a horrible toxin from its horn.",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "attacks": [
    "investida",
    "voadora"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5643fcd754d8612c0d6f4c2c"),
  "name": "Nidoqueen",
  "description": "Nidoqueen's body is encased in extremely hard scales. It is adept at sending foes flying with harsh tackles. This Pokémon is at its strongest when it is defending its young.",
  "attack": 50,
  "defense": 40,
  "height": 1.3,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("565679ca56581f73436aff07"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "attack": null,
  "defense": null,
  "height": null
}
Fetched 6 record(s) in 1ms
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 20.
```
miller-nt(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{attacks: {$in: [/investida/i]}}, {defense: {$not: {$lte: 20}}}]}
miller-nt(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643fcd754d8612c0d6f4c2a"),
  "name": "Raichu",
  "description": "If the electrical sacs become excessively charged, Raichu plants its tail in the ground and discharges. Scorched patches of ground will be found near this Pokémon's nest.",
  "attack": 50,
  "defense": 30,
  "height": 0.8,
  "attacks": [
    "investida",
    "voadora"
  ],
  "moves": [
    "desvio"
  ]
}
Fetched 1 record(s) in 1ms
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
miller-nt(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{type: /água/i}, {attack: {$lt: 50}}]}
miller-nt(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```
