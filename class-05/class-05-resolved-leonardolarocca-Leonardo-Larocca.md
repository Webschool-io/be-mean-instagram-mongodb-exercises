## MongoDB - Aula 05 resolvido
Autor: Leonardo Larocca

## 1 - Importando a collection `restaurantes` e `pokemons`
```
➜  MEAN git:(master) ✗ mongoimport --host 127.0.0.1 --db be-mean-pokemons --collection pokemons --drop --file pokemons.json
2016-01-27T21:00:16.892-0200	connected to: 127.0.0.1
2016-01-27T21:00:16.893-0200	dropping: be-mean-pokemons.pokemons
2016-01-27T21:00:16.980-0200	imported 610 documents
➜  MEAN git:(master) ✗ 

➜  MEAN git:(master) ✗ mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file restaurantes.json
2016-01-27T22:52:02.567-0200	connected to: 127.0.0.1
2016-01-27T22:52:02.567-0200	dropping: be-mean.restaurantes
2016-01-27T22:52:03.883-0200	imported 25359 documents
➜  MEAN git:(master) ✗ 

```

## 2 - Distinct por `cuisine` na restaurantes
```
asus(mongod-3.0.8) be-mean> db.restaurantes.distinct("cuisine").sort()
[
  "Afghan",
  "African",
  "American ",
  "Armenian",
  "Asian",
  "Australian",
  "Bagels/Pretzels",
  "Bakery",
  "Bangladeshi",
  "Barbecue",
  "Bottled beverages, including water, sodas, juices, etc.",
  "Brazilian",
  "CafÃ©/Coffee/Tea",
  "Café/Coffee/Tea",
  "Cajun",
  "Californian",
  "Caribbean",
  "Chicken",
  "Chilean",
  "Chinese",
  "Chinese/Cuban",
  "Chinese/Japanese",
  "Continental",
  "Creole",
  "Creole/Cajun",
  "Czech",
  "Delicatessen",
  "Donuts",
  "Eastern European",
  "Egyptian",
  "English",
  "Ethiopian",
  "Filipino",
  "French",
  "Fruits/Vegetables",
  "German",
  "Greek",
  "Hamburgers",
  "Hawaiian",
  "Hotdogs",
  "Hotdogs/Pretzels",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Indian",
  "Indonesian",
  "Iranian",
  "Irish",
  "Italian",
  "Japanese",
  "Jewish/Kosher",
  "Juice, Smoothies, Fruit Salads",
  "Korean",
  "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
  "Mediterranean",
  "Mexican",
  "Middle Eastern",
  "Moroccan",
  "Not Listed/Not Applicable",
  "Nuts/Confectionary",
  "Other",
  "Pakistani",
  "Pancakes/Waffles",
  "Peruvian",
  "Pizza",
  "Pizza/Italian",
  "Polish",
  "Polynesian",
  "Portuguese",
  "Russian",
  "Salads",
  "Sandwiches",
  "Sandwiches/Salads/Mixed Buffet",
  "Scandinavian",
  "Seafood",
  "Soul Food",
  "Soups",
  "Soups & Sandwiches",
  "Southwestern",
  "Spanish",
  "Steak",
  "Tapas",
  "Tex-Mex",
  "Thai",
  "Turkish",
  "Vegetarian",
  "Vietnamese/Cambodian/Malaysia"
]

```
## 3 - Distinct por `types`no pokemons
```
asus(mongod-3.0.8) be-mean-pokemons> db.pokemons.distinct("types").sort()
[
  "bug",
  "dark",
  "dragon",
  "electric",
  "fairy",
  "fighting",
  "fire",
  "flying",
  "ghost",
  "grass",
  "ground",
  "ice",
  "normal",
  "poison",
  "psychic",
  "rock",
  "steel",
  "water"
]
asus(mongod-3.0.8) be-mean-pokemons> 
```

## 4 - As primeiras 3 páginas com `.limit()` e `.skip()` de pokemons (5 em 5)
```
asus(mongod-3.0.8) be-mean-pokemons> db.pokemons.find({},{name:1, _id: 0}).limit(5).skip(5*0)
{
  "name": "Rattata"
}
{
  "name": "Charmander"
}
{
  "name": "Wartortle"
}
{
  "name": "Charmeleon"
}
{
  "name": "Blastoise"
}
Fetched 5 record(s) in 2ms
asus(mongod-3.0.8) be-mean-pokemons> db.pokemons.find({},{name:1, _id: 0}).limit(5).skip(5*1)
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
  "name": "Kakuna"
}
{
  "name": "Spearow"
}
Fetched 5 record(s) in 2ms
asus(mongod-3.0.8) be-mean-pokemons> db.pokemons.find({},{name:1, _id: 0}).limit(5).skip(5*2)
{
  "name": "Farfetchd"
}
{
  "name": "Magnemite"
}
{
  "name": "Magneton"
}
{
  "name": "Seel"
}
{
  "name": "Dodrio"
}
Fetched 5 record(s) in 2ms
asus(mongod-3.0.8) be-mean-pokemons> 

```

## 5 - Group ou Aggregate contando a quantidade de pokemons de cada tipo.
```
]
asus(mongod-3.0.8) be-mean-pokemons> db.pokemons.group({
	initial:{total:0},
	reduce: function(curr,result){
		curr.types.forEach(function(type) {
			if(result[type]){
				result[type]++;
			}else{
				result[type] = 1;
			}
			result.total++;
		});
	}
});

[
  {
    "total": 915,
    "normal": 78,
    "fire": 47,
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
asus(mongod-3.0.8) be-mean-pokemons> 

```