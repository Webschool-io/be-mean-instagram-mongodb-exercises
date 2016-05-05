# MongoDB - Aula 05 - Exercício
autor: Janaína P. dos Santos

## 1. Importar as collections restaurantes e pokemons. ##
#### Restaurantes
```
> mongoimport -h 127.0.0.1 -d be-mean -c restaurantes --drop --file restaurantes.json
```
#### Pokemons
```
> mongoimport -h 127.0.0.1 -d be-mean -c pokemons --drop --file pokemons.json
```

## 2. Distinct por `cuisine` na restaurantes. ##
```
> db.restaurantes.distinct("cuisine");
```

##### Saída

```
[
  "Bakery",
  "Irish",
  "American ",
  "Jewish/Kosher",
  "Delicatessen",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Chinese",
  "Other",
  "Chicken",
  "Hamburgers",
  "Turkish",
  "Caribbean",
  "Donuts",
  "Bagels/Pretzels",
  "Continental",
  "Pizza",
  "Sandwiches/Salads/Mixed Buffet",
  "Italian",
  "Steak",
  "Polish",
  "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
  "German",
  "French",
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

## 3. Distinct por `types` na pokemons. ##
```
> db.pokemons.distinct("types");
```
##### Saída
```
[
  "normal",
  "fire",
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

## 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5). ##
```
> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 0);
> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 1);
> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 2);
```

## 5. Group ou Aggregate contando a quantidade de pokemons de cada tipo. ##
```
> db.pokemons.group({
	initial: {total: 0},
	reduce: function(cur, result){
		cur.types.forEach(function(type){
			if(result[type]){
				result[type]++;
			} else{
				result[type] = 1;
			}
			result.total++;
		});
	}
});
```

## 6. Realizar 3 counts na pokemons. ## 
```
db.pokemons.count();
db.pokemons.count({types: 'electric'});
db.pokemons.count(attack:{$lt:60});
```