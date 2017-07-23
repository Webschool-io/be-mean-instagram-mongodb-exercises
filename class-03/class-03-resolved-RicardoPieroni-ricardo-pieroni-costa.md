## MongoDb Aula - 03

Autor: Ricardo Pieroni Costa

## 1. Liste todos Pokemons com a altura menor que 0.5
```
 var query = {height:{$lt:0.5}}
 db.pokemons.find(query)
{ "_id" : ObjectId("56facf4ff085eb276b1d94bd"), "nome" : "Caterpie", "description" : "Larva", "type" : "inseto", "atack"
 : 20, "height" : 0.3, "defense" : 20 }
{ "_id" : ObjectId("56fad0f5f085eb276b1d94be"), "nome" : "Pikachu", "description" : "bixa", "type" : "eletrico", "atack"
 : 50, "height" : 0.3, "defense" : 20 }
```
## 2. Liste todos Pokemons com a altura maior ou igual que 0.5
```
 var query = {height:{$gte:0.5}}
 db.pokemons.find(query)
{ "_id" : ObjectId("56f1f86073ed2430c3fed72b"), "nome" : "Charizard", "description" : "Lagartão do mangue", "type" : "fl
ame", "atack" : 60, "height" : 1.7, "defense" : 50 }
{ "_id" : ObjectId("56f28653cc5cba5a6e01385f"), "nome" : "Blastoise", "description" : "Cabeça das tartarugas", "type" :
"Shellfish", "atack" : 40, "height" : 1.6, "defense" : 50 }
{ "_id" : ObjectId("56f28746cc5cba5a6e013860"), "nome" : "Beedrill", "description" : "Abelha do CV", "type" : "Bug, pois
on", "atack" : 42, "height" : 1, "defense" : 30 }
{ "_id" : ObjectId("56f28862cc5cba5a6e013861"), "nome" : "Pidgeot", "description" : "Gavião", "type" : "Flying", "atack"
 : 38, "height" : 1.5, "defense" : 40 }
{ "_id" : ObjectId("56f288eecc5cba5a6e013862"), "nome" : "Sandslash", "description" : "Rato", "type" : "Ground", "atack"
 : 40, "height" : 1, "defense" : 45 }
{ "_id" : ObjectId("56facd2df085eb276b1d94bc"), "nome" : "Bulbasaur", "description" : "Javali", "type" : "grama", "atack
" : 50, "height" : 0.7, "defense" : 20 }


```
## 3. Liste todos Pokemons com a altura menor ou igual que 0.5 e do tipo grama
```

use be-mean-pokemons
switched to db be-mean-pokemons 
var query = {$and:[{height:{$lte:0.5}},{type:"grama"}]}
 query
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
 db.pokemons.find(query)
{ "_id" : ObjectId("56facf4ff085eb276b1d94bd"), "nome" : "Caterpie", "description" : "Larva", "type" : "grama", "atack"
: 0.4, "height" : 0.3, "defense" : 20 }

```
## 4. Liste todos Pokemons com o nome 'Pikachu' ou com attack menor ou igual que 0.5
```
 var query = {$or:[{atack:{$lte:0.5}},{nome:"Pikachu"}]}
 db.pokemons.find(query)
{ "_id" : ObjectId("56facf4ff085eb276b1d94bd"), "nome" : "Caterpie", "description" : "Larva", "type" : "grama", "atack"
: 0.4, "height" : 0.3, "defense" : 20 }
{ "_id" : ObjectId("56fad0f5f085eb276b1d94be"), "nome" : "Pikachu", "description" : "bixa", "type" : "eletrico", "atack"
 : 50, "height" : 0.3, "defense" : 20 }


```
## 5. Liste todos Pokemons com o attack maior ou igual que 48 e com height menor ou igual que 0.5
```

var query = {$and: [{height:{$lte:0.5}},{atack:{$gte:48}}]}
query
{
        "$and" : [
                {
                        "height" : {
                                "$lte" : 0.5
                        }
                },
                {
                        "atack" : {
                                "$gte" : 48
                        }
                }
        ]
}
db.pokemons.find(query)
{ "_id" : ObjectId("56fad0f5f085eb276b1d94be"), "nome" : "Pikachu", "description" : "bixa", "type" : "eletrico", "atack"
 : 50, "height" : 0.3, "defense" : 20 }


```