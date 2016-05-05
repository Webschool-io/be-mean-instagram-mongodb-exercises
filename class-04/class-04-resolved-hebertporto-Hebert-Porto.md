## MongoDb - Aula 04 - Exercício Resolvido - Hebert Porto
Autor: Hebert Porto

### 1 - **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander. ###

```js
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> var query = { $or: [{name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbassauro/i}, {name: /charmander/i}]}
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> var mod = { $pushAll: { moves: ['pular','voar']}}
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> var options = {multi: true}
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 2ms
```

### 2 - **Adicionar** 1 movimento em todos os pokemons: `desvio`. ###

```js
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> var query = {}
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> var mod = { $pushAll: { moves: ['investida']}}
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 9 existing record(s) in 2ms
```

### **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".###

```js
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> var query = {name: /NaoExistemon/i }
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> var mod = { $set: {active: true}, $setOnInsert: {name: "NaoExisteMon", attack: null, defense:null, height: null, des}}
                                                         var mod = { $set: {active: true}, $setOnInsert: {name: "NaoExisteMon", attack: null, defense:null, height: null, descr
iption: "Sem maiores informações"}}
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> var options = {upsert: true}
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> db.pokemons.update(query,mod,options)
Updated 1 new record(s) in 1ms
```

### Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.###

```js
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> var query = {moves: {$in:['investida','voar']}}
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56bb392384277bd0550d32bf"),
  "attack": 132,
  "defense": 2121,
  "description": "Sinistros de dia e de noite",
  "height": 2,
  "moves": [
    "investida"
  ],
  "name": "Charizard",
  "type": "ghost"
}
{
  "_id": ObjectId("56bb394184277bd0550d32c0"),
  "attack": 99,
  "defense": 890,
  "description": "Sinistros de dia e de noite",
  "height": 56.6,
  "moves": [
    "investida"
  ],
  "name": "Mew",
  "type": "fighter"
}
{
  "_id": ObjectId("56bb395784277bd0550d32c1"),
  "attack": 55,
  "defense": 21,
  "description": "Sinistros de dia e de noite",
  "height": 4,
  "moves": [
    "investida"
  ],
  "name": "Dragonite",
  "type": "fire"
}
{
  "_id": ObjectId("56bb39c384277bd0550d32c2"),
  "attack": 12,
  "defense": 222,
  "description": "Sinistros de dia e de noite",
  "height": 21,
  "moves": [
    "investida"
  ],
  "name": "Eevee",
  "type": "water"
}
{
  "_id": ObjectId("56bb39d084277bd0550d32c3"),
  "attack": 356,
  "defense": 250,
  "description": "Nova Description",
  "height": 0.4,
  "moves": [
    "investida"
  ],
  "name": "Vaporeon",
  "type": "rock"
}
{
  "_id": ObjectId("56bccbebff983fd5961c8a31"),
  "attack": 8000,
  "defense": 8000,
  "description": "Pokemon teste",
  "height": 2.1,
  "moves": [
    "pular",
    "voar",
    "investida"
  ],
  "name": "Pikachu"
}
{
  "_id": ObjectId("56bccc20ff983fd5961c8a32"),
  "attack": 8000,
  "defense": 8000,
  "description": "Pokemon teste",
  "height": 2.1,
  "moves": [
    "pular",
    "voar",
    "investida"
  ],
  "name": "Squirtle",
  "type": "agua"
}
{
  "_id": ObjectId("56bccc3eff983fd5961c8a33"),
  "attack": 8000,
  "defense": 8000,
  "description": "Pokemon teste",
  "height": 2.1,
  "moves": [
    "pular",
    "voar",
    "investida"
  ],
  "name": "Bulbassauro",
  "type": "grama"
}
{
  "_id": ObjectId("56bccc58ff983fd5961c8a34"),
  "attack": 80,
  "defense": 8000,
  "description": "Pokemon teste",
  "height": 2.1,
  "moves": [
    "pular",
    "voar",
    "investida"
  ],
  "name": "Charmander",
  "type": "fogo"
}
Fetched 9 record(s) in 11ms
```

### Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.###
```js
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> var query = {moves: {$in:['investida']}}
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56bb392384277bd0550d32bf"),
  "attack": 132,
  "defense": 2121,
  "description": "Sinistros de dia e de noite",
  "height": 2,
  "moves": [
    "investida"
  ],
  "name": "Charizard",
  "type": "ghost"
}
{
  "_id": ObjectId("56bb394184277bd0550d32c0"),
  "attack": 99,
  "defense": 890,
  "description": "Sinistros de dia e de noite",
  "height": 56.6,
  "moves": [
    "investida"
  ],
  "name": "Mew",
  "type": "fighter"
}
{
  "_id": ObjectId("56bb395784277bd0550d32c1"),
  "attack": 55,
  "defense": 21,
  "description": "Sinistros de dia e de noite",
  "height": 4,
  "moves": [
    "investida"
  ],
  "name": "Dragonite",
  "type": "fire"
}
{
  "_id": ObjectId("56bb39c384277bd0550d32c2"),
  "attack": 12,
  "defense": 222,
  "description": "Sinistros de dia e de noite",
  "height": 21,
  "moves": [
    "investida"
  ],
  "name": "Eevee",
  "type": "water"
}
{
  "_id": ObjectId("56bb39d084277bd0550d32c3"),
  "attack": 356,
  "defense": 250,
  "description": "Nova Description",
  "height": 0.4,
  "moves": [
    "investida"
  ],
  "name": "Vaporeon",
  "type": "rock"
}
{
  "_id": ObjectId("56bccbebff983fd5961c8a31"),
  "attack": 8000,
  "defense": 8000,
  "description": "Pokemon teste",
  "height": 2.1,
  "moves": [
    "pular",
    "voar",
    "investida"
  ],
  "name": "Pikachu"
}
{
  "_id": ObjectId("56bccc20ff983fd5961c8a32"),
  "attack": 8000,
  "defense": 8000,
  "description": "Pokemon teste",
  "height": 2.1,
  "moves": [
    "pular",
    "voar",
    "investida"
  ],
  "name": "Squirtle",
  "type": "agua"
}
{
  "_id": ObjectId("56bccc3eff983fd5961c8a33"),
  "attack": 8000,
  "defense": 8000,
  "description": "Pokemon teste",
  "height": 2.1,
  "moves": [
    "pular",
    "voar",
    "investida"
  ],
  "name": "Bulbassauro",
  "type": "grama"
}
{
  "_id": ObjectId("56bccc58ff983fd5961c8a34"),
  "attack": 80,
  "defense": 8000,
  "description": "Pokemon teste",
  "height": 2.1,
  "moves": [
    "pular",
    "voar",
    "investida"
  ],
  "name": "Charmander",
  "type": "fogo"
}
Fetched 9 record(s) in 10ms
```

### Pesquisar **todos** os pokemons que não são do tipo `elétrico`.###
```js
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> var query = {type: {$ne: "Eletrico"}}
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56bb392384277bd0550d32bf"),
  "attack": 132,
  "defense": 2121,
  "description": "Sinistros de dia e de noite",
  "height": 2,
  "moves": [
    "investida"
  ],
  "name": "Charizard",
  "type": "ghost"
}
{
  "_id": ObjectId("56bb394184277bd0550d32c0"),
  "attack": 99,
  "defense": 890,
  "description": "Sinistros de dia e de noite",
  "height": 56.6,
  "moves": [
    "investida"
  ],
  "name": "Mew",
  "type": "fighter"
}
{
  "_id": ObjectId("56bb395784277bd0550d32c1"),
  "attack": 55,
  "defense": 21,
  "description": "Sinistros de dia e de noite",
  "height": 4,
  "moves": [
    "investida"
  ],
  "name": "Dragonite",
  "type": "fire"
}
{
  "_id": ObjectId("56bb39c384277bd0550d32c2"),
  "attack": 12,
  "defense": 222,
  "description": "Sinistros de dia e de noite",
  "height": 21,
  "moves": [
    "investida"
  ],
  "name": "Eevee",
  "type": "water"
}
{
  "_id": ObjectId("56bb39d084277bd0550d32c3"),
  "attack": 356,
  "defense": 250,
  "description": "Nova Description",
  "height": 0.4,
  "moves": [
    "investida"
  ],
  "name": "Vaporeon",
  "type": "rock"
}
{
  "_id": ObjectId("56bccc20ff983fd5961c8a32"),
  "attack": 8000,
  "defense": 8000,
  "description": "Pokemon teste",
  "height": 2.1,
  "moves": [
    "pular",
    "voar",
    "investida"
  ],
  "name": "Squirtle",
  "type": "agua"
}
{
  "_id": ObjectId("56bccc3eff983fd5961c8a33"),
  "attack": 8000,
  "defense": 8000,
  "description": "Pokemon teste",
  "height": 2.1,
  "moves": [
    "pular",
    "voar",
    "investida"
  ],
  "name": "Bulbassauro",
  "type": "grama"
}
{
  "_id": ObjectId("56bccc58ff983fd5961c8a34"),
  "attack": 80,
  "defense": 8000,
  "description": "Pokemon teste",
  "height": 2.1,
  "moves": [
    "pular",
    "voar",
    "investida"
  ],
  "name": "Charmander",
  "type": "fogo"
}
{
  "_id": ObjectId("56bcd1ff8b518598445be16b"),
  "active": true,
  "attack": null,
  "defense": null,
  "description": "Sem maiores informações",
  "height": null,
  "name": "NaoExisteMon"
}
Fetched 9 record(s) in 14ms
```

### Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.###

```js
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> var query = {$and: [{moves: {$in: [/investida/i]}}, {attack: {$not: {$lte: 49} } }
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56bb392384277bd0550d32bf"),
  "attack": 132,
  "defense": 2121,
  "description": "Sinistros de dia e de noite",
  "height": 2,
  "moves": [
    "investida"
  ],
  "name": "Charizard",
  "type": "ghost"
}
{
  "_id": ObjectId("56bb394184277bd0550d32c0"),
  "attack": 99,
  "defense": 890,
  "description": "Sinistros de dia e de noite",
  "height": 56.6,
  "moves": [
    "investida"
  ],
  "name": "Mew",
  "type": "fighter"
}
{
  "_id": ObjectId("56bb395784277bd0550d32c1"),
  "attack": 55,
  "defense": 21,
  "description": "Sinistros de dia e de noite",
  "height": 4,
  "moves": [
    "investida"
  ],
  "name": "Dragonite",
  "type": "fire"
}
{
  "_id": ObjectId("56bb39d084277bd0550d32c3"),
  "attack": 356,
  "defense": 250,
  "description": "Nova Description",
  "height": 0.4,
  "moves": [
    "investida"
  ],
  "name": "Vaporeon",
  "type": "rock"
}
{
  "_id": ObjectId("56bccc20ff983fd5961c8a32"),
  "attack": 8000,
  "defense": 8000,
  "description": "Pokemon teste",
  "height": 2.1,
  "moves": [
    "pular",
    "voar",
    "investida"
  ],
  "name": "Squirtle",
  "type": "agua"
}
{
  "_id": ObjectId("56bccc3eff983fd5961c8a33"),
  "attack": 8000,
  "defense": 8000,
  "description": "Pokemon teste",
  "height": 2.1,
  "moves": [
    "pular",
    "voar",
    "investida"
  ],
  "name": "Bulbassauro",
  "type": "grama"
}
{
  "_id": ObjectId("56bccc58ff983fd5961c8a34"),
  "attack": 80,
  "defense": 8000,
  "description": "Pokemon teste",
  "height": 2.1,
  "moves": [
    "pular",
    "voar",
    "investida"
  ],
  "name": "Charmander",
  "type": "fogo"
}
{
  "_id": ObjectId("56bccbebff983fd5961c8a31"),
  "attack": 8000,
  "defense": 8000,
  "description": "Pokemon teste",
  "height": 2.1,
  "moves": [
    "pular",
    "voar",
    "investida"
  ],
  "name": "Pikachu",
  "type": "Eletrico"
}
Fetched 8 record(s) in 8ms
```

### Remova **todos** os pokemons do tipo água e com attack menor que 50. ###

```js
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> var query = {$and: [{type: 'agua'}, {attack: {$lt: 50}}]}
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> db.pokemons.remove(query)
Removed 0 record(s) in 1ms
```