# MongoDB - Aula 04 - Exercício
autor: ERIC LESSA

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
elcarvalho(mongod-3.2.4) be-mean-pokemons> var query = { "name" : /pikachu/i }
elcarvalho(mongod-3.2.4) be-mean-pokemons> var mod = { $pushAll : { moves : ['Thunderbolt', 'Thunder wave'] } }
elcarvalho(mongod-3.2.4) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 3ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

elcarvalho(mongod-3.2.4) be-mean-pokemons> var query = { "name" : /squirtle/i }
elcarvalho(mongod-3.2.4) be-mean-pokemons> var mod = { $pushAll : { moves : ['Hydro pump', 'Tail whip'] } }
elcarvalho(mongod-3.2.4) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 4ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

elcarvalho(mongod-3.2.4) be-mean-pokemons> var query = { "name" : /bulbasaur/i }
elcarvalho(mongod-3.2.4) be-mean-pokemons> var mod = { $pushAll : { moves : ['Spore', 'Gigadrain'] } }
elcarvalho(mongod-3.2.4) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 6ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

elcarvalho(mongod-3.2.4) be-mean-pokemons> var query = { "name" : /charmander/i }
elcarvalho(mongod-3.2.4) be-mean-pokemons> var mod = { $pushAll : { moves : ['Fire blast', 'Flamethrower'] } }
elcarvalho(mongod-3.2.4) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```

## **Adicionar** 1 movimento em todos os pokemons: desvio.

```
elcarvalho(mongod-3.2.4) be-mean-pokemons> var query = {}
elcarvalho(mongod-3.2.4) be-mean-pokemons> var mod = { $push : { 'moves' : 'desvio' }}
elcarvalho(mongod-3.2.4) be-mean-pokemons> var opt = { multi : true }
elcarvalho(mongod-3.2.4) be-mean-pokemons> db.pokemons.update(query, mod, opt)
Updated 13 existing record(s) in 1ms
WriteResult({
  "nMatched": 13,
  "nUpserted": 0,
  "nModified": 13
})
```

## **Adicionar** o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".

```
elcarvalho(mongod-3.2.4) be-mean-pokemons> var query = { "name" : /AindaNaoExisteMon/i }
elcarvalho(mongod-3.2.4) be-mean-pokemons> var mod = { $setOnInsert : { "name" : "AindaNaoExisteMon", "description" : "Sem maiores informações", "attack" : null, "defense" : null, "height" : null, "type" : null } }
elcarvalho(mongod-3.2.4) be-mean-pokemons> var opt = {upsert:true}
elcarvalho(mongod-3.2.4) be-mean-pokemons> db.pokemons.update(query, mod, opt)
Updated 1 new record(s) in 2ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("56ec5baeb70042448494bdd1")
})
```

## Pesquisar **todos** o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.

```
elcarvalho(mongod-3.2.4) be-mean-pokemons> var query = { "moves" : {$in : ['investida', 'Fireblast']}}
elcarvalho(mongod-3.2.4) be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("56e9b5cd5cf4bdfce34de41d"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "attack": 49,
  "defense": 49,
  "height": 0.7,
  "moves": [
    "investida",
    "Vine whip",
    "Spore",
    "Gigadrain",
    "desvio"
  ]
}
{
  "_id": ObjectId("56e9b5cd5cf4bdfce34de41e"),
  "name": "Ivysaur",
  "description": "There is a bud on this Pokémon's back. To support its weight, Ivysaur's legs and trunk grow thick and strong. If it starts spending more time lying in the sunlight, it's a sign that the bud will bloom into a large flower soon.",
  "attack": 62,
  "defense": 63,
  "height": 1,
  "type": "Grass",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56e9b5cd5cf4bdfce34de41f"),
  "name": "Venusaur",
  "description": "There is a large flower on Venusaur's back. The flower is said to take on vivid colors if it gets plenty of nutrition and sunlight. The flower's aroma soothes the emotions of people.",
  "attack": 100,
  "defense": 123,
  "height": 2,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56e9b5cd5cf4bdfce34de420"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
  "attack": 52,
  "defense": 43,
  "height": 0.6,
  "moves": [
    "investida",
    "Ember",
    "Fire blast",
    "Flamethrower",
    "desvio"
  ]
}

...

Fetched 13 record(s) in 12ms
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```
elcarvalho(mongod-3.2.4) be-mean-pokemons> var query = { "moves" : {$in : ['Hydro pump', 'Fire blast', 'Gigadrain']}}
elcarvalho(mongod-3.2.4) be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("56e9b5cd5cf4bdfce34de41d"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "attack": 49,
  "defense": 49,
  "height": 0.7,
  "moves": [
    "investida",
    "Vine whip",
    "Spore",
    "Gigadrain",
    "desvio"
  ]
}
{
  "_id": ObjectId("56e9b5cd5cf4bdfce34de420"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
  "attack": 52,
  "defense": 43,
  "height": 0.6,
  "moves": [
    "investida",
    "Ember",
    "Fire blast",
    "Flamethrower",
    "desvio"
  ]
}
{
  "_id": ObjectId("56e9b5cd5cf4bdfce34de423"),
  "name": "Squirtle",
  "description": "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "moves": [
    "investida",
    "Water gun",
    "Hydro pump",
    "Tail whip",
    "desvio"
  ]
}
Fetched 3 record(s) in 6ms
```

## Pesquisar **todos** os pokemons que não são do tipo elétrico.

```
elcarvalho(mongod-3.2.4) be-mean-pokemons> var query = {"type" : {$not : /eletric/i}}
elcarvalho(mongod-3.2.4) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56e9b5cd5cf4bdfce34de41d"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "attack": 49,
  "defense": 49,
  "height": 0.7,
  "moves": [
    "investida",
    "Vine whip",
    "Spore",
    "Gigadrain",
    "desvio"
  ],
  "type": "Grass"
}
{
  "_id": ObjectId("56e9b5cd5cf4bdfce34de41e"),
  "name": "Ivysaur",
  "description": "There is a bud on this Pokémon's back. To support its weight, Ivysaur's legs and trunk grow thick and strong. If it starts spending more time lying in the sunlight, it's a sign that the bud will bloom into a large flower soon.",
  "attack": 62,
  "defense": 63,
  "height": 1,
  "type": "Grass",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56e9b5cd5cf4bdfce34de41f"),
  "name": "Venusaur",
  "description": "There is a large flower on Venusaur's back. The flower is said to take on vivid colors if it gets plenty of nutrition and sunlight. The flower's aroma soothes the emotions of people.",
  "attack": 100,
  "defense": 123,
  "height": 2,
  "moves": [
    "investida",
    "desvio"
  ],
  "type": "Grass"
}
{
  "_id": ObjectId("56e9b5cd5cf4bdfce34de420"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
  "attack": 52,
  "defense": 43,
  "height": 0.6,
  "moves": [
    "investida",
    "Ember",
    "Fire blast",
    "Flamethrower",
    "desvio"
  ]
}
{
  "_id": ObjectId("56e9b5cd5cf4bdfce34de421"),
  "name": "Charmeleon",
  "description": "Charmeleon mercilessly destroys its foes using its sharp claws. If it encounters a strong foe, it turns aggressive. In this excited state, the flame at the tip of its tail flares with a bluish white color.",
  "attack": 64,
  "defense": 58,
  "height": 1.1,
  "moves": [
    "investida",
    "desvio"
  ],
  "type": "Fire"
}
{
  "_id": ObjectId("56e9b5cd5cf4bdfce34de422"),
  "name": "Charizard",
  "description": "Charizard flies around the sky in search of powerful opponents. It breathes fire of such great heat that it melts anything. However, it never turns its fiery breath on any opponent weaker than itself.",
  "attack": 84,
  "defense": 78,
  "height": 1.7,
  "moves": [
    "investida",
    "desvio"
  ],
  "type": "Fly"
}
{
  "_id": ObjectId("56e9b5cd5cf4bdfce34de423"),
  "name": "Squirtle",
  "description": "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "moves": [
    "investida",
    "Water gun",
    "Hydro pump",
    "Tail whip",
    "desvio"
  ],
  "type": "Water"
}
{
  "_id": ObjectId("56e9b5cd5cf4bdfce34de424"),
  "name": "Wartortle",
  "description": "ts tail is large and covered with a rich, thick fur. The tail becomes increasingly deeper in color as Wartortle ages. The scratches on its shell are evidence of this Pokémon's toughness as a battler.",
  "attack": 63,
  "defense": 80,
  "height": 1,
  "moves": [
    "investida",
    "desvio"
  ],
  "type": "Water"
}
{
  "_id": ObjectId("56e9b5cd5cf4bdfce34de425"),
  "name": "Blastoise",
  "description": "Blastoise has water spouts that protrude from its shell. The water spouts are very accurate. They can shoot bullets of water with enough accuracy to strike empty cans from a distance of over 160 feet.",
  "attack": 83,
  "defense": 100,
  "height": 1.6,
  "moves": [
    "investida",
    "desvio"
  ],
  "type": "water"
}
{
  "_id": ObjectId("56ea04e469e48ecf93ac6a96"),
  "name": "Paras",
  "description": "Paras has parasitic mushrooms growing on its back called tochukaso. They grow large by drawing nutrients from this Bug Pokémon host. They are highly valued as a medicine for extending life.",
  "attack": 70,
  "defense": 55,
  "height": 0.3,
  "moves": [
    "investida",
    "desvio"
  ],
  "type": "Poison"
}
{
  "_id": ObjectId("56ea04e469e48ecf93ac6a97"),
  "name": "MissingNo",
  "description": "Is an unofficial Pokémon species found in the video games Pokémon Red and Blue. Standing for Missing Number, MissingNo. are used as error handlers by game developer Game Freak",
  "attack": 0.4,
  "defense": 55,
  "height": 0.3,
  "moves": [
    "investida",
    "desvio"
  ],
  "type": "Normal"
}
{
  "_id": ObjectId("56ec4b14b70042448494bdcf"),
  "active": true,
  "name": "PokemonInexistente",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem informações",
  "moves": [
    "investida",
    "desvio"
  ],
  "type": null
}
{
  "_id": ObjectId("56ec5baeb70042448494bdd1"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "attack": null,
  "defense": null,
  "height": null,
  "type": null
}
Fetched 13 record(s) in 10ms
```

## Pesquisar **todos** pokemons que tenham o ataque investida **E** tenham a defesa **não** menor ou igual** a 49.

```
elcarvalho(mongod-3.2.4) be-mean-pokemons> var query = {$and: [{ "defense" : { $not : {$lte:49} } }, { "moves" : { $in : ['investida'] } }] }
elcarvalho(mongod-3.2.4) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56e9b5cd5cf4bdfce34de41e"),
  "name": "Ivysaur",
  "description": "There is a bud on this Pokémon's back. To support its weight, Ivysaur's legs and trunk grow thick and strong. If it starts spending more time lying in the sunlight, it's a sign that the bud will bloom into a large flower soon.",
  "attack": 62,
  "defense": 63,
  "height": 1,
  "type": "Grass",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56e9b5cd5cf4bdfce34de41f"),
  "name": "Venusaur",
  "description": "There is a large flower on Venusaur's back. The flower is said to take on vivid colors if it gets plenty of nutrition and sunlight. The flower's aroma soothes the emotions of people.",
  "attack": 100,
  "defense": 123,
  "height": 2,
  "moves": [
    "investida",
    "desvio"
  ],
  "type": "Grass"
}
{
  "_id": ObjectId("56e9b5cd5cf4bdfce34de421"),
  "name": "Charmeleon",
  "description": "Charmeleon mercilessly destroys its foes using its sharp claws. If it encounters a strong foe, it turns aggressive. In this excited state, the flame at the tip of its tail flares with a bluish white color.",
  "attack": 64,
  "defense": 58,
  "height": 1.1,
  "moves": [
    "investida",
    "desvio"
  ],
  "type": "Fire"
}
{
  "_id": ObjectId("56e9b5cd5cf4bdfce34de422"),
  "name": "Charizard",
  "description": "Charizard flies around the sky in search of powerful opponents. It breathes fire of such great heat that it melts anything. However, it never turns its fiery breath on any opponent weaker than itself.",
  "attack": 84,
  "defense": 78,
  "height": 1.7,
  "moves": [
    "investida",
    "desvio"
  ],
  "type": "Fly"
}
{
  "_id": ObjectId("56e9b5cd5cf4bdfce34de423"),
  "name": "Squirtle",
  "description": "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "moves": [
    "investida",
    "Water gun",
    "Hydro pump",
    "Tail whip",
    "desvio"
  ],
  "type": "Water"
}
{
  "_id": ObjectId("56e9b5cd5cf4bdfce34de424"),
  "name": "Wartortle",
  "description": "ts tail is large and covered with a rich, thick fur. The tail becomes increasingly deeper in color as Wartortle ages. The scratches on its shell are evidence of this Pokémon's toughness as a battler.",
  "attack": 63,
  "defense": 80,
  "height": 1,
  "moves": [
    "investida",
    "desvio"
  ],
  "type": "Water"
}
{
  "_id": ObjectId("56e9b5cd5cf4bdfce34de425"),
  "name": "Blastoise",
  "description": "Blastoise has water spouts that protrude from its shell. The water spouts are very accurate. They can shoot bullets of water with enough accuracy to strike empty cans from a distance of over 160 feet.",
  "attack": 83,
  "defense": 100,
  "height": 1.6,
  "moves": [
    "investida",
    "desvio"
  ],
  "type": "water"
}
{
  "_id": ObjectId("56ea04e469e48ecf93ac6a96"),
  "name": "Paras",
  "description": "Paras has parasitic mushrooms growing on its back called tochukaso. They grow large by drawing nutrients from this Bug Pokémon host. They are highly valued as a medicine for extending life.",
  "attack": 70,
  "defense": 55,
  "height": 0.3,
  "moves": [
    "investida",
    "desvio"
  ],
  "type": "Poison"
}
{
  "_id": ObjectId("56ea04e469e48ecf93ac6a97"),
  "name": "MissingNo",
  "description": "Is an unofficial Pokémon species found in the video games Pokémon Red and Blue. Standing for Missing Number, MissingNo. are used as error handlers by game developer Game Freak",
  "attack": 0.4,
  "defense": 55,
  "height": 0.3,
  "moves": [
    "investida",
    "desvio"
  ],
  "type": "Normal"
}
{
  "_id": ObjectId("56ec4b14b70042448494bdcf"),
  "active": true,
  "name": "PokemonInexistente",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem informações",
  "moves": [
    "investida",
    "desvio"
  ],
  "type": null
}
Fetched 10 record(s) in 11ms
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
elcarvalho(mongod-3.2.4) be-mean-pokemons> var query = { $and: [ { "type": "Water" }, { "attack": { $lt: 50 } } ] }
elcarvalho(mongod-3.2.4) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 3ms
WriteResult({
  "nRemoved": 1
})
```