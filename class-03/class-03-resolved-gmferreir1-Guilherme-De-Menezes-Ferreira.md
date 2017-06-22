# MongoDB - Aula 03 - Exercício
autor: Guilherme de Menezes Ferreira

## Listando Pokemons com a altura menor que 0.5

```
(mongod-3.2.1) be-mean-pokemons> var query = {height:{$lt:0.5}}
(mongod-3.2.1) be-mean-pokemons> query
{
  "height": {
    "$lt": 0.5
  }
}
(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 79ms
```

## Listando Pokemons com a altura maior ou igual que 0.5

```
(mongod-3.2.1) be-mean-pokemons> var query = {height:{$gte:0.5}}
(mongod-3.2.1) be-mean-pokemons> query
{
  "height": {
    "$gte": 0.5
  }
}
(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56bdb4c87ee78537f807d681"),
  "name": "bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the suns rays, the seed grows progressively larger",
  "attack": 30,
  "defense": 20,
  "height": 7
}
{
  "_id": ObjectId("56bdb4c87ee78537f807d682"),
  "name": "ivysaur",
  "description": "There is a bud on this Pokémon's back. To support its weight, Ivysaur's legs and trunk grow thick and strong. If it starts spending more time lying in the sunlight, it's a sign that the bud will bloom into a large flower soon.",
  "attack": 30,
  "defense": 30,
  "height": 10
}
{
  "_id": ObjectId("56bdb4c87ee78537f807d683"),
  "name": "Squirtle",
  "description": "Descrição alterada",
  "attack": 300,
  "defense": 300,
  "height": 0.5
}
{
  "_id": ObjectId("56bdb4c87ee78537f807d684"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
  "attack": 300,
  "defense": 200,
  "height": 0.6
}
{
  "_id": ObjectId("56bdb4c87ee78537f807d685"),
  "name": "Farfetch'd",
  "description": "Farfetch'd is always seen with a stalk from a plant of some sort. Apparently, there are good stalks and bad stalks. This Pokémon has been known to fight with others over stalks.",
  "attack": 300,
  "defense": 300,
  "height": 0.8
}
Fetched 5 record(s) in 304ms
```
## Listando Pokemons com a altura menor ou igual 0.5 E do tipo grama

```
(mongod-3.2.1) be-mean-pokemons> var query = {$and:[{height:{$lte:0.5}},{type:'grama'}]}
(mongod-3.2.1) be-mean-pokemons> query
{
  "$and": [
    {
      "height": {
        "$lte": 0.5
      }
    },
    {
      "type": "grama"
    }
  ]
}
(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 40ms
```

## Listando pokemons com o attack MAIOR OU IGUAL QUE 48 E com height MENOR OU IGUAL QUE 0.5

```
(mongod-3.2.1) be-mean-pokemons> var query = {$and:[{attack:{$gte:48}},{height:{$lte:0.5}}]}
(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56bdb4c87ee78537f807d683"),
  "name": "Squirtle",
  "description": "Descrição alterada",
  "attack": 300,
  "defense": 300,
  "height": 0.5
}
Fetched 1 record(s) in 3ms
```



