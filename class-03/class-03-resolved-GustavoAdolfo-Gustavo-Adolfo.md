# MongoDB - Aula 03 - Exercício
autor: Gustavo Adolfo gustavo.adolfo.as@gmail.com

## Liste todos Pokemons com a altura **menor que** 0.5;
```
> var query = {'height':{$lt:0.5}};
> db.pokemons.find(query);
{ "_id" : ObjectId("56c860be06d4893022ac072c"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 100, "height" : 0.4 }
{ "_id" : ObjectId("56c860be06d4893022ac072d"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }
{ "_id" : ObjectId("56c860be06d4893022ac0730"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3 }
>

```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
> var query = {'height':{$gte:0.5}};
> db.pokemons.find(query);
{ "_id" : ObjectId("56c860be06d4893022ac072e"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6 }
{ "_id" : ObjectId("56c860be06d4893022ac072f"), "name" : "Squirtle", "description" : "Pokemon mijão", "type" : "água", "attack" : 48, "height" : 0.5 }
>
```


## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```
> query = { $and : [ { 'height' : { $lte : 0.5 } }, { 'type' : 'grama' } ] };
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
{ "_id" : ObjectId("56c860be06d4893022ac072d"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }
>

```


## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```
> query = { $or : [ { 'name' : 'Pikachu' }, { 'attack' : {$lte : 0.5 } } ] };
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
> db.pokemons.find(query);
{ "_id" : ObjectId("56c860be06d4893022ac072c"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 100, "height" : 0.4 }
>

```


## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```
> query = { $and : [ { 'height' : { $lte : 0.t } }, { 'attack' : {$gte : 48 } } ] };
2016-02-21T12:05:21.315-0300 E QUERY    [thread1] SyntaxError: identifier starts immediately after numeric literal @(shell):1:41

> db.pokemons.find(query);
{ "_id" : ObjectId("56c860be06d4893022ac072c"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 100, "height" : 0.4 }
>

```
