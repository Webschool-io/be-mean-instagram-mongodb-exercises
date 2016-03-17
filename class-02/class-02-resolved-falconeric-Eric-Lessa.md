# MongoDB - Aula 02 - Exercício
autor: ERIC LESSA

## Liste quais databases você possui nesse servidor;

```
show dbs

be-mean-instagram → 0.005GB
be-mean-pokemons  → 0.000GB
local             → 0.000GB
```

## Liste quais coleções você possui nessa database;

```
show collections

pokemons → 0.003MB / 0.035MB
```

## Crie uma database chamada be-mean-pokemons; Insira pelo menos 5 pokemons;

```
use be-mean-pokemons
switched to db be-mean-pokemons

ericlessa(mongod-3.2.4) be-mean-pokemons> var pokemons = [{"name":"Bulbasaur","description":"Bulbasaur can be seen napping in bright sunlight. There is a seed on its back.","attack":49,"defense":49,"height":0.7},{"name":"Ivysaur","description":"There is a bud on this Pokémon's back. To support its weight, Ivysaur's legs and trunk grow thick and strong. If it starts spending more time lying in the sunlight, it's a sign that the bud will bloom into a large flower soon.","attack":62,"defense":63,"height":1},{"name":"Venusaur","description":"There is a large flower on Venusaur's back. The flower is said to take on vivid colors if it gets plenty of nutrition and sunlight. The flower's aroma soothes the emotions of people.","attack":100,"defense":123,"height":2},{"name":"Charmander","description":"The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.","attack":52,"defense":43,"height":0.6},{"name":"Charmeleon","description":"Charmeleon mercilessly destroys its foes using its sharp claws. If it encounters a strong foe, it turns aggressive. In this excited state, the flame at the tip of its tail flares with a bluish white color.","attack":64,"defense":58,"height":1.1},{"name":"Charizard","description":"Charizard flies around the sky in search of powerful opponents. It breathes fire of such great heat that it melts anything. However, it never turns its fiery breath on any opponent weaker than itself.","attack":84,"defense":78,"height":1.7},{"name":"Squirtle","description":"Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.","attack":48,"defense":65,"height":0.5},{"name":"Wartortle","description":"ts tail is large and covered with a rich, thick fur. The tail becomes increasingly deeper in color as Wartortle ages. The scratches on its shell are evidence of this Pokémon's toughness as a battler.","attack":63,"defense":80,"height":1},{"name":"Blastoise","description":"Blastoise has water spouts that protrude from its shell. The water spouts are very accurate. They can shoot bullets of water with enough accuracy to strike empty cans from a distance of over 160 feet.","attack":83,"defense":100,"height":1.6}]

ericlessa(mongod-3.2.4) be-mean-pokemons> db.pokemons.save(pokemons)
Inserted 1 record(s) in 40ms
BulkWriteResult({
  "writeErrors": [ ],
  "writeConcernErrors": [ ],
  "nInserted": 9,
  "nUpserted": 0,
  "nMatched": 0,
  "nModified": 0,
  "nRemoved": 0,
  "upserted": [ ]
})
```

## Liste os pokemons existentes na sua coleção;

```
db.pokemons.find()
{
  "_id": ObjectId("56e9b5cd5cf4bdfce34de41d"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back.",
  "attack": 49,
  "defense": 49,
  "height": 0.7
}
{
  "_id": ObjectId("56e9b5cd5cf4bdfce34de41e"),
  "name": "Ivysaur",
  "description": "There is a bud on this Pokémon's back. To support its weight, Ivysaur's legs and trunk grow thick and strong. If it starts spending more time lying in the sunlight, it's a sign that the bud will bloom into a large flower soon.",
  "attack": 62,
  "defense": 63,
  "height": 1
}
{
  "_id": ObjectId("56e9b5cd5cf4bdfce34de41f"),
  "name": "Venusaur",
  "description": "There is a large flower on Venusaur's back. The flower is said to take on vivid colors if it gets plenty of nutrition and sunlight. The flower's aroma soothes the emotions of people.",
  "attack": 100,
  "defense": 123,
  "height": 2
}
{
  "_id": ObjectId("56e9b5cd5cf4bdfce34de420"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
  "attack": 52,
  "defense": 43,
  "height": 0.6
}
{
  "_id": ObjectId("56e9b5cd5cf4bdfce34de421"),
  "name": "Charmeleon",
  "description": "Charmeleon mercilessly destroys its foes using its sharp claws. If it encounters a strong foe, it turns aggressive. In this excited state, the flame at the tip of its tail flares with a bluish white color.",
  "attack": 64,
  "defense": 58,
  "height": 1.1
}
{
  "_id": ObjectId("56e9b5cd5cf4bdfce34de422"),
  "name": "Charizard",
  "description": "Charizard flies around the sky in search of powerful opponents. It breathes fire of such great heat that it melts anything. However, it never turns its fiery breath on any opponent weaker than itself.",
  "attack": 84,
  "defense": 78,
  "height": 1.7
}
{
  "_id": ObjectId("56e9b5cd5cf4bdfce34de423"),
  "name": "Squirtle",
  "description": "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
  "attack": 48,
  "defense": 65,
  "height": 0.5
}
{
  "_id": ObjectId("56e9b5cd5cf4bdfce34de424"),
  "name": "Wartortle",
  "description": "ts tail is large and covered with a rich, thick fur. The tail becomes increasingly deeper in color as Wartortle ages. The scratches on its shell are evidence of this Pokémon's toughness as a battler.",
  "attack": 63,
  "defense": 80,
  "height": 1
}
{
  "_id": ObjectId("56e9b5cd5cf4bdfce34de425"),
  "name": "Blastoise",
  "description": "Blastoise has water spouts that protrude from its shell. The water spouts are very accurate. They can shoot bullets of water with enough accuracy to strike empty cans from a distance of over 160 feet.",
  "attack": 83,
  "defense": 100,
  "height": 1.6
}
Fetched 9 record(s) in 7ms
```

## Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada `poke`;

```
ericlessa(mongod-3.2.4) be-mean-pokemons> var query = {"name":"Bulbasaur"}
ericlessa(mongod-3.2.4) be-mean-pokemons> var poke = db.pokemons.findOne(query)
ericlessa(mongod-3.2.4) be-mean-pokemons> poke
{
  "_id": ObjectId("56e9b5cd5cf4bdfce34de41d"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back.",
  "attack": 49,
  "defense": 49,
  "height": 0.7
}

ericlessa(mongod-3.2.4) be-mean-pokemons> poke.description = "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger."
Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.

ericlessa(mongod-3.2.4) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 3ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```