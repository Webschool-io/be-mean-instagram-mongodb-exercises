# MongoDb - Aula 02 - Exercício
autor: Alessandro barreto

## Crie uma database chamada be-mean-pokemons;

```

> use be-mean-pokemons
switched to db be-mean-pokemons
>

```
## Liste quais databases você possui nesse servidor;

```

> show dbs
be-mean           0.078GB
local             0.078GB
>

```
## Liste quais coleções você possui nessa database;

```

> show collections
>

```

## Insira pelo menos 5 pokemons A SUA ESCOLHA;

```

> var p1 = {name: "Bulbasaur", description: "Bulbasaur can be seen napping in bright sunlight", attack: 3, defense: 2, height: 2.04}
> db.pokemons.insert(p1)
WriteResult({ "nInserted" : 1 })
> var p2 = {name: "Ivysaur", description: "There is a bud on this Pokémon's back", attack: 3, defense: 3, height: 3.03}
> db.pokemons.insert(p2)
WriteResult({ "nInserted" : 1 })
> var p3 = {name: "Venusaur", description: "There is a large flower on Venusaur's back", attack: 4, defense: 4, height: 6.07}
> db.pokemons.insert(p3)
WriteResult({ "nInserted" : 1 })
> var p4 = {name: "Charmander", description: "The flame that burns at the tip of its tail is an indication of its emotions", attack: 3, defense: 2, height: 2.00}
> db.pokemons.insert(p4)
WriteResult({ "nInserted" : 1 })
> var p5 = {name: "Charmeleon", description: "Charmeleon mercilessly destroys its foes using its sharp claws", attack: 3, defense: 3, height: 3.07}
> db.pokemons.insert(p5)
WriteResult({ "nInserted" : 1 })

```

## Liste os pokemons existentes na sua coleção;

```

> db.pokemons.find() {
  "_id": ObjectId("575f6ef44d619e056552f51a"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight",
  "attack": 3,
  "defense": 2,
  "height": 2.04
} {
  "_id": ObjectId("575f6f064d619e056552f51b"),
  "name": "Ivysaur",
  "description": "There is a bud on this Pokémon's back",
  "attack": 3,
  "defense": 3,
  "height": 3.03
} {
  "_id": ObjectId("575f6f104d619e056552f51c"),
  "name": "Venusaur",
  "description": "There is a large flower on Venusaur's back",
  "attack": 4,
  "defense": 4,
  "height": 6.07
} {
  "_id": ObjectId("575f6f1a4d619e056552f51d"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions",
  "attack": 3,
  "defense": 2,
  "height": 2
} {
  "_id": ObjectId("575f6f214d619e056552f51e"),
  "name": "Charmeleon",
  "description": "Charmeleon mercilessly destroys its foes using its sharp claws",
  "attack": 3,
  "defense": 3,
  "height": 3.07
}


```

## Busque o pokemon da sua escolha, pelo nome, e armazene-o em uma variável chamada poke;

```

> var q = {name:"Bulbasaur"}
> var poke = db.pokemons.findOne(q)
> poke
{
        "_id" : ObjectId("575f6ef44d619e056552f51a"),
        "name" : "Bulbasaur",
        "description" : "Bulbasaur can be seen napping in bright sunlight",
        "attack" : 3,
        "defense" : 2,
        "height" : 2.04
}

```

## Modifique sua description e salvê-o;

```

> poke.description = "Modificando a descricao"
Modificando a descricao
> db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })

```
