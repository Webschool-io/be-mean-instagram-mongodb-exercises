# MongoDB - Aula 04 - Exercício
autor: **Igor Vidotto Felipe**

**1 -** **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokémons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
var query = {$or: [{name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbassauro/i}, {name: /charmander/i}]};
var mod = {$pushAll: {moves: ["Ataque Rápido", "Investida Rápida"]}};
var opt = {multi: true};
db.pokemons.update(query, mod, opt);
```

#### Saída

>```
Updated 4 existing record(s) in 3ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
```

**2 -** **Adicionar** 1 movimento em todos os pokémons: `desvio`.

```
var query = {};
var mod = {$push: {moves: "Desvio"}};
var opt = {multi: true};
db.pokemons.update(query, mod, opt);
```

#### Saída

>```
Updated 12 existing record(s) in 3ms
WriteResult({
  "nMatched": 12,
  "nUpserted": 0,
  "nModified": 12
})
```

**3 -** **Adicionar** o pokémon `AindaNaoExisteMon`, caso ele não exista, com todos os dados com o valor `null` e a descrição: "Sem maiores informações".

```
var query = {name: /AindaNaoExisteMon/i};
var opt = {upsert: true};
var mod = {
  	$setOnInsert: {
		name: "AindaNaoExisteMon",
		type: null,
		attack: null,
		defense: null,
		height: null,
		description: "Sem maiores informações"
  	}
};
db.pokemons.update(query, mod, opt);
```

#### Saída

>```
Updated 1 new record(s) in 2ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564f4c5ecc33dcb835ba60f1")
})
```

**4 -** Pesquisar todos os pokémons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokémon favorito.

#### Todos: 
```
var attacks = ["Investida", "Lança Chamas"];
var everybody = {moves: {$all: attacks}};
db.pokemons.find(todos);
```

#### Saída

>```
{
  "_id": ObjectId("564dc6463e726cf185f880a0"),
  "name": "Charizard",
  "description": "Dragão fodelão motherfucker que AshNoob abandona",
  "type": "fogo/voador",
  "attack": 84,
  "defense": 78,
  "height": 1.7,
  "moves": [
    "Investida",
    "Desvio",
    "Lança Chamas"
  ],
  "active": false
}
{
  "_id": ObjectId("5648ce1eb2b455d5cd60fd7d"),
  "name": "Charmander",
  "description": "Queima a rosca 4ever",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "Investida",
    "Ataque Rápido",
    "Investida Rápida",
    "Desvio",
    "Lança Chamas"
  ]
}
Fetched 2 record(s) in 2ms
```

#### Favorito: 
```
var favorite = {$and: [everybody, {name: /charizard/i}]};
db.pokemons.find(favorite);
```

#### Saída

>```
{
  "_id": ObjectId("564dc6463e726cf185f880a0"),
  "name": "Charizard",
  "description": "Dragão fodelão motherfucker que AshNoob abandona",
  "type": "fogo/voador",
  "attack": 84,
  "defense": 78,
  "height": 1.7,
  "moves": [
    "Investida",
    "Desvio",
    "Lança Chamas"
  ],
  "active": false
}
Fetched 1 record(s) in 1ms
```

**5 -** Pesquisar **todos** os pokémons que possuam os ataques que você adicionou, escolha seu pokémon favorito.

#### Todos

```
var myAdds = ["Ataque Rápido", "Investida Rápida"];
var everybody = {moves: {$all: myAdds}};
db.pokemons.find(everybody);
```
#### Saída

>```
{
  "_id": ObjectId("5648ce1eb2b455d5cd60fd7e"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "Investida",
    "Ataque Rápido",
    "Investida Rápida",
    "Desvio",
    "Hidro Bomba"
  ]
}
{
  "_id": ObjectId("5648ce1eb2b455d5cd60fd7c"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "Investida",
    "Folha Navalha",
    "Ataque Rápido",
    "Investida Rápida",
    "Desvio"
  ]
}
{
  "_id": ObjectId("5648ce1eb2b455d5cd60fd7d"),
  "name": "Charmander",
  "description": "Queima a rosca 4ever",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "Investida",
    "Ataque Rápido",
    "Investida Rápida",
    "Desvio",
    "Lança Chamas"
  ]
}
{
  "_id": ObjectId("564dc38c3e726cf185f8809d"),
  "name": "Pikachu",
  "description": "Rato elétrico",
  "type": "elétrico",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "Investida",
    "Choque do Trovão",
    "Ataque Rápido",
    "Investida Rápida",
    "Desvio"
  ],
  "active": false
}
Fetched 4 record(s) in 3ms
```

#### Favorito:
```
var favorite = {$and: [everybody, {name: /pikachu/i}]};
db.pokemons.find(favorite);
```

#### Saída

>```
{
  "_id": ObjectId("564dc38c3e726cf185f8809d"),
  "name": "Pikachu",
  "description": "Rato elétrico",
  "type": "elétrico",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "Investida",
    "Choque do Trovão",
    "Ataque Rápido",
    "Investida Rápida",
    "Desvio"
  ],
  "active": false
}
Fetched 1 record(s) in 1ms
```

**6 -** Pesquisar **todos** os pokémons que não são do tipo `elétrico`.

```
var query = {type: {$nin: ["elétrico"]}};
db.pokemons.find(query);
```

#### Saída

>```
{
  "_id": ObjectId("5648cf46b2b455d5cd60fd7f"),
  "name": "Caterpie",
  "description": "Larva lutadora lixosa",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "active": false,
  "moves": [
    "Investida",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564dc6463e726cf185f8809e"),
  "name": "Ninetales",
  "description": "Cachorro/Lobo que possui nove caldas (ah vá)",
  "type": "fogo",
  "attack": 76,
  "defense": 75,
  "height": 1.1,
  "active": false,
  "moves": [
    "Investida",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564dc6463e726cf185f8809f"),
  "name": "Jigglypuff",
  "description": "Uma bolinha de pelos rosa que canta",
  "type": "normal/fada",
  "attack": 45,
  "defense": 20,
  "height": 0.5,
  "active": false,
  "moves": [
    "Investida",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564dc6463e726cf185f880a0"),
  "name": "Charizard",
  "description": "Dragão fodelão motherfucker que AshNoob abandona",
  "type": "fogo/voador",
  "attack": 84,
  "defense": 78,
  "height": 1.7,
  "moves": [
    "Investida",
    "Desvio",
    "Lança Chamas"
  ],
  "active": false
}
{
  "_id": ObjectId("564dc6463e726cf185f880a1"),
  "name": "ButterFree",
  "description": "Última evolução do Caterpie, nesse estágio se torna uma borboleta (Ash também abandona)",
  "type": "inseto/voador",
  "attack": 45,
  "defense": 50,
  "height": 1.1,
  "active": false,
  "moves": [
    "Investida",
    "Desvio"
  ]
}
{
  "_id": ObjectId("5648ce1eb2b455d5cd60fd7e"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "Investida",
    "Ataque Rápido",
    "Investida Rápida",
    "Desvio",
    "Hidro Bomba"
  ]
}
{
  "_id": ObjectId("5648ce1eb2b455d5cd60fd7c"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "Investida",
    "Folha Navalha",
    "Ataque Rápido",
    "Investida Rápida",
    "Desvio"
  ]
}
{
  "_id": ObjectId("5648ce1eb2b455d5cd60fd7d"),
  "name": "Charmander",
  "description": "Queima a rosca 4ever",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "Investida",
    "Ataque Rápido",
    "Investida Rápida",
    "Desvio",
    "Lança Chamas"
  ]
}
{
  "_id": ObjectId("564dc6463e726cf185f880a2"),
  "name": "Pidgeot",
  "description": "Pássaro muito grande, um dos pokémons normais/voadores mais fortes",
  "type": "normal/voador",
  "attack": 80,
  "defense": 75,
  "height": 1.5,
  "active": false,
  "moves": [
    "Investida",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564f4c5ecc33dcb835ba60f1"),
  "name": "AindaNaoExisteMon",
  "type": null,
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 10 record(s) in 3ms
```

**7 -** Pesquisar **todos** os pokémons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.

```
var pokes = {moves: {$all: ["Investida"]}};
var condition = {defense: {$not: {$lte: 49}}};
var query = {$and: [pokes, condition]};
```

#### Saída

>```
{
  "_id": ObjectId("564dc6463e726cf185f8809e"),
  "name": "Ninetales",
  "description": "Cachorro/Lobo que possui nove caldas (ah vá)",
  "type": "fogo",
  "attack": 76,
  "defense": 75,
  "height": 1.1,
  "active": false,
  "moves": [
    "Investida",
    "Desvio"
  ]
}
{
  "_id": ObjectId("564dc6463e726cf185f880a0"),
  "name": "Charizard",
  "description": "Dragão fodelão motherfucker que AshNoob abandona",
  "type": "fogo/voador",
  "attack": 84,
  "defense": 78,
  "height": 1.7,
  "moves": [
    "Investida",
    "Desvio",
    "Lança Chamas"
  ],
  "active": false
}
{
  "_id": ObjectId("564dc6463e726cf185f880a1"),
  "name": "ButterFree",
  "description": "Última evolução do Caterpie, nesse estágio se torna uma borboleta (Ash também abandona)",
  "type": "inseto/voador",
  "attack": 45,
  "defense": 50,
  "height": 1.1,
  "active": false,
  "moves": [
    "Investida",
    "Desvio"
  ]
}
{
  "_id": ObjectId("5648ce1eb2b455d5cd60fd7e"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "Investida",
    "Ataque Rápido",
    "Investida Rápida",
    "Desvio",
    "Hidro Bomba"
  ]
}
{
  "_id": ObjectId("5648ce1eb2b455d5cd60fd7c"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "Investida",
    "Folha Navalha",
    "Ataque Rápido",
    "Investida Rápida",
    "Desvio"
  ]
}
{
  "_id": ObjectId("5648ce1eb2b455d5cd60fd7d"),
  "name": "Charmander",
  "description": "Queima a rosca 4ever",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "Investida",
    "Ataque Rápido",
    "Investida Rápida",
    "Desvio",
    "Lança Chamas"
  ]
}
{
  "_id": ObjectId("564dc38c3e726cf185f8809d"),
  "name": "Pikachu",
  "description": "Rato elétrico",
  "type": "elétrico",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "Investida",
    "Choque do Trovão",
    "Ataque Rápido",
    "Investida Rápida",
    "Desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("564dc6463e726cf185f880a2"),
  "name": "Pidgeot",
  "description": "Pássaro muito grande, um dos pokémons normais/voadores mais fortes",
  "type": "normal/voador",
  "attack": 80,
  "defense": 75,
  "height": 1.5,
  "active": false,
  "moves": [
    "Investida",
    "Desvio"
  ]
}
Fetched 8 record(s) in 3ms
```

**8 -** Remova **todos** os pokémons do tipo água e com attack menor que 50.

```
var pokes = {type: {$all: ["água"]}};
var condition = {attack: {$lt: 50}};
var query = {$and: [pokes, condition]};
db.pokemons.remove(query);
```

#### Saída

>```
Removed 1 record(s) in 2ms
WriteResult({
  "nRemoved": 1
})
```



