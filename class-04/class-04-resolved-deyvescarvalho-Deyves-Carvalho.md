# MongoDB - Aula 04 - Exercício
autor: Deyves Carvalho

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> var query = {name: /butterfree/i}
deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> var mod = {$pushAll: {moves:['voacao doica', 'raio laser']}}
deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms


deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> var query = {name: /psyduck/i}
deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> var mod = {$pushAll: {moves:['bugar miolo', 'mente aberta']}}
deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms


deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> var query = {name: /nidorino/i}
deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> var mod = {$pushAll: {moves:['fuga sagaz', 'rino massacrador']}}
deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms


deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> var query = {name: /alakazam/i}
deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> var mod = {$pushAll: {moves:['zoa mentes', 'muda cabeças']}}
deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms


## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> var mod = {$push: {moves: 'desvio'}}
deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> var options = {multi: true}
deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 6 existing record(s) in 2ms



## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}
deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> var mod = {$setOnInsert: {name: 'AindaNaoExisteMon', type: null, attack: null, defense: null, height: null, description: 'Sem maiores informações'}}
deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> var options = {upsert: true}
deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 1ms

deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56e8a90a16e26c5bfc408b93"),
  "attack": null,
  "defense": null,
  "description": "Sem maiores informações",
  "height": null,
  "name": "AindaNaoExisteMon",
  "type": null
}
Fetched 1 record(s) in 3ms


## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> var query = {
... moves: {$in: [/investida/i, /magia porra/i]}}
deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56e2500c7a4c407e4ead4dad"),
  "active": false,
  "attack": 20,
  "defense": 20,
  "description": "Borboleta com super ataque, através dos seus olhos de BLACK KAMEN RIDER.",
  "height": 1.1,
  "moves": [
    "investida",
    "Magia porra",
    "voacao doica",
    "raio laser",
    "desvio"
  ],
  "name": "Butterfree"
}
{
  "_id": ObjectId("56e749e084033fe24ed99568"),
  "active": false,
  "attack": 7100,
  "defense": 8000,
  "description": "Pokemon de teste",
  "moves": [
    "investida",
    "desvio"
  ],
  "name": "Testemon"
}
{
  "_id": ObjectId("56e2500c7a4c407e4ead4dac"),
  "active": false,
  "attack": 30,
  "defense": 20,
  "description": "Rato, que pode infectar facilmente seus oponentes.",
  "height": 0.3,
  "moves": [
    "investida",
    "Magia porra",
    "desvio"
  ],
  "name": "Rattata"
}
{
  "_id": ObjectId("56e2500c7a4c407e4ead4daa"),
  "active": false,
  "attack": 30,
  "defense": 20,
  "description": "Pato, que manja das magias mais fodas.",
  "height": 0.8,
  "moves": [
    "investida",
    "bugar miolo",
    "mente aberta",
    "desvio"
  ],
  "name": "Psyduck"
}
{
  "_id": ObjectId("56e2500c7a4c407e4ead4dab"),
  "active": false,
  "attack": 40,
  "defense": 30,
  "description": "Rinoceronte muito malandro",
  "height": 0.9,
  "moves": [
    "investida",
    "fuga sagaz",
    "rino massacrador",
    "desvio"
  ],
  "name": "Nidorino"
}
{
  "_id": ObjectId("56e2500c7a4c407e4ead4da9"),
  "active": false,
  "attack": 30,
  "defense": 20,
  "description": "Esse mago, é um mago mui loco",
  "height": 1.5,
  "moves": [
    "investida",
    "Magia porra",
    "zoa mentes",
    "muda cabeças",
    "desvio"
  ],
  "name": "Alakazam"
}
Fetched 6 record(s) in 230ms


## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> var query = {
... moves: {$all: [/investida/i, /magia porra/i]}}
deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56e2500c7a4c407e4ead4dad"),
  "active": false,
  "attack": 20,
  "defense": 20,
  "description": "Borboleta com super ataque, através dos seus olhos de BLACK KAMEN RIDER.",
  "height": 1.1,
  "moves": [
    "investida",
    "Magia porra",
    "voacao doica",
    "raio laser",
    "desvio"
  ],
  "name": "Butterfree"
}
{
  "_id": ObjectId("56e2500c7a4c407e4ead4dac"),
  "active": false,
  "attack": 30,
  "defense": 20,
  "description": "Rato, que pode infectar facilmente seus oponentes.",
  "height": 0.3,
  "moves": [
    "investida",
    "Magia porra",
    "desvio"
  ],
  "name": "Rattata"
}
{
  "_id": ObjectId("56e2500c7a4c407e4ead4da9"),
  "active": false,
  "attack": 30,
  "defense": 20,
  "description": "Esse mago, é um mago mui loco",
  "height": 1.5,
  "moves": [
    "investida",
    "Magia porra",
    "zoa mentes",
    "muda cabeças",
    "desvio"
  ],
  "name": "Alakazam"
}
Fetched 3 record(s) in 216ms

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> var query = {type: {$not: /eletrico/i}
... }
deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56e2500c7a4c407e4ead4dad"),
  "active": false,
  "attack": 20,
  "defense": 20,
  "description": "Borboleta com super ataque, através dos seus olhos de BLACK KAMEN RIDER.",
  "height": 1.1,
  "moves": [
    "investida",
    "Magia porra",
    "voacao doica",
    "raio laser",
    "desvio"
  ],
  "name": "Butterfree"
}
{
  "_id": ObjectId("56e749e084033fe24ed99568"),
  "active": false,
  "attack": 7100,
  "defense": 8000,
  "description": "Pokemon de teste",
  "moves": [
    "investida",
    "desvio"
  ],
  "name": "Testemon"
}
{
  "_id": ObjectId("56e2500c7a4c407e4ead4dac"),
  "active": false,
  "attack": 30,
  "defense": 20,
  "description": "Rato, que pode infectar facilmente seus oponentes.",
  "height": 0.3,
  "moves": [
    "investida",
    "Magia porra",
    "desvio"
  ],
  "name": "Rattata"
}
{
  "_id": ObjectId("56e2500c7a4c407e4ead4daa"),
  "active": false,
  "attack": 30,
  "defense": 20,
  "description": "Pato, que manja das magias mais fodas.",
  "height": 0.8,
  "moves": [
    "investida",
    "bugar miolo",
    "mente aberta",
    "desvio"
  ],
  "name": "Psyduck"
}
{
  "_id": ObjectId("56e2500c7a4c407e4ead4dab"),
  "active": false,
  "attack": 40,
  "defense": 30,
  "description": "Rinoceronte muito malandro",
  "height": 0.9,
  "moves": [
    "investida",
    "fuga sagaz",
    "rino massacrador",
    "desvio"
  ],
  "name": "Nidorino"
}
{
  "_id": ObjectId("56e2500c7a4c407e4ead4da9"),
  "active": false,
  "attack": 30,
  "defense": 20,
  "description": "Esse mago, é um mago mui loco",
  "height": 1.5,
  "moves": [
    "investida",
    "Magia porra",
    "zoa mentes",
    "muda cabeças",
    "desvio"
  ],
  "name": "Alakazam"
}
{
  "_id": ObjectId("56e8a90a16e26c5bfc408b93"),
  "attack": null,
  "defense": null,
  "description": "Sem maiores informações",
  "height": null,
  "name": "AindaNaoExisteMon",
  "type": null
}
Fetched 7 record(s) in 6ms


## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> var query = {$and: [ {moves: {$in: ['investida']}}, {attack: {$not: {$lte: 49}}}]}
deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56e749e084033fe24ed99568"),
  "active": false,
  "attack": 7100,
  "defense": 8000,
  "description": "Pokemon de teste",
  "moves": [
    "investida",
    "desvio"
  ],
  "name": "Testemon"
}
Fetched 1 record(s) in 221ms


## Remova **todos** os pokemons do tipo água e com attack menor que 50.

deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> var query = {$and: [ {type: /agua/i}, {attack: {$lt: 50}}]}
deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> db.pokemons.remove(query)
Removed 0 record(s) in 1ms
