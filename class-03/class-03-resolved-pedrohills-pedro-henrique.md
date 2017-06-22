# MongoDB - Aula 03 - Exercício
autor: Pedro Henrique

## Liste todos Pokemons com a altura **menor que** 0.5;
```
> var query = {height: {$lt: 0.5}}
> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("564291b535f1b5fe4ead743f"),
        "name" : "Charmander",
        "description" : "Um pokémon de fogo muito forte",
        "attack" : 40,
        "defense" : 35,
        "height" : 0.4
}
{
        "_id" : ObjectId("564291b535f1b5fe4ead7440"),
        "name" : "Squirtle",
        "description" : "Um pokémon de água muito forte",
        "attack" : 37,
        "defense" : 30,
        "height" : 0.3
}
{
        "_id" : ObjectId("564291b535f1b5fe4ead7441"),
        "name" : "Bulbasauro",
        "description" : "Um pokémon de planta muito forte",
        "attack" : 45,
        "defense" : 28,
        "height" : 0.4
}
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
> var query = {height: {$gte: 0.5}}
> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("564291b535f1b5fe4ead743e"),
        "name" : "Pikachu",
        "description" : "Descrição editada, porém, continua sendo um pokémon de choque muito forte.",
        "attack" : 35,
        "defense" : 40,
        "height" : 0.5
}
{
        "_id" : ObjectId("564291b535f1b5fe4ead7442"),
        "name" : "Pidgey",
        "description" : "Um pokémon de vento muito forte",
        "attack" : 30,
        "defense" : 50,
        "height" : 0.5
}
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama (PS: Não cadastrei o atributo type nos pokemons, por isso não retornou nada...)
```
> var query1 = {height: {$lte: 0.5}}
> var query2 = {type: "grama"}
> db.pokemons.find({$and: [query1, query2]}).pretty()
```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```
> var query = {name: "Pikachu", $or: [{attack: {$lte: 0.5}}]}
> db.pokemons.find(query).pretty()
```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```
> var query1 = {attack: {$gte: 48}}
> var query2 = {height: {$lte: 0.5}}
> db.pokemons.find({$and: [query1, query2]}).pretty()
```

# Por conta própria
## Liste todos os Pokemons do banco
```
> db.pokemons.find().pretty()
{
        "_id" : ObjectId("564291b535f1b5fe4ead743e"),
        "name" : "Pikachu",
        "description" : "Descrição editada, porém, continua sendo um pokémon de choque muito forte.",
        "attack" : 35,
        "defense" : 40,
        "height" : 0.5
}
{
        "_id" : ObjectId("564291b535f1b5fe4ead743f"),
        "name" : "Charmander",
        "description" : "Um pokémon de fogo muito forte",
        "attack" : 40,
        "defense" : 35,
        "height" : 0.4
}
{
        "_id" : ObjectId("564291b535f1b5fe4ead7440"),
        "name" : "Squirtle",
        "description" : "Um pokémon de água muito forte",
        "attack" : 37,
        "defense" : 30,
        "height" : 0.3
}
{
        "_id" : ObjectId("564291b535f1b5fe4ead7441"),
        "name" : "Bulbasauro",
        "description" : "Um pokémon de planta muito forte",
        "attack" : 45,
        "defense" : 28,
        "height" : 0.4
}
{
        "_id" : ObjectId("564291b535f1b5fe4ead7442"),
        "name" : "Pidgey",
        "description" : "Um pokémon de vento muito forte",
        "attack" : 30,
        "defense" : 50,
        "height" : 0.5
}
```