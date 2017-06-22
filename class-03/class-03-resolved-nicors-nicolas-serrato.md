# MongoDB - Aula 03 - Exercício
Autor: Nicolas Serrato

# Liste todos Pokemons com a altura menor que 0.5;

```
> var query = {height: {$lt: 0.5}}
> db.pokemons.find(query)
{
  "_id": ObjectId("587d2ab7a83165806b92aa90"),
  "attack": 56,
  "defense": 35,
  "description": "Normal",
  "height": 0.3,
  "name": "Rattatá"
}
Fetched 1 record(s) in 4ms
```
# Liste todos Pokemons com a altura maior ou igual que 0.5
```
> var query = {height: {$lte: 0.5}}
> db.pokemons.find(query)
{
  "_id": ObjectId("587d2ab7a83165806b92aa90"),
  "attack": 56,
  "defense": 35,
  "description": "Normal",
  "height": 0.3,
  "name": "Rattatá"
}
Fetched 1 record(s) in 4ms
```
# Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama
```
> var query = {$and: [{height: {$lte: 0.5}}, {type: /grama/}]}
> db.pokemons.find(query)
Fetched 0 record(s) in 41ms
```
# Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5

```
> var query = {$or: [{name: /Pikachu/}, {attack: {lte: 0.5}}]}
> db.pokemons.find(query)
Fetched 0 record(s) in 16ms
```
# Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5
```
> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
> db.pokemons.find(query)
{
  "_id": ObjectId("587d2ab7a83165806b92aa90"),
  "attack": 56,
  "defense": 35,
  "description": "Normal",
  "height": 0.3,
  "name": "Rattatá"
}
Fetched 1 record(s) in 4ms
```


