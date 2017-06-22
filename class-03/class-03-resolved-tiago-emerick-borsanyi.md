# Liste todos Pokemons com a altura menor que 0.5;

  ```
 db.pokemons.find()
{ "_id" : ObjectId("5643a0fd0de0851ffeecb67a"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4 }
{ "_id" : ObjectId("5643a79b5c013fb08a6d5b2e"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }
{ "_id" : ObjectId("5643a79b5c013fb08a6d5b2f"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6 }
{ "_id" : ObjectId("5643a79b5c013fb08a6d5b30"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5 }
{ "_id" : ObjectId("5643aa429f927bdc79712d88"), "name" : "Pidgeotto", "description" : "Garras mega foda", "type" : "Brird", "attack" : 58, "height" : 0.9 }
{ "_id" : ObjectId("5643aa429f927bdc79712d89"), "name" : "Kakuna", "description" : "Poderes da cevada", "type" : "cocoon", "attack" : 28, "height" : 0.7 }
{ "_id" : ObjectId("5643aa429f927bdc79712d8a"), "name" : "Venusaur", "description" : "Meio dinossauro com água de coco pra colocar no wisk", "attack" : 60, "height" : 10.6 }
```

# Liste todos Pokemons com a altura maior ou igual que 0.5;

```
> query = {height: {$gte: 0.5}}
{ "height" : { "$gte" : 0.5 } }
> db.pokemons.find(query)
{ "_id" : ObjectId("5643a79b5c013fb08a6d5b2f"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6 }
{ "_id" : ObjectId("5643a79b5c013fb08a6d5b30"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5 }
{ "_id" : ObjectId("5643aa429f927bdc79712d88"), "name" : "Pidgeotto", "description" : "Garras mega foda", "type" : "Brird", "attack" : 58, "height" : 0.9 }
{ "_id" : ObjectId("5643aa429f927bdc79712d89"), "name" : "Kakuna", "description" : "Poderes da cevada", "type" : "cocoon", "attack" : 28, "height" : 0.7 }
{ "_id" : ObjectId("5643aa429f927bdc79712d8a"), "name" : "Venusaur", "description" : "Meio dinossauro com água de coco pra colocar no wisk", "attack" : 60, "height" : 10.6 }
```

# Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama;

```
> var query1 = {height: {$lte: 0.5}}
> var query2 = {type: 'grama'}
> db.pokemons.find({$and: [query1, query2]})
{ "_id" : ObjectId("5643a79b5c013fb08a6d5b2e"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }
```
# Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5;

```
> var query1 = {name: 'Pikachu'}
> var query2 = {attack: {$lte: 0.5}}
> db.pokemons.find({$or: [query1, query2]})
{ "_id" : ObjectId("5643a0fd0de0851ffeecb67a"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4 }
```
# Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5

```
> var query1 = {attack: {$gte: 48}}
> var query2 = {height: {$lte: 0.5}}
> db.pokemons.find({$and: [query1, query2]})
{ "_id" : ObjectId("5643a0fd0de0851ffeecb67a"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4 }
{ "_id" : ObjectId("5643a79b5c013fb08a6d5b2e"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }
{ "_id" : ObjectId("5643a79b5c013fb08a6d5b30"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5 }
```
