```md
# MongoDB - Aula 04 - Exercício
autor: JOSÉ CARLOS DA SILVA DE CARVALHO	

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
carlos-pc(mongod-3.0.7) be-mean-pokemons> var query = {name: {$in: ["Hitmonlee", "Cubone", "Raichu", "Magna"]}}
carlos-pc(mongod-3.0.7) be-mean-pokemons> var attacks = ["Cabeçada", "Jogar Pedra"]
carlos-pc(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll: {attacks: attacks}}
carlos-pc(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 2ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
carlos-pc(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("565fb437096fb0ddd2aaac99"),
  "name": "Hitmonlee",
  "description": "Lutador com chute potente",
  "attack": 120,
  "defence": 80,
  "height": 1.5,
  "active": false,
  "moves": [
    "investida",
    "chute alto"
  ],
  "attacks": [
    "Cabeçada",
    "Jogar Pedra"
  ]
}
{
  "_id": ObjectId("565fb4d8096fb0ddd2aaac9b"),
  "name": "Magna",
  "description": "Uma nova descrição para o pokemon",
  "attack": 60,
  "defence": 80,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "Cabeçada Forte",
    "Super Pulo"
  ],
  "attacks": [
    "Cabeçada",
    "Jogar Pedra"
  ]
}
{
  "_id": ObjectId("565fb664096fb0ddd2aaac9f"),
  "name": "Cubone",
  "description": "Bixinho de pelúcia com uma caveira na cabeça",
  "attack": 30,
  "defence": 40,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "cacetada forte"
  ],
  "attacks": [
    "Cabeçada",
    "Jogar Pedra"
  ]
}
{
  "_id": ObjectId("565fb497096fb0ddd2aaac9a"),
  "name": "Raichu",
  "description": "Rato gigante, a evolução do pickachu",
  "attack": 90,
  "defence": 50,
  "height": 0.8,
  "active": false,
  "moves": [
    "investida",
    "choque do trovão"
  ],
  "attacks": [
    "Cabeçada",
    "Jogar Pedra"
  ]
}
Fetched 4 record(s) in 2ms


## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
carlos-pc(mongod-3.0.7) be-mean-pokemons> var query = {}
carlos-pc(mongod-3.0.7) be-mean-pokemons> var movimento = ["desvio"]
carlos-pc(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll: {moves: movimento}}
carlos-pc(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 10 existing record(s) in 3ms
WriteResult({
  "nMatched": 10,
  "nUpserted": 0,
  "nModified": 10
})
carlos-pc(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("565fb522096fb0ddd2aaac9c"),
  "name": "Sandshrew",
  "description": "Rato grande azul e com orelhas gigantes",
  "attack": 30,
  "defence": 20,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("565fb630096fb0ddd2aaac9e"),
  "name": "Exeggcute",
  "description": "Esse é muito estranho, parece um monte de ovos",
  "attack": 20,
  "defence": 40,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "hipnose",
    "desvio"
  ]
}
{
  "_id": ObjectId("565fb585096fb0ddd2aaac9d"),
  "name": "Voltorb",
  "description": "Se parece com uma pokebola e pode explodir",
  "attack": 20,
  "defence": 20,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
[...]mais 7

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
carlos-pc(mongod-3.0.7) be-mean-pokemons> var query = {name: "AindaNaoExisteMon"}
carlos-pc(mongod-3.0.7) be-mean-pokemons> var mod = {
... $set: {active: true},
... $setOnInsert: {"name": "AindaNaoExisteMon", "description": "Sem maiores informações", "attack": null,"defence": null,"height": null}
... }
carlos-pc(mongod-3.0.7) be-mean-pokemons> var options = {upsert: true}
carlos-pc(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 10ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("566c69a24b0360f9c9d98fa1")
})
carlos-pc(mongod-3.0.7) be-mean-pokemons> var query = {"_id": ObjectId("566c69a24b0360f9c9d98fa1")}
carlos-pc(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("566c69a24b0360f9c9d98fa1"),
  "name": "AindaNaoExisteMon",
  "active": true,
  "description": "Sem maiores informações",
  "attack": null,
  "defence": null,
  "height": null
}
Fetched 1 record(s) in 1ms

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
carlos-pc(mongod-3.0.7) be-mean-pokemons> var query = { $or: [  {attacks: "Cabeçada"}, {name: "Voltorb"} ] }
carlos-pc(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("565fb585096fb0ddd2aaac9d"),
  "name": "Voltorb",
  "description": "Se parece com uma pokebola e pode explodir",
  "attack": 20,
  "defence": 20,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("565fb437096fb0ddd2aaac99"),
  "name": "Hitmonlee",
  "description": "Lutador com chute potente",
  "attack": 120,
  "defence": 80,
  "height": 1.5,
  "active": false,
  "moves": [
    "investida",
    "chute alto",
    "desvio"
  ],
  "attacks": [
    "Cabeçada",
    "Jogar Pedra"
  ]
}
{
  "_id": ObjectId("565fb4d8096fb0ddd2aaac9b"),
  "name": "Magna",
  "description": "Uma nova descrição para o pokemon",
  "attack": 60,
  "defence": 80,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "Cabeçada Forte",
    "Super Pulo",
    "desvio"
  ],
  "attacks": [
    "Cabeçada",
    "Jogar Pedra"
  ]
}
{
  "_id": ObjectId("565fb664096fb0ddd2aaac9f"),
  "name": "Cubone",
  "description": "Bixinho de pelúcia com uma caveira na cabeça",
  "attack": 30,
  "defence": 40,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "cacetada forte",
    "desvio"
  ],
  "attacks": [
    "Cabeçada",
    "Jogar Pedra"
  ]
}
{
  "_id": ObjectId("565fb497096fb0ddd2aaac9a"),
  "name": "Raichu",
  "description": "Rato gigante, a evolução do pickachu",
  "attack": 90,
  "defence": 50,
  "height": 0.8,
  "active": false,
  "moves": [
    "investida",
    "choque do trovão",
    "desvio"
  ],
  "attacks": [
    "Cabeçada",
    "Jogar Pedra"
  ]
}
Fetched 5 record(s) in 3ms

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
carlos-pc(mongod-3.0.7) be-mean-pokemons> var query = { $or: [  {attacks: ["Cabeçada", "Jogar Pedra"]}, {name: "Voltorb"} ] }
carlos-pc(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("565fb585096fb0ddd2aaac9d"),
  "name": "Voltorb",
  "description": "Se parece com uma pokebola e pode explodir",
  "attack": 20,
  "defence": 20,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("565fb437096fb0ddd2aaac99"),
  "name": "Hitmonlee",
  "description": "Lutador com chute potente",
  "attack": 120,
  "defence": 80,
  "height": 1.5,
  "active": false,
  "moves": [
    "investida",
    "chute alto",
    "desvio"
  ],
  "attacks": [
    "Cabeçada",
    "Jogar Pedra"
  ]
}
{
  "_id": ObjectId("565fb4d8096fb0ddd2aaac9b"),
  "name": "Magna",
  "description": "Uma nova descrição para o pokemon",
  "attack": 60,
  "defence": 80,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "Cabeçada Forte",
    "Super Pulo",
    "desvio"
  ],
  "attacks": [
    "Cabeçada",
    "Jogar Pedra"
  ]
}
{
  "_id": ObjectId("565fb664096fb0ddd2aaac9f"),
  "name": "Cubone",
  "description": "Bixinho de pelúcia com uma caveira na cabeça",
  "attack": 30,
  "defence": 40,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "cacetada forte",
    "desvio"
  ],
  "attacks": [
    "Cabeçada",
    "Jogar Pedra"
  ]
}
{
  "_id": ObjectId("565fb497096fb0ddd2aaac9a"),
  "name": "Raichu",
  "description": "Rato gigante, a evolução do pickachu",
  "attack": 90,
  "defence": 50,
  "height": 0.8,
  "active": false,
  "moves": [
    "investida",
    "choque do trovão",
    "desvio"
  ],
  "attacks": [
    "Cabeçada",
    "Jogar Pedra"
  ]
}
Fetched 5 record(s) in 4ms

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
carlos-pc(mongod-3.0.7) be-mean-pokemons> var query = {type: {$not: "elétrico"}}
carlos-pc(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query).limit(3)
Error: error: {
  "$err": "Can't canonicalize query: BadValue $not needs a regex or a document",
  "code": 17287
}
carlos-pc(mongod-3.0.7) be-mean-pokemons> var query = {type: {$not: /elétrico/i}}
carlos-pc(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query).limit(3)
{
  "_id": ObjectId("565fb522096fb0ddd2aaac9c"),
  "name": "Sandshrew",
  "description": "Rato grande azul e com orelhas gigantes",
  "attack": 30,
  "defence": 20,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ],
  "type": null
}
{
  "_id": ObjectId("565fb630096fb0ddd2aaac9e"),
  "name": "Exeggcute",
  "description": "Esse é muito estranho, parece um monte de ovos",
  "attack": 20,
  "defence": 40,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "hipnose",
    "desvio"
  ],
  "type": null
}
{
  "_id": ObjectId("565fb585096fb0ddd2aaac9d"),
  "name": "Voltorb",
  "description": "Se parece com uma pokebola e pode explodir",
  "attack": 20,
  "defence": 20,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ],
  "type": null
}
Fetched 3 record(s) in 1ms

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **menor ou igual** a 49.##
carlos-pc(mongod-3.0.7) be-mean-pokemons> var query = { $and: [{ moves: "investida" }, {defence: {$lte: 49} }] }
carlos-pc(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query).limit(3)
{
  "_id": ObjectId("565fb522096fb0ddd2aaac9c"),
  "name": "Sandshrew",
  "description": "Rato grande azul e com orelhas gigantes",
  "attack": 30,
  "defence": 20,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ],
  "type": null
}
{
  "_id": ObjectId("565fb630096fb0ddd2aaac9e"),
  "name": "Exeggcute",
  "description": "Esse é muito estranho, parece um monte de ovos",
  "attack": 20,
  "defence": 40,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "hipnose",
    "desvio"
  ],
  "type": null
}
{
  "_id": ObjectId("565fb585096fb0ddd2aaac9d"),
  "name": "Voltorb",
  "description": "Se parece com uma pokebola e pode explodir",
  "attack": 20,
  "defence": 20,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ],
  "type": null
}
Fetched 3 record(s) in 1ms

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
carlos-pc(mongod-3.0.7) be-mean-pokemons> var query = {type: "água"}
carlos-pc(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("566c69a24b0360f9c9d98fa1"),
  "name": "AindaNaoExisteMon",
  "active": true,
  "description": "Sem maiores informações",
  "attack": null,
  "defence": null,
  "height": null,
  "type": "água"
}
Fetched 1 record(s) in 2ms
carlos-pc(mongod-3.0.7) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 3ms
WriteResult({
  "nRemoved": 1
})
carlos-pc(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms

```
