# MongoDB - Aula 03 - Exercício
autor: Ely Richardson

## Liste todos Pokemons com a altura **menor que** 0.5;

> var query = {height:{$lt:0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("5644923acf5faf88f1c1cebb"), "name" : "Blastoise", "description" : "deu trabalho para encontrar", "type" : "water", "attack" : 83, "height" : 0.4 }
{ "_id" : ObjectId("56449246cf5faf88f1c1cebc"), "name" : "Caterpie", "description" : "deu trabalho para encontrar", "type" : "bug", "attack" : 30, "height" : 0.3 }

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

> var query = {height:{$gte:0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("56449212cf5faf88f1c1ceb8"), "name" : "Magnemite", "description" : "deu trabalho para encontrar", "type" : "electric", "attack" : 35, "height" : 0.6 }
{ "_id" : ObjectId("56449222cf5faf88f1c1ceb9"), "name" : "Gastly", "description" : "deu trabalho para encontrar", "type" : "ghost", "attack" : 35, "height" : 0.6 }
{ "_id" : ObjectId("5644922dcf5faf88f1c1ceba"), "name" : "Ivysaur", "description" : "deu trabalho para encontrar", "type" : "grass", "attack" : 62, "height" : 0.7 }
{ "_id" : ObjectId("56449258cf5faf88f1c1cebd"), "name" : "Pidgeotto", "description" : "deu trabalho para encontrar", "type" : "normal", "attack" : 60, "height" : 0.6 }
{ "_id" : ObjectId("56449263cf5faf88f1c1cebe"), "name" : "Raichu", "description" : "descricao alterada", "type" : "electric", "attack" : 90, "height" : 0.6 }

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama

> var query = {$and:[{height:{$lte:0.5}},{type:"grama"}]}
> db.pokemons.find(query)
> 

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

> var query = {$or:[{name: "Pikachu"}, {attack:{$lte:0.5}}]}
> db.pokemons.find(query)
>

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

> var query = {$and:[{attack:{$gte:48}},{height:{$lte:0.5}}]}
> db.pokemons.find(query)
{ "_id" : ObjectId("5644923acf5faf88f1c1cebb"), "name" : "Blastoise", "description" : "deu trabalho para encontrar", "type" : "water", "attack" : 83, "height" : 0.4 }
> 

