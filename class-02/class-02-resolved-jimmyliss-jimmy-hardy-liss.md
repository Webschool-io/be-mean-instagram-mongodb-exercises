# MongoDB - Aula 02 - Exercício
autor: JIMMY HARDY LISS

## Criando uma database chamada be-mean-pokemons
```
> use be-mean-pokemons
switched to db be-mean-pokemons
> db
be-mean-pokemons
```
## Listando databases nesse servidor
```
> show dbs
be-mean            0.005GB
be-mean-instagram  0.000GB
local              0.000GB
```
## Listando coleções nessa database
```
> show collections
>
```
## Inserindo 5 pokemons
```
> var pokemon = {name: "Bulbasaur", description: "Bulbasaur can be seen napping in bright sunlight", attack: 3, defense: 2, height: 2.04}
> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })
> var pokemon = {name: "Charmander", description: "The flame that burns at the tip of its tail is an indication of its emotions", attack: 3, defense: 2, height: 2.00}
> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })
> var pokemon = {name: "Pidgeot",description: "This Pokémon has a dazzling plumage of beautifully glossy feathers.",type: "Normal", attack:67, defense:69, height:1.5}
> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })
> var pokemon = {name: "Caterpie", description: "Caterpie has a voracious appetite. It can devour leaves bigger than its body right before your eyes. From its antenna, this Pokémon releases a terrific ally strong odor.", attack: 200, defense: 200, height: 0.3}
> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })
> var pokemon = {name: "Abra", description: "Abra sleeps for eighteen hours a day. However, it can sense the presence of foes even while it is sleeping. In such a situation, this Pokémon immediately teleports to safety.", attack: 100, defense: 100, height: 0.9}
> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })
>
```
## Listando os pokemons da coleção
```
> db.pokemons.find()
{ "_id" : ObjectId("57c03bc79511bc8d116874c2"), "name" : "Bulbasaur", "description" : "Bulbasaur can be seen napping in bright sunlight", "attack" : 3, "defense" : 2, "height" : 2.04 }
{ "_id" : ObjectId("57c03bfc9511bc8d116874c3"), "name" : "Charmander", "description" : "The flame that burns at the tip of its tail is an indication of its emotions", "attack" : 3, "defense" : 2, "height" : 2 }
{ "_id" : ObjectId("57c03c979511bc8d116874c4"), "name" : "Pidgeot", "description" : "This Pokémon has a dazzling plumage of beautifully glossy feathers.", "type" : "Normal", "attack" : 67, "defense" : 69, "height" : 1.5 }
{ "_id" : ObjectId("57c03d0b9511bc8d116874c5"), "name" : "Caterpie", "description" : "Caterpie has a voracious appetite. It can devour leaves bigger than its body right before your eyes. From its antenna, this Pokémon releases a terrifically strong odor.", "attack" : 200, "defense" : 200, "height" : 0.3 }
{ "_id" : ObjectId("57c03d3c9511bc8d116874c6"), "name" : "Abra", "description" : "Abra sleeps for eighteen hours a day. However, it can sense the presence of foes even while it is sleeping. In such a situation, this Pokémon immediately teleports to safety.", "attack" : 100, "defense" : 100, "height" : 0.9 }
>
```
## Buscando pokemons pelo nome e armazenando na variável _poke_
```
> var query = {name: "Abra"}
> var poke = db.pokemons.findOne(query)
> poke
{
        "_id" : ObjectId("57c03d3c9511bc8d116874c6"),
        "name" : "Abra",
        "description" : "Abra sleeps for eighteen hours a day. However, it can sense the presence of foes even while it is sleeping. In such a situation, this Pokémon immediately teleports to safety."
,
        "attack" : 100,
        "defense" : 100,
        "height" : 0.9
}
>
```
## Modificando a description e salvando
```
> poke.description =   "Abra dorme durante dezoito horas por dia. No entanto, ele pode sentir a presença de inimigos, mesmo enquanto ele está dormindo. Em tal situação, este Pokémon teletransporta imediatamente para ficar em segurança"
Abra dorme durante dezoito horas por dia. No entanto, ele pode sentir a presença de inimigos, mesmo enquanto ele está dormindo. Em tal situação, este Pokémon teletransporta imediatamente para ficar em segurança
> db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
>
> poke
{
        "_id" : ObjectId("57c03d3c9511bc8d116874c6"),
        "name" : "Abra",
        "description" : "Abra dorme durante dezoito horas por dia. No entanto, ele pode sentir a presença de inimigos, mesmo enquanto ele está dormindo. Em tal situação, este Pokémon teletransporta imediatamente para ficar em segurança",
        "attack" : 100,
        "defense" : 100,
        "height" : 0.9
}
>
```