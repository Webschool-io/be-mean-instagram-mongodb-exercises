# MongoDB - Aula 04 - Exercício
autor: Jean Santos

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbasaur e Charmander.
```
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> var query = {$or: [{name: /Pikachu/i}, {name: /Squirtle/i}, {name: /Bulbasaur/i}, {name: /Charmander/i}]};
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll: {moves: ['investida', 'ataque rápido']}};
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> var options = {multi: true};
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options);
Updated 4 existing record(s) in 4ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> var query = {};
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> var mod = {$push: {moves: 'desvio'}};
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> var options = {multi: true};
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options);
Updated 610 existing record(s) in 17ms
WriteResult({
  "nMatched": 610,
  "nUpserted": 0,
  "nModified": 610
})
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i};
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> var mod = {
...   $set: {
...     "description": "Sem maiores informações"
...   },
...   $setOnInsert: {
...     "attack": null,
...     "defense": null,
...     "height": null,
...     "hp": null,
...     "name": "AindaNaoExisteMon",
...     "speed": null,
...     "types": null,
...     "moves": null,  
...   }
... };
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> var options = {upsert: true};
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options);
Updated 1 new record(s) in 18ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564e54c1ffef810218043c4f")
})
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$all: ['investida', 'desvio']}};
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query);
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
    "investida",
    "ataque rápido",
    "desvio"
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
    "investida",
    "ataque rápido",
    "desvio"
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
  "moves": [
    "investida",
    "ataque rápido",
    "desvio"
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
    "investida",
    "ataque rápido",
    "desvio"
  ]
}
Fetched 4 record(s) in 11ms
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$in: ['investida', 'ataque rápido', 'desvio']}};
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query);
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
    "investida",
    "ataque rápido",
    "desvio"
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
    "desvio"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d047b"),
  "attack": 64,
  "created": "2013-11-03T15:05:41.273462",
  "defense": 58,
  "height": "11",
  "hp": 58,
  "name": "Charmeleon",
  "speed": 80,
  "types": [
    "fire"
  ],
  "moves": [
    "desvio"
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
    "desvio"
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
    "desvio"
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
    "desvio"
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
    "desvio"
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
    "desvio"
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
    "desvio"
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
    "desvio"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d0484"),
  "attack": 35,
  "created": "2013-11-03T15:05:41.435237",
  "defense": 70,
  "height": "3",
  "hp": 25,
  "name": "Magnemite",
  "speed": 45,
  "types": [
    "steel",
    "electric"
  ],
  "moves": [
    "desvio"
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
    "desvio"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d0485"),
  "attack": 60,
  "created": "2013-11-03T15:05:41.437483",
  "defense": 95,
  "height": "10",
  "hp": 50,
  "name": "Magneton",
  "speed": 70,
  "types": [
    "steel",
    "electric"
  ],
  "moves": [
    "desvio"
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
    "desvio"
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
    "desvio"
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
    "desvio"
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
    "desvio"
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
    "desvio"
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
    "desvio"
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
    "desvio"
  ]
}
Fetched 20 record(s) in 10ms -- More[true]
```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> var query = {types: {$ne: 'electric'}};
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> db.pokemons.remove(query);
Removed 571 record(s) in 26ms
WriteResult({
  "nRemoved": 571
})
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{attack: {$in: ['investida']}}, {defense: {$not: {$lte: 49}}}]}
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 7ms
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{types: 'water'}, {attack: {$lt: 50}}]}
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> db.pokemons.remove(query);
Removed 1 record(s) in 3ms
WriteResult({
  "nRemoved": 1
})
```
