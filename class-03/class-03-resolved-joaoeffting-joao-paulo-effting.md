# MongoDB - Aula 03 - Exercício
autor: João Paulo Effting

## Liste todos Pokemons com a altura **menor que** 0.5;
```
joaopaulo(mongod-2.6.3) be-mean-pokemons> var query = {height: {$lt:0.5}}
joaopaulo(mongod-2.6.3) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5706fb446255d7b0b7284492"),
  "name": "Ditto",
  "description": "Chang Sung dos pokémons",
  "attack": 100,
  "defense": 115,
  "height": 0.4
}
Fetched 1 record(s) in 1ms

```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
joaopaulo(mongod-2.6.3) be-mean-pokemons> var query = {height: {$gte:0.5}}

joaopaulo(mongod-2.6.3) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5706fa736255d7b0b728448e"),
  "name": "Pikachu",
  "description": "Ratinho fofinho",
  "attack": 50,
  "defense": 25,
  "height": 20
}
{
  "_id": ObjectId("5706facb6255d7b0b728448f"),
  "name": "Raichu",
  "description": "Evolução feia do pikachu",
  "attack": 70,
  "defense": 35,
  "height": 30
}
{
  "_id": ObjectId("5706faf06255d7b0b7284490"),
  "name": "Squartle",
  "description": "Tartaruga Badass",
  "attack": 50,
  "defense": 25,
  "height": 28
}
{
  "_id": ObjectId("5706fb196255d7b0b7284491"),
  "name": "Chicorita",
  "description": "Pokémon que gosta do mesmo sexo",
  "attack": 10,
  "defense": 15,
  "height": 18
}
Fetched 4 record(s) in 1ms

```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```
joaopaulo(mongod-2.6.3) be-mean-pokemon> var query = {height:{$lte:'0.5'},$and:[{types:'grass'}]}
joaopaulo(mongod-2.6.3) be-mean-pokemon> db.pokemons.find(query)
{
  "_id": ObjectId("564b1ddb25337263280d0634"),
  "attack": 107,
  "created": "2013-11-03T15:05:42.387813",
  "defense": 122,
  "height": "0",
  "hp": 88,
  "name": "Chesnaught",
  "speed": 64,
  "types": [
    "fighting",
    "grass"
  ]
}
{
  "_id": ObjectId("564b1de325337263280d068b"),
  "attack": 132,
  "created": "2013-11-03T15:05:42.580477",
  "defense": 105,
  "height": "0",
  "hp": 90,
  "name": "Abomasnow-mega",
  "speed": 30,
  "types": [
    "grass",
    "ice"
  ]
}
{
  "_id": ObjectId("564b1de625337263280d06b3"),
  "attack": 66,
  "created": "2013-11-03T15:05:42.530130",
  "defense": 70,
  "height": "0",
  "hp": 54,
  "name": "Pumpkaboo-large",
  "speed": 46,
  "types": [
    "ghost",
    "grass"
  ]
}
{
  "_id": ObjectId("564b1de625337263280d06b4"),
  "attack": 66,
  "created": "2013-11-03T15:05:42.531530",
  "defense": 70,
  "height": "0",
  "hp": 59,
  "name": "Pumpkaboo-super",
  "speed": 41,
  "types": [
    "ghost",
    "grass"
  ]
}
{
  "_id": ObjectId("564b1de625337263280d06b5"),
  "attack": 85,
  "created": "2013-11-03T15:05:42.532916",
  "defense": 122,
  "height": "0",
  "hp": 55,
  "name": "Gourgeist-small",
  "speed": 99,
  "types": [
    "ghost",
    "grass"
  ]
}
{
  "_id": ObjectId("564b1de625337263280d06b6"),
  "attack": 95,
  "created": "2013-11-03T15:05:42.534443",
  "defense": 122,
  "height": "0",
  "hp": 75,
  "name": "Gourgeist-large",
  "speed": 69,
  "types": [
    "ghost",
    "grass"
  ]
}
{
  "_id": ObjectId("564b1de625337263280d06b7"),
  "attack": 100,
  "created": "2013-11-03T15:05:42.535834",
  "defense": 122,
  "height": "0",
  "hp": 85,
  "name": "Gourgeist-super",
  "speed": 54,
  "types": [
    "ghost",
    "grass"
  ]
}
{
  "_id": ObjectId("564b1de625337263280d06b8"),
  "attack": 100,
  "created": "2013-11-03T15:05:42.537211",
  "defense": 123,
  "height": "0",
  "hp": 80,
  "name": "Venusaur-mega",
  "speed": 80,
  "types": [
    "poison",
    "grass"
  ]
}
{
  "_id": ObjectId("564b1de725337263280d06d9"),
  "attack": 65,
  "created": "2013-11-03T15:05:42.418475",
  "defense": 48,
  "height": "0",
  "hp": 66,
  "name": "Skiddo",
  "speed": 52,
  "types": [
    "grass"
  ]
}
{
  "_id": ObjectId("564b1de725337263280d06da"),
  "attack": 100,
  "created": "2013-11-03T15:05:42.420234",
  "defense": 62,
  "height": "0",
  "hp": 123,
  "name": "Gogoat",
  "speed": 68,
  "types": [
    "grass"
  ]
}
Fetched 10 record(s) in 4ms


```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```
joaopaulo(mongod-2.6.3) be-mean-pokemon> var query = {$or:[{name: 'Pikachu'},{attack:{$lte:0.5}}]}
joaopaulo(mongod-2.6.3) be-mean-pokemon> db.pokemons.find(query)
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
  ]
}
Fetched 1 record(s) in 2ms


```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```
joaopaulo(mongod-2.6.3) be-mean-pokemon> var query = {$and:[{attack:{$gte:48}},{height:{$lte:'0.5'}}]}
joaopaulo(mongod-2.6.3) be-mean-pokemon> db.pokemons.find(query)
{
  "_id": ObjectId("564b1ddb25337263280d0634"),
  "attack": 107,
  "created": "2013-11-03T15:05:42.387813",
  "defense": 122,
  "height": "0",
  "hp": 88,
  "name": "Chesnaught",
  "speed": 64,
  "types": [
    "fighting",
    "grass"
  ]
}
{
  "_id": ObjectId("564b1de125337263280d066d"),
  "attack": 82,
  "created": "2013-11-03T15:05:42.421867",
  "defense": 62,
  "height": "0",
  "hp": 67,
  "name": "Pancham",
  "speed": 43,
  "types": [
    "fighting"
  ]
}
{
  "_id": ObjectId("564b1de125337263280d066e"),
  "attack": 48,
  "created": "2013-11-03T15:05:42.427766",
  "defense": 76,
  "height": "0",
  "hp": 74,
  "name": "Meowstic-male",
  "speed": 104,
  "types": [
    "psychic"
  ]
}
{
  "_id": ObjectId("564b1de125337263280d066f"),
  "attack": 80,
  "created": "2013-11-03T15:05:42.424899",
  "defense": 60,
  "height": "0",
  "hp": 75,
  "name": "Furfrou",
  "speed": 102,
  "types": [
    "normal"
  ]
}
{
  "_id": ObjectId("564b1de125337263280d0670"),
  "attack": 48,
  "created": "2013-11-03T15:05:42.426356",
  "defense": 54,
  "height": "0",
  "hp": 62,
  "name": "Espurr",
  "speed": 68,
  "types": [
    "psychic"
  ]
}
{
  "_id": ObjectId("564b1de125337263280d0671"),
  "attack": 80,
  "created": "2013-11-03T15:05:42.429220",
  "defense": 100,
  "height": "0",
  "hp": 45,
  "name": "Honedge",
  "speed": 28,
  "types": [
    "ghost",
    "steel"
  ]
}
{
  "_id": ObjectId("564b1de125337263280d0672"),
  "attack": 110,
  "created": "2013-11-03T15:05:42.430705",
  "defense": 150,
  "height": "0",
  "hp": 59,
  "name": "Doublade",
  "speed": 35,
  "types": [
    "ghost",
    "steel"
  ]
}
{
  "_id": ObjectId("564b1de125337263280d0673"),
  "attack": 52,
  "created": "2013-11-03T15:05:42.433633",
  "defense": 60,
  "height": "0",
  "hp": 78,
  "name": "Spritzee",
  "speed": 23,
  "types": [
    "fairy"
  ]
}
{
  "_id": ObjectId("564b1de125337263280d0674"),
  "attack": 48,
  "created": "2013-11-03T15:05:42.436632",
  "defense": 66,
  "height": "0",
  "hp": 62,
  "name": "Swirlix",
  "speed": 49,
  "types": [
    "fairy"
  ]
}
{
  "_id": ObjectId("564b1de125337263280d0675"),
  "attack": 72,
  "created": "2013-11-03T15:05:42.435078",
  "defense": 72,
  "height": "0",
  "hp": 101,
  "name": "Aromatisse",
  "speed": 29,
  "types": [
    "fairy"
  ]
}
{
  "_id": ObjectId("564b1de125337263280d0676"),
  "attack": 80,
  "created": "2013-11-03T15:05:42.438232",
  "defense": 86,
  "height": "0",
  "hp": 82,
  "name": "Slurpuff",
  "speed": 72,
  "types": [
    "fairy"
  ]
}
{
  "_id": ObjectId("564b1de325337263280d068b"),
  "attack": 132,
  "created": "2013-11-03T15:05:42.580477",
  "defense": 105,
  "height": "0",
  "hp": 90,
  "name": "Abomasnow-mega",
  "speed": 30,
  "types": [
    "grass",
    "ice"
  ]
}
{
  "_id": ObjectId("564b1de525337263280d069f"),
  "attack": 155,
  "created": "2013-11-03T15:05:42.551365",
  "defense": 109,
  "height": "0",
  "hp": 95,
  "name": "Gyarados-mega",
  "speed": 81,
  "types": [
    "water",
    "dark"
  ]
}
{
  "_id": ObjectId("564b1de525337263280d06a0"),
  "attack": 95,
  "created": "2013-11-03T15:05:42.557962",
  "defense": 105,
  "height": "0",
  "hp": 90,
  "name": "Ampharos-mega",
  "speed": 45,
  "types": [
    "electric",
    "dragon"
  ]
}
{
  "_id": ObjectId("564b1de525337263280d06a1"),
  "attack": 135,
  "created": "2013-11-03T15:05:42.552922",
  "defense": 85,
  "height": "0",
  "hp": 80,
  "name": "Aerodactyl-mega",
  "speed": 150,
  "types": [
    "flying",
    "rock"
  ]
}
{
  "_id": ObjectId("564b1de525337263280d06a2"),
  "attack": 190,
  "created": "2013-11-03T15:05:42.554794",
  "defense": 100,
  "height": "0",
  "hp": 106,
  "name": "Mewtwo-mega-x",
  "speed": 130,
  "types": [
    "fighting",
    "psychic"
  ]
}
{
  "_id": ObjectId("564b1de525337263280d06a3"),
  "attack": 150,
  "created": "2013-11-03T15:05:42.556347",
  "defense": 70,
  "height": "0",
  "hp": 106,
  "name": "Mewtwo-mega-y",
  "speed": 140,
  "types": [
    "psychic"
  ]
}
{
  "_id": ObjectId("564b1de525337263280d06a4"),
  "attack": 150,
  "created": "2013-11-03T15:05:42.559647",
  "defense": 140,
  "height": "0",
  "hp": 70,
  "name": "Scizor-mega",
  "speed": 75,
  "types": [
    "bug",
    "steel"
  ]
}
{
  "_id": ObjectId("564b1de525337263280d06a5"),
  "attack": 100,
  "created": "2013-11-03T15:05:42.571921",
  "defense": 85,
  "height": "0",
  "hp": 60,
  "name": "Medicham-mega",
  "speed": 100,
  "types": [
    "fighting",
    "psychic"
  ]
}
{
  "_id": ObjectId("564b1de525337263280d06a6"),
  "attack": 185,
  "created": "2013-11-03T15:05:42.561123",
  "defense": 115,
  "height": "0",
  "hp": 80,
  "name": "Heracross-mega",
  "speed": 75,
  "types": [
    "fighting",
    "bug"
  ]
}
Fetched 20 record(s) in 12ms -- More[true]



```
