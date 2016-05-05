# MongoDB - Aula 04 - Exercício

Autor: Wendell Adriel Luiz Silva

## Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro, Charmander

```
be-mean> var query = { $or : [{ name : /pikachu/i }, { name : /squirtle/i }, { name : /bulbassauro/i }, { name : /charmander/i }, ] }
be-mean> var mod = { $set : { moves : ['shadow ball', 'solar beam'] } }
be-mean> var options = { multi : true }
be-mean> db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 121ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
```

## Adicionar 1 movimento em todos os pokemons: 'desvio'

```
be-mean> var query = {}
be-mean> var mod = { $set : { moves : 'desvio' } }
be-mean> var options = { multi : true }
be-mean> db.pokemons.update(query, mod, options)
Updated 610 existing record(s) in 15ms
WriteResult({
  "nMatched": 610,
  "nUpserted": 0,
  "nModified": 610
})
```

## Adicionar o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição `Sem maiores informações`

```
be-mean> var query = { name : /AindaNaoExisteMon/i }
be-mean> var mod = { $setOnInsert : { name : 'AindaNaoExisteMom', attack : null, height : null, defense : null, moves : [], description : 'Sem maiores informações' } }
be-mean> var options = { upsert : true }
be-mean> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 47ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("56b3e91f9cd1c5e1ccc6b1a7")
})
```

```
be-mean> var query = { _id : ObjectId('56b3e91f9cd1c5e1ccc6b1a7') }
be-mean> db.pokemons.find(query)
{
  "_id": ObjectId("56b3e91f9cd1c5e1ccc6b1a7"),
  "name": "AindaNaoExisteMom",
  "attack": null,
  "height": null,
  "defense": null,
  "moves": [ ],
  "description": "Sem maiores informações"
}
Fetched 1 record(s) in 35ms
```

## Pesquisar todos o pokemons que possuam o ataque 'investida' e mais um que você adicionou

```
be-mean> var query = { moves : { $in : [/investida/i, /shadow ball/i] } }
be-mean> db.pokemons.find(query)
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
    "investida",
    "ataque rapido"
  ]
}
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
    "shadow ball",
    "solar beam"
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
    "investida",
    "ataque rapido"
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
    "investida",
    "ataque rapido"
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
    "investida",
    "ataque rapido"
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
    "shadow ball",
    "solar beam"
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
    "shadow ball",
    "solar beam"
  ]
}
{
  "_id": ObjectId("564b1de625337263280d06bb"),
  "attack": 103,
  "created": "2013-11-03T15:05:42.542919",
  "defense": 120,
  "height": "0",
  "hp": 79,
  "name": "Blastoise-mega",
  "speed": 78,
  "types": [
    "water"
  ],
  "moves": [
    "investida",
    "ataque rapido"
  ]
}
Fetched 8 record(s) in 96ms
```

## Pesquisar 'todos' o pokemons que possuam os ataques que você adicionou
```
be-mean> var query = { moves : { $in : [/solar beam/i, /shadow ball/i] } }
be-mean> db.pokemons.find(query)
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
    "shadow ball",
    "solar beam"
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
    "shadow ball",
    "solar beam"
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
    "shadow ball",
    "solar beam"
  ]
}
{
  "_id": ObjectId("56b3ed2cac9217aeebf4168b"),
  "attack": 10,
  "defense": 50,
  "height": "5",
  "hp": 39,
  "name": "bulbassauro",
  "speed": 35,
  "types": [
    "grass"
  ],
  "moves": [
    "solar bem",
    "shadow ball"
  ]
}
Fetched 4 record(s) in 71ms
```

## Pesquisar todos os pokemons que não são do tipo `elétrico`

```
be-mean> var query = { type : { $ne : 'electric' } }
be-mean> db.pokemons.find(query)
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
  "moves": "desvio"
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
  "moves": "desvio"
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
    "investida",
    "ataque rapido"
  ]
}
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
    "shadow ball",
    "solar beam"
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
  "moves": "desvio"
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
    "investida",
    "ataque rapido"
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
    "investida",
    "ataque rapido"
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
  "moves": "desvio"
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
  "moves": "desvio"
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
    "investida",
    "ataque rapido"
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
  "moves": "desvio"
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
  "moves": "desvio"
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
  "moves": "desvio"
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
  "moves": "desvio"
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
  "moves": "desvio"
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
  "moves": "desvio"
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
  "moves": "desvio"
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
  "moves": "desvio"
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
  "moves": "desvio"
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
  "moves": "desvio"
}
Fetched 20 record(s) in 250ms -- More[true]
```

## Pesquisar todos pokemons que tenham o ataque `investida` E tenham a `defesa não menor ou igual` a `49`

```
be-mean> var query = { $and: [{ moves : { $in : ['investida'] } }, { defense : { $not: { $lte : 49 } } }] }
be-mean> db.pokemons.find(query)
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
    "investida",
    "ataque rapido"
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
    "investida",
    "ataque rapido"
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
    "investida",
    "ataque rapido"
  ]
}
{
  "_id": ObjectId("564b1de625337263280d06bb"),
  "attack": 103,
  "created": "2013-11-03T15:05:42.542919",
  "defense": 120,
  "height": "0",
  "hp": 79,
  "name": "Blastoise-mega",
  "speed": 78,
  "types": [
    "water"
  ],
  "moves": [
    "investida",
    "ataque rapido"
  ]
}
Fetched 4 record(s) in 45ms
```

## Remover todos os pokemons do tipo `água` E com `attack menor` que `50`

```
be-mean> var query = { $and : [{ types : 'water' }, { attack : { $lt : 50 } }] }
be-mean> db.pokemons.remove(query)
Removed 21 record(s) in 42ms
WriteResult({
  "nRemoved": 21
})
```

## Esse item não está no vídeo e se você fizer significa que você lê as coisas, nesse exercício demonstre qual a diferença entre os operadores `$ne` e `$not`

> $ne: Seleciona todos documentos onde o valor do atributo **não é igual** ao valor passado no comando, incluindo documentos que não contém o atributo.

> $not: Funciona como o operador lógico **NOT** na expressão passada no comando, selecionando todos os documentos que não enquadram na expressão passada, incluindo documentos que não contém o atributo.
