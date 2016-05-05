#MongoDB Aula 02 - Exercício
autor: Jefferson Luiz de Lima

## Crie uma database chamada be-mean-pokemons;

> use be-mean-pokemons

## Liste quais databases você possui nesse servidor;

> show dbs
be-mean           0.078GB
be-mean-pokemons  0.078GB
local             0.078GB
teste             0.078GB

## Liste quais coleções você possui nessa database;

> show collections
pokemons
system.indexes

## Insira pelo menos 5 pokemons A SUA ESCOLHA utilizando o mesmo padrão de campos utilizado: name, description, attack, defense e height;

> var pokemon1 = {'name':'Hitmonlee', 'description':'O demômio dos chutes', 'attack':'120', 'defense':'53', 'height':'4.11'}
>  db.pokemons.save(pokemon1)

> var pokemon2 ={'name':'Hitmonchan', 'description':'O demônio dos socos', 'attack':'105', 'defense':'79', 'height':'4.7'}
> db.pokemons.save(pokemon2)

> var pokemon3 ={'name':'Snorlax', 'description':'Pokemon dorminhoco', 'attack':'110', 'defense':'65', 'height':'6.11'}
> db.pokemons.save(pokemon3)

> var pokemon4 ={'name':'Pidgeotto', 'description':'Pardal boladão', 'attack':'60', 'defense':'55', 'height':'3.7'}
> db.pokemons.save(pokemon4)

> var pokemon5 ={'name':'Rattata', 'description':'Ratazana atentada', 'attack':'56', 'defense':'35', 'height':'1.0'}
> db.pokemons.save(pokemon5)

## Liste os pokemons existentes na sua coleção;

> var cur = db.pokemons.find()
> while(cur.hasNext()){print(tojson(cur.next()))}
{
        "_id" : ObjectId("564bc007a66154f771078f03"),
        "name" : "Hitmonlee",
        "description" : "O demômio dos chutes",
        "attack" : "120",
        "defense" : "53",
        "height" : "4.11"
}
{
        "_id" : ObjectId("564bc00da66154f771078f04"),
        "name" : "Hitmonchan",
        "description" : "O demônio dos socos",
        "attack" : "105",
        "defense" : "79",
        "height" : "4.7"
}
{
        "_id" : ObjectId("564bc013a66154f771078f05"),
        "name" : "Snorlax",
        "description" : "Pokemon dorminhoco",
        "attack" : "110",
        "defense" : "65",
        "height" : "6.11"
}
{
        "_id" : ObjectId("564bc017a66154f771078f06"),
        "name" : "Pidgeotto",
        "description" : "Pardal boladão",
        "attack" : "60",
        "defense" : "55",
        "height" : "3.7"
}
{
        "_id" : ObjectId("564bc01ba66154f771078f07"),
        "name" : "Rattata",
        "description" : "Ratazana atentada",
        "attack" : "56",
        "defense" : "35",
        "height" : "1.0"
}
>
## Busque o pokemon a sua escolha, pelo nome, e armazene-o em uma variável chamada `poke`;

> var query = {'name':'Hitmonchan'}
> var  poke = db.pokemons.findOne(query)

## Modifique sua `description` e salvê-o

> poke.description = 'Demônio dos socos, pique Mike Tyson'
Demônio dos socos, pique Mike Tyson
> db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> poke
{
        "_id" : ObjectId("564bc00da66154f771078f04"),
        "name" : "Hitmonchan",
        "description" : "Demônio dos socos, pique Mike Tyson",
        "attack" : "105",
        "defense" : "79",
        "height" : "4.7"
}