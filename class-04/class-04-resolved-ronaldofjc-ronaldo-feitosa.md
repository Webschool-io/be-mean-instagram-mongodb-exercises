# MongoDB - Aula 04 - Exercício
autor: Ronaldo Feitosa

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander;

```
var query = {name: /pikachu/i}
var attacks = ['raio elétrico', 'rajada de raios']
var mod = {$pushAll:{moves: attacks}}
db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

db.pokemons.find(query)
{
  "_id": ObjectId("56e74e19334563dc5915b2f2"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "raio elétrico",
    "rajada de raios"
  ],
  "active": false
}
Fetched 1 record(s) in 1ms

var query = {name: /squirtle/i}
var attacks = ['tsunami', 'fúria do mar']
var mod = {$pushAll:{moves: attacks}}
db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

db.pokemons.find(query)
{
  "_id": ObjectId("56e74e6a334563dc5915b2f5"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "tsunami",
    "fúria do mar"
  ]
}
Fetched 1 record(s) in 1ms

var query = {name: /bulbassauro/i}
var attacks = ['galhos cortantes', 'explosão verde']
var mod = {$pushAll:{moves: attacks}}
db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
db.pokemons.find(query)
{
  "_id": ObjectId("56e74e2e334563dc5915b2f3"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "galhos cortantes",
    "explosão verde"
  ]
}
Fetched 1 record(s) in 3ms

var query = {name: /charmander/i}
var attacks = ['vulcão em erupção', 'tempestade de fogo']
var mod = {$pushAll:{moves: attacks}}
db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

db.pokemons.find(query)
{
  "_id": ObjectId("56e74e4b334563dc5915b2f4"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança chamas",
    "vulcão em erupção",
    "tempestade de fogo"
  ]
}
Fetched 1 record(s) in 1ms

```


## **Adicionar** 1 movimento em todos os pokemons: 'desvio';

```
var query = {}
var mod = {$push:{moves: 'desvio'}}
var options = {multi: true}
db.pokemons.update(query, mod, options)

```


## **Adicionar** o pokemon 'AindaNaoExisteMon' caso ele não exista com todos os dados com o valor 'null' e a descrição: "Sem maiores informações";

```
var query = {name: /AindaNaoExisteMon/i}
var mod = {$setOnInsert:{name: "AindaNaoExisteMon", type: null, attack: null, height: null, active: false, moves: null, description: "Sem maiores informações"}}
var options = {upsert: true}
db.pokemons.update(query, mod, options)

Updated 1 new record(s) in 1ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("56e990f87e3a81c70cb353a9")
})

db.pokemons.find(query)
{
  "_id": ObjectId("56e990f87e3a81c70cb353a9"),
  "name": "AindaNaoExisteMon",
  "type": null,
  "attack": null,
  "height": null,
  "active": false,
  "moves": null,
  "description": "Sem maiores informações"
}
Fetched 1 record(s) in 2ms

```


## Pesquisar todos os pokemons que possuam o ataque 'investida' e mais um que você adicionou, escolha seu pokemon favorito;

```
var query = {moves: {$in: [/investida/i, /tsunami/i]}}
db.pokemons.find(query)

```
## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito;

```
var query = {moves: {$all: [/investida/i, /tsunami/i]}}
db.pokemons.find(query)
{
  "_id": ObjectId("56e74e6a334563dc5915b2f5"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "tsunami",
    "fúria do mar",
    "desvio"
  ]
}
Fetched 1 record(s) in 0ms

```


## Pesquisar **todos** os pokemons que não são do tipo 'elétrico';

```
var query = {type: {$ne: 'electric'}}
db.pokemons.find(query)
{
  "_id": ObjectId("56e5be1c1ed08ada9f1ebe72"),
  "name": "Mewtwo",
  "description": "Pokemon super poderoso",
  "type": "psíquico",
  "height": "6.7",
  "attack": 35,
  "defense": 30,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56e5bef71ed08ada9f1ebe74"),
  "name": "Kadabra",
  "description": "Mestre das colheres tortas",
  "type": "psíquico",
  "height": 4.3,
  "attack": 35,
  "defense": 30,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56e5bfe41ed08ada9f1ebe75"),
  "name": "Cubone",
  "description": "Pokemon cabeça de Osso",
  "type": "terra",
  "height": 1.4,
  "attack": 50,
  "defense": 95,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56e5c0c61ed08ada9f1ebe76"),
  "name": "Vaporeon",
  "description": "Pokemon aquático evoluído do Eevee",
  "type": "água",
  "height": 3.3,
  "attack": 65,
  "defense": 60,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56e5c0ff1ed08ada9f1ebe77"),
  "name": "Butterfree",
  "description": "Pokemon voador",
  "type": "vento",
  "height": 3.7,
  "attack": 45,
  "defense": 50,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56e5c1931ed08ada9f1ebe78"),
  "name": "Golbat",
  "description": "Morcego sanguinário",
  "type": "vento e veneno",
  "height": 5.3,
  "attack": 80,
  "defense": 70,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56e74e2e334563dc5915b2f3"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "galhos cortantes",
    "explosão verde",
    "desvio"
  ]
}
{
  "_id": ObjectId("56e74e6a334563dc5915b2f5"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "tsunami",
    "fúria do mar",
    "desvio"
  ]
}
{
  "_id": ObjectId("56e9535771ff65fe620a04a7"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56e990f87e3a81c70cb353a9"),
  "name": "AindaNaoExisteMon",
  "type": null,
  "attack": null,
  "height": null,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ],
  "description": "Sem maiores informações"
}
{
  "_id": ObjectId("56e74e4b334563dc5915b2f4"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "vulcão em erupção",
    "tempestade de fogo",
    "desvio"
  ]
}
Fetched 11 record(s) in 4ms

```


## Pesquisar **todos** os pokemons que tenham o ataque 'investida' **E**tenham o attack **não menor ou igual** a 49;

```
var query = {$and: [{moves: {$in: ['investida']}}, {attack: {$not: {$lte: 49}}}]}
db.pokemons.find(query)
{
  "_id": ObjectId("56e5bfe41ed08ada9f1ebe75"),
  "name": "Cubone",
  "description": "Pokemon cabeça de Osso",
  "type": "terra",
  "height": 1.4,
  "attack": 50,
  "defense": 95,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56e5c0c61ed08ada9f1ebe76"),
  "name": "Vaporeon",
  "description": "Pokemon aquático evoluído do Eevee",
  "type": "água",
  "height": 3.3,
  "attack": 65,
  "defense": 60,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56e5c1931ed08ada9f1ebe78"),
  "name": "Golbat",
  "description": "Morcego sanguinário",
  "type": "vento e veneno",
  "height": 5.3,
  "attack": 80,
  "defense": 70,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56e9535771ff65fe620a04a7"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56e74e19334563dc5915b2f2"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "raio elétrico",
    "rajada de raios",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("56e990f87e3a81c70cb353a9"),
  "name": "AindaNaoExisteMon",
  "type": null,
  "attack": null,
  "height": null,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ],
  "description": "Sem maiores informações"
}
{
  "_id": ObjectId("56e74e4b334563dc5915b2f4"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "vulcão em erupção",
    "tempestade de fogo",
    "desvio"
  ]
}
Fetched 7 record(s) in 4ms

```

## Remova **todos** os pokemons do tipo água e com attack menor que 50;

```
var query = {$and: [{type: /água/i}, {attack: {$lt: 50 }}]}
db.pokemons.remove(query)
Removed 1 record(s) in 1ms
WriteResult({
  "nRemoved": 1
})

```

