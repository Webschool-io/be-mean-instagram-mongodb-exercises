# MongoDB - Aula 05 - Exercício
autor: Vander Amorin

## 1. Importar as collections restaurantes e pokemons
```
mongoimport --db be_mean --collection pokemons --drop --file pokemons.json
2015-11-20T10:36:47.768-0200	connected to: localhost
2015-11-20T10:36:47.768-0200	dropping: be_mean.pokemons
2015-11-20T10:36:47.841-0200	imported 610 documents

mongoimport --db be_mean --collection restaurantes --drop --file restaurantes.json
2015-11-20T10:38:51.803-0200	connected to: localhost
2015-11-20T10:38:51.803-0200	dropping: be_mean.restaurantes
2015-11-20T10:38:53.985-0200	imported 25359 documents
```


## 2. Distinct por cuisine na restaurantes
```
be_mean> db.restaurantes.distinct('cuisine')
[
  "Bakery",
  "Hamburgers",
  "Irish",
  "American ",
  "Jewish/Kosher",
  "Delicatessen",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Other",
  "Chinese",
  "Chicken",
  "Turkish",
  "Caribbean",
  "Donuts",
  "Sandwiches/Salads/Mixed Buffet",
  "Bagels/Pretzels",
  "Continental",
  "Pizza",
  "Italian",
  "Steak",
  "Polish",
  "German",
  "French",
  "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
  "Pizza/Italian",
  "Mexican",
  "Spanish",
  "Café/Coffee/Tea",
  "Tex-Mex",
  "Pancakes/Waffles",
  "Soul Food",
  "Seafood",
  "Hotdogs",
  "Greek",
  "Not Listed/Not Applicable",
  "African",
  "Japanese",
  "Indian",
  "Armenian",
  "Thai",
  "Chinese/Cuban",
  "Mediterranean",
  "Korean",
  "Bottled beverages, including water, sodas, juices, etc.",
  "Russian",
  "Eastern European",
  "Middle Eastern",
  "Asian",
  "Ethiopian",
  "Vegetarian",
  "Barbecue",
  "Egyptian",
  "English",
  "Sandwiches",
  "Portuguese",
  "Indonesian",
  "Chinese/Japanese",
  "Filipino",
  "Juice, Smoothies, Fruit Salads",
  "Brazilian",
  "Afghan",
  "Vietnamese/Cambodian/Malaysia",
  "CafÃ©/Coffee/Tea",
  "Soups & Sandwiches",
  "Tapas",
  "Moroccan",
  "Pakistani",
  "Peruvian",
  "Bangladeshi",
  "Czech",
  "Salads",
  "Creole",
  "Fruits/Vegetables",
  "Iranian",
  "Cajun",
  "Scandinavian",
  "Polynesian",
  "Soups",
  "Australian",
  "Hotdogs/Pretzels",
  "Southwestern",
  "Nuts/Confectionary",
  "Hawaiian",
  "Creole/Cajun",
  "Californian",
  "Chilean"
]
```

## 3. Distinct por types na pokemons
```
be_mean> db.pokemons.distinct('types')
[
  "fire",
  "normal",
  "water",
  "bug",
  "flying",
  "poison",
  "electric",
  "steel",
  "ice",
  "ghost",
  "fighting",
  "psychic",
  "grass",
  "ground",
  "fairy",
  "rock",
  "dark",
  "dragon"
]
```

## 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)
```
be_mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 0)
{
  "name": "Charmander"
}
{
  "name": "Rattata"
}
{
  "name": "Charmeleon"
}
{
  "name": "Wartortle"
}
{
  "name": "Blastoise"
}
Fetched 5 record(s) in 1ms

be_mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 1)
{
  "name": "Caterpie"
}
{
  "name": "Metapod"
}
{
  "name": "Butterfree"
}
{
  "name": "Spearow"
}
{
  "name": "Kakuna"
}
Fetched 5 record(s) in 1ms

be_mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 2)
{
  "name": "Farfetchd"
}
{
  "name": "Magneton"
}
{
  "name": "Magnemite"
}
{
  "name": "Doduo"
}
{
  "name": "Seel"
}
Fetched 5 record(s) in 0ms
```

## 5 . Group ou Aggregate contando a quantidade de pokemons de cada tipo
```
be_mean> db.pokemons.group({

	initial: {total: 0},

	reduce: function(curr, result) {

		curr.types.forEach(function(type) {

			if(result[type]) result[type]++;
			else result[type] = 1;

			result.total++;

		});
	}

});

[
  {
    "total": 915,
    "fire": 47,
    "normal": 78,
    "water": 105,
    "bug": 61,
    "flying": 77,
    "poison": 54,
    "steel": 37,
    "electric": 40,
    "ice": 24,
    "ghost": 34,
    "fighting": 38,
    "psychic": 62,
    "grass": 75,
    "ground": 51,
    "fairy": 28,
    "rock": 46,
    "dark": 38,
    "dragon": 20
  }
]

be_mean> db.pokemons.aggregate([

	{ $unwind: "$types" },

	{

		$group: {

			_id: "$types",
			quantidade: {$sum: 1}
		}
	}

]);

{
  "result": [
    {
      "_id": "fairy",
      "quantidade": 28
    },
    {
      "_id": "psychic",
      "quantidade": 62
    },
    {
      "_id": "fighting",
      "quantidade": 38
    },
    {
      "_id": "dark",
      "quantidade": 38
    },
    {
      "_id": "ground",
      "quantidade": 51
    },
    {
      "_id": "grass",
      "quantidade": 75
    },
    {
      "_id": "electric",
      "quantidade": 40
    },
    {
      "_id": "steel",
      "quantidade": 37
    },
    {
      "_id": "rock",
      "quantidade": 46
    },
    {
      "_id": "flying",
      "quantidade": 77
    },
    {
      "_id": "fire",
      "quantidade": 47
    },
    {
      "_id": "ice",
      "quantidade": 24
    },
    {
      "_id": "bug",
      "quantidade": 61
    },
    {
      "_id": "poison",
      "quantidade": 54
    },
    {
      "_id": "ghost",
      "quantidade": 34
    },
    {
      "_id": "dragon",
      "quantidade": 20
    },
    {
      "_id": "water",
      "quantidade": 105
    },
    {
      "_id": "normal",
      "quantidade": 78
    }
  ],
  "ok": 1
}

```

## 6. Realizar 3 counts na pokemons.
```
be_mean> db.pokemons.count()
610

be_mean> db.pokemons.count({ types: "water"  })
105

be_mean> db.pokemons.count({ attack: { $gte: 50  }  })
492
```

