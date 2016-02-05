## 1. Importar as collections restaurantes e pokemons
```
~$ mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file pokemons.json

~$ mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file restaurantes.json 


```


## 2. Distinct por `cuisine` na restaurantes
``
```
m0nk3y(mongod-3.0.7) be-mean> db.restaurantes.distinct('cuisine');
```

## 3. Distinct por `types` na pokemons
```
m0nk3y(mongod-3.0.7) be-mean> db.pokemons.distinct('types');

```

## 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)
```
m0nk3y(mongod-3.0.7) be-mean> db.pokemons.find().limit(5).skip(5)
m0nk3y(mongod-3.0.7) be-mean> db.pokemons.find().limit(5).skip(10)
m0nk3y(mongod-3.0.7) be-mean> db.pokemons.find().limit(5).skip(15)
```

## 5 . Group ou Aggregate contando a quantidade de pokemons de cada tipo
```

m0nk3y(mongod-3.0.7) be-mean> db.pokemons.aggregate([
	{ $unwind: '$types' },
	{ $group: {
		_id: '$types',
		count: { $sum: 1 }
		}
	}
	]);	

```

## 6. Realizar 3 counts na pokemons.
m0nk3y(mongod-3.0.7) be-mean>  db.pokemons.count()
m0nk3y(mongod-3.0.7) be-mean> db.pokemons.count({types: 'fire'})
m0nk3y(mongod-3.0.7) be-mean> db.pokemons.count({attack:{$gt:70}})
