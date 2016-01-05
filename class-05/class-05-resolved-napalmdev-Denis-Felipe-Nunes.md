# MongoDB - Aula 05 - Exercício
autor: Dênis Nunes


##1. Importar as collections restaurantes e pokemons.

```js
   mongoimport -d be-mean -c restaurantes --drop --file restaurantes.json
   mongoimport -d be-mean -c pokedex --drop --file pokemons.json
```

##2. Distinct por cuisine na restaurantes.

```js
   db.restaurantes.distinct('cuisine');
```

##3- Distinct por types na pokemons.

```js
  db.pokedex.distinct('types');
```

##4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)

```js
  var limit = 5;
  db.pokedex.find().limit(limit).skip(limit * 0);
  db.pokedex.find().limit(limit).skip(limit * 1);
  db.pokedex.find().limit(limit).skip(limit * 2);
```



##5 . Group ou Aggregate contando a quantidade de pokemons de cada tipo

```js
  db.pokedex.aggregate([
    {$unwind: "$types"}, 
    {$group :{ 
      _id:"$types", 
      total: {$sum: 1}
      }
    }
  ]);
```

##6. Realizar 3 counts na pokemons.

```js
  db.pokedex.count({types:/fire/i});
  db.pokedex.count({attack: {$gt: 50}});
  db.pokedex.count({moves:/desvio/i});  
```