# MongoDB - Aula 05 - Exercício
autor: Wellington Fernandes

## Passo 1

    ```
	mongoimport --db be-mean-pokemons --collection restaurantes --drop --file c:/restaurantes.json
	mongoimport --db be-mean-pokemons --collection pokemons --drop --file c:/pokemons.json
	
    ```	

## Passo 2

    ```
    db.restaurantes.distinct('cuisine').sort()
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

## Passo 3

    ```
    db.pokemons.distinct('types').sort()
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

    ```

## Passo 4

    ```
    db.pokemons.find().limit(5).skip(5 * 1)
	{
	    "_id": ObjectId("564a7c362c153ed825a6905c"),
	    "attack": 90,
	    "created": "2013-11-03T15:05:41.318944",
	    "defense": 55,
	    "height": "8",
	    "hp": 60,
	    "name": "Raichu",
	    "speed": 110,
	    "types": [
	        "electric"
	    ]
	}
	{
	    "_id": ObjectId("564a7c362c153ed825a6905b"),
	    "attack": 60,
	    "created": "2013-11-03T15:05:41.313816",
	    "defense": 44,
	    "height": "20",
	    "hp": 35,
	    "name": "Ekans",
	    "speed": 55,
	    "types": [
	        "poison"
	    ]
	}
	{
	    "_id": ObjectId("564a7c362c153ed825a6905a"),
	    "attack": 55,
	    "created": "2013-11-03T15:05:41.317235",
	    "defense": 40,
	    "height": "4",
	    "hp": 35,
	    "name": "Pikachu",
	    "speed": 90,
	    "types": [
	        "electric"
	    ]
	}
	{
	    "_id": ObjectId("564a7c362c153ed825a69058"),
	    "attack": 81,
	    "created": "2013-11-03T15:05:41.308092",
	    "defense": 60,
	    "height": "7",
	    "hp": 55,
	    "name": "Raticate",
	    "speed": 97,
	    "types": [
	        "normal"
	    ]
	}
	{
	    "_id": ObjectId("564a7c362c153ed825a6905d"),
	    "attack": 85,
	    "created": "2013-11-03T15:05:41.315504",
	    "defense": 69,
	    "height": "35",
	    "hp": 60,
	    "name": "Arbok",
	    "speed": 80,
	    "types": [
	        "poison"
	    ]
	}
	Fetched 5 record(s) in 1ms

    ```

## Passo 5

    ```    
    db.pokemons.group({
		initial: { total: 0 },
		cond: { types: 'dark' },
		reduce: function(curr, result) {
			curr.types.forEach(function(type) {
				if (result[type] && type === 'dark') {
					result[type]++;
					result.total++;
				}else if(type === 'dark'){
					result[type] = 1;
					result.total++;
				}
			});
		}
	});

    ```

## Passo 6

	```    
    db.pokemons.count({})
    db.pokemons.count({types: 'fire'})
    db.pokemons.count({defense: {$gt: 70}})

    ```