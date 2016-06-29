# MongoDB - Aula 04 - Exercício
autor: sirrommer - Rômulo Brasil

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
WriteResult({ 
  "nMatched" : 5, 
  "nUpserted" : 0, 
  "nModified" : 5 
})
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
var query = { name: /AindaNaoExisteMon/i } 
var mod = { 
  $setOnInsert: { 
    name: "AindaNaoExisteMon", 
    attack: null, 
    height: null, 
    defense: null, 
    moves: [], 
    description: "Sem maiores informações" 
  }
}
var opts = { upsert: true }
db.pokemons.update(query, mod, opts)
WriteResult({
"nMatched" : 0,
"nUpserted" : 1,
"nModified" : 0,
"_id" : ObjectId("5661e1d5476145fe95385411")
})
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
var query = { moves: { $all: ['investida', /choque do trovão/i] }}
db.pokemons.find(query)
{ 
  "_id" : ObjectId("564a467a740cc428f1f83908"), 
  "name" : "Pikachu", 
  "description" : "Rato elétrico bem fofinho", 
  "type" : "electric", 
  "attack" : 100, 
  "height" : 0.4, 
  "moves" : [ "esquiva", "corrida", "desvio" ], 
  "active": false 
}
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```
var query = { moves: { $in: [/esquiva/i] }}
db.pokemons.find(query)
{ 
  "_id" : ObjectId("564a467a740cc428f1f83908"), 
  "name" : "Pikachu", 
  "description" : "Rato elétrico bem fofinho", 
  "type" : "electric", 
  "attack" : 100, 
  "height" : 0.4, 
  "moves" : [ "esquiva", "corrida", "desvio" ],
  "active": false 
}
{ 
  "_id" : ObjectId("564a467f740cc428f1f83909"), 
  "name" : "Bulbassauro", 
  "description" : "Chicote de trepadeira", 
  "type" : "grama", 
  "attack" : 49, 
  "height" : 0.4, 
  "moves" : [ "esquiva", "corrida", "desvio" ],
  "active": false 
}
{ 
  "_id" : ObjectId("564a4685740cc428f1f8390a"), 
  "name" : "Charmander", 
  "description" : "Esse é o cão chupando manga de fofinho", 
  "type" : "fogo", 
  "attack" : 52, 
  "height" : 0.6, 
  "moves" : [ "esquiva", "corrida", "desvio" ],
  "active": false 
}

```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```
var query = { type: { $ne: "elétrico" }};
db.pokemons.find(query)
{ 
  "_id" : ObjectId("564a467a740cc428f1f83908"), 
  "name" : "Pikachu", 
  "description" : "Rato elétrico bem fofinho", 
  "type" : "electric", 
  "attack" : 100, 
  "height" : 0.4,
  "moves" : [ "esquiva", "corrida", "desvio" ],
  "active": false 
}
{ 
  "_id" : ObjectId("564a467f740cc428f1f83909"), 
  "name" : "Bulbassauro", 
  "description" : "Chicote de trepadeira",
  "type" : "grama", 
  "attack" : 49, 
  "height" : 0.4, 
  "moves" : [ "esquiva", "corrida", "desvio" ],
  "active": false 
}
{ 
  "_id" : ObjectId("564a4685740cc428f1f8390a"),
  "name" : "Charmander", 
  "description" : "Esse é o cão chupando manga de fofinho", 
  "type" : "fogo", 
  "attack" : 52,
  "height" : 0.6, 
  "moves" : [ "esquiva", "corrida", "desvio" ],
  "active": false 
}
{ 
  "_id" : ObjectId("564a4696740cc428f1f8390b"), 
  "name" : "Caterpie", 
  "description" : "Larva Lutadora", 
  "type" : "inseto", 
  "attack" : 30, 
  "height" : 0.3, 
  "moves" : [ "desvio" ],
  "active": false 
}
{ 
  "_id" : ObjectId("564a46d7740cc428f1f8390c"), 
  "name" : "charizard", 
  "description" : "Charizard é um Pokémon tipo Fogo e Voador. Ele é a forma final da evolução de Charmander e Charmeleon quando chega no nível 36", 
  "type" : "fogo", 
  "attack" : 40, 
  "defense" : 30, 
  "heigth" : 90, 
  "moves" : [ "desvio" ],
  "active": false 
}
{ 
  "_id" : ObjectId("5661e1d5476145fe95385411"), 
  "name" : "AindaNaoExisteMon", 
  "attack" : null,
  "height" : null, 
  "defense" : null, 
  "moves" : [ ], 
  "description" : "Sem maiores informações"
}
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
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
var query = { $and:[ { type: "água" }, { attack: { $lt: 50 }} ]}
db.pokemons.remove(query)
WriteResult({
  "nRemoved": 1
})
```
