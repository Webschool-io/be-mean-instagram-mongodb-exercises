
# MongoDB - Aula 02 - Exercício
autor: Guilherme de Menezes Ferreira

## Criar Database be-mean-pokemons (etapa 1)

```
MacBook-Pro-de-Guilherme(mongod-3.2.1) test> use be-mean-pokemons
switched to db be-mean-pokemons
MacBook-Pro-de-Guilherme(mongod-3.2.1) be-mean-pokemons>

```

## Listagem das databases (etapa 2)

```
MacBook-Pro-de-Guilherme(mongod-3.2.1) be-mean-pokemons> show dbs
be-mean → 0.078GB
local   → 0.078GB

```

## Listagem das coleções (Etapa 3)

```
MacBook-Pro-de-Guilherme(mongod-3.2.1) be-mean-pokemons> show collections
pokemons       → 0.000MB / 0.008MB
system.indexes → 0.000MB / 0.008MB

```

## Cadastro dos pokemons (Etapa 4)

```
MacBook-Pro-de-Guilherme(mongod-3.2.1) be-mean-pokemons> db.pokemons.insert([{
... name: 'bulbasaur', 
... description: "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the suns rays, the seed grows progressively larger", 
... attack: 30, 
... defense: 20, 
... height: 7
... },
... 
... {
... name: 'ivysaur', 
... description: "There is a bud on this Pokémon's back. To support its weight, Ivysaur's legs and trunk grow thick and strong. If it starts spending more time lying in the sunlight, it's a sign that the bud will bloom into a large flower soon.", 
... attack: 30, 
... defense: 30, 
... height: 10
... },
... 
... {
... name:"Squirtle", 
... description: "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.", 
... attack: 300, 
... defense:300, 
... height:0.5
... },
... 
... {
... 
...   name: "Charmander",
...   description: "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
...   attack: 300,
...   defense: 200,
...   height: 0.6
... },
... 
... {
... name: "Farfetch'd",
...   description: "Farfetch'd is always seen with a stalk from a plant of some sort. Apparently, there are good stalks and bad stalks. This Pokémon has been known to fight with others over stalks.",
...   attack: 300,
...   defense: 300,
...   height: 0.8
... }])
Inserted 1 record(s) in 43ms
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

## Listagem dos pokemons (Etapa 5)

```
MacBook-Pro-de-Guilherme(mongod-3.2.1) be-mean-pokemons> db.pokemons.find()
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
  "description": "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
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
Fetched 5 record(s) in 65ms

```


## Pikachu (Etapa 6)

```
MacBook-Pro-de-Guilherme(mongod-3.2.1) be-mean-pokemons> var query = {name:"Squirtle"}
MacBook-Pro-de-Guilherme(mongod-3.2.1) be-mean-pokemons> var poke = db.pokemons.findOne(query)
MacBook-Pro-de-Guilherme(mongod-3.2.1) be-mean-pokemons> poke
{
  "_id": ObjectId("56bdb4c87ee78537f807d683"),
  "name": "Squirtle",
  "description": "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
  "attack": 300,
  "defense": 300,
  "height": 0.5
}

```

## Atualização do Pikachu (Etapa 7)

```
MacBook-Pro-de-Guilherme(mongod-3.2.1) be-mean-pokemons> poke.description = "Descrição alterada"
Descrição alterada
MacBook-Pro-de-Guilherme(mongod-3.2.1) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 124ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

```