## 1. Importar as collections restaurantes e pokemons
```
mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file ~/javascript/mean/pokemons.json

 mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file ~/javascript/mean/restaurantes.json 


```


## 2. Distinct por `cuisine` na restaurantes
```
db.restaurantes.distinct('cuisine')
```

## 3. Distinct por `types` na pokemons
```
db.pokemons.distinct('types')
```

## 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)
```
db.pokemons.find().limit(5).skip(5)
db.pokemons.find().limit(5).skip(10)
db.pokemons.find().limit(5).skip(15)
```

## 5 . Group ou Aggregate contando a quantidade de pokemons de cada tipo
```

db.pokemons.aggregate([
	{ $unwind: '$types' },
	{ $group: {
		_id: '$types',
		count: { $sum: 1 }
		}
	}
	]);	

[
  {
    "total" : 796,
    "fire" : 41,
    "water" : 92,
    "bug" : 54,
    "flying" : 67,
    "normal" : 59,
    "steel" : 37,
    "electric" : 31,
    "poison" : 45,
    "ice" : 21,
    "fighting" : 33,
    "grass" : 67,
    "ground" : 47,
    "fairy" : 21,
    "psychic" : 55,
    "rock" : 45,
    "dark" : 30,
    "dragon" : 20,
    "ghost" : 31
  }
]
```

## 6. Realizar 3 counts na pokemons.
db.pokemons.count()
db.pokemons.count({types: 'fire'})
db.pokemons.count({attack:{$gt:70}})
