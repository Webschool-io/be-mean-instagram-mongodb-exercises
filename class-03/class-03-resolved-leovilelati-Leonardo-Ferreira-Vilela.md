# MongoDB - Aula 03 - Exercício
autor: Leonardo Ferreira Vilela

## Liste todos Pokemons com a altura **menor que** 0.5;
```
> var query = {'height': {$lt: 0.5}};
> db.pokemons.find(query);
{ "_id" : ObjectId("564be0166c04f578f355b78d"), "name" : "SoujiroMon", "descript
ion" : "Bicho bunito de papai", "attack" : 20, "defense" : 30, "height" : 0.4, "
type" : "grama" }
{ "_id" : ObjectId("564be0166c04f578f355b790"), "name" : "Metapod", "description
" : "Que bicho mais estranho", "attack" : 60, "defense" : 10, "height" : 0.1, "t
ype" : "fogo" }

```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
> var query = {'height': {$gte:0.5}};
> db.pokemons.find(query)
{ "_id" : ObjectId("564be0166c04f578f355b78e"), "name" : "Charmander", "descript
ion" : "Bichinho fofinho", "attack" : 40, "defense" : 50, "height" : 0.6, "type"
 : "fogo" }
{ "_id" : ObjectId("564be0166c04f578f355b78f"), "name" : "Charizard", "descripti
on" : "Top demais", "attack" : 50, "defense" : 80, "height" : 0.6, "type" : "Agu
a" }
{ "_id" : ObjectId("564be0166c04f578f355b791"), "name" : "Weedle", "description"
 : "Este document foi aletrado.", "attack" : 40, "defense" : 80, "height" : 0.5,
 "type" : "grama" }
```


## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```
> var query = { $and: [ {'height':{$lte: 0.5}}, {'type':'grama'}]  }
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
> db.pokemons.find(query);
{ "_id" : ObjectId("564be0166c04f578f355b78d"), "name" : "SoujiroMon", "descript
ion" : "Bicho bunito de papai", "attack" : 20, "defense" : 30, "height" : 0.4, "
type" : "grama" }
{ "_id" : ObjectId("564be0166c04f578f355b791"), "name" : "Weedle", "description"
 : "Este document foi aletrado.", "attack" : 40, "defense" : 80, "height" : 0.5,
 "type" : "grama" }
>

```


## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```
> var query = { $or: [ { 'name': 'pikachu'}, {'attack': { $lte:0.5}}]  }
> db.pokemons.find(query);

```


## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```
> var query =  { $and:[ {'attack': {$gte:48}}, {height: {$lte:0.5}}] }
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
> db.pokemons.find(query);
{ "_id" : ObjectId("564be0166c04f578f355b790"), "name" : "Metapod", "description
" : "Que bicho mais estranho", "attack" : 60, "defense" : 10, "height" : 0.1, "t
ype" : "fogo" }

```
