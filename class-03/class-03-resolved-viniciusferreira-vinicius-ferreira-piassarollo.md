# MongoDB - Aula 03 - Exercício
autor: VINICIUS FERREIRA PIASSAROLLO 

## Liste todos Pokemons com a altura **menor que** 0.5;

```
MacBook-Pro-de-vinicius(mongod-3.0.4) be-be-mean-pokemons> var query = {height: {$lt:0.5}}; db.pokemons.find(query);
{
  "_id": ObjectId("564500af1dda97189e69dd23"),
  "name": "KankRaxixeHaker",
  "description": " It stays still because it is prepared.",
  "attack": 46,
  "defense": 15,
  "height": 0.2
}
Fetched 1 record(s) in 6ms
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
MacBook-Pro-de-vinicius(mongod-3.0.4) be-be-mean-pokemons> var query = {height: {$lte:0.5}}; db.pokemons.find(query);
{
  "_id": ObjectId("564500af1dda97189e69dd23"),
  "name": "KankRaxixeHaker",
  "description": " It stays still because it is prepared.",
  "attack": 46,
  "defense": 15,
  "height": 0.2
}
Fetched 1 record(s) in 37ms

```


## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```
MacBook-Pro-de-vinicius(mongod-3.0.4) be-mean-pokemons> var query = {$and: [{ height:{ $gte:0.5 } } , { type: "grama" } ]}
MacBook-Pro-de-vinicius(mongod-3.0.4) be-mean-pokemons> db.pokemons.find(query);
Fetched 0 record(s) in 1ms

```


## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```
MacBook-Pro-de-vinicius(mongod-3.0.4) be-mean-pokemons> var query = {$or: [{name:"Pikachu"}, { attack:{$lte:0.5}}]}
MacBook-Pro-de-vinicius(mongod-3.0.4) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```


## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```
acBook-Pro-de-vinicius(mongod-3.0.4) be-mean-pokemons> var query = {$or: [{name:"Pikachu"}, { attack:{$lte:0.5}}]}
MacBook-Pro-de-vinicius(mongod-3.0.4) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564500af1dda97189e69dd23"),
  "name": "KankRaxixeHaker",
  "description": " It stays still because it is prepared.",
  "attack": 48,
  "defense": 15,
  "height": 0.2
}
Fetched 1 record(s) in 37ms

```