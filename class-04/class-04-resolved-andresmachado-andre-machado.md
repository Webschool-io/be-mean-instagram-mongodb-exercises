# MongoDB - Aula 04 - Exercício
autor: André Machado

# Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

> AndrePC(mongod-3.0.7) be-mean-pokemons> var query = {name: {$in: [/Pikachu/i,/bulbassauro/i,/squirtle/i,/charmander/i]}};

> AndrePC(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll: {moves: ["cabecada", "tackle"]}};

> AndrePC(mongod-3.0.7) be-mean-pokemons> var opt = {multi: true};

> AndrePC(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, opt);

> AndrePC(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)

>{
  "_id": ObjectId("5643d3acc8e7c6976cee0169"),
  "name": "Pikachu",
  "description": "Ratinho eletrico fofinho",
  "type": "eletrico",
  "attack": 55,
  "height": 0.4,
  "defense": 40,
  "active": false,
  "moves": [
    "investida",
    "choque do trovão",
    "desvio",
    "cabecada",
    "tackle"
  ]
}

>{
  "_id": ObjectId("564e663e5975c0830562c1ae"),
  "name": "Squirtle",
  "description": "Joga agua",
  "type": "Agua",
  "attack": 48,
  "height": 0.5,
  "defense": 65,
  "active": false,
  "moves": [
    "desvio",
    "cabecada",
    "tackle"
  ]
}

>{
  "_id": ObjectId("564e66855975c0830562c1af"),
  "name": "Bulbassauro",
  "description": "Chicote de navalha do mal",
  "type": "grama",
  "attack": 49,
  "height": 0.7,
  "defense": 49,
  "active": false,
  "moves": [
    "desvio",
    "cabecada",
    "tackle"
  ]
}

>{
  "_id": ObjectId("564e66bd5975c0830562c1b0"),
  "name": "Charmander",
  "description": "Fogo no rabo",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "defense": 43,
  "active": false,
  "moves": [
    "desvio",
    "cabecada",
    "tackle"
  ]
}

---

# Adicionar 1 movimento em todos os pokemons: desvio.

> AndrePC(mongod-3.0.7) be-mean-pokemons> var query = {};

> AndrePC(mongod-3.0.7) be-mean-pokemons> var mod = {$push: {moves: "desvio"}};

> AndrePC(mongod-3.0.7) be-mean-pokemons> var opt = {multi: true}

> AndrePC(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, opt);

---

# Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".

> AndrePC(mongod-3.0.7) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}

> AndrePC(mongod-3.0.7) be-mean-pokemons> var opt = {upsert: true};

> AndrePC(mongod-3.0.7) be-mean-pokemons> var mod = {$setOnInsert: {name: "AindaNaoExiteMon", attack: null, defense: null, height: null, description: "Sem maiores informações"}}

> AndrePC(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, opt);

> Updated 1 new record(s) in 2ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564e6ac811ac130d1767dbab")
})

> AndrePC(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query);

> {
  "_id": ObjectId("564e6ac811ac130d1767dbab"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 1 record(s) in 1

---

# Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.

> AndrePC(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$in: ["investida"]}}

> {
  "_id": ObjectId("5643d253c8e7c6976cee0168"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "active": false,
  "moves": [
    "investida",
    "endurecer",
    "desvio",
    "desvio",
    "desvio"
  ]
}

> {
  "_id": ObjectId("5643d4eec8e7c6976cee016b"),
  "name": "Nidoran",
  "description": "Um ratinho venenoso do fofinho",
  "type": "veneno",
  "attack": 47,
  "height": 0.4,
  "defense": 52,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}

> {
  "_id": ObjectId("5643d548c8e7c6976cee016c"),
  "name": "Mr. Mime",
  "description": "Um palhaco muito do estranho",
  "type": "psiquico/fada",
  "attack": 45,
  "height": 1.3,
  "defense": 65,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}

> {
  "_id": ObjectId("564bcba49c72c38b07a0301a"),
  "description": "Alterando a parada toda aqui",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}

> {
  "_id": ObjectId("5643d3acc8e7c6976cee0169"),
  "name": "Pikachu",
  "description": "Ratinho eletrico fofinho",
  "type": "eletrico",
  "attack": 55,
  "height": 0.4,
  "defense": 40,
  "active": false,
  "moves": [
    "investida",
    "choque do trovão",
    "desvio",
    "cabecada",
    "tackle"
  ]
}

> {
  "_id": ObjectId("564dcb6811ac130d1767dbaa"),
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

> {
  "_id": ObjectId("5643d479c8e7c6976cee016a"),
  "name": "Tangela",
  "description": "Cabelo de medusa muito louco",
  "type": "grama",
  "attack": 55,
  "height": 0.3,
  "defense": 115,
  "active": false,
  "moves": [
    "investida",
    "chicote de trepadeira",
    "desvio"
  ]
}

---

# Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

> AndrePC(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$in: ["tackle", "cabecada"]}}

> AndrePC(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query);

> {
  "_id": ObjectId("5643d3acc8e7c6976cee0169"),
  "name": "Pikachu",
  "description": "Ratinho eletrico fofinho",
  "type": "eletrico",
  "attack": 55,
  "height": 0.4,
  "defense": 40,
  "active": false,
  "moves": [
    "investida",
    "choque do trovão",
    "desvio",
    "cabecada",
    "tackle"
  ]
}

> {
  "_id": ObjectId("564e663e5975c0830562c1ae"),
  "name": "Squirtle",
  "description": "Joga agua",
  "type": "Agua",
  "attack": 48,
  "height": 0.5,
  "defense": 65,
  "active": false,
  "moves": [
    "desvio",
    "cabecada",
    "tackle"
  ]
}

>{
  "_id": ObjectId("564e66855975c0830562c1af"),
  "name": "Bulbassauro",
  "description": "Chicote de navalha do mal",
  "type": "grama",
  "attack": 49,
  "height": 0.7,
  "defense": 49,
  "active": false,
  "moves": [
    "desvio",
    "cabecada",
    "tackle"
  ]
}

>{
  "_id": ObjectId("564e66bd5975c0830562c1b0"),
  "name": "Charmander",
  "description": "Fogo no rabo",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "defense": 43,
  "active": false,
  "moves": [
    "desvio",
    "cabecada",
    "tackle"
  ]
}


---

# Pesquisar todos os pokemons que não são do tipo elétrico.

> AndrePC(mongod-3.0.7) be-mean-pokemons> var query = {type: {$ne: "eletrico"}};

> AndrePC(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query);

> {
  "_id": ObjectId("5643d253c8e7c6976cee0168"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "active": false,
  "moves": [
    "investida",
    "endurecer",
    "desvio",
    "desvio",
    "desvio"
  ]
}

> {
  "_id": ObjectId("5643d4eec8e7c6976cee016b"),
  "name": "Nidoran",
  "description": "Um ratinho venenoso do fofinho",
  "type": "veneno",
  "attack": 47,
  "height": 0.4,
  "defense": 52,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}

> {
  "_id": ObjectId("5643d548c8e7c6976cee016c"),
  "name": "Mr. Mime",
  "description": "Um palhaco muito do estranho",
  "type": "psiquico/fada",
  "attack": 45,
  "height": 1.3,
  "defense": 65,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}

> {
  "_id": ObjectId("564bcba49c72c38b07a0301a"),
  "description": "Alterando a parada toda aqui",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}

> {
  "_id": ObjectId("564dcb6811ac130d1767dbaa"),
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

> {
  "_id": ObjectId("5643d479c8e7c6976cee016a"),
  "name": "Tangela",
  "description": "Cabelo de medusa muito louco",
  "type": "grama",
  "attack": 55,
  "height": 0.3,
  "defense": 115,
  "active": false,
  "moves": [
    "investida",
    "chicote de trepadeira",
    "desvio"
  ]
}

> {
  "_id": ObjectId("564e663e5975c0830562c1ae"),
  "name": "Squirtle",
  "description": "Joga agua",
  "type": "Agua",
  "attack": 48,
  "height": 0.5,
  "defense": 65,
  "active": false,
  "moves": [
    "desvio",
    "cabecada",
    "tackle"
  ]
}

> {
  "_id": ObjectId("564e66855975c0830562c1af"),
  "name": "Bulbassauro",
  "description": "Chicote de navalha do mal",
  "type": "grama",
  "attack": 49,
  "height": 0.7,
  "defense": 49,
  "active": false,
  "moves": [
    "desvio",
    "cabecada",
    "tackle"
  ]
}

> {
  "_id": ObjectId("564e66bd5975c0830562c1b0"),
  "name": "Charmander",
  "description": "Fogo no rabo",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "defense": 43,
  "active": false,
  "moves": [
    "desvio",
    "cabecada",
    "tackle"
  ]
}

> {
  "_id": ObjectId("564e6ac811ac130d1767dbab"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}

> Fetched 10 record(s) in

---

# Pesquisar todos pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49.

> AndrePC(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{moves: {$in: ["investida"]}}, {attack: {$gt: 49}}]};

> AndrePC(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query);

> {
  "_id": ObjectId("5643d3acc8e7c6976cee0169"),
  "name": "Pikachu",
  "description": "Ratinho eletrico fofinho",
  "type": "eletrico",
  "attack": 55,
  "height": 0.4,
  "defense": 40,
  "active": false,
  "moves": [
    "investida",
    "choque do trovão",
    "desvio",
    "cabecada",
    "tackle"
  ]
}

> {
  "_id": ObjectId("5643d479c8e7c6976cee016a"),
  "name": "Tangela",
  "description": "Cabelo de medusa muito louco",
  "type": "grama",
  "attack": 55,
  "height": 0.3,
  "defense": 115,
  "active": false,
  "moves": [
    "investida",
    "chicote de trepadeira",
    "desvio"
  ]
}

> Fetched 2 record(s) in 0ms

---

# Remova todos os pokemons do tipo água e com attack menor que 50.

> AndrePC(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{type: "agua"}, {attack: {$lt: 50}}]}

> AndrePC(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)

> {
  "_id": ObjectId("564e6fd35975c0830562c1b1"),
  "name": "Poliwag",
  "description": "Um peixinho muito fofinho com uma espiral no peito",
  "type": "agua",
  "attack": 49,
  "height": 0.6,
  "defese": 40,
  "active": false,
  "moves": [
    "desvio"
  ]
}
Fetched 1 record(s) in

> AndrePC(mongod-3.0.7) be-mean-pokemons> db.pokemons.remove(query);

> Removed 1 record(s) in 1ms
WriteResult({
  "nRemoved": 1
})
