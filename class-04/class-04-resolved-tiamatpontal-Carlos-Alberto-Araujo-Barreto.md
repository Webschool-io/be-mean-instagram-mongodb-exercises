## Exercício 04
autor: Carlos Alberto de Araujo Barreto

### Passo 1: adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: pikachu, squirtle, bulbassauro e charmander.
```
carlos-VirtualBox(mongod-2.4.9) be-mean-pokemons> var query = {name: {$in : ['pikachu', 'charmander', 'squirtle', 'bulbassauro']}}
carlos-VirtualBox(mongod-2.4.9) be-mean-pokemons> var attacks = ['cabeçada', 'evasiva']
carlos-VirtualBox(mongod-2.4.9) be-mean-pokemons> var mod = {$pushAll: {moves: attacks}}
carlos-VirtualBox(mongod-2.4.9) be-mean-pokemons> var options = {multi: true}
carlos-VirtualBox(mongod-2.4.9) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 2ms

```

### Passo 2: adicionar 1 movimento em todos os pokemons: 'desvio'
```
carlos-VirtualBox(mongod-2.4.9) be-mean-pokemons> var query = {}
carlos-VirtualBox(mongod-2.4.9) be-mean-pokemons> var mod = {$push: {moves: 'desvio'}}
carlos-VirtualBox(mongod-2.4.9) be-mean-pokemons> var options = {multi: true}
carlos-VirtualBox(mongod-2.4.9) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 10 existing record(s) in 2ms
```

### Passo 3: adicionar o pokemon 'AindaNaoExistMon' caso ele não exista com todos os dados com o valor 'null' e a descrição: "Sem maiores informações".
```
carlos-VirtualBox(mongod-2.4.9) be-mean-pokemons> var query = {name: "AindaNaoExisteMon"}
carlos-VirtualBox(mongod-2.4.9) be-mean-pokemons> var mod = {$setOnInsert: {
... name: "AindaNaoExisteMon", description: "Sem maiores informações", type: null, attack: null, defense: null}}
carlos-VirtualBox(mongod-2.4.9) be-mean-pokemons> var options = {upsert: true}
carlos-VirtualBox(mongod-2.4.9) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 2ms
```

### Passo 4: pesquisar todos os pokemons que possuam o ataque investida e mais um que voce adiconou, escolha seu pokemon favorito.
```
carlos-VirtualBox(mongod-2.4.9) be-mean-pokemons> var query = {moves: {$all : ['investida','desvio']}}
carlos-VirtualBox(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564a2da728ccce8415450488"),
  "active": false,
  "attack": 55,
  "defense": 40,
  "description": "Rato de raio",
  "height": 0.4,
  "moves": [
    "choque do trovão",
    "investida",
    "cabeçada",
    "evasiva",
    "desvio"
  ],
  "name": "pikachu",
  "type": "elétrico"
}
{
  "_id": ObjectId("564deecf7c992ec0c2ab3d66"),
  "active": false,
  "attack": null,
  "defense": null,
  "description": "Sem informações",
  "height": null,
  "moves": [
    "investida",
    "desvio"
  ],
  "name": "NaoExiste"
}
{
  "_id": ObjectId("564a2dc028ccce841545048c"),
  "active": false,
  "attack": 90,
  "defense": 55,
  "description": "Ratazana elétrica boladona",
  "height": 0.8,
  "moves": [
    "investida",
    "desvio"
  ],
  "name": "raichu",
  "type": "elétrico"
}
{
  "_id": ObjectId("564a2dbd28ccce841545048b"),
  "active": false,
  "attack": 60,
  "defense": 70,
  "description": "Lego",
  "height": 0.8,
  "moves": [
    "investida",
    "desvio"
  ],
  "name": "porygon",
  "type": "normal"
}
{
  "_id": ObjectId("564a2db728ccce8415450489"),
  "active": false,
  "attack": 84,
  "defense": 78,
  "description": "Lagarto de asas que cospe fogo",
  "height": 1.7,
  "moves": [
    "investida",
    "lança-chamas",
    "desvio"
  ],
  "name": "charizard",
  "type": "fogo"
}
{
  "_id": ObjectId("564a2dbb28ccce841545048a"),
  "active": false,
  "attack": 83,
  "defense": 100,
  "description": "Tartaruga bolada",
  "height": 1.6,
  "moves": [
    "investida",
    "hidro bomba",
    "desvio"
  ],
  "name": "blastoise",
  "type": "água"
}
{
  "_id": ObjectId("564b410341b4b3a29f92f505"),
  "active": false,
  "attack": 62,
  "defense": 63,
  "description": "Pokemon com broto em suas costas",
  "height": 1,
  "moves": [
    "investida",
    "folha navalha",
    "desvio"
  ],
  "name": "ivysaur",
  "type": "grama"
}
Fetched 7 record(s) in 4ms
```

### Passo 5: pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito
```
carlos-VirtualBox(mongod-2.4.9) be-mean-pokemons> var query = {moves: {$all : ['folha navalha','desvio']}}
carlos-VirtualBox(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564b410341b4b3a29f92f505"),
  "active": false,
  "attack": 62,
  "defense": 63,
  "description": "Pokemon com broto em suas costas",
  "height": 1,
  "moves": [
    "investida",
    "folha navalha",
    "desvio"
  ],
  "name": "ivysaur",
  "type": "grama"
}
Fetched 1 record(s) in 1ms
```

### Passo 6: pesquisar todos os pokemons que não são do tipo elétrico.
```
carlos-VirtualBox(mongod-2.4.9) be-mean-pokemons> var query = {type: {$ne: 'elétrico'}}
carlos-VirtualBox(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564deecf7c992ec0c2ab3d66"),
  "active": false,
  "attack": null,
  "defense": null,
  "description": "Sem informações",
  "height": null,
  "moves": [
    "investida",
    "desvio"
  ],
  "name": "NaoExiste"
}
{
  "_id": ObjectId("56533220dd79bffe83d7b5d5"),
  "attack": 49,
  "defense": 49,
  "description": "Pequeno broto",
  "height": 0.7,
  "moves": [
    "cabeçada",
    "evasiva",
    "desvio"
  ],
  "name": "bulbassauro",
  "type": "grama"
}
{
  "_id": ObjectId("56533394dd79bffe83d7b5d8"),
  "attack": 48,
  "defense": 65,
  "description": "Tartaruga de água",
  "height": 0.5,
  "moves": [
    "cabeçada",
    "evasiva",
    "desvio"
  ],
  "name": "squirtle",
  "type": "agua"
}
{
  "_id": ObjectId("56535325f8a2bb82ae52a904"),
  "attack": null,
  "defense": null,
  "description": "Sem maiores informações",
  "moves": [
    "desvio"
  ],
  "name": "AindaNaoExisteMon",
  "type": null
}
{
  "_id": ObjectId("56533332dd79bffe83d7b5d7"),
  "attack": 52,
  "defense": 43,
  "description": "Lagartixa de fogo",
  "height": 0.6,
  "moves": [
    "cabeçada",
    "evasiva",
    "desvio"
  ],
  "name": "charmander",
  "type": "fogo"
}
{
  "_id": ObjectId("564a2dbd28ccce841545048b"),
  "active": false,
  "attack": 60,
  "defense": 70,
  "description": "Lego",
  "height": 0.8,
  "moves": [
    "investida",
    "desvio"
  ],
  "name": "porygon",
  "type": "normal"
}
{
  "_id": ObjectId("564a2db728ccce8415450489"),
  "active": false,
  "attack": 84,
  "defense": 78,
  "description": "Lagarto de asas que cospe fogo",
  "height": 1.7,
  "moves": [
    "investida",
    "lança-chamas",
    "desvio"
  ],
  "name": "charizard",
  "type": "fogo"
}
{
  "_id": ObjectId("564a2dbb28ccce841545048a"),
  "active": false,
  "attack": 83,
  "defense": 100,
  "description": "Tartaruga bolada",
  "height": 1.6,
  "moves": [
    "investida",
    "hidro bomba",
    "desvio"
  ],
  "name": "blastoise",
  "type": "água"
}
{
  "_id": ObjectId("564b410341b4b3a29f92f505"),
  "active": false,
  "attack": 62,
  "defense": 63,
  "description": "Pokemon com broto em suas costas",
  "height": 1,
  "moves": [
    "investida",
    "folha navalha",
    "desvio"
  ],
  "name": "ivysaur",
  "type": "grama"
}
Fetched 9 record(s) in 5ms
```

Passo 7: pesquisar todos os pokemons que tenham o ataque investida e tenham a defesa não menor ou igual a 49.
```
carlos-VirtualBox(mongod-2.4.9) be-mean-pokemons> var query = {$and: [{moves: 'investida'},{attack: {$not: {$lte: 49}}}]}
carlos-VirtualBox(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564a2da728ccce8415450488"),
  "active": false,
  "attack": 55,
  "defense": 40,
  "description": "Rato de raio",
  "height": 0.4,
  "moves": [
    "choque do trovão",
    "investida",
    "cabeçada",
    "evasiva",
    "desvio"
  ],
  "name": "pikachu",
  "type": "elétrico"
}
{
  "_id": ObjectId("564a2dc028ccce841545048c"),
  "active": false,
  "attack": 90,
  "defense": 55,
  "description": "Ratazana elétrica boladona",
  "height": 0.8,
  "moves": [
    "investida",
    "desvio"
  ],
  "name": "raichu",
  "type": "elétrico"
}
{
  "_id": ObjectId("564a2dbd28ccce841545048b"),
  "active": false,
  "attack": 60,
  "defense": 70,
  "description": "Lego",
  "height": 0.8,
  "moves": [
    "investida",
    "desvio"
  ],
  "name": "porygon",
  "type": "normal"
}
{
  "_id": ObjectId("564a2db728ccce8415450489"),
  "active": false,
  "attack": 84,
  "defense": 78,
  "description": "Lagarto de asas que cospe fogo",
  "height": 1.7,
  "moves": [
    "investida",
    "lança-chamas",
    "desvio"
  ],
  "name": "charizard",
  "type": "fogo"
}
{
  "_id": ObjectId("564a2dbb28ccce841545048a"),
  "active": false,
  "attack": 83,
  "defense": 100,
  "description": "Tartaruga bolada",
  "height": 1.6,
  "moves": [
    "investida",
    "hidro bomba",
    "desvio"
  ],
  "name": "blastoise",
  "type": "água"
}
{
  "_id": ObjectId("564b410341b4b3a29f92f505"),
  "active": false,
  "attack": 62,
  "defense": 63,
  "description": "Pokemon com broto em suas costas",
  "height": 1,
  "moves": [
    "investida",
    "folha navalha",
    "desvio"
  ],
  "name": "ivysaur",
  "type": "grama"
}
Fetched 6 record(s) in 4ms
```

### Passo 8: remova todos os pokemons do tipo água e com attack menor que 50.
carlos-VirtualBox(mongod-2.4.9) be-mean-pokemons> var query = {$and: [{type: 'agua'}, {attack: {$lt: 50}}]}
carlos-VirtualBox(mongod-2.4.9) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 1ms

