# MongoDB - Aula 04 - Exercício
autor: Douglas Salin Zuqueto

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```javascript
fedora(mongod-3.0.4) be-mean-pokemons> var q = {name: {$in:[/bulbasaur/i, /charmander/i, /squirtle/i,/pikachu/i]}}
fedora(mongod-3.0.4) be-mean-pokemons> m = {$pushAll:{moves:['ataque1','ataque2']}}
fedora(mongod-3.0.4) be-mean-pokemons> var o = {multi:true}
fedora(mongod-3.0.4) be-mean-pokemons> db.pokemons.update(q,m,o)

fedora(mongod-3.0.4) be-mean-pokemons> db.pokemons.find(q)
{
  "_id": ObjectId("56546206f242e0f8e8d0e1e2"),
  "name": "Pikachu",
  "description": "Modificando a Descrição do Pikachu",
  "attack": "30",
  "defense": null,
  "height": "0.4",
  "moves": [
    "Choque do Trovão",
    "ataque para todos os pokemons",
    "ataque1",
    "ataque2"
  ]
}
{
  "_id": ObjectId("5654df224c073b416125c7fd"),
  "attack": 48,
  "created": "2013-11-03T15:05:41.278310",
  "defense": 65,
  "height": "5",
  "hp": 44,
  "name": "Squirtle",
  "speed": 43,
  "types": [
    "water"
  ],
  "moves": [
    "ataque1",
    "ataque2"
  ]
}
{
  "_id": ObjectId("5654df764c073b416125c7fe"),
  "attack": 52,
  "created": "2013-11-03T15:05:41.271082",
  "defense": 43,
  "height": "6",
  "hp": 39,
  "name": "Charmander",
  "speed": 65,
  "types": [
    "fire"
  ],
  "moves": [
    "ataque1",
    "ataque2"
  ]
}
{
  "_id": ObjectId("5654dfa24c073b416125c7ff"),
  "attack": 49,
  "created": "2013-11-03T15:05:41.260678",
  "defense": 49,
  "height": "7",
  "hp": 45,
  "name": "Bulbasaur",
  "speed": 45,
  "types": [
    "poison",
    "grass"
  ],
  "moves": [
    "ataque1",
    "ataque2"
  ]
}
Fetched 4 record(s) in 2ms

```

## 2. **Adicionar** 1 movimento em todos os pokemons: 'desvio'.

```javascript
fedora(mongod-3.0.4) be-mean-pokemons> var q = {}
fedora(mongod-3.0.4) be-mean-pokemons> var m = {$push: {moves:'desvio'}}
fedora(mongod-3.0.4) be-mean-pokemons> var o = {multi:true}
fedora(mongod-3.0.4) be-mean-pokemons> db.pokemons.update(q,m,o)
Updated 11 existing record(s) in 4ms
WriteResult({
  "nMatched": 11,
  "nUpserted": 0,
  "nModified": 11
})

fedora(mongod-3.0.4) be-mean-pokemons> db.pokemons.find(q)
{
  "_id": ObjectId("56546206f242e0f8e8d0e1e4"),
  "name": "Nidoran",
  "description": "Nidoran? has barbs that secrete a powerful poison.",
  "attack": "30",
  "defense": null,
  "height": "0.4",
  "moves": [
    "ataque para todos os pokemons",
    "desvio"
  ]
}
{
  "_id": ObjectId("5654a6d278f162f96c14f803"),
  "name": "Testemon",
  "attack": 7991,
  "defense": null,
  "height": 3.1,
  "description": "Pokemon de teste",
  "moves": [
    /teste/,
    "teste",
    "ataque para todos os pokemons",
    "desvio"
  ]
}
{
  "_id": ObjectId("56546206f242e0f8e8d0e1e2"),
  "name": "Pikachu",
  "description": "Modificando a Descrição do Pikachu",
  "attack": "30",
  "defense": null,
  "height": "0.4",
  "moves": [
    "Choque do Trovão",
    "ataque para todos os pokemons",
    "ataque1",
    "ataque2",
    "desvio"
  ]
}
{
  "_id": ObjectId("56546206f242e0f8e8d0e1e5"),
  "name": "Raichu",
  "description": "If the electrical sacs become excessively charged, Raichu plants its tail in the ground and discharges.",
  "attack": "50",
  "defense": null,
  "height": "0.8",
  "moves": [
    "ataque para todos os pokemons",
    "desvio"
  ]
}
{
  "_id": ObjectId("56546206f242e0f8e8d0e1e6"),
  "name": "Sandshrew",
  "description": "Sandshrew's body is configured to absorb water without waste, enabling it to survive in an arid desert.",
  "attack": "40",
  "defense": null,
  "height": "0.6",
  "moves": [
    "ataque para todos os pokemons",
    "desvio"
  ]
}
{
  "_id": ObjectId("5654b30de253f3e89013d82d"),
  "active": true,
  "defense": null,
  "moves": [
    "ataque para todos os pokemons",
    "desvio"
  ]
}
{
  "_id": ObjectId("5654b46ae253f3e89013d82e"),
  "active": true,
  "name": "NaoExiste",
  "attack": null,
  "defense": null,
  "description": "Sem maiores informacoes",
  "moves": [
    "ataque para todos os pokemons",
    "desvio"
  ]
}
{
  "_id": ObjectId("5654df224c073b416125c7fd"),
  "attack": 48,
  "created": "2013-11-03T15:05:41.278310",
  "defense": 65,
  "height": "5",
  "hp": 44,
  "name": "Squirtle",
  "speed": 43,
  "types": [
    "water"
  ],
  "moves": [
    "ataque1",
    "ataque2",
    "desvio"
  ]
}
{
  "_id": ObjectId("5654df764c073b416125c7fe"),
  "attack": 52,
  "created": "2013-11-03T15:05:41.271082",
  "defense": 43,
  "height": "6",
  "hp": 39,
  "name": "Charmander",
  "speed": 65,
  "types": [
    "fire"
  ],
  "moves": [
    "ataque1",
    "ataque2",
    "desvio"
  ]
}
{
  "_id": ObjectId("56546206f242e0f8e8d0e1e3"),
  "name": "Sandslash",
  "description": "Sandslash's body is covered by tough spikes, which are hardened sections of its hide.",
  "attack": "50",
  "defense": null,
  "height": "1.0",
  "moves": [
    "ataque para todos os pokemons",
    "desvio"
  ]
}
{
  "_id": ObjectId("5654dfa24c073b416125c7ff"),
  "attack": 49,
  "created": "2013-11-03T15:05:41.260678",
  "defense": 49,
  "height": "7",
  "hp": 45,
  "name": "Bulbasaur",
  "speed": 45,
  "types": [
    "poison",
    "grass"
  ],
  "moves": [
    "ataque1",
    "ataque2",
    "desvio"
  ]
}
Fetched 11 record(s) in 1ms

```

## 3. Adicionar o pokemon 'AindaNaoExisteMon' caso ele nao exista com todos os dados com o valor 'null' e a descricao: 'Sem maiores informacoes'.

```javascript
fedora(mongod-3.0.4) be-mean-pokemons> q = {name: 'AindaNaoExisteMon'}
fedora(mongod-3.0.4) be-mean-pokemons> m = {$setOnInsert:{attack:null,defense:null,name:'AindaNaoExisteMon', description: 'Sem maiores informações', height:4}}
{
  "$setOnInsert": {
    "attack": null,
    "defense": null,
    "name": "AindaNaoExisteMon",
    "description": "Sem maiores informações",
    "height": 4
  }
}
fedora(mongod-3.0.4) be-mean-pokemons> o = {upsert:true}
fedora(mongod-3.0.4) be-mean-pokemons> db.pokemons.update(q,m,o)
Updated 1 new record(s) in 1ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("5654f016e253f3e89013d82f")
})

fedora(mongod-3.0.4) be-mean-pokemons> db.pokemons.find(q)
{
  "_id": ObjectId("5654f016e253f3e89013d82f"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "description": "Sem maiores informações",
  "height": 4
}
Fetched 1 record(s) in 1ms

```

## 4. Pesquisar todos os pokemons que possuam o ataque 'investida' e mais um que voce adicionou, escolha seu pokemon favorito.

```javascript
fedora(mongod-3.0.4) be-mean-pokemons> q = {moves:{$in:['investida','ataque1']}, name:{$in:[/pikachu/i]}}
{
  "moves": {
    "$in": [
      "investida",
      "ataque1"
    ]
  },
  "name": {
    "$in": [
      /pikachu/i
    ]
  }
}
fedora(mongod-3.0.4) be-mean-pokemons> db.pokemons.find(q)
{
  "_id": ObjectId("56546206f242e0f8e8d0e1e2"),
  "name": "Pikachu",
  "description": "Modificando a Descrição do Pikachu",
  "attack": "30",
  "defense": null,
  "height": "0.4",
  "moves": [
    "Choque do Trovão",
    "ataque para todos os pokemons",
    "ataque1",
    "ataque2",
    "desvio"
  ]
}
Fetched 1 record(s) in 1ms

```


## 5. Pesquisar todos os pokemons que possuam os ataques que voce adicionou, escolha seu pokemon favorito.

```javascript
fedora(mongod-3.0.4) be-mean-pokemons> q = {moves:{$in:['ataque1','ataque2']}, name:{$in:[/squirtle/i]}}
{
  "moves": {
    "$in": [
      "ataque1",
      "ataque2"
    ]
  },
  "name": {
    "$in": [
      /squirtle/i
    ]
  }
}
fedora(mongod-3.0.4) be-mean-pokemons> db.pokemons.find(q)
{
  "_id": ObjectId("5654df224c073b416125c7fd"),
  "attack": 48,
  "created": "2013-11-03T15:05:41.278310",
  "defense": 65,
  "height": "5",
  "hp": 44,
  "name": "Squirtle",
  "speed": 43,
  "types": [
    "water"
  ],
  "moves": [
    "ataque1",
    "ataque2",
    "desvio"
  ]
}
Fetched 1 record(s) in 1ms

```

## 6. Pesquisar todos os pokemons que nao sao do tipo 'eletrico'.

```javascript
fedora(mongod-3.0.4) be-mean-pokemons> q = {type:{$ne:'electric'}}
{
  "type": {
    "$ne": "electric"
  }
}
fedora(mongod-3.0.4) be-mean-pokemons> db.pokemons.find(q)
{
  "_id": ObjectId("56546206f242e0f8e8d0e1e4"),
  "name": "Nidoran",
  "description": "Nidoran? has barbs that secrete a powerful poison.",
  "attack": "30",
  "defense": null,
  "height": "0.4",
  "moves": [
    "ataque para todos os pokemons",
    "desvio"
  ]
}
{
  "_id": ObjectId("5654a6d278f162f96c14f803"),
  "name": "Testemon",
  "attack": 7991,
  "defense": null,
  "height": 3.1,
  "description": "Pokemon de teste",
  "moves": [
    /teste/,
    "teste",
    "ataque para todos os pokemons",
    "desvio"
  ]
}
{
  "_id": ObjectId("56546206f242e0f8e8d0e1e2"),
  "name": "Pikachu",
  "description": "Modificando a Descrição do Pikachu",
  "attack": "30",
  "defense": null,
  "height": "0.4",
  "moves": [
    "Choque do Trovão",
    "ataque para todos os pokemons",
    "ataque1",
    "ataque2",
    "desvio"
  ]
}
{
  "_id": ObjectId("56546206f242e0f8e8d0e1e5"),
  "name": "Raichu",
  "description": "If the electrical sacs become excessively charged, Raichu plants its tail in the ground and discharges.",
  "attack": "50",
  "defense": null,
  "height": "0.8",
  "moves": [
    "ataque para todos os pokemons",
    "desvio"
  ]
}
{
  "_id": ObjectId("56546206f242e0f8e8d0e1e6"),
  "name": "Sandshrew",
  "description": "Sandshrew's body is configured to absorb water without waste, enabling it to survive in an arid desert.",
  "attack": "40",
  "defense": null,
  "height": "0.6",
  "moves": [
    "ataque para todos os pokemons",
    "desvio"
  ]
}
{
  "_id": ObjectId("5654b30de253f3e89013d82d"),
  "active": true,
  "defense": null,
  "moves": [
    "ataque para todos os pokemons",
    "desvio"
  ]
}
{
  "_id": ObjectId("5654b46ae253f3e89013d82e"),
  "active": true,
  "name": "NaoExiste",
  "attack": null,
  "defense": null,
  "description": "Sem maiores informacoes",
  "moves": [
    "ataque para todos os pokemons",
    "desvio"
  ]
}
{
  "_id": ObjectId("5654df224c073b416125c7fd"),
  "attack": 48,
  "created": "2013-11-03T15:05:41.278310",
  "defense": 65,
  "height": "5",
  "hp": 44,
  "name": "Squirtle",
  "speed": 43,
  "types": [
    "water"
  ],
  "moves": [
    "ataque1",
    "ataque2",
    "desvio"
  ]
}
{
  "_id": ObjectId("5654df764c073b416125c7fe"),
  "attack": 52,
  "created": "2013-11-03T15:05:41.271082",
  "defense": 43,
  "height": "6",
  "hp": 39,
  "name": "Charmander",
  "speed": 65,
  "types": [
    "fire"
  ],
  "moves": [
    "ataque1",
    "ataque2",
    "desvio"
  ]
}
{
  "_id": ObjectId("56546206f242e0f8e8d0e1e3"),
  "name": "Sandslash",
  "description": "Sandslash's body is covered by tough spikes, which are hardened sections of its hide.",
  "attack": "50",
  "defense": null,
  "height": "1.0",
  "moves": [
    "ataque para todos os pokemons",
    "desvio"
  ]
}
{
  "_id": ObjectId("5654dfa24c073b416125c7ff"),
  "attack": 49,
  "created": "2013-11-03T15:05:41.260678",
  "defense": 49,
  "height": "7",
  "hp": 45,
  "name": "Bulbasaur",
  "speed": 45,
  "types": [
    "poison",
    "grass"
  ],
  "moves": [
    "ataque1",
    "ataque2",
    "desvio"
  ]
}
{
  "_id": ObjectId("5654f016e253f3e89013d82f"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "description": "Sem maiores informações",
  "height": 4,
  "moves": [
    "investida"
  ]
}
Fetched 12 record(s) in 2ms

```

## 7. Pesquisar todos os pokemons que tenha o ataque 'investida' E tenham a defesa nao menor ou igual a  49.

```javascript

fedora(mongod-3.0.4) be-mean-pokemons> var q1 = {$all:['investida']}
fedora(mongod-3.0.4) be-mean-pokemons> var q2 = {$not:{$lte:49}}
fedora(mongod-3.0.4) be-mean-pokemons> var q = {moves:q1, defense:q2}
fedora(mongod-3.0.4) be-mean-pokemons> db.pokemons.find(q)
{
  "_id": ObjectId("5654f016e253f3e89013d82f"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": 55,
  "description": "Sem maiores informações",
  "height": 4,
  "moves": [
    "investida"
  ]
}
Fetched 1 record(s) in 0ms

```

## 8. Remova todos os pokemons do tipo agua e com attack menor que 50.

```javascript
fedora(mongod-3.0.4) be-mean-pokemons> q1 = {type:/agua/}
fedora(mongod-3.0.4) be-mean-pokemons> q2 = {attack:{$lt:50}}
fedora(mongod-3.0.4) be-mean-pokemons> q = {$and:[q1,q2]}

fedora(mongod-3.0.4) be-mean-pokemons> db.pokemons.remove(q)
Removed 0 record(s) in 5ms
WriteResult({
  "nRemoved": 0
})


```
