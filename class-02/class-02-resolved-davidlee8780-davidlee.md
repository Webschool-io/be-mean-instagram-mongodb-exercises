# MongoDB - Aula 02 - Exercício
autor: David Lee

## Criando a database

```
be-mean-instagram> use be-mean-pokemons
switched to db be-mean-pokemons
```

## Listar databases

```
be-mean-pokemons> show dbs
aulaMongo         → 0.078GB
be-mean-instagram → 0.078GB
be-mean           → 0.078GB
local             → 0.078GB
```

## Listar coleções

```
show collections
```

## Lista de Pokemons

```
db.pokemons.find()
{
  "_id": ObjectId("56889d2c137160758cca04da"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity.",
  "type": "Eletric",
  "attack": 30,
  "defense": 20,
  "height": 1.04
}
{
  "_id": ObjectId("56889e03137160758cca04db"),
  "name": "Raichu",
  "description": "If the electrical sacs become excessively charged, Raichu plants its tail in the ground and discharges. Scorched patches of ground will be found near this Pokémons nest.",
  "type": "Eletric",
  "attack": 50,
  "defense": 30,
  "height": 2.07
}
{
  "_id": ObjectId("56889e67137160758cca04dc"),
  "name": "Sandshrew",
  "description": "Sandshrews body is configured to absorb water without waste, enabling it to survive in an arid desert.",
  "type": "Ground",
  "attack": 40,
  "defense": 40,
  "height": 2
}
{
  "_id": ObjectId("56889eb2137160758cca04dd"),
  "name": "Sandslash",
  "description": "Sandslashs body is covered by tough spikes, which are hardened sections of its hide.",
  "type": "Ground",
  "attack": 50,
  "defense": 50,
  "height": 3.03
}
{
  "_id": ObjectId("56889ef1137160758cca04de"),
  "name": "Nidoran",
  "description": "Nidoran? has barbs that secrete a powerful poison. They are thought to have developed as protection for this small-bodied Pokémon.",
  "type": "Poison",
  "attack": 30,
  "defense": 20,
  "height": 1.04
}
{
  "_id": ObjectId("56889f2a137160758cca04df"),
  "name": "Nidorina",
  "description": "When Nidorina are with their friends or family, they keep their barbs tucked away to prevent hurting each other.",
  "type": "Poison",
  "attack": 30,
  "defense": 30,
  "height": 2.07
}
{
  "_id": ObjectId("56889f70137160758cca04e0"),
  "name": "Nidoqueen",
  "description": "Nidoqueens body is encased in extremely hard scales. It is adept at sending foes flying with harsh tackles.",
  "type": "Poison/Ground",
  "attack": 50,
  "defense": 40,
  "height": 4.03
}
Fetched 7 record(s) in 4ms
```

## Buscando o pokemon 'Nidorina'

```
var poke = {name: 'Nidorina'}
```

## Modificando description e salvando

```
var poke = {name: 'Nidorina'}
be-mean-pokemons> var p = db.pokemons.findOne(poke)
be-mean-pokemons> p.description = 'Muito protetor quando está com os amigos ou familia'
Muito protetor quando está com os amigos ou familia
be-mean-pokemons> db.pokemons.save(p)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
``
