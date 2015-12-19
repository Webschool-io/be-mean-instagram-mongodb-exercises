# MongoDB - Aula 04 - Exercício
autor: José Antonio Gaeta Mendes

## Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
var query = { $or: [ {name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbassauro/i}, {name: /charmander/i} ]};

var mod = { $pushAll: { moves: ['dança da chuva','ataque oculto']}};

var opt = {multi: true}

db.pokemons.update(query, mod, opt);
Updated 4 existing record(s) in 2ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})

db.pokemons.find(query)

{
  "_id": ObjectId("564292c5a42672eb82036d26"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "dança da chuva",
    "ataque oculto"
  ]
}
{
  "_id": ObjectId("5642934fa42672eb82036d27"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "dança da chuva",
    "ataque oculto"
  ]
}
{
  "_id": ObjectId("564293b2a42672eb82036d28"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.5,
  "moves": [
    "dança da chuva",
    "ataque oculto"
  ]
}
{
  "_id": ObjectId("56429404a42672eb82036d29"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "dança da chuva",
    "ataque oculto"
  ]
}
Fetched 4 record(s) in 3ms
```

## Adicionar 1 movimento em todos os pokemons: `desvio`

```
var query = {};
var mod = { $push: { moves: "desvio"}};
var opt = { multi: true };
db.pokemons.update(query, mod, opt);
Updated 10 existing record(s) in 2ms
WriteResult({
  "nMatched": 10,
  "nUpserted": 0,
  "nModified": 10
})
```

## Adicionar o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações"

```
query
{
  "name": /AindaNaoExisteMon/i
}

mod
{
  "$setOnInsert": {
    "name": "AindaNaoExisteMon",
    "attack": null,
    "height": null,
    "defense": null,
    "moves": [ ],
    "description": "Sem maiores informações"
  }
}

opt
{
  "upsert": true
}

db.pokemons.update(query, mod, opt);
Updated 1 new record(s) in 4ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564dcfc4bdd56b75faba3b49")
})
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito

```
var query = { moves: { $in: [/investida/i, /dança da chuva/i] }};
db.pokemons.find(query)
{
  "_id": ObjectId("564292c5a42672eb82036d26"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "dança da chuva",
    "ataque oculto",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642934fa42672eb82036d27"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "dança da chuva",
    "ataque oculto",
    "desvio"
  ]
}
{
  "_id": ObjectId("564293b2a42672eb82036d28"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.5,
  "moves": [
    "dança da chuva",
    "ataque oculto",
    "desvio"
  ]
}
{
  "_id": ObjectId("56429404a42672eb82036d29"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "dança da chuva",
    "ataque oculto",
    "desvio"
  ]
}
Fetched 4 record(s) in 2ms
```

## Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito

```
var query = {moves: {$in: ['dança da chuva','ataque oculto']}}
db.pokemons.find(query);
{
  "_id": ObjectId("564292c5a42672eb82036d26"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "dança da chuva",
    "ataque oculto",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642934fa42672eb82036d27"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "dança da chuva",
    "ataque oculto",
    "desvio"
  ]
}
{
  "_id": ObjectId("564293b2a42672eb82036d28"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.5,
  "moves": [
    "dança da chuva",
    "ataque oculto",
    "desvio"
  ]
}
{
  "_id": ObjectId("56429404a42672eb82036d29"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "dança da chuva",
    "ataque oculto",
    "desvio"
  ]
}
Fetched 4 record(s) in 2ms
```

## Pesquisar todos os pokemons que não são do tipo `elétrico`

```
MacBookPro(mongod-3.0.7) be-mean-instagram> var query = { type: { $ne: 'eletric'} }
MacBookPro(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query);
{
  "_id": ObjectId("5642934fa42672eb82036d27"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "dança da chuva",
    "ataque oculto",
    "desvio"
  ]
}
{
  "_id": ObjectId("564293b2a42672eb82036d28"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.5,
  "moves": [
    "dança da chuva",
    "ataque oculto",
    "desvio"
  ]
}
{
  "_id": ObjectId("56429404a42672eb82036d29"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "dança da chuva",
    "ataque oculto",
    "desvio"
  ]
}
{
  "_id": ObjectId("56429595a42672eb82036d2a"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564478e7dcab83cf1ffdacfd"),
  "name": "Blastoise",
  "description": "Manda balas de água para todo lado",
  "type": "marisco",
  "attack": 63,
  "defense": 80,
  "height": 0.1,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56447908dcab83cf1ffdacfe"),
  "name": "Butterfree",
  "description": "Antenada no mel das flores",
  "type": "borboleta",
  "attack": 45,
  "defense": 50,
  "height": 0.11,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5644791ddcab83cf1ffdacff"),
  "name": "Weedle",
  "description": "Olfato privilegiado",
  "type": "inseto cabeludo",
  "attack": 35,
  "defense": 30,
  "height": 0.3,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5644793adcab83cf1ffdad00"),
  "name": "Beedrill",
  "description": "Defende seu território",
  "type": "abelha venenosa",
  "attack": 90,
  "defense": 40,
  "height": 0.1,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56447953dcab83cf1ffdad01"),
  "name": "Rattata",
  "description": "Bichinho muito arisco",
  "type": "rato",
  "attack": 56,
  "defense": 35,
  "height": 0.3,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564dcfc4bdd56b75faba3b49"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "height": null,
  "defense": null,
  "moves": [ ],
  "description": "Sem maiores informações"
}
Fetched 10 record(s) in 5ms
```

## Pesquisar todos pokemons que tenham o ataque `investida` E tenham a defesa não menor ou igual a 49

```
var query = { $and:[ { moves: { $in: [/investida/i]} }, { defense: { $lte: 49 } } ]};
MacBookPro(mongod-3.0.7) be-mean-instagram> var query = { $and:[ { moves: { $in: [/investida/i]} }, { defense: { $lte: 49 } } ]};
MacBookPro(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query);
Fetched 0 record(s) in 1ms
```

## Remova todos os pokemons do tipo água e com attack menor que 50

```
MacBookPro(mongod-3.0.7) be-mean-instagram> var query = { $and:[ { type: "água" }, { attack: { $lt: 50 }} ]};
MacBookPro(mongod-3.0.7) be-mean-instagram> db.pokemons.remove(query);
Removed 1 record(s) in 2ms
WriteResult({
  "nRemoved": 1
})
```
