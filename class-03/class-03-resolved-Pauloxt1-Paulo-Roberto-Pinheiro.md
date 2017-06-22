# MongoDB - Aula 03 - Exercício
Autor: Paulo Roberto

## Liste todos Pokemons com a altura **menor que** 0.5
```
> var query = {height: {$lt: 0.5}}
> db.pokemons.find(query)

{ "_id" : ObjectId("567ae99e38081f084b27fc7e"), "description" : "Rato elétrico bem fofinho", 
"type" : "eletric", "attack" : 55, "height" : 0.4, "name" : "Pikachu" }

{ "_id" : ObjectId("567aeac938081f084b27fc7f"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", 
"type" : "grama", "attack" : 49, "height" : 0.4}

{ "_id" : ObjectId("567af1c138081f084b27fc82"), "name" : "Caterpie", "description" : "Larva lutadora", 
"type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35 }
```
## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
> var query = {height: {$gte: 0.5}}
> db.pokemons.find(query)

{ "_id" : ObjectId("567aeadc38081f084b27fc80"), "name" : "Charmander", "description" : "Esse é o cão chupando manga fofinho", 
"type" : "fogo", "attack" : 52, "height" : 0.6 }

{ "_id" : ObjectId("567aeae838081f084b27fc81"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", 
"type" : "água", "attack" : 48, "height" : 0.5 }
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```
> var query = {$and:[{height:{$lte:0.5}}, {type:'grama'}]}
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

{ "_id" : ObjectId("567aeac938081f084b27fc7f"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", 
"type" : "grama", "attack" : 49, "height" : 0.4}
```
## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```
> var query = {$or:[{attack:{$lte:0.5}}, {name:'Pikachu'}]}
> db.pokemons.find(query)

{ "_id" : ObjectId("567ae99e38081f084b27fc7e"), "description" : "Rato elétrico bem fofinho",
"type" : "eletric", "attack" : 55, "height" : 0.4, "name" : "Pikachu" }
```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```
> var query = {$and:[{attack:{$gte:48}}, {height:{$lte:0.5}}]}
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

{ "_id" : ObjectId("567ae99e38081f084b27fc7e"), "description" : "Rato elétrico bem fofinho", 
"type" : "eletric", "attack" : 55, "height" : 0.4, "name" : "Pikachu" }

{ "_id" : ObjectId("567aeac938081f084b27fc7f"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", 
"type" : "grama", "attack" : 49, "height" : 0.4}

{ "_id" : ObjectId("567aeae838081f084b27fc81"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", 
"type" : "água", "attack" : 48, "height" : 0.5 }
```

