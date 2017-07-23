# MongoDB - Aula 03 - Exercício
autor: Augusto Cesar Vieira Formentão


## 1. Liste todos Pokemons com a altura menor que 0.5;

```
> var value = 0.5
> var alturamenorque = {height: {$lt: value}}
>db.pokemons.find(alturamenorque)
{ 	"_id" : ObjectId("5643fa05fe1647e46ab2a82e"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4 }
{ 	"_id" : ObjectId("5643fca5fe1647e46ab2a82f"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }
{   "_id" : ObjectId("5643fe49fe1647e46ab2a832"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35 }

```

## 2. Liste todos Pokemons com a altura maior ou igual que 0.5;

```
> var value = 0.5
> var query = {height: {$gte: value}}
> db.pokemons.find(query)
{ "_id" : ObjectId("5643fcedfe1647e46ab2a830"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6 }
{ "_id" : ObjectId("5643fd3efe1647e46ab2a831"), "name" : "Squirtle", "description" : "Ejeta agua que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5 }


```

## 3. Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama;

```
    > var value = 0.5
    > var query1 = {height : {$lte : value}}
    > var query2 = {type : "grama"}
    > db.pokemons.find({$and : [query1, query2]})

```

## 4. Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5;

```
> var query1 = {name: 'Pikachu'}
> var query2 = {attack:{$lte:0.5}}
> db.pokemons.find({$or:[query1,query2]})
{ "_id" : ObjectId("5643fa05fe1647e46ab2a82e"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" :0.4 }

```

## 5. Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5;

```
> var query1 = {attack: {$gte:48}}
> var query2 = {height:{$lte:0.5}}
> db.pokemons.find({$and:[query1, query2]})
{ "_id" : ObjectId("5643fa05fe1647e46ab2a82e"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" :0.4 }
{ "_id" : ObjectId("5643fca5fe1647e46ab2a82f"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }
{ "_id" : ObjectId("5643fd3efe1647e46ab2a831"), "name" : "Squirtle", "description" : "Ejeta agua que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5 }

```