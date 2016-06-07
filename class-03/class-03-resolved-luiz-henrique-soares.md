# MongoDB - Aula 03 - Exercício
autor: Luiz Henrique Soares

## Listando Pokemons com altura menor que 0.5 (Passo 1)
```
> var query = {height: {$lt: 0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("5755e80f2f92092e978764fa"), "name" : "Caterpie", "description" : "Caterpie has a voracious appetite. It can devour leaves bigger than its body right before your eyes. From its antenna, this Pokémon releases a terrifically strong odor.", "attack" : 200, "defense" : 200, "height" : 0.3 }
```

## Listando Pokemons com altura maior ou igual que 0.5 (Passo 2)
```
> var query = {height: {$gte: 0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("5755e6c091e61aa6dbc5c10b"), "name" : "Bulbasaur", "description" : "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.", "attack" : 300, "defense" : 200, "height" : 0.7 }
{ "_id" : ObjectId("5755e7cb2f92092e978764f7"), "name" : "Abra", "description" : "Abra sleeps for eighteen hours a day. However, it can sense the presence of foes even while it is sleeping. In such a situation, this Pokémon immediately teleports to safety.", "attack" : 100, "defense" : 100, "height" : 0.9 }
{ "_id" : ObjectId("5755e7e62f92092e978764f8"), "name" : "Charmander", "description" : "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.", "attack" : 300, "defense" : 200, "height" : 0.6 }
{ "_id" : ObjectId("5755e8022f92092e978764f9"), "name" : "Squirtle", "description" : "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.", "attack" : 300, "defense" : 300, "height" : 0.5 }
```

## Listando Pokemons com altura menor ou igual que 0.5 E do tipo grama (Passo 3)
```
> var query = {$and: [{height: {$lte: 0.5}},{type: "grama"}] }
> query
{
        "$and" : [
                {
                        "height" : {
                                "$lte" : 0.5
                        }
                },
                {
                        "type" : "grama"
                }
        ]
}
> db.pokemons.find(query)
{ "_id" : ObjectId("57268e9579836121bc5d265c"), "name" : "Ivysaur", "description" : "There is a bud on this Pokémon's back", "attack" : 3, "defense" : 3, "height" : 0.4, "type" : "grama" }

```

## Listando Pokemons com o name 'Pìkachu' OU com attack menor ou igual que 0.5 (Passo 4)
```
> var query = { $or: [ {name: "Pikachu"}, {attack : {$lte: 0.5}} ]  }
> query
{
        "$or" : [
                {
                        "name" : "Pikachu"
                },
                {
                        "attack" : {
                                "$lte" : 0.5
                        }
                }
        ]
}
> db.pokemons.find(query)
>
```

## Listando Pokemons com attack maior ou igual que 48 E com altura menor ou igual que 0.5 (Passo 5)
```
> var query = { $and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]  }
> query
{
        "$and" : [
                {
                        "attack" : {
                                "$gte" : 48
                        }
                },
                {
                        "height" : {
                                "$lte" : 0.5
                        }
                }
        ]
}
> db.pokemons.find(query)
>
```
