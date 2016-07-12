# MongoDB - Aula 02 - Exercício
autor: Weslley Alves de Barros

## Crie uma database chamada be-mean-pokemons;

```
   mongo be-mean-pokemons (Sim, Sou muito preguiçoso)


```
## 2. Liste quais databases você possui nesse servidor;

```
  show dbs
    be-mean → 0.005GB
    local   → 0.000GB

```


## 3. Liste quais coleções você possui nessa database;
```
  show collections
  (retorno nada pois acabei de cria-la.)

```

## 4. Insira pelo menos 5 pokemons A SUA ESCOLHA

```
 var pokebolas = [

    "name": "Charizard",
    "description": "Charizard flies around the sky in search of powerful opponents. It breathes fire of such great heat that it melts anything. However, it never turns its fiery breath on any opponent weaker than itself.",
    "attack": 40,
    "defense": 30,
    "height": 1.7
  },
  {
    "name": "Mewtwo",
    "description": "Mewtwo is a Pokémon that was created by genetic manipulation. However, even though the scientific power of humans created this Pokémon's body, they failed to endow Mewtwo with a compassionate heart.",
    "attack": 60,
    "defense": 40,
    "height": 2
  },
  {
    "name": "Celebi",
    "description": "This Pokémon came from the future by crossing over time. It is thought that so long as Celebi appears, a bright and shining future awaits us.",
    "attack": 50,
    "defense": 40,
    "height": 0.6
  },
  {
    "name": "Sigilyph",
    "description": "The guardians of an ancient city, they use their psychic power to attack enemies that invade their territory.",
    "attack": 30,
    "defense": 40,
    "height": 1.4
  },
  {
    "name": "Sawk",
    "description": "Desiring the strongest karate chop, they seclude themselves in mountains and train without sleeping.",
    "attack": 60,
    "defense": 30,
    "height": 1.4
  },
  {
    "name": "Ho-Oh",
    "description": "",
    "attack": 70,
    "defense": 40,
    "height": 3.8
  }
]

MacBook-Pro-de-Weslley(mongod-3.2.4) be-mean> db.pokemons.insert(pokebolas)
Inserted 1 record(s) in 468ms
BulkWriteResult({
  "writeErrors": [ ],
  "writeConcernErrors": [ ],
  "nInserted": 6,
  "nUpserted": 0,
  "nMatched": 0,
  "nModified": 0,
  "nRemoved": 0,
  "upserted": [ ]
})



```

## 5. Liste os pokemons existentes na sua coleção;
```
   b.pokemons.find()
{
  "_id": ObjectId("574b40cdd5035b142be6d86b"),
  "name": "Charizard",
  "description": "Charizard flies around the sky in search of powerful opponents. It breathes fire of such great heat that it melts anything. However, it never turns its fiery breath on any opponent weaker than itself.",
  "attack": 40,
  "defense": 30,
  "height": 1.7
}
{
  "_id": ObjectId("574b40cdd5035b142be6d86c"),
  "name": "Mewtwo",
  "description": "Mewtwo is a Pokémon that was created by genetic manipulation. However, even though the scientific power of humans created this Pokémon's body, they failed to endow Mewtwo with a compassionate heart.",
  "attack": 60,
  "defense": 40,
  "height": 2
}
{
  "_id": ObjectId("574b40cdd5035b142be6d86d"),
  "name": "Celebi",
  "description": "This Pokémon came from the future by crossing over time. It is thought that so long as Celebi appears, a bright and shining future awaits us.",
  "attack": 50,
  "defense": 40,
  "height": 0.6
}
{
  "_id": ObjectId("574b40cdd5035b142be6d86e"),
  "name": "Sigilyph",
  "description": "The guardians of an ancient city, they use their psychic power to attack enemies that invade their territory.",
  "attack": 30,
  "defense": 40,
  "height": 1.4
}
{
  "_id": ObjectId("574b40cdd5035b142be6d86f"),
  "name": "Sawk",
  "description": "Desiring the strongest karate chop, they seclude themselves in mountains and train without sleeping.",
  "attack": 60,
  "defense": 30,
  "height": 1.4
}
{
  "_id": ObjectId("574b40cdd5035b142be6d870"),
  "name": "Ho-Oh",
  "description": "",
  "attack": 70,
  "defense": 40,
  "height": 3.8
}
Fetched 6 record(s) in 3ms


```

## 6. Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada `poke`;

```

MacBook-Pro-de-Weslley(mongod-3.2.4) be-mean> poke = db.pokemons.findOne({"name": "Ho-Oh"})
{
  "_id": ObjectId("574b40cdd5035b142be6d870"),
  "name": "Ho-Oh",
  "description": "",
  "attack": 70,
  "defense": 40,
  "height": 3.8
}

MacBook-Pro-de-Weslley(mongod-3.2.4) be-mean> poke.description = "Ho-Oh's feathers glow in seven colors depending on the angle at which they are struck by light. These feathers are said to bring happiness to the bearers. This Pokémon is said to live at the foot of a rainbow."
Ho-Oh's feathers glow in seven colors depending on the angle at which they are struck by light. These feathers are said to bring happiness to the bearers. This Pokémon is said to live at the foot of a rainbow.


```

## 7. Modifique sua `description` e salvê-o
```
MacBook-Pro-de-Weslley(mongod-3.2.4) be-mean> poke.description = "Ho-Oh's feathers glow in seven colors depending on the angle at which they are struck by light. These feathers are said to bring happiness to the bearers. This Pokémon is said to live at the foot of a rainbow."
Ho-Oh's feathers glow in seven colors depending on the angle at which they are struck by light. These feathers are said to bring happiness to the bearers. This Pokémon is said to live at the foot of a rainbow.

MacBook-Pro-de-Weslley(mongod-3.2.4) be-mean> db.pokemons.save(poke)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

```