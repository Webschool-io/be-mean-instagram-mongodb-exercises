# MongoDB - Aula 04 - Exercício
autor: Welder Marcos

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```js
Welder-Mint(mongod-3.2.0) be-mean> d
be-mean.pokemons
Welder-Mint(mongod-3.2.0) be-mean> qry
{
  "name": {
    "$in": [
      /pikachu/i,
      /squirtle/i,
      /bulbasaur/i,
      /charmander/i 
    ]
  }
}
Welder-Mint(mongod-3.2.0) be-mean> atk
[
  "Ataque Rápido",
  "Investida"
]
Welder-Mint(mongod-3.2.0) be-mean> d.update(qry, {$push: {ataques: atk}}, {multi: "True"})
Updated 4 existing record(s) in 6ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
Welder-Mint(mongod-3.2.0) be-mean> d.find(qry)
{
  "_id": ObjectId("564b1dad25337263280d047a"),
  "attack": 52,
  "created": "2013-11-03T15:05:41.271082",
  "defense": 43,
  "height": "6",
  "hp": 39,
  "name": "Charmander",
  "speed": 65,
  "types": [
    "fire"
  ],
  "ataques": [
    [
      "Ataque Rápido",
      "Investida"
    ]
  ]
}
{
  "_id": ObjectId("564b1db125337263280d04a7"),
  "attack": 55,
  "created": "2013-11-03T15:05:41.317235",
  "defense": 40,
  "height": "4",
  "hp": 35,
  "name": "Pikachu",
  "speed": 90,
  "types": [
    "electric"
  ],
  "ataques": [
    [
      "Ataque Rápido",
      "Investida"
    ]
  ]
}
{
  "_id": ObjectId("564b1db425337263280d04b6"),
  "attack": 48,
  "created": "2013-11-03T15:05:41.278310",
  "defense": 65,
  "height": "5",
  "hp": 44,
  "name": "Squirtle",
  "speed": 43,
  "types": [
    "water"
  ],
  "ataques": [
    [
      "Ataque Rápido",
      "Investida"
    ]
  ]
}
{
  "_id": ObjectId("564b1de325337263280d068c"),
  "attack": 49,
  "created": "2013-11-03T15:05:41.260678",
  "defense": 49,
  "height": "7",
  "hp": 45,
  "name": "Bulbasaur",
  "speed": 45,
  "types": [
    "poison",
    "grass"
  ],
  "ataques": [
    [
      "Ataque Rápido",
      "Investida"
    ]
  ]
}
Fetched 4 record(s) in 7ms

```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.

```js
Welder-Mint(mongod-3.2.0) be-mean> d
be-mean.pokemons
Welder-Mint(mongod-3.2.0) be-mean> des
{
  "moves": [
    "Desvio"
  ]
}
Welder-Mint(mongod-3.2.0) be-mean> d.update({}, {$set: des}, {multi: "True"})
Updated 610 existing record(s) in 7ms
WriteResult({
  "nMatched": 610,
  "nUpserted": 0,
  "nModified": 610
})
Welder-Mint(mongod-3.2.0) be-mean> d.findOne()
{
  "_id": ObjectId("564b1dad25337263280d047a"),
  "attack": 52,
  "created": "2013-11-03T15:05:41.271082",
  "defense": 43,
  "height": "6",
  "hp": 39,
  "name": "Charmander",
  "speed": 65,
  "types": [
    "fire"
  ],
  "ataques": [
    [
      "Ataque Rápido",
      "Investida"
    ]
  ],
  "moves": [
    "Desvio"
  ]
}

```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".

```js
Welder-Mint(mongod-3.2.0) be-mean> d
be-mean.pokemons
Welder-Mint(mongod-3.2.0) be-mean> qry
{
  "name": /AindaNaoExistemon/i
}
Welder-Mint(mongod-3.2.0) be-mean> poke
{
  "attack": null,
  "created": null,
  "defense": null,
  "height": null,
  "hp": null,
  "name": "AindaNaoExistemon",
  "speed": null,
  "description": "Sem maiores informações"
}
Welder-Mint(mongod-3.2.0) be-mean> d.update(qry, {$setOnInsert: poke}, {upsert: "true"})
Updated 1 new record(s) in 3ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("568ae8bdd02b46663fd9d90e")
})
Welder-Mint(mongod-3.2.0) be-mean> d.find({"_id": ObjectId("568ae8bdd02b46663fd9d90e")})
{
  "_id": ObjectId("568ae8bdd02b46663fd9d90e"),
  "attack": null,
  "created": null,
  "defense": null,
  "height": null,
  "hp": null,
  "name": "AindaNaoExistemon",
  "speed": null,
  "description": "Sem maiores informações"
}
Fetched 1 record(s) in 0ms
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.

```js
Welder-Mint(mongod-3.2.0) be-mean> d
be-mean.pokemons
Welder-Mint(mongod-3.2.0) be-mean> qry
{
  "ataques": {
    "$in": [
      /investida/i,
      /hidro bomba/i
    ]
  }
}
Welder-Mint(mongod-3.2.0) be-mean> d.find(qry)
{
  "_id": ObjectId("564b1dad25337263280d047a"),
  "attack": 52,
  "created": "2013-11-03T15:05:41.271082",
  "defense": 43,
  "height": "6",
  "hp": 39,
  "name": "Charmander",
  "speed": 65,
  "types": [
    "fire"
  ],
  "moves": [
    "Desvio"
  ],
  "ataques": [
    "Investida",
    "Ataque Rápido"
  ]
}
{
  "_id": ObjectId("564b1db125337263280d04a7"),
  "attack": 55,
  "created": "2013-11-03T15:05:41.317235",
  "defense": 40,
  "height": "4",
  "hp": 35,
  "name": "Pikachu",
  "speed": 90,
  "types": [
    "electric"
  ],
  "moves": [
    "Desvio"
  ],
  "ataques": [
    "Investida",
    "Ataque Rápido"
  ]
}
{
  "_id": ObjectId("564b1de325337263280d068c"),
  "attack": 49,
  "created": "2013-11-03T15:05:41.260678",
  "defense": 49,
  "height": "7",
  "hp": 45,
  "name": "Bulbasaur",
  "speed": 45,
  "types": [
    "poison",
    "grass"
  ],
  "moves": [
    "Desvio"
  ],
  "ataques": [
    "Investida",
    "Ataque Rápido"
  ]
}
{
  "_id": ObjectId("568af80bae62279d27338547"),
  "attack": 48,
  "created": "2013-11-03T15:05:41.278310",
  "defense": 65,
  "height": "5",
  "hp": 44,
  "name": "Squirtle",
  "speed": 43,
  "types": [
    "water"
  ],
  "moves": [
    "Desvio"
  ],
  "ataques": [
    "Investida",
    "Ataque Rápido",
    "Hidro Bomba"
  ]
}
Fetched 4 record(s) in 5m
```

## Pesquisar **todos** os pokemons que possuam todos ataques que você adicionou, escolha seu pokemon favorito.

```js
Welder-Mint(mongod-3.2.0) be-mean> d
be-mean.pokemons
Welder-Mint(mongod-3.2.0) be-mean> qry
{
  "ataques": {
    "$all": [
      /investida/i,
      /hidro bomba/i,
      /ataque rápido/i
    ]
  }
}
Welder-Mint(mongod-3.2.0) be-mean> d.find(qry)
{
  "_id": ObjectId("568af80bae62279d27338547"),
  "attack": 48,
  "created": "2013-11-03T15:05:41.278310",
  "defense": 65,
  "height": "5",
  "hp": 44,
  "name": "Squirtle",
  "speed": 43,
  "types": [
    "water"
  ],
  "moves": [
    "Desvio"
  ],
  "ataques": [
    "Investida",
    "Ataque Rápido",
    "Hidro Bomba"
  ]
}
Fetched 1 record(s) in 2ms

```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.

```js
Welder-Mint(mongod-3.2.0) be-mean> d
be-mean.pokemons
Welder-Mint(mongod-3.2.0) be-mean> qry
{
  "types": {
    "$nin": [
      /electric/i
    ]
  }
}
Welder-Mint(mongod-3.2.0) be-mean> d.find(qry)
{
  "_id": ObjectId("564b1dad25337263280d047a"),
  "attack": 52,
  "created": "2013-11-03T15:05:41.271082",
  "defense": 43,
  "height": "6",
  "hp": 39,
  "name": "Charmander",
  "speed": 65,
  "types": [
    "fire"
  ],
  "moves": [
    "Desvio"
  ],
  "ataques": [
    "Investida",
    "Ataque Rápido"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d047d"),
  "attack": 83,
  "created": "2013-11-03T15:05:41.282985",
  "defense": 100,
  "height": "16",
  "hp": 79,
  "name": "Blastoise",
  "speed": 78,
  "types": [
    "water"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d047e"),
  "attack": 30,
  "created": "2013-11-03T15:05:41.285736",
  "defense": 35,
  "height": "3",
  "hp": 45,
  "name": "Caterpie",
  "speed": 45,
  "types": [
    "bug"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d047f"),
  "attack": 20,
  "created": "2013-11-03T15:05:41.288107",
  "defense": 55,
  "height": "7",
  "hp": 50,
  "name": "Metapod",
  "speed": 30,
  "types": [
    "bug"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d0480"),
  "attack": 45,
  "created": "2013-11-03T15:05:41.290411",
  "defense": 50,
  "height": "11",
  "hp": 60,
  "name": "Butterfree",
  "speed": 70,
  "types": [
    "flying",
    "bug"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d047c"),
  "attack": 63,
  "created": "2013-11-03T15:05:41.280718",
  "defense": 80,
  "height": "10",
  "hp": 59,
  "name": "Wartortle",
  "speed": 58,
  "types": [
    "water"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d0481"),
  "attack": 60,
  "created": "2013-11-03T15:05:41.310402",
  "defense": 30,
  "height": "3",
  "hp": 40,
  "name": "Spearow",
  "speed": 70,
  "types": [
    "normal",
    "flying"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d0479"),
  "attack": 56,
  "created": "2013-11-03T15:05:41.305777",
  "defense": 35,
  "height": "3",
  "hp": 30,
  "name": "Rattata",
  "speed": 72,
  "types": [
    "normal"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d0482"),
  "attack": 25,
  "created": "2013-11-03T15:05:41.294947",
  "defense": 50,
  "height": "6",
  "hp": 45,
  "name": "Kakuna",
  "speed": 35,
  "types": [
    "poison",
    "bug"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d0483"),
  "attack": 65,
  "created": "2013-11-03T15:05:41.439497",
  "defense": 55,
  "height": "8",
  "hp": 52,
  "name": "Farfetchd",
  "speed": 60,
  "types": [
    "normal",
    "flying"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d0486"),
  "attack": 85,
  "created": "2013-11-03T15:05:41.441502",
  "defense": 45,
  "height": "14",
  "hp": 35,
  "name": "Doduo",
  "speed": 75,
  "types": [
    "normal",
    "flying"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d0487"),
  "attack": 45,
  "created": "2013-11-03T15:05:41.445749",
  "defense": 55,
  "height": "11",
  "hp": 65,
  "name": "Seel",
  "speed": 45,
  "types": [
    "water"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d0488"),
  "attack": 110,
  "created": "2013-11-03T15:05:41.443720",
  "defense": 70,
  "height": "18",
  "hp": 60,
  "name": "Dodrio",
  "speed": 100,
  "types": [
    "normal",
    "flying"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d0489"),
  "attack": 70,
  "created": "2013-11-03T15:05:41.447897",
  "defense": 80,
  "height": "17",
  "hp": 90,
  "name": "Dewgong",
  "speed": 70,
  "types": [
    "water",
    "ice"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d048a"),
  "attack": 35,
  "created": "2013-11-03T15:05:41.457865",
  "defense": 30,
  "height": "13",
  "hp": 30,
  "name": "Gastly",
  "speed": 80,
  "types": [
    "poison",
    "ghost"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d048b"),
  "attack": 95,
  "created": "2013-11-03T15:05:41.456387",
  "defense": 180,
  "height": "15",
  "hp": 50,
  "name": "Cloyster",
  "speed": 70,
  "types": [
    "water",
    "ice"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d048c"),
  "attack": 105,
  "created": "2013-11-03T15:05:41.452237",
  "defense": 75,
  "height": "12",
  "hp": 105,
  "name": "Muk",
  "speed": 50,
  "types": [
    "poison"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1daf25337263280d048d"),
  "attack": 50,
  "created": "2013-11-03T15:05:41.388462",
  "defense": 40,
  "height": "6",
  "hp": 40,
  "name": "Poliwag",
  "speed": 90,
  "types": [
    "water"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1daf25337263280d048e"),
  "attack": 65,
  "created": "2013-11-03T15:05:41.390744",
  "defense": 65,
  "height": "10",
  "hp": 65,
  "name": "Poliwhirl",
  "speed": 90,
  "types": [
    "water"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1daf25337263280d048f"),
  "attack": 95,
  "created": "2013-11-03T15:05:41.393388",
  "defense": 95,
  "height": "13",
  "hp": 90,
  "name": "Poliwrath",
  "speed": 70,
  "types": [
    "fighting",
    "water"
  ],
  "moves": [
    "Desvio"
  ]
}
Fetched 20 record(s) in 21ms -- More[true]

```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.

```js
Welder-Mint(mongod-3.2.0) be-mean> d
be-mean.pokemons
Welder-Mint(mongod-3.2.0) be-mean> def
{
  "$and": [
    {
      "defense": {
        "$gt": 49
      }
    },
    {
      "ataques": {
        "$in": [
          /investida/i
        ]
      }
    }
  ]
}
Welder-Mint(mongod-3.2.0) be-mean> d.find(def)
{
  "_id": ObjectId("568af80bae62279d27338547"),
  "attack": 48,
  "created": "2013-11-03T15:05:41.278310",
  "defense": 65,
  "height": "5",
  "hp": 44,
  "name": "Squirtle",
  "speed": 43,
  "types": [
    "water"
  ],
  "moves": [
    "Desvio"
  ],
  "ataques": [
    "Investida",
    "Ataque Rápido",
    "Hidro Bomba"
  ]
}
Fetched 1 record(s) in 5ms

```

## Remova **todos** os pokemons do tipo água E com attack menor que 50.

```js
Welder-Mint(mongod-3.2.0) be-mean> d
be-mean.pokemons
Welder-Mint(mongod-3.2.0) be-mean> var atk = {$and: [{attack: {$lt: 50}},{types: {$in: [/water/i]}}]}
Welder-Mint(mongod-3.2.0) be-mean> d.find(atk)
{
  "_id": ObjectId("564b1dae25337263280d0487"),
  "attack": 45,
  "created": "2013-11-03T15:05:41.445749",
  "defense": 55,
  "height": "11",
  "hp": 65,
  "name": "Seel",
  "speed": 45,
  "types": [
    "water"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1db625337263280d04ca"),
  "attack": 40,
  "created": "2013-11-03T15:05:41.496373",
  "defense": 70,
  "height": "4",
  "hp": 30,
  "name": "Horsea",
  "speed": 60,
  "types": [
    "water"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1db625337263280d04ce"),
  "attack": 45,
  "created": "2013-11-03T15:05:41.503513",
  "defense": 55,
  "height": "8",
  "hp": 30,
  "name": "Staryu",
  "speed": 85,
  "types": [
    "water"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1db825337263280d04df"),
  "attack": 40,
  "created": "2013-11-03T15:05:41.676497",
  "defense": 70,
  "height": "21",
  "hp": 65,
  "name": "Mantine",
  "speed": 70,
  "types": [
    "flying",
    "water"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1db925337263280d04ea"),
  "attack": 45,
  "created": "2013-11-03T15:05:41.627694",
  "defense": 45,
  "height": "4",
  "hp": 55,
  "name": "Wooper",
  "speed": 15,
  "types": [
    "ground",
    "water"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1dbe25337263280d051b"),
  "attack": 20,
  "created": "2013-11-03T15:05:41.611027",
  "defense": 50,
  "height": "4",
  "hp": 70,
  "name": "Marill",
  "speed": 40,
  "types": [
    "water",
    "fairy"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1dbf25337263280d0527"),
  "attack": 30,
  "created": "2013-11-03T15:05:41.947867",
  "defense": 55,
  "height": "6",
  "hp": 43,
  "name": "Luvdisc",
  "speed": 97,
  "types": [
    "water"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1dc225337263280d0543"),
  "attack": 30,
  "created": "2013-11-03T15:05:41.759350",
  "defense": 30,
  "height": "5",
  "hp": 40,
  "name": "Lotad",
  "speed": 30,
  "types": [
    "water",
    "grass"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1dc525337263280d0561"),
  "attack": 40,
  "created": "2013-11-03T15:05:41.534717",
  "defense": 100,
  "height": "4",
  "hp": 35,
  "name": "Omanyte",
  "speed": 35,
  "types": [
    "rock",
    "water"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1dc525337263280d0563"),
  "attack": 40,
  "created": "2013-11-03T15:05:41.415512",
  "defense": 35,
  "height": "9",
  "hp": 40,
  "name": "Tentacool",
  "speed": 70,
  "types": [
    "poison",
    "water"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1dc825337263280d0574"),
  "attack": 38,
  "created": "2013-11-03T15:05:41.589626",
  "defense": 38,
  "height": "5",
  "hp": 75,
  "name": "Chinchou",
  "speed": 67,
  "types": [
    "water",
    "electric"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1dcb25337263280d0593"),
  "attack": 49,
  "created": "2013-11-03T15:05:42.085455",
  "defense": 56,
  "height": "4",
  "hp": 49,
  "name": "Finneon",
  "speed": 66,
  "types": [
    "water"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1dcb25337263280d0594"),
  "attack": 20,
  "created": "2013-11-03T15:05:42.088388",
  "defense": 50,
  "height": "10",
  "hp": 45,
  "name": "Mantyke",
  "speed": 50,
  "types": [
    "flying",
    "water"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1dce25337263280d05b1"),
  "attack": 30,
  "created": "2013-11-03T15:05:41.779585",
  "defense": 32,
  "height": "5",
  "hp": 40,
  "name": "Surskit",
  "speed": 65,
  "types": [
    "bug",
    "water"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1dd925337263280d05f1"),
  "attack": 48,
  "created": "2013-11-03T15:05:41.897229",
  "defense": 43,
  "height": "4",
  "hp": 50,
  "name": "Barboach",
  "speed": 60,
  "types": [
    "ground",
    "water"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1dda25337263280d0602"),
  "attack": 30,
  "created": "2013-11-03T15:05:41.771944",
  "defense": 30,
  "height": "6",
  "hp": 40,
  "name": "Wingull",
  "speed": 85,
  "types": [
    "flying",
    "water"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1dda25337263280d060d"),
  "attack": 15,
  "created": "2013-11-03T15:05:41.913978",
  "defense": 20,
  "height": "6",
  "hp": 20,
  "name": "Feebas",
  "speed": 80,
  "types": [
    "water"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1dda25337263280d0619"),
  "attack": 40,
  "created": "2013-11-03T15:05:41.936228",
  "defense": 50,
  "height": "8",
  "hp": 70,
  "name": "Spheal",
  "speed": 25,
  "types": [
    "water",
    "ice"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1de325337263280d0694"),
  "attack": 48,
  "created": "2013-11-03T15:05:42.035373",
  "defense": 48,
  "height": "3",
  "hp": 76,
  "name": "Shellos",
  "speed": 34,
  "types": [
    "water"
  ],
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("564b1de625337263280d06c1"),
  "attack": 40,
  "created": "2013-11-03T15:05:42.297039",
  "defense": 50,
  "height": "12",
  "hp": 55,
  "name": "Frillish",
  "speed": 40,
  "types": [
    "ghost",
    "water"
  ],
  "moves": [
    "Desvio"
  ]
}
Fetched 20 record(s) in 17ms -- More[true]
Welder-Mint(mongod-3.2.0) be-mean> d.remove(atk)
Removed 21 record(s) in 3ms
WriteResult({
  "nRemoved": 21
})

```

