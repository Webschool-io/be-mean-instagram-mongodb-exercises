# MongoDB - Aula 03 - Exercício
autor: Felipe Leão

## Liste todos Pokemons com a altura menor que 0.5

```
> var query = {height: {$lt: 0.5}}
> db.pokemons.find(query)
```

## Liste todos Pokemons com a altura maior ou igual que 0.5

```
> var query = {height: {$gte: 0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("5647aab44d79adb38b688cdc"), "name" : "Voltorb", "description" : "Pokemon sinistro.", "attack" : 30, "defense" : 50, "height" : 5 }
{ "_id" : ObjectId("5647ab884d79adb38b688cdd"), "name" : "Weezing", "description" : "Bacana demais", "attack" : 90, "defense" : 120, "height" : 12 }
{ "_id" : ObjectId("5647abe44d79adb38b688cde"), "name" : "Butterfree", "description" : "Voa e tudo mais", "attack" : 45, "defense" : 50, "height" : 11 }
{ "_id" : ObjectId("5647ac314d79adb38b688cdf"), "name" : "Pidgey", "description" : "Parece um pardal", "attack" : 45, "defense" : 40, "height" : 3 }
{ "_id" : ObjectId("5647ac894d79adb38b688ce0"), "name" : "Ekans", "description" : "Cobra", "attack" : 60, "defense" : 44, "height" : 20 }
```

## Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama

```
> var query = {$and: [{height: {$lte: 0.5}},{tipo: 'grama'}]}
> db.pokemons.find(query)
```

## Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5

```
> var query = {$or : [{name: 'Pikachu'},{attack: {$lte: 0.5}}]}
> db.pokemons.find(query)
```

## Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5

```
> var query = {$and : [{attack: {$gte: 48}},{height: {$lte : 0.5}}]}
> db.pokemons.find(query)
```