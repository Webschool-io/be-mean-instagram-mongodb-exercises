# MongoDB - Aula 04 - Exercício
autor: Jadir J. Silva Junior

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
ubuntu(mongod-3.0.7) be-mean-pokemons-01> db.pokemons.findOne({name:/bulbasaur/i})
{
  "_id": ObjectId("565849392d2ce8b8b6eeb13c"),
  "name": "Bulbasaur",
  "description": "Bulbasaur is a Grass/Poison type pokemon. It is known as the 'Seed Pokemon'",
  "attack": 49,
  "defense": 49,
  "height": 0.7,
  "types": [
    "grass",
    "poison"
  ]
}
ubuntu(mongod-3.0.7) be-mean-pokemons-01> var query = {"_id": ObjectId("565849392d2ce8b8b6eeb13c")}
ubuntu(mongod-3.0.7) be-mean-pokemons-01> var attacks = ["Overgrow", "Chlorophyll"]
ubuntu(mongod-3.0.7) be-mean-pokemons-01> var mod = {$pushAll: {moves: attacks}}
ubuntu(mongod-3.0.7) be-mean-pokemons-01> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

ubuntu(mongod-3.0.7) be-mean-pokemons-01> db.pokemons.findOne({name:/charmander/i})
{
  "_id": ObjectId("5658499f2d2ce8b8b6eeb13d"),
  "name": "Charmander",
  "description": "Charmander is a Fire type pokemon. It is known as the 'Lizard Pokemon'",
  "attack": 52,
  "defense": 43,
  "height": 0.6,
  "types": [
    "fire"
  ]
}
ubuntu(mongod-3.0.7) be-mean-pokemons-01> var query = {"_id": ObjectId("5658499f2d2ce8b8b6eeb13d")}
ubuntu(mongod-3.0.7) be-mean-pokemons-01> var attacks = ["Blaze", "Solar Power"]
ubuntu(mongod-3.0.7) be-mean-pokemons-01> var mod = {$pushAll: {moves: attacks}}
ubuntu(mongod-3.0.7) be-mean-pokemons-01> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

ubuntu(mongod-3.0.7) be-mean-pokemons-01> db.pokemons.findOne({name: /squirtle/i})
{
  "_id": ObjectId("56584a072d2ce8b8b6eeb13e"),
  "name": "Squirtle",
  "description": "Squirtle is a Water type pokemon. It is known as the 'Turtle Pokemon'",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "types": [
    "water"
  ]
}
ubuntu(mongod-3.0.7) be-mean-pokemons-01> var query = {"_id": ObjectId("56584a072d2ce8b8b6eeb13e")}
ubuntu(mongod-3.0.7) be-mean-pokemons-01> var attacks = ["Torrent","Rain Dish"]
ubuntu(mongod-3.0.7) be-mean-pokemons-01> var mod = {$pushAll: {moves: attacks}}
ubuntu(mongod-3.0.7) be-mean-pokemons-01> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

ubuntu(mongod-3.0.7) be-mean-pokemons-01> db.pokemons.findOne({name: /pikachu/i})
{
  "_id": ObjectId("56589e0e258cc2cc1c7517a4"),
  "name": "Pikachu",
  "description": "Pikachu is an Electric type Pokemon. It is known as the 'Mouse Pokemon'",
  "attack": 55,
  "defense": 40,
  "height": 0.4,
  "types": [
    "eletric"
  ]
}
ubuntu(mongod-3.0.7) be-mean-pokemons-01> var query = {"_id": ObjectId("56589e0e258cc2cc1c7517a4")}
ubuntu(mongod-3.0.7) be-mean-pokemons-01> var attacks = ["Static","Lightning Rod"]
ubuntu(mongod-3.0.7) be-mean-pokemons-01> var mod = {$pushAll: {moves: attacks}}
ubuntu(mongod-3.0.7) be-mean-pokemons-01> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

```
## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```
ubuntu(mongod-3.0.7) be-mean-pokemons-01> var query = {}
ubuntu(mongod-3.0.7) be-mean-pokemons-01> var mod = {$push: {moves: "desvio"}}
ubuntu(mongod-3.0.7) be-mean-pokemons-01> var options = {multi: true}
ubuntu(mongod-3.0.7) be-mean-pokemons-01> db.pokemons.update(query, mod, options)
Updated 9 existing record(s) in 3ms
WriteResult({
  "nMatched": 9,
  "nUpserted": 0,
  "nModified": 9
})
```
## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
ubuntu(mongod-3.0.7) be-mean-pokemons-01> var query = {name: "AindaNaoExisteMon"}
ubuntu(mongod-3.0.7) be-mean-pokemons-01> var mod = {
... $set: {active: true},
... $setOnInsert: {name: "AindaNaoExisteMon", attack: null, defense: null, height:null, description: "Sem maiores inforamções"}
... }
ubuntu(mongod-3.0.7) be-mean-pokemons-01> var options  = {upsert: true}
ubuntu(mongod-3.0.7) be-mean-pokemons-01> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 60ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("565c2fb89180c6eea572838b")
})
```
## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
ubuntu(mongod-3.0.7) be-mean-pokemons-01> var query = {$or: [{name:/squirtle/i},{moves: {$in: ['investida']}}]}
ubuntu(mongod-3.0.7) be-mean-pokemons-01> db.pokemons.find(query)
```
## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```
ubuntu(mongod-3.0.7) be-mean-pokemons-01> var query = {moves: {$in: ['investida', 'Static']}}
ubuntu(mongod-3.0.7) be-mean-pokemons-01> db.pokemons.find(query)
```
## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```
ubuntu(mongod-3.0.7) be-mean-pokemons-01> var query = {types: {$in: ['eletric']}}
ubuntu(mongod-3.0.7) be-mean-pokemons-01> db.pokemons.find(query)
```
## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```
ubuntu(mongod-3.0.7) be-mean-pokemons-01> var query = {$and: [{moves: {$in: ['investida']}}, {defense: {$lte: 49}}]}
ubuntu(mongod-3.0.7) be-mean-pokemons-01> db.pokemons.find(query)
```
## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
ubuntu(mongod-3.0.7) be-mean-pokemons-01> var query = {$and: [{types: {$in: ['water']}}, {attack: {$lt: 50}}]}
db.pokemons.remove(query)
```
