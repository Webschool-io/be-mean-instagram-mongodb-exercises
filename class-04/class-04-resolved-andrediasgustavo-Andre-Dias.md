# MongoDB - Aula 04 - Exercício
autor: André Dias

**Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: hitmonlee, magneton, haunter e machamp(troquei por que na minha collection não tem aqueles pokemons).**

```
andre-dias-skywalker(mongod-3.0.7) be-mean-pokemons> var query = {$or : [{nome: /hitmonlee/i},{nome: /magneton/i},{nome: /haunter/i},{nome : /machamp/i}]}
andre-dias-skywalker(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll : {moves : ["cabeçada", "jab"]}}
andre-dias-skywalker(mongod-3.0.7) be-mean-pokemons> var opt = {multi : true}
andre-dias-skywalker(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, opt)
Updated 4 existing record(s) in 2ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
```

**Adicionar 1 movimento em todos os pokemons: `desvio`.**

```
andre-dias-skywalker(mongod-3.0.7) be-mean-pokemons> var query = {}
andre-dias-skywalker(mongod-3.0.7) be-mean-pokemons> var mod = {$push : {moves : "desvio"}}
andre-dias-skywalker(mongod-3.0.7) be-mean-pokemons> var opt = {multi : true}
andre-dias-skywalker(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, opt)
Updated 13 existing record(s) in 33ms
WriteResult({
  "nMatched": 13,
  "nUpserted": 0,
  "nModified": 13
})
```

**Adicionar o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".**

```
andre-dias-skywalker(mongod-3.0.7) be-mean-pokemons> var query = {nome : /AindaNaoExisteMon/i}
andre-dias-skywalker(mongod-3.0.7) be-mean-pokemons> var mod = {$setOnInsert : {nome: "AindaNaoExisteMon", type: null, attack: null, height: null, active: false, description: "Sem maiores informações"}}

andre-dias-skywalker(mongod-3.0.7) be-mean-pokemons> var opt = {upsert : true}
andre-dias-skywalker(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, opt)
Updated 1 new record(s) in 2ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564e25c95c07ced38fbff723")
})

```

**Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.**

```
andre-dias-skywalker(mongod-3.0.7) be-mean-pokemons> var query = {moves : {$in : [/investida/i, /telecinese/i]}}
andre-dias-skywalker(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5642a2a3b03182128350bb20"),
  "nome": "Machamp",
  "description": "É o Zangief de 4 braços",
  "type": "Lutador",
  "attack": 130,
  "height": 1.6,
  "active": true,
  "moves": [
    "investida",
    "Porrada",
    "cabeçada",
    "jab",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a369b03182128350bb21"),
  "nome": "Magneton",
  "description": "É um imã maneiro com olhos",
  "type": "Eletrico e Ferro",
  "attack": 60,
  "height": 1,
  "active": true,
  "moves": [
    "investida",
    "cabeçada",
    "jab",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a42ab03182128350bb22"),
  "nome": "Haunter",
  "description": "Fastasminha camarada é o Caraleoo",
  "type": "Fantasma",
  "attack": 50,
  "height": 1.6,
  "active": true,
  "moves": [
    "investida",
    "cabeçada",
    "jab",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a511b03182128350bb23"),
  "nome": "Snorlax",
  "description": "Gordinho perigoso",
  "type": "Normal",
  "attack": 110,
  "height": 2.1,
  "active": true,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a604b03182128350bb24"),
  "nome": "Mewtwo",
  "description": "Esse é o ZICA mesmo",
  "type": "Psiquico",
  "attack": 110,
  "height": 2,
  "active": true,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a6a8b03182128350bb25"),
  "nome": "Mew",
  "description": "É tipo o shun dos pokemons",
  "type": "Psiquico",
  "attack": 100,
  "height": 0.4,
  "active": true,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a751b03182128350bb26"),
  "nome": "Alakazan",
  "description": "Não é a colher que entorta, e sim você. Não há colher!",
  "type": "Psiquico",
  "attack": 50,
  "height": 1.5,
  "active": true,
  "moves": [
    "investida",
    "telecinese",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a7deb03182128350bb27"),
  "nome": "Hitmonlee",
  "description": "Esse é faixa preta do taekwondo",
  "type": "Lutador",
  "attack": 120,
  "height": 1.5,
  "active": true,
  "moves": [
    "investida",
    "bicuda",
    "cabeçada",
    "jab",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a8d5b03182128350bb29"),
  "nome": "Rhyhorn",
  "description": "Rinoceronte maneiro",
  "type": "Pedra, Terra",
  "attack": 85,
  "height": 1,
  "active": true,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564b380bebfeaf707278b03d"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "height": 2.1,
  "moves": [
    "investida",
    "desvio"
  ],
  "active": true
}
{
  "_id": ObjectId("564dfe7d5c07ced38fbff722"),
  "active": true,
  "name": "NãoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem informações",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564deceb5c07ced38fbff720"),
  "active": true,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564dfbe25c07ced38fbff721"),
  "active": true,
  "moves": [
    "investida",
    "desvio"
  ]
}
Fetched 13 record(s) in 4ms

```

** Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.**

```
andre-dias-skywalker(mongod-3.0.7) be-mean-pokemons> var query = {moves : {$in : [/cabeçada/i, /jab/i]}}
andre-dias-skywalker(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5642a2a3b03182128350bb20"),
  "nome": "Machamp",
  "description": "É o Zangief de 4 braços",
  "type": "Lutador",
  "attack": 130,
  "height": 1.6,
  "active": true,
  "moves": [
    "investida",
    "Porrada",
    "cabeçada",
    "jab",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a369b03182128350bb21"),
  "nome": "Magneton",
  "description": "É um imã maneiro com olhos",
  "type": "Eletrico e Ferro",
  "attack": 60,
  "height": 1,
  "active": true,
  "moves": [
    "investida",
    "cabeçada",
    "jab",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a42ab03182128350bb22"),
  "nome": "Haunter",
  "description": "Fastasminha camarada é o Caraleoo",
  "type": "Fantasma",
  "attack": 50,
  "height": 1.6,
  "active": true,
  "moves": [
    "investida",
    "cabeçada",
    "jab",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a7deb03182128350bb27"),
  "nome": "Hitmonlee",
  "description": "Esse é faixa preta do taekwondo",
  "type": "Lutador",
  "attack": 120,
  "height": 1.5,
  "active": true,
  "moves": [
    "investida",
    "bicuda",
    "cabeçada",
    "jab",
    "desvio"
  ]
}
Fetched 4 record(s) in 1ms
```

**Pesquisar todos os pokemons que não são do tipo `Lutador`.**

```
andre-dias-skywalker(mongod-3.0.7) be-mean-pokemons> var query = {type : {$not : /lutador/i}}
andre-dias-skywalker(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5642a369b03182128350bb21"),
  "nome": "Magneton",
  "description": "É um imã maneiro com olhos",
  "type": "Eletrico e Ferro",
  "attack": 60,
  "height": 1,
  "active": true,
  "moves": [
    "investida",
    "cabeçada",
    "jab",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a42ab03182128350bb22"),
  "nome": "Haunter",
  "description": "Fastasminha camarada é o Caraleoo",
  "type": "Fantasma",
  "attack": 50,
  "height": 1.6,
  "active": true,
  "moves": [
    "investida",
    "cabeçada",
    "jab",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a511b03182128350bb23"),
  "nome": "Snorlax",
  "description": "Gordinho perigoso",
  "type": "Normal",
  "attack": 110,
  "height": 2.1,
  "active": true,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a604b03182128350bb24"),
  "nome": "Mewtwo",
  "description": "Esse é o ZICA mesmo",
  "type": "Psiquico",
  "attack": 110,
  "height": 2,
  "active": true,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a6a8b03182128350bb25"),
  "nome": "Mew",
  "description": "É tipo o shun dos pokemons",
  "type": "Psiquico",
  "attack": 100,
  "height": 0.4,
  "active": true,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a751b03182128350bb26"),
  "nome": "Alakazan",
  "description": "Não é a colher que entorta, e sim você. Não há colher!",
  "type": "Psiquico",
  "attack": 50,
  "height": 1.5,
  "active": true,
  "moves": [
    "investida",
    "telecinese",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a8d5b03182128350bb29"),
  "nome": "Rhyhorn",
  "description": "Rinoceronte maneiro",
  "type": "Pedra, Terra",
  "attack": 85,
  "height": 1,
  "active": true,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564b380bebfeaf707278b03d"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "height": 2.1,
  "moves": [
    "investida",
    "desvio"
  ],
  "active": true
}
{
  "_id": ObjectId("564dfe7d5c07ced38fbff722"),
  "active": true,
  "name": "NãoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem informações",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564deceb5c07ced38fbff720"),
  "active": true,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564dfbe25c07ced38fbff721"),
  "active": true,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564e25c95c07ced38fbff723"),
  "nome": "AindaNaoExisteMon",
  "type": null,
  "attack": null,
  "height": null,
  "active": false,
  "description": "Sem maiores informações"
}
Fetched 12 record(s) in 2ms

```
**Pesquisar todos os pokemons que tenham o ataque `investida` E tenham a defesa não menor ou igual a 49.**

```
andre-dias-skywalker(mongod-3.0.7) be-mean-pokemons> var query = {$and : [{moves: "investida"}, {attack : {$not : {$lte: 49}}}]}
andre-dias-skywalker(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5642a2a3b03182128350bb20"),
  "nome": "Machamp",
  "description": "É o Zangief de 4 braços",
  "type": "Lutador",
  "attack": 130,
  "height": 1.6,
  "active": true,
  "moves": [
    "investida",
    "Porrada",
    "cabeçada",
    "jab",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a369b03182128350bb21"),
  "nome": "Magneton",
  "description": "É um imã maneiro com olhos",
  "type": "Eletrico e Ferro",
  "attack": 60,
  "height": 1,
  "active": true,
  "moves": [
    "investida",
    "cabeçada",
    "jab",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a42ab03182128350bb22"),
  "nome": "Haunter",
  "description": "Fastasminha camarada é o Caraleoo",
  "type": "Fantasma",
  "attack": 50,
  "height": 1.6,
  "active": true,
  "moves": [
    "investida",
    "cabeçada",
    "jab",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a511b03182128350bb23"),
  "nome": "Snorlax",
  "description": "Gordinho perigoso",
  "type": "Normal",
  "attack": 110,
  "height": 2.1,
  "active": true,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a604b03182128350bb24"),
  "nome": "Mewtwo",
  "description": "Esse é o ZICA mesmo",
  "type": "Psiquico",
  "attack": 110,
  "height": 2,
  "active": true,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a6a8b03182128350bb25"),
  "nome": "Mew",
  "description": "É tipo o shun dos pokemons",
  "type": "Psiquico",
  "attack": 100,
  "height": 0.4,
  "active": true,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a751b03182128350bb26"),
  "nome": "Alakazan",
  "description": "Não é a colher que entorta, e sim você. Não há colher!",
  "type": "Psiquico",
  "attack": 50,
  "height": 1.5,
  "active": true,
  "moves": [
    "investida",
    "telecinese",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a7deb03182128350bb27"),
  "nome": "Hitmonlee",
  "description": "Esse é faixa preta do taekwondo",
  "type": "Lutador",
  "attack": 120,
  "height": 1.5,
  "active": true,
  "moves": [
    "investida",
    "bicuda",
    "cabeçada",
    "jab",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a8d5b03182128350bb29"),
  "nome": "Rhyhorn",
  "description": "Rinoceronte maneiro",
  "type": "Pedra, Terra",
  "attack": 85,
  "height": 1,
  "active": true,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564b380bebfeaf707278b03d"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "height": 2.1,
  "moves": [
    "investida",
    "desvio"
  ],
  "active": true
}
{
  "_id": ObjectId("564dfe7d5c07ced38fbff722"),
  "active": true,
  "name": "NãoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem informações",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564deceb5c07ced38fbff720"),
  "active": true,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564dfbe25c07ced38fbff721"),
  "active": true,
  "moves": [
    "investida",
    "desvio"
  ]
}
Fetched 13 record(s) in 12ms

```

**Remova todos os pokemons do tipo psiquico e com attack menor que 60.**

```
andre-dias-skywalker(mongod-3.0.7) be-mean-pokemons> var query = {$and : [{type: /psiquico/i}, {attack : {$lt : 60}}]}
andre-dias-skywalker(mongod-3.0.7) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 7ms
WriteResult({
  "nRemoved": 1
})

```

