# MongoDB - Aula 02 - Exercício
autor: Jean F. Santos

## Criando database be-mean-pokemons

```
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-instagram> use be-mean-pokemons
switched to db be-mean-pokemons
```

## Listando os databases

```
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> show dbs
be-mean-instagram  0.078GB
be-mean            0.078GB
local              0.078GB
```

## Listando as collections

```
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> show collections
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons>
```

## Inserindo dos pokemons
```
var pokemons = [
  {
    name: "Bulbasaur",
    description: "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
    attack: 30,
    defense: 20,
    height: 0.7
  },
  {
    name: "Charmander",
    description: "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
    attack: 30,
    defense: 20,
    height: 0.6
  },
  {
    name: "Squirtle",
    description: "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
    attack: 30,
    defense: 30,
    height: 0.5
  },
  {
    name: "Weedle",
    description: "Weedle has an extremely acute sense of smell. It is capable of distinguishing its favorite kinds of leaves from those it dislikes just by sniffing with its big red proboscis (nose).",
    attack: 20,
    defense: 20,
    height: 0.3
  },
  {
    name: "Clefairy",
    description: "On every night of a full moon, groups of this Pokémon come out to play. When dawn arrives, the tired Clefairy return to their quiet mountain retreats and go to sleep nestled up against each other.",
    attack: 20,
    defense: 20,
    height: 0.6
  }    
];
```

```
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemons);
Inserted 1 record(s) in 766ms
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

## Listando os pokemons

```
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> db.pokemons.find();
{
  "_id": ObjectId("56478e8a946eb268a71e80d0"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "attack": 30,
  "defense": 20,
  "height": 0.7
}
{
  "_id": ObjectId("56478e8a946eb268a71e80d1"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
  "attack": 30,
  "defense": 20,
  "height": 0.6
}
{
  "_id": ObjectId("56478e8a946eb268a71e80d2"),
  "name": "Squirtle",
  "description": "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
  "attack": 30,
  "defense": 30,
  "height": 0.5
}
{
  "_id": ObjectId("56478e8a946eb268a71e80d3"),
  "name": "Weedle",
  "description": "Weedle has an extremely acute sense of smell. It is capable of distinguishing its favorite kinds of leaves from those it dislikes just by sniffing with its big red proboscis (nose).",
  "attack": 20,
  "defense": 20,
  "height": 0.3
}
{
  "_id": ObjectId("56478e8a946eb268a71e80d4"),
  "name": "Clefairy",
  "description": "On every night of a full moon, groups of this Pokémon come out to play. When dawn arrives, the tired Clefairy return to their quiet mountain retreats and go to sleep nestled up against each other.",
  "attack": 20,
  "defense": 20,
  "height": 0.6
}
Fetched 5 record(s) in 13ms
```

## Buscando pokemon

```
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne({name: 'Charmander'});
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> poke
{
  "_id": ObjectId("56478e8a946eb268a71e80d1"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
  "attack": 30,
  "defense": 20,
  "height": 0.6
}
```

## Alterando descrição do pokemon

```
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> poke.description = 'alterando description';
alterando description
MacBook-Pro-de-jean(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 28ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```
