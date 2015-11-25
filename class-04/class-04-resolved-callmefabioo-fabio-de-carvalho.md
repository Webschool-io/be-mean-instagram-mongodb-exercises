# MongoDB - Aula 04 - Exercício
# Autor: Fábio de Carvalho

## Step 1: Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
Admin-PC(C:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> var query = { $or: [{name: /Pikachu/i}, {name: /Squirtle/i}, {name: /Bulbassauro/i}, {name:/Charmander/i}] }
Admin-PC(C:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> var mod = {$set: { attacks: ['Investida', 'Cabeçada'] } }
Admin-PC(C:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> var options = {multi: true}
Admin-PC(C:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 2ms
WriteResult({
    "nMatched": 4,
    "nUpserted": 0,
    "nModified": 4
})
Admin-PC(C:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
    "_id": ObjectId("564e71027915960423727624"),
    "name": "Pikachu",
    "description": "Rato dos raios",
    "type": "Eletric",
    "attack": 55,
    "defense": 40,
    "height": 0.4,
    "attacks": [
        "Investida",
        "Cabeçada"
    ]
}
{
    "_id": ObjectId("564e712e7915960423727625"),
    "name": "Squirtle",
    "description": "Tartaruga de água",
    "type": "Water",
    "attack": 48,
    "defense": 65,
    "height": 0.5,
    "attacks": [
        "Investida",
        "Cabeçada"
    ]
}
{
    "_id": ObjectId("564e71597915960423727626"),
    "name": "Bulbassauro",
    "description": "Bixo do mato",
    "type": "Grass",
    "attack": 49,
    "defense": 49,
    "height": 0.7,
    "attacks": [
        "Investida",
        "Cabeçada"
    ]
}
{
    "_id": ObjectId("564e717b7915960423727627"),
    "name": "Charmander",
    "description": "Menino do fogo",
    "type": "Fire",
    "attack": 52,
    "defense": 43,
    "height": 0.6,
    "attacks": [
        "Investida",
        "Cabeçada"
    ]
}
Fetched 4 record(s) in 24ms
```

## Step 2: Adicionar 1 movimento em todos os pokemons: desvio.
```
Admin-PC(C:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> var query = {}
Admin-PC(C:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> var options = {multi: true}
Admin-PC(C:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> var mod = {$set: {moves: 'Desvio'}}
Admin-PC(C:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 9 existing record(s) in 1ms
WriteResult({
    "nMatched": 9,
    "nUpserted": 0,
    "nModified": 9
})
Admin-PC(C:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> db.pokemons.find()
{
    "_id": ObjectId("5642a225b313f9771f455cf0"),
    "name": "Blastoise",
    "description": "Tartaruga mal encarada com canhões de água",
    "type": "Water",
    "attack": 83,
    "height": 16,
    "moves": "Desvio"
}
{
    "_id": ObjectId("5642a231b313f9771f455cf1"),
    "name": "Vulpix",
    "description": "Um \"Kyuubi wannabe\" do caralho\"",
    "type": "Fire",
    "attack": 41,
    "height": 6,
    "moves": "Desvio"
}
{
    "_id": ObjectId("5642a23fb313f9771f455cf2"),
    "name": "Kadabra",
    "description": "Neo do mundo pokemon",
    "type": "Psychic",
    "attack": 35,
    "height": 13,
    "defense": 30,
    "moves": "Desvio"
}
{
    "_id": ObjectId("5642a249b313f9771f455cf3"),
    "name": "Hitmonlee",
    "description": "O da voadora com os dois pés na cara",
    "type": "Fighting",
    "attack": 120,
    "height": 15,
    "moves": "Desvio"
}
{
    "_id": ObjectId("5642a254b313f9771f455cf4"),
    "name": "Hitmonchan",
    "description": "Soquinho, soquinho, soquinho...",
    "type": "Fighting",
    "attack": 105,
    "height": 14,
    "moves": "Desvio"
}
{
    "_id": ObjectId("564e71027915960423727624"),
    "name": "Pikachu",
    "description": "Rato dos raios",
    "type": "Eletric",
    "attack": 55,
    "defense": 40,
    "height": 0.4,
    "moves": "Desvio",
    "attacks": [
        "Investida",
        "Cabeçada"
    ]
}
{
    "_id": ObjectId("564e712e7915960423727625"),
    "name": "Squirtle",
    "description": "Tartaruga de água",
    "type": "Water",
    "attack": 48,
    "defense": 65,
    "height": 0.5,
    "moves": "Desvio",
    "attacks": [
        "Investida",
        "Cabeçada"
    ]
}
{
    "_id": ObjectId("564e71597915960423727626"),
    "name": "Bulbassauro",
    "description": "Bixo do mato",
    "type": "Grass",
    "attack": 49,
    "defense": 49,
    "height": 0.7,
    "moves": "Desvio",
    "attacks": [
        "Investida",
        "Cabeçada"
    ]
}
{
    "_id": ObjectId("564e717b7915960423727627"),
    "name": "Charmander",
    "description": "Menino do fogo",
    "type": "Fire",
    "attack": 52,
    "defense": 43,
    "height": 0.6,
    "moves": "Desvio",
    "attacks": [
        "Investida",
        "Cabeçada"
    ]
}
Fetched 9 record(s) in 72ms
```

## Step 3: Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".
```
Admin-PC(C:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}
Admin-PC(C:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> var options = {upsert: true}
Admin-PC(C:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> var mod = { $push: {moves: 'Desvio'}, $setOnInsert: { name: 'AindaNaoExisteMom', description: 'Sem maiores informações', type: null, attack: null, defense: null }}
Admin-PC(C:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 4ms
WriteResult({
    "nMatched": 0,
    "nUpserted": 1,
    "nModified": 0,
    "_id": ObjectId("564e769c70297c046dba356e")
})
Admin-PC(C:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> db.pokemons.find()
{
    "_id": ObjectId("5642a225b313f9771f455cf0"),
    "name": "Blastoise",
    "description": "Tartaruga mal encarada com canhões de água",
    "type": "Water",
    "attack": 83,
    "height": 16,
    "moves": "Desvio"
}
{
    "_id": ObjectId("5642a231b313f9771f455cf1"),
    "name": "Vulpix",
    "description": "Um \"Kyuubi wannabe\" do caralho\"",
    "type": "Fire",
    "attack": 41,
    "height": 6,
    "moves": "Desvio"
}
{
    "_id": ObjectId("5642a23fb313f9771f455cf2"),
    "name": "Kadabra",
    "description": "Neo do mundo pokemon",
    "type": "Psychic",
    "attack": 35,
    "height": 13,
    "defense": 30,
    "moves": "Desvio"
}
{
    "_id": ObjectId("5642a249b313f9771f455cf3"),
    "name": "Hitmonlee",
    "description": "O da voadora com os dois pés na cara",
    "type": "Fighting",
    "attack": 120,
    "height": 15,
    "moves": "Desvio"
}
{
    "_id": ObjectId("5642a254b313f9771f455cf4"),
    "name": "Hitmonchan",
    "description": "Soquinho, soquinho, soquinho...",
    "type": "Fighting",
    "attack": 105,
    "height": 14,
    "moves": "Desvio"
}
{
    "_id": ObjectId("564e71027915960423727624"),
    "name": "Pikachu",
    "description": "Rato dos raios",
    "type": "Eletric",
    "attack": 55,
    "defense": 40,
    "height": 0.4,
    "moves": "Desvio",
    "attacks": [
        "Investida",
        "Cabeçada"
    ]
}
{
    "_id": ObjectId("564e712e7915960423727625"),
    "name": "Squirtle",
    "description": "Tartaruga de água",
    "type": "Water",
    "attack": 48,
    "defense": 65,
    "height": 0.5,
    "moves": "Desvio",
    "attacks": [
        "Investida",
        "Cabeçada"
    ]
}
{
    "_id": ObjectId("564e71597915960423727626"),
    "name": "Bulbassauro",
    "description": "Bixo do mato",
    "type": "Grass",
    "attack": 49,
    "defense": 49,
    "height": 0.7,
    "moves": "Desvio",
    "attacks": [
        "Investida",
        "Cabeçada"
    ]
}
{
    "_id": ObjectId("564e717b7915960423727627"),
    "name": "Charmander",
    "description": "Menino do fogo",
    "type": "Fire",
    "attack": 52,
    "defense": 43,
    "height": 0.6,
    "moves": "Desvio",
    "attacks": [
        "Investida",
        "Cabeçada"
    ]
}
{
    "_id": ObjectId("564e769c70297c046dba356e"),
    "moves": [
        "Desvio"
    ],
    "name": "AindaNaoExisteMom",
    "description": "Sem maiores informações",
    "type": null,
    "attack": null,
    "defense": null
}
Fetched 10 record(s) in 67ms
```

## Step 4: Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.
```
Admin-PC(C:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> var query = {attacks: {$all: ['Investida', 'Cabeçada']}}
Admin-PC(C:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
    "_id": ObjectId("564e71027915960423727624"),
    "name": "Pikachu",
    "description": "Rato dos raios",
    "type": "Eletric",
    "attack": 55,
    "defense": 40,
    "height": 0.4,
    "moves": "Desvio",
    "attacks": [
        "Investida",
        "Cabeçada"
    ]
}
{
    "_id": ObjectId("564e712e7915960423727625"),
    "name": "Squirtle",
    "description": "Tartaruga de água",
    "type": "Water",
    "attack": 48,
    "defense": 65,
    "height": 0.5,
    "moves": "Desvio",
    "attacks": [
        "Investida",
        "Cabeçada"
    ]
}
{
    "_id": ObjectId("564e71597915960423727626"),
    "name": "Bulbassauro",
    "description": "Bixo do mato",
    "type": "Grass",
    "attack": 49,
    "defense": 49,
    "height": 0.7,
    "moves": "Desvio",
    "attacks": [
        "Investida",
        "Cabeçada"
    ]
}
{
    "_id": ObjectId("564e717b7915960423727627"),
    "name": "Charmander",
    "description": "Menino do fogo",
    "type": "Fire",
    "attack": 52,
    "defense": 43,
    "height": 0.6,
    "moves": "Desvio",
    "attacks": [
        "Investida",
        "Cabeçada"
    ]
}
Fetched 4 record(s) in 36ms
```

## Step 5: Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```
Admin-PC(C:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> var query = {name: /Squirtle/i, attacks: {$all: ['Investida', 'Cabeçada']}}
Admin-PC(C:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
    "_id": ObjectId("564e712e7915960423727625"),
    "name": "Squirtle",
    "description": "Tartaruga de água",
    "type": "Water",
    "attack": 48,
    "defense": 65,
    "height": 0.5,
    "moves": "Desvio",
    "attacks": [
        "Investida",
        "Cabeçada"
    ]
}
Fetched 1 record(s) in 9ms
```

## Step 6: Pesquisar todos os pokemons que não são do tipo elétrico.

```
Admin-PC(C:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> var query = {type: {$ne: 'Eletric'}}
Admin-PC(C:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
    "_id": ObjectId("5642a225b313f9771f455cf0"),
    "name": "Blastoise",
    "description": "Tartaruga mal encarada com canhões de água",
    "type": "Water",
    "attack": 83,
    "height": 16,
    "moves": "Desvio"
}
{
    "_id": ObjectId("5642a231b313f9771f455cf1"),
    "name": "Vulpix",
    "description": "Um \"Kyuubi wannabe\" do caralho\"",
    "type": "Fire",
    "attack": 41,
    "height": 6,
    "moves": "Desvio"
}
{
    "_id": ObjectId("5642a23fb313f9771f455cf2"),
    "name": "Kadabra",
    "description": "Neo do mundo pokemon",
    "type": "Psychic",
    "attack": 35,
    "height": 13,
    "defense": 30,
    "moves": "Desvio"
}
{
    "_id": ObjectId("5642a249b313f9771f455cf3"),
    "name": "Hitmonlee",
    "description": "O da voadora com os dois pés na cara",
    "type": "Fighting",
    "attack": 120,
    "height": 15,
    "moves": "Desvio"
}
{
    "_id": ObjectId("5642a254b313f9771f455cf4"),
    "name": "Hitmonchan",
    "description": "Soquinho, soquinho, soquinho...",
    "type": "Fighting",
    "attack": 105,
    "height": 14,
    "moves": "Desvio"
}
{
    "_id": ObjectId("564e712e7915960423727625"),
    "name": "Squirtle",
    "description": "Tartaruga de água",
    "type": "Water",
    "attack": 48,
    "defense": 65,
    "height": 0.5,
    "moves": "Desvio",
    "attacks": [
        "Investida",
        "Cabeçada"
    ]
}
{
    "_id": ObjectId("564e71597915960423727626"),
    "name": "Bulbassauro",
    "description": "Bixo do mato",
    "type": "Grass",
    "attack": 49,
    "defense": 49,
    "height": 0.7,
    "moves": "Desvio",
    "attacks": [
        "Investida",
        "Cabeçada"
    ]
}
{
    "_id": ObjectId("564e717b7915960423727627"),
    "name": "Charmander",
    "description": "Menino do fogo",
    "type": "Fire",
    "attack": 52,
    "defense": 43,
    "height": 0.6,
    "moves": "Desvio",
    "attacks": [
        "Investida",
        "Cabeçada"
    ]
}
{
    "_id": ObjectId("564e769c70297c046dba356e"),
    "moves": [
        "Desvio"
    ],
    "name": "AindaNaoExisteMom",
    "description": "Sem maiores informações",
    "type": null,
    "attack": null,
    "defense": null
}
Fetched 9 record(s) in 64ms
```

## Step 7: Pesquisar todos pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 0.49.
```
Admin-PC(C:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> var query = { $and: [{attacks: { $in: ['Investida']}}, {defense: { $lte: 49}}]}
Admin-PC(C:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
    "_id": ObjectId("564e71027915960423727624"),
    "name": "Pikachu",
    "description": "Rato dos raios",
    "type": "Eletric",
    "attack": 55,
    "defense": 40,
    "height": 0.4,
    "moves": "Desvio",
    "attacks": [
        "Investida",
        "Cabeçada"
    ]
}
{
    "_id": ObjectId("564e71597915960423727626"),
    "name": "Bulbassauro",
    "description": "Bixo do mato",
    "type": "Grass",
    "attack": 49,
    "defense": 49,
    "height": 0.7,
    "moves": "Desvio",
    "attacks": [
        "Investida",
        "Cabeçada"
    ]
}
{
    "_id": ObjectId("564e717b7915960423727627"),
    "name": "Charmander",
    "description": "Menino do fogo",
    "type": "Fire",
    "attack": 52,
    "defense": 43,
    "height": 0.6,
    "moves": "Desvio",
    "attacks": [
        "Investida",
        "Cabeçada"
    ]
}
Fetched 3 record(s) in 22ms
```

## Step 8: Remova todos os pokemons do tipo água e com defense menor que 1.
```
Admin-PC(C:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> var query = { $and: [{type: /Water/i}, {defense: { $lt: 1}}]}
Admin-PC(C:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
Admin-PC(C:\mongodb\bin\mongod.exe-3.0.7) be-mean-pokemons>
```
