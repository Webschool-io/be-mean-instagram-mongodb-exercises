# MongoDB - Aula 05 - Exercício
autor: Leonardo Barbosa de Oliveira

## 1. importar as collections restaurantes.json e pokemons.json

	$ mongoimport --host 127.0.0.1 --db be-mean-instagram --collection restaurantes --drop --file restaurantes.json
	2015-11-19T00:20:58.674-0200    connected to: 127.0.0.1
	2015-11-19T00:20:58.686-0200    dropping: be-mean-instagram.restaurantes
	2015-11-19T00:21:00.539-0200    imported 25359 documents

	$ mongoimport --host 127.0.0.1 --db be-mean-pokemons --collection novospokemons --drop --file pokemons.json
	2015-11-19T00:14:29.167-0200    connected to: 127.0.0.1
	2015-11-19T00:14:29.218-0200    dropping: be-mean-pokemons.novospokemons
	2015-11-19T00:14:29.429-0200    imported 610 documents

## 2. Distinct 'cuisine'na restaurantes

	 db.restaurantes.distinct('cuisine')
	[
	        "Bakery",
	        "Hamburgers",
	        "Irish",
	        "American ",
	        "Jewish/Kosher",
	        "Delicatessen",
	        "Ice Cream, Gelato, Yogurt, Ices",
	        "Chinese",
	        "Other",
	        "Chicken",
	        "Turkish",
	        "Caribbean",
	        "Donuts",
	        "Sandwiches/Salads/Mixed Buffet",
	        "Bagels/Pretzels",
	        "Pizza",
	        "Continental",
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
	>

## 3. Distinct 'types'na pokemons
	
	db.novospokemons.distinct('types')
	[
	        "fire",
	        "water",
	        "bug",
	        "flying",
	        "normal",
	        "poison",
	        "electric",
	        "steel",
	        "ghost",
	        "ice",
	        "fighting",
	        "psychic",
	        "grass",
	        "ground",
	        "fairy",
	        "rock",
	        "dark",
	        "dragon"
	]
	>

## 4. As primeiras 3 páginas com limit e skip de pokemons (5 em 5)
		
		> db.novospokemons.find().limit(5).skip(3*0)
		{ "_id" : ObjectId("564b1dad25337263280d047b"), "attack" : 64, "created" : "2013-11-03T15:05:41.273462", "defense" : 58, "height" : "11", "hp" : 58, "name" : "Charmeleon", "speed" : 80, "types" : [ "fire" ] }
		{ "_id" : ObjectId("564b1dad25337263280d047c"), "attack" : 63, "created" : "2013-11-03T15:05:41.280718", "defense" : 80, "height" : "10", "hp" : 59, "name" : "Wartortle", "speed" : 58, "types" : [ "water" ] }
		{ "_id" : ObjectId("564b1dad25337263280d047a"), "attack" : 52, "created" : "2013-11-03T15:05:41.271082", "defense" : 43, "height" : "6", "hp" : 39, "name" : "Charmander", "speed" : 65, "types" : [ "fire" ] }
		{ "_id" : ObjectId("564b1dad25337263280d047e"), "attack" : 30, "created" : "2013-11-03T15:05:41.285736", "defense" : 35, "height" : "3", "hp" : 45, "name" : "Caterpie", "speed" : 45, "types" : [ "bug" ] }
		{ "_id" : ObjectId("564b1dad25337263280d047d"), "attack" : 83, "created" : "2013-11-03T15:05:41.282985", "defense" : 100, "height" : "16", "hp" : 79, "name" : "Blastoise", "speed" : 78, "types" : [ "water" ] }
		>

		> db.novospokemons.find().limit(5).skip(3*1)
		{ "_id" : ObjectId("564b1dad25337263280d047e"), "attack" : 30, "created" : "2013-11-03T15:05:41.285736", "defense" : 35, "height" : "3", "hp" : 45, "name" : "Caterpie", "speed" : 45, "types" : [ "bug" ] }
		{ "_id" : ObjectId("564b1dad25337263280d047d"), "attack" : 83, "created" : "2013-11-03T15:05:41.282985", "defense" : 100, "height" : "16", "hp" : 79, "name" : "Blastoise", "speed" : 78, "types" : [ "water" ] }
		{ "_id" : ObjectId("564b1dad25337263280d047f"), "attack" : 20, "created" : "2013-11-03T15:05:41.288107", "defense" : 55, "height" : "7", "hp" : 50, "name" : "Metapod", "speed" : 30, "types" : [ "bug" ] }
		{ "_id" : ObjectId("564b1dad25337263280d0480"), "attack" : 45, "created" : "2013-11-03T15:05:41.290411", "defense" : 50, "height" : "11", "hp" : 60, "name" : "Butterfree", "speed" : 70, "types" : [ "flying", "bug" ]		}
		{ "_id" : ObjectId("564b1dad25337263280d0481"), "attack" : 60, "created" : "2013-11-03T15:05:41.310402", "defense" : 30, "height" : "3", "hp" : 40, "name" : "Spearow", "speed" : 70, "types" : [ "normal", "flying" ] }
		>

		> db.novospokemons.find().limit(5).skip(3*2)
		{ "_id" : ObjectId("564b1dad25337263280d0480"), "attack" : 45, "created" : "2013-11-03T15:05:41.290411", "defense" : 50, "height" : "11", "hp" : 60, "name" : "Butterfree", "speed" : 70, "types" : [ "flying", "bug" ]		}
		{ "_id" : ObjectId("564b1dad25337263280d0481"), "attack" : 60, "created" : "2013-11-03T15:05:41.310402", "defense" : 30, "height" : "3", "hp" : 40, "name" : "Spearow", "speed" : 70, "types" : [ "normal", "flying" ] }
		{ "_id" : ObjectId("564b1dad25337263280d0482"), "attack" : 25, "created" : "2013-11-03T15:05:41.294947", "defense" : 50, "height" : "6", "hp" : 45, "name" : "Kakuna", "speed" : 35, "types" : [ "poison", "bug" ] }
		{ "_id" : ObjectId("564b1dae25337263280d0483"), "attack" : 65, "created" : "2013-11-03T15:05:41.439497", "defense" : 55, "height" : "8", "hp" : 52, "name" : "Farfetchd", "speed" : 60, "types" : [ "normal", "flying" ] }
		{ "_id" : ObjectId("564b1dae25337263280d0484"), "attack" : 35, "created" : "2013-11-03T15:05:41.435237", "defense" : 70, "height" : "3", "hp" : 25, "name" : "Magnemite", "speed" : 45, "types" : [ "steel", "electric"] }
		>

## 5. Fazer group ou aggregate contando 
	> db.novospokemons.aggregate({ $group: { _id:{}, types: {$sum: '$types'} } })
	{ "_id" : {  }, "types" : 0 }
	> db.novospokemons.group({
	... initial: {total: 0},
	... reduce: function(curr, result) {
	... curr.types.forEach(function(type){
	... if(result[type]){
	... result[type]++;
	... }else{
	... result[type] = 1;
	... }
	... result.total++;
	... });
	... }
	... });
	[
	        {
	                "total" : 915,
	                "fire" : 47,
	                "water" : 105,
	                "bug" : 61,
	                "flying" : 77,
	                "normal" : 78,
	                "poison" : 54,
	                "steel" : 37,
	                "electric" : 40,
	                "ghost" : 34,
	                "ice" : 24,
	                "fighting" : 38,
	                "psychic" : 62,
	                "grass" : 75,
	                "ground" : 51,
	                "fairy" : 28,
	                "rock" : 46,
	                "dark" : 38,
	                "dragon" : 20
	        }
	]
	>




## 6. Realizar 3 counts na pokemons

	.count -- todos
	
	> db.novospokemons.count()
	610

	.count -- só do tipo fogo

	> db.novospokemons.count({types: 'fire'})
	47

	.count --  so de quantos tem a defesa maior que 70
		
	> db.novospokemons.count({defense:{$gt: 70}})
	250

