
# MongoDB - Aula 02 - Exercício
autor: Guilherme Coelho Piovesan

## Listagem das databases (passo 2)

```
guilherme-UB(mongod-3.0.7) be-mean-instagram> use be-mean-pokemons
switched to db be-mean-pokemons


guilherme-UB(mongod-3.0.7) be-mean-pokemons> show dbs
be-mean           → 0.078GB
be-mean-instagram → 0.078GB
test              → 0.078GB
local             → 0.078GB
```

## Listagem das coleções (passo 3)

```
show collections
guilherme-UB(mongod-3.0.7) be-mean-pokemons> 
```

## Cadastro dos pokemons (passo 4)

```
guilherme-UB(mongod-3.0.7) be-mean-pokemons> var pokemons = [{name: 'Charizard', description: 'Charizard flies around the sky in search of powerful opponents. It breathes fire of such great heat that it melts anything. However, it never turns its fiery breath on any opponent weaker than itself.', type: 'fire', attack: 84, defense: 78, height: 17},{name: 'Psyduck', description: 'Psyduck uses a mysterious power. When it does so, this Pokémon generates brain waves that are supposedly only seen in sleepers. This discovery spurred controversy among scholars.', type: 'water', attack: 52, defense: 48, height: 8},{name: 'Totodile', description: "Despite the smallness of its body, Totodile's jaws are very powerful. While the Pokémon may think it is just playfully nipping, its bite has enough power to cause serious injury.", type: 'water', attack: 65, defense: 64, height: 6},{name: 'Snorlax', description: "Snorlax's typical day consists of nothing more than eating and sleeping. It is such a docile Pokémon that there are children who use its expansive belly as a place to play.", type: 'normal', attack: 110, defense: 65, height: 21},{name: 'Meowth', description: 'Meowth withdraws its sharp claws into its paws to slinkily sneak about without making any incriminating footsteps. For some reason, this Pokémon loves shiny coins that glitter with light.', type: 'normal', attack: 45, defense: 35, height: 4}]

guilherme-UB(mongod-3.0.7) be-mean-pokemons> pokemons
[
  {
    "name": "Charizard",
    "description": "Charizard flies around the sky in search of powerful opponents. It breathes fire of such great heat that it melts anything. However, it never turns its fiery breath on any opponent weaker than itself.",
    "type": "fire",
    "attack": 84,
    "defense": 78,
    "height": 17
  },
  {
    "name": "Psyduck",
    "description": "Psyduck uses a mysterious power. When it does so, this Pokémon generates brain waves that are supposedly only seen in sleepers. This discovery spurred controversy among scholars.",
    "type": "water",
    "attack": 52,
    "defense": 48,
    "height": 8
  },
  {
    "name": "Totodile",
    "description": "Despite the smallness of its body, Totodile's jaws are very powerful. While the Pokémon may think it is just playfully nipping, its bite has enough power to cause serious injury.",
    "type": "water",
    "attack": 65,
    "defense": 64,
    "height": 6
  },
  {
    "name": "Snorlax",
    "description": "Snorlax's typical day consists of nothing more than eating and sleeping. It is such a docile Pokémon that there are children who use its expansive belly as a place to play.",
    "type": "normal",
    "attack": 110,
    "defense": 65,
    "height": 21
  },
  {
    "name": "Meowth",
    "description": "Meowth withdraws its sharp claws into its paws to slinkily sneak about without making any incriminating footsteps. For some reason, this Pokémon loves shiny coins that glitter with light.",
    "type": "normal",
    "attack": 45,
    "defense": 35,
    "height": 4
  }
]
guilherme-UB(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 2ms
BulkWriteResult({
  "writeErrors": [ ],
  "writeConcernErrors": [ ],
  "nInserted": 5,
  "nUpserted": 0,
  "nMatched": 0,
  "nModified": 0,
  "nRemoved": 0,
  "upserted": [ ]
})
```

## Lista dos pokemons (passo 5)

```
guilherme-UB(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("5645366db273d5f44f617b9e"),
  "name": "Charizard",
  "description": "Charizard flies around the sky in search of powerful opponents. It breathes fire of such great heat that it melts anything. However, it never turns its fiery breath on any opponent weaker than itself.",
  "type": "fire",
  "attack": 84,
  "defense": 78,
  "height": 17
}
{
  "_id": ObjectId("5645366db273d5f44f617b9f"),
  "name": "Psyduck",
  "description": "Psyduck uses a mysterious power. When it does so, this Pokémon generates brain waves that are supposedly only seen in sleepers. This discovery spurred controversy among scholars.",
  "type": "water",
  "attack": 52,
  "defense": 48,
  "height": 8
}
{
  "_id": ObjectId("5645366db273d5f44f617ba0"),
  "name": "Totodile",
  "description": "Despite the smallness of its body, Totodile's jaws are very powerful. While the Pokémon may think it is just playfully nipping, its bite has enough power to cause serious injury.",
  "type": "water",
  "attack": 65,
  "defense": 64,
  "height": 6
}
{
  "_id": ObjectId("5645366db273d5f44f617ba1"),
  "name": "Snorlax",
  "description": "Snorlax's typical day consists of nothing more than eating and sleeping. It is such a docile Pokémon that there are children who use its expansive belly as a place to play.",
  "type": "normal",
  "attack": 110,
  "defense": 65,
  "height": 21
}
{
  "_id": ObjectId("5645366db273d5f44f617ba2"),
  "name": "Meowth",
  "description": "Meowth withdraws its sharp claws into its paws to slinkily sneak about without making any incriminating footsteps. For some reason, this Pokémon loves shiny coins that glitter with light.",
  "type": "normal",
  "attack": 45,
  "defense": 35,
  "height": 4
}
Fetched 5 record(s) in 5ms
```

## Pokemon (passo 6)

```
guilherme-UB(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne({name: "Psyduck"})
guilherme-UB(mongod-3.0.7) be-mean-pokemons> poke
{
  "_id": ObjectId("5645366db273d5f44f617b9f"),
  "name": "Psyduck",
  "description": "Psyduck uses a mysterious power. When it does so, this Pokémon generates brain waves that are supposedly only seen in sleepers. This discovery spurred controversy among scholars.",
  "type": "water",
  "attack": 52,
  "defense": 48,
  "height": 8
}
```

## Atualização do Pokemon (passo 7)

```
guilherme-UB(mongod-3.0.7) be-mean-pokemons> poke.description = "Psyduck uses a mysterious power. When it does so, this Pokémon generates brain waves that are supposedly only seen in sleepers. This discovery spurred controversy among scholars. Psy y y!!"
Psyduck uses a mysterious power. When it does so, this Pokémon generates brain waves that are supposedly only seen in sleepers. This discovery spurred controversy among scholars. Psy y y!!
guilherme-UB(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
guilherme-UB(mongod-3.0.7) be-mean-pokemons> db.pokemons.findOne({name: "Psyduck"})
{
  "_id": ObjectId("5645366db273d5f44f617b9f"),
  "name": "Psyduck",
  "description": "Psyduck uses a mysterious power. When it does so, this Pokémon generates brain waves that are supposedly only seen in sleepers. This discovery spurred controversy among scholars. Psy y y!!",
  "type": "water",
  "attack": 52,
  "defense": 48,
  "height": 8
}
```

