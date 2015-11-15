# MongoDB - Aula 02 - Exercício
Autor: Henrique Antonini Silvério

## Listagem das databases (passo 2)

```bash
show dbs
be-mean        0.078GB
local          0.078GB
marionetteify  0.078GB
```


## Listagem das coleções (passo 3)

```bash
show collections
```


## Cadastro dos pokemons (passo 4)

```bash
var pokemons = [{
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "attack": 30,
  "defense": 20,
  "height": 0.7
}, {
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely. ",
  "attack": 30,
  "defense": 20,
  "height": 0.6
}, {
  "name": "Blastoise",
  "description": "Blastoise has water spouts that protrude from its shell. The water spouts are very accurate. They can shoot bullets of water with enough accuracy to strike empty cans from a distance of over 160 feet. ",
  "attack": 40,
  "defense": 40,
  "height": 1.6
}, {
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge. ",
  "attack": 30,
  "defense": 20,
  "height": 0.4
}, {
  "name": "Alakazam",
  "description": "Alakazam's brain continually grows, making its head far too heavy to support with its neck. This Pokémon holds its head up using its psychokinetic power instead. ",
  "attack": 30,
  "defense": 20,
  "height": 1.5
}];

db.pokemons.insert(pokemons);
```


## Lista dos pokemons (passo 5)

```bash
db.pokemons.find()
{
  "_id": ObjectId("5646158d50351dcd5c271be7"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "attack": 30,
  "defense": 20,
  "height": 0.7
}
{
  "_id": ObjectId("5646158d50351dcd5c271be8"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely. ",
  "attack": 30,
  "defense": 20,
  "height": 0.6
}
{
  "_id": ObjectId("5646158d50351dcd5c271be9"),
  "name": "Blastoise",
  "description": "Blastoise has water spouts that protrude from its shell. The water spouts are very accurate. They can shoot bullets of water with enough accuracy to strike empty cans from a distance of over 160 feet. ",
  "attack": 40,
  "defense": 40,
  "height": 1.6
}
{
  "_id": ObjectId("5646158d50351dcd5c271bea"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge. ",
  "attack": 30,
  "defense": 20,
  "height": 0.4
}
{
  "_id": ObjectId("5646158d50351dcd5c271beb"),
  "name": "Alakazam",
  "description": "Alakazam's brain continually grows, making its head far too heavy to support with its neck. This Pokémon holds its head up using its psychokinetic power instead. ",
  "attack": 30,
  "defense": 20,
  "height": 1.5
}
Fetched 5 record(s) in 2ms
```


## Pikachu (passo 6)

```bash
var query = { name: "Pikachu" };
db.pokemons.find(query);
{
  "_id": ObjectId("5646158d50351dcd5c271bea"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge. ",
  "attack": 30,
  "defense": 20,
  "height": 0.4
}
Fetched 1 record(s) in 75ms
```


## Atualização do Pikachu (passo 6)

```bash
var poke = db.pokemons.findOne({ name: "Pikachu" });
```

```bash
poke

{
  "_id": ObjectId("5646158d50351dcd5c271bea"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge. ",
  "attack": 30,
  "defense": 20,
  "height": 0.4
}
Fetched 1 record(s) in 1ms
```

```bash
poke.description = "A new description to Pikachu";
```

```bash
db.pokemons.save(poke);

Updated 1 existing record(s) in 71ms

WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```
