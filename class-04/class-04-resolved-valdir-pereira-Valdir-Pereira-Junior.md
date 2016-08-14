# MongoDB - Aula 04 - Exercício
autor: Valdir Pereira Júnior

#1. **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
var poke = ["Pikachu", "Squirtle", "Bulbassauro", "Charmander"]

var query = {"name": {"$in": poke } }

var attacks = ['soco', 'chute']

var mod = {$pushAll: {moves: attacks} }

var options = {multi: true}

db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 5ms
WriteResult({
    "nMatched": 4,
    "nUpserted": 0,
    "nModified": 4
})
Valdir(c:\mongodb\bin\mongod.exe-3.2.8) be-mean-pokemons> db.pokemons.find(query)
{
    "_id": ObjectId("579a3e6cc649704e7ea6da1a"),
    "name": "Pikachu",
    "description": "Rato elétrico bem fofinho",
    "type": "electric",
    "attack": 55,
    "height": 0.4,
    "moves": [
        "soco",
        "chute"
    ]
}
{
    "_id": ObjectId("579a3e8ec649704e7ea6da1b"),
    "name": "Bulbassauro",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 49,
    "height": 0.4,
    "moves": [
        "soco",
        "chute"
    ]
}
{
    "_id": ObjectId("579a3e9fc649704e7ea6da1c"),
    "name": "Charmander",
    "description": "Esse é o cão chupando manga de fofinho",
    "type": "fogo",
    "attack": 52,
    "height": 0.6,
    "moves": [
        "soco",
        "chute"
    ]
}
{
    "_id": ObjectId("579a3ebcc649704e7ea6da1d"),
    "name": "Squirtle",
    "description": "Ejeta água que passarinho não bebe",
    "type": "água",
    "attack": 48,
    "height": 0.5,
    "moves": [
        "soco",
        "chute"
    ]
}

```

# 2. **Adicionar** 1 movimento em todos os pokemons: `desvio`.
```
var query = {}
var options = {multi: true}
var mod = {$push: {moves: 'desvio'} }
db.pokemons.update(query, mod, options)

Updated 9 existing record(s) in 10ms
WriteResult({
    "nMatched": 9,
    "nUpserted": 0,
    "nModified": 9
})

Valdir(c:\mongodb\bin\mongod.exe-3.2.8) be-mean-pokemons> db.pokemons.find(query)
{
    "_id": ObjectId("57967ba5fe47bfe10c515abf"),
    "name": "Butterfree",
    "description": "Borboleta Fofinha",
    "type": "voador",
    "attack": 20,
    "height": 30,
    "moves": [
        "desvio"
    ]
}
{
    "_id": ObjectId("57967c05fe47bfe10c515ac0"),
    "name": "Metapode",
    "description": "Folha viva",
    "type": "bug",
    "attack": 10,
    "height": 0.7,
    "moves": [
        "desvio"
    ]
}
{
    "_id": ObjectId("57967c66fe47bfe10c515ac1"),
    "name": "Abra",
    "description": "Gato psicólogo",
    "type": "phychic",
    "attack": 10,
    "height": 0.9,
    "moves": [
        "desvio"
    ]
}
{
    "_id": ObjectId("5797a162bfffaaec99114615"),
    "description": "Pokemon de teste",
    "name": "Testemon",
    "attack": 8000,
    "defense": 8000,
    "moves": [
        "choque do Trovão",
        "desvio"
    ]
}
{
    "_id": ObjectId("579a3e6cc649704e7ea6da1a"),
    "name": "Pikachu",
    "description": "Rato elétrico bem fofinho",
    "type": "electric",
    "attack": 55,
    "height": 0.4,
    "moves": [
        "soco",
        "chute",
        "desvio"
    ]
}
{
    "_id": ObjectId("579a3e8ec649704e7ea6da1b"),
    "name": "Bulbassauro",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 49,
    "height": 0.4,
    "moves": [
        "soco",
        "chute",
        "desvio"
    ]
}
{
    "_id": ObjectId("579a3e9fc649704e7ea6da1c"),
    "name": "Charmander",
    "description": "Esse é o cão chupando manga de fofinho",
    "type": "fogo",
    "attack": 52,
    "height": 0.6,
    "moves": [
        "soco",
        "chute",
        "desvio"
    ]
}
{
    "_id": ObjectId("579a3ebcc649704e7ea6da1d"),
    "name": "Squirtle",
    "description": "Ejeta água que passarinho não bebe",
    "type": "água",
    "attack": 48,
    "height": 0.5,
    "moves": [
        "soco",
        "chute",
        "desvio"
    ]
}
{
    "_id": ObjectId("579a40dcc649704e7ea6da1e"),
    "name": "Moltres",
    "description": "Bird on Fire",
    "type": "fire",
    "attack": 50,
    "height": 2,
    "moves": [
        "desvio"
    ]
}
```


# 3. **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações
```
var query = {name: /AindaNaoExisteMon/i}
var mod = {
	$set: {
		name: 'AindaNaoExisteMon'
	},
	$setOnInsert: {
		"description": null,
		"type": null,
		"attack": null,
		"height": null,
	}
}
var options = {upsert: true}

db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 7ms
WriteResult({
    "nMatched": 0,
    "nUpserted": 1,
    "nModified": 0,
    "_id": ObjectId("579a440c1f0cbf10a45d5f34")
})
Valdir(c:\mongodb\bin\mongod.exe-3.2.8) be-mean-pokemons> db.pokemons.find(query)
{
    "_id": ObjectId("579a440c1f0cbf10a45d5f34"),
    "name": "AindaNaoExisteMon",
    "description": null,
    "type": null,
    "attack": null,
    "height": null
}
```

# 4. Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.
```
var query = {moves: {$in: ['investida', 'Fogo Flamejante']}}

Valdir(c:\mongodb\bin\mongod.exe-3.2.8) be-mean-pokemons> db.pokemons.find(query)
{
    "_id": ObjectId("579a40dcc649704e7ea6da1e"),
    "name": "Moltres",
    "description": "Bird on Fire",
    "type": "fire",
    "attack": 50,
    "height": 2,
    "moves": [
        "desvio",
        "Fogo Flamejante"
    ]
}
{
    "_id": ObjectId("579a3ebcc649704e7ea6da1d"),
    "name": "Squirtle",
    "description": "Ejeta água que passarinho não bebe",
    "type": "água",
    "attack": 48,
    "height": 0.5,
    "moves": [
        "soco",
        "chute",
        "desvio",
        "hidro bomba",
        "investida"
    ]
}

```

# 5. Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.
```
var query = {moves: {$in: ['Fogo Flamejante', 'cabeçada']}}

db.pokemons.find(query)
{
    "_id": ObjectId("57967c05fe47bfe10c515ac0"),
    "name": "Metapode",
    "description": "Folha viva",
    "type": "bug",
    "attack": 10,
    "height": 0.7,
    "moves": [
        "desvio",
        "cabeçada"
    ]
}
{
    "_id": ObjectId("579a40dcc649704e7ea6da1e"),
    "name": "Moltres",
    "description": "Bird on Fire",
    "type": "fire",
    "attack": 50,
    "height": 2,
    "moves": [
        "desvio",
        "Fogo Flamejante"
    ]
}
```

# 6. Pesquisar **todos** os pokemons que não são do tipo `elétrico`.
```
var query = {type: {$not: /electric/i}}
Valdir(c:\mongodb\bin\mongod.exe-3.2.8) be-mean-pokemons> db.pokemons.find(query)
{
    "_id": ObjectId("57967ba5fe47bfe10c515abf"),
    "name": "Butterfree",
    "description": "Borboleta Fofinha",
    "type": "voador",
    "attack": 20,
    "height": 30,
    "moves": [
        "desvio"
    ]
}
{
    "_id": ObjectId("57967c05fe47bfe10c515ac0"),
    "name": "Metapode",
    "description": "Folha viva",
    "type": "bug",
    "attack": 10,
    "height": 0.7,
    "moves": [
        "desvio",
        "cabeçada"
    ]
}
{
    "_id": ObjectId("57967c66fe47bfe10c515ac1"),
    "name": "Abra",
    "description": "Gato psicólogo",
    "type": "phychic",
    "attack": 10,
    "height": 0.9,
    "moves": [
        "desvio"
    ]
}
{
    "_id": ObjectId("5797a162bfffaaec99114615"),
    "description": "Pokemon de teste",
    "name": "Testemon",
    "attack": 8000,
    "defense": 8000,
    "moves": [
        "choque do Trovão",
        "desvio"
    ]
}
{
    "_id": ObjectId("579a3e8ec649704e7ea6da1b"),
    "name": "Bulbassauro",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 49,
    "height": 0.4,
    "moves": [
        "soco",
        "chute",
        "desvio",
        "folha navalha"
    ]
}
{
    "_id": ObjectId("579a3e9fc649704e7ea6da1c"),
    "name": "Charmander",
    "description": "Esse é o cão chupando manga de fofinho",
    "type": "fogo",
    "attack": 52,
    "height": 0.6,
    "moves": [
        "soco",
        "chute",
        "desvio",
        "lança-chamas"
    ]
}
{
    "_id": ObjectId("579a40dcc649704e7ea6da1e"),
    "name": "Moltres",
    "description": "Bird on Fire",
    "type": "fire",
    "attack": 50,
    "height": 2,
    "moves": [
        "desvio",
        "Fogo Flamejante"
    ]
}
{
    "_id": ObjectId("579a440c1f0cbf10a45d5f34"),
    "name": "AindaNaoExisteMon",
    "description": null,
    "type": null,
    "attack": null,
    "height": null
}
{
    "_id": ObjectId("579a3ebcc649704e7ea6da1d"),
    "name": "Squirtle",
    "description": "Ejeta água que passarinho não bebe",
    "type": "água",
    "attack": 48,
    "height": 0.5,
    "moves": [
        "soco",
        "chute",
        "desvio",
        "hidro bomba",
        "investida"
    ]
}
```

# 7. Pesquisar **todos** pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.
```
var action = {moves: {$in: ['investida']}}

var defense = {attack: {$lte: 49} }

var query  = {$and: [action, defense]}

db.pokemons.find(query)
{
    "_id": ObjectId("579a3ebcc649704e7ea6da1d"),
    "name": "Squirtle",
    "description": "Ejeta água que passarinho não bebe",
    "type": "água",
    "attack": 48,
    "height": 0.5,
    "moves": [
        "soco",
        "chute",
        "desvio",
        "hidro bomba",
        "investida"
    ]
}
```

# 8. Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
var type = {type:'água'}

var query = {$and: [attack, type] }

Valdir(c:\mongodb\bin\mongod.exe-3.2.8) be-mean-pokemons> query
{
    "$and": [
        {
            "attack": {
                "$lt": 50
            }
        },
        {
            "type": "água"
        }
    ]
}

Valdir(c:\mongodb\bin\mongod.exe-3.2.8) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 6ms
WriteResult({
    "nRemoved": 1
})

 var query = {type: 'água'}
Valdir(c:\mongodb\bin\mongod.exe-3.2.8) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```
