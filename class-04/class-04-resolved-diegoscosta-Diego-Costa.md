# MongoDB - Aula 04 - Exercício
autor: Diego Costa

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
DIEGO-LAPTOP(mongod-3.0.7) be-mean-pokemons> var query = { $or: [{ name: /Pikachu/i },  { name: /Squirtle/i }, { name: /Bulbasaur/i }, { name: /Charmander/i } ]}
DIEGO-LAPTOP(mongod-3.0.7) be-mean-pokemons> var mod = { $set: { 'moves' : ['Quick Attack', 'Tackle']  } }
DIEGO-LAPTOP(mongod-3.0.7) be-mean-pokemons> var options = { multi: true }

DIEGO-LAPTOP(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 77ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})

```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

```
DIEGO-LAPTOP(mongod-3.0.7) be-mean-pokemons> var query = {}
DIEGO-LAPTOP(mongod-3.0.7) be-mean-pokemons> var mod = { $push: { moves: "Desvio" } }
DIEGO-LAPTOP(mongod-3.0.7) be-mean-pokemons> var options = { multi: true }

DIEGO-LAPTOP(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 5 existing record(s) in 1ms
WriteResult({
  "nMatched": 5,
  "nUpserted": 0,
  "nModified": 5
})

```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

```
DIEGO-LAPTOP(mongod-3.0.7) be-mean-pokemons> var query = { name: /AindaNaoExisteMon/i }
DIEGO-LAPTOP(mongod-3.0.7) be-mean-pokemons> var mod = { $setOnInsert: { 
	name: 'AindaNaoExisteMon',
	description: 'Sem maiores informações',
    type: null,
    attack: null,
    height: null,
    defense: null,
    moves: []
} }

DIEGO-LAPTOP(mongod-3.0.7) be-mean-pokemons> var options = { upsert: true }

DIEGO-LAPTOP(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 83ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564bf2f6466a6dba40613be5")
})
DIEGO-LAPTOP(mongod-3.0.7) be-mean-pokemons>

```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
DIEGO-LAPTOP(mongod-3.0.7) be-mean-pokemons> var query = { moves : { $all: ['Quick Attack', 'Flamethrower'] } }
DIEGO-LAPTOP(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643ea5074d288f816215407"),
  "name": "Charmander",
  "description": "Charmander is a Fire-type Pokémon.",
  "attack": 52,
  "defense": 43,
  "height": 0.6,
  "moves": [
    "Quick Attack",
    "Tackle",
    "Desvio",
    "Flamethrower"
  ]
}
Fetched 1 record(s) in 3ms
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

```
DIEGO-LAPTOP(mongod-3.0.7) be-mean-pokemons> var query = { moves : { $in: ['Desvio'] } }
DIEGO-LAPTOP(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643ea5074d288f816215406"),
  "name": "Bulbasaur",
  "description": "Bulbasaur is a dual-type Grass/Poison Pokémon.",
  "attack": 49,
  "defense": 49,
  "height": 0.7,
  "moves": [
    "Quick Attack",
    "Tackle",
    "Desvio"
  ]
}
{
  "_id": ObjectId("5643ea5074d288f816215407"),
  "name": "Charmander",
  "description": "Charmander is a Fire-type Pokémon.",
  "attack": 52,
  "defense": 43,
  "height": 0.6,
  "moves": [
    "Quick Attack",
    "Tackle",
    "Desvio",
    "Flamethrower"
  ]
}
{
  "_id": ObjectId("5643ea5074d288f816215408"),
  "name": "Squirtle",
  "description": "Squirtle is a Water-type Pokémon.",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "moves": [
    "Quick Attack",
    "Tackle",
    "Desvio"
  ]
}
{
  "_id": ObjectId("5643ea5074d288f816215409"),
  "name": "Pikachu",
  "description": "Pikachu is an Eletric-type Pokémon.",
  "attack": 55,
  "defense": 30,
  "height": 0.4,
  "moves": [
    "Quick Attack",
    "Tackle",
    "Desvio"
  ]
}
{
  "_id": ObjectId("5643ea5074d288f81621540a"),
  "name": "Meowth",
  "description": "Meowth is a Normal-type Pokémon and he speaks",
  "attack": 45,
  "defense": 35,
  "height": 0.4,
  "moves": [
    "Quick Attack",
    "Tackle",
    "Desvio"
  ]
}
Fetched 5 record(s) in 20ms
```
## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

```
DIEGO-LAPTOP(mongod-3.0.7) be-mean-pokemons> var query = { type : { $ne: 'Eletric' } }
DIEGO-LAPTOP(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643ea5074d288f816215407"),
  "name": "Charmander",
  "description": "Charmander is a Fire-type Pokémon.",
  "attack": 52,
  "defense": 43,
  "height": 0.6,
  "moves": [
    "Quick Attack",
    "Tackle",
    "Desvio",
    "Flamethrower"
  ],
  "type": "Fire"
}
{
  "_id": ObjectId("5643ea5074d288f816215408"),
  "name": "Squirtle",
  "description": "Squirtle is a Water-type Pokémon.",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "moves": [
    "Quick Attack",
    "Tackle",
    "Desvio"
  ],
  "type": "Water"
}
{
  "_id": ObjectId("5643ea5074d288f81621540a"),
  "name": "Meowth",
  "description": "Meowth is a Normal-type Pokémon and he speaks",
  "attack": 45,
  "defense": 35,
  "height": 0.4,
  "moves": [
    "Quick Attack",
    "Tackle",
    "Desvio"
  ],
  "type": "Normal"
}
{
  "_id": ObjectId("564bf2f6466a6dba40613be5"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null,
  "defense": null,
  "moves": [ ]
}
Fetched 4 record(s) in 14ms
```
## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```
DIEGO-LAPTOP(mongod-3.0.7) be-mean-pokemons> var query = { $and : [ { moves: { $in : [/Quick Attack/i] } }, { defense : { $not : { $lte : 49 } } } ] }

DIEGO-LAPTOP(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643ea5074d288f816215408"),
  "name": "Squirtle",
  "description": "Squirtle is a Water-type Pokémon.",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "moves": [
    "Quick Attack",
    "Tackle",
    "Desvio"
  ],
  "type": "Water"
}
Fetched 1 record(s) in 8ms
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
DIEGO-LAPTOP(mongod-3.0.7) be-mean-pokemons> var query = { $and : [ { 'type' : 'Water' }, { 'attack' : { $lt: 50 } } ] }

DIEGO-LAPTOP(mongod-3.0.7) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 2ms
WriteResult({
  "nRemoved": 1
})