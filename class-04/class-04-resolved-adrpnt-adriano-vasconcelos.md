# MongoDB - Aula 04 - Exercício
autor: Adriano Vasconcelos

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
var query = { $or: [ {name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbassauro/i}, {name: /charmander/i} ]};
var mod = { $pushAll: { moves: ['esquiva','corrida']}};
var opts = { multi: true };
db.pokemons.update(query, mod, opts);
Updated 4 existing record(s) in 360ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```
var query = {};
var mod = { $push: { moves: "desvio"}}
var opts = { multi: true }
db.pokemons.update(query, mod, opts)
Updated 11 existing record(s) in 3ms
WriteResult({
  "nMatched": 11,
  "nUpserted": 0,
  "nModified": 11
})
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
var query = { name: /AindaNaoExisteMon/i }
var mod = { $setOnInsert: {
    name: "AindaNaoExisteMon"
  , attack: null
  , height: null
  , defense: null
  , moves: []
  , description: "Sem maiores informações"
}}
var opts = { upsert: true }
db.pokemons.update(query, mod, opts)
Updated 1 new record(s) in 5ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564f6eb6a6be0ea29a29c1b1")
})
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
var query = { moves: { $all: ['investida', /choque do trovão/i] }}
db.pokemons.find(query)
{
  "_id": ObjectId("564f6d83afbe680047500283"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "esquiva",
    "corrida",
    "desvio",
    "investida",
    "choque do trovão"
  ],
  "active": false
}
Fetched 1 record(s) in 1ms
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```
var query = { moves: { $in: [/esquiva/i] }}
db.pokemons.find(query)
{
  "_id": ObjectId("564f6da1afbe680047500284"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "esquiva",
    "corrida",
    "desvio",
    "investida"
  ],
  "active": false
}
{
  "_id": ObjectId("564f6db4afbe680047500285"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "esquiva",
    "corrida",
    "desvio",
    "investida"
  ],
  "active": false
}
{
  "_id": ObjectId("564f6de0afbe680047500286"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "esquiva",
    "corrida",
    "desvio",
    "investida"
  ],
  "active": false
}
{
  "_id": ObjectId("564f6d83afbe680047500283"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "esquiva",
    "corrida",
    "desvio",
    "investida",
    "choque do trovão"
  ],
  "active": false
}
Fetched 4 record(s) in 1ms
```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```
var query = { type: { $ne: "elétrico" }};
db.pokemons.find(query)
{
  "_id": ObjectId("564f6da1afbe680047500284"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "esquiva",
    "corrida",
    "desvio",
    "investida"
  ],
  "active": false
}
{
  "_id": ObjectId("564f6db4afbe680047500285"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "esquiva",
    "corrida",
    "desvio",
    "investida"
  ],
  "active": false
}
{
  "_id": ObjectId("564f6de0afbe680047500286"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "moves": [
    "esquiva",
    "corrida",
    "desvio",
    "investida"
  ],
  "active": false
}
{
  "_id": ObjectId("564379f8750d5acfe9690da9"),
  "name": "Butterfree",
  "description": "In battle, it flaps its wings at high speed to release highly toxic dust into the air.",
  "type": "inseto",
  "attack": 45,
  "defense": 50,
  "height": 0.3,
  "heigth": 0.3,
  "moves": [
    "desvio",
    "investida"
  ],
  "active": false
}
{
  "_id": ObjectId("56437bb5750d5acfe9690dab"),
  "name": "Ninetales",
  "description": "Its nine tails are said to be imbued with a mystic power. It can live for a thousand years.",
  "type": "fogo",
  "attack": 76,
  "defense": 75,
  "height": 0.3,
  "moves": [
    "desvio",
    "investida"
  ],
  "active": false
}
{
  "_id": ObjectId("56437c43750d5acfe9690dac"),
  "name": "Grimer",
  "description": "Appears in filthy areas. Thrives by sucking up polluted sludge that is pumped out of factories.",
  "type": "veneno",
  "attack": 80,
  "defense": 50,
  "height": 0.2,
  "moves": [
    "desvio",
    "investida"
  ],
  "active": false
}
{
  "_id": ObjectId("56437e14750d5acfe9690db0"),
  "name": "Nidorina",
  "description": "When NIDORINA are with their friends or family, they keep their barbs tucked away to prevent hurting each other.",
  "type": "veneno",
  "attack": 62,
  "defense": 67,
  "height": 0.2,
  "moves": [
    "desvio",
    "investida"
  ],
  "active": false
}
{
  "_id": ObjectId("564f6eb6a6be0ea29a29c1b1"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "height": null,
  "defense": null,
  "moves": [
    "investida"
  ],
  "description": "Sem maiores informações",
  "active": false
}
{
  "_id": ObjectId("56437b1d750d5acfe9690daa"),
  "name": "Arbok",
  "description": "The frightening patterns on its belly have been studied. Six variations have been confirmed.",
  "type": "veneno",
  "attack": 85,
  "defense": 69,
  "height": 0.9,
  "moves": [
    "desvio",
    "investida"
  ],
  "active": false
}
{
  "_id": ObjectId("56437cbb750d5acfe9690dad"),
  "name": "Dewgong",
  "description": "Stores thermal energy in its body. Swims at a steady 8 knots even in intensely cold waters.",
  "type": "água",
  "attack": 70,
  "defense": 80,
  "height": 0.4,
  "moves": [
    "desvio",
    "investida"
  ],
  "active": false
}
{
  "_id": ObjectId("56437e14750d5acfe9690daf"),
  "name": "Beedrill",
  "description": "It can take down any opponent with its powerful poi son stingers.",
  "type": "inseto",
  "attack": 90,
  "defense": 40,
  "height": 0.2,
  "moves": [
    "desvio",
    "investida"
  ],
  "active": false
}
Fetched 11 record(s) in 5ms
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```
var query = { $and:[ { moves: { $in: [/investida/i]} }, { defense: { $gt: 49 } } ]}
db.pokemons.find(query)
{
  "_id": ObjectId("564379f8750d5acfe9690da9"),
  "name": "Butterfree",
  "description": "In battle, it flaps its wings at high speed to release highly toxic dust into the air.",
  "type": "inseto",
  "attack": 45,
  "defense": 50,
  "height": 0.3,
  "heigth": 0.3,
  "moves": [
    "desvio",
    "investida"
  ],
  "active": false
}
{
  "_id": ObjectId("56437bb5750d5acfe9690dab"),
  "name": "Ninetales",
  "description": "Its nine tails are said to be imbued with a mystic power. It can live for a thousand years.",
  "type": "fogo",
  "attack": 76,
  "defense": 75,
  "height": 0.3,
  "moves": [
    "desvio",
    "investida"
  ],
  "active": false
}
{
  "_id": ObjectId("56437c43750d5acfe9690dac"),
  "name": "Grimer",
  "description": "Appears in filthy areas. Thrives by sucking up polluted sludge that is pumped out of factories.",
  "type": "veneno",
  "attack": 80,
  "defense": 50,
  "height": 0.2,
  "moves": [
    "desvio",
    "investida"
  ],
  "active": false
}
{
  "_id": ObjectId("56437e14750d5acfe9690db0"),
  "name": "Nidorina",
  "description": "When NIDORINA are with their friends or family, they keep their barbs tucked away to prevent hurting each other.",
  "type": "veneno",
  "attack": 62,
  "defense": 67,
  "height": 0.2,
  "moves": [
    "desvio",
    "investida"
  ],
  "active": false
}
{
  "_id": ObjectId("56437b1d750d5acfe9690daa"),
  "name": "Arbok",
  "description": "The frightening patterns on its belly have been studied. Six variations have been confirmed.",
  "type": "veneno",
  "attack": 85,
  "defense": 69,
  "height": 0.9,
  "moves": [
    "desvio",
    "investida"
  ],
  "active": false
}
{
  "_id": ObjectId("56437cbb750d5acfe9690dad"),
  "name": "Dewgong",
  "description": "Stores thermal energy in its body. Swims at a steady 8 knots even in intensely cold waters.",
  "type": "água",
  "attack": 70,
  "defense": 80,
  "height": 0.4,
  "moves": [
    "desvio",
    "investida"
  ],
  "active": false
}
Fetched 6 record(s) in 5ms

```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
var query = { $and:[ { type: "água" }, { attack: { $lt: 50 }} ]}
db.pokemons.remove(query)
Removed 1 record(s) in 2ms
WriteResult({
  "nRemoved": 1
})
```
