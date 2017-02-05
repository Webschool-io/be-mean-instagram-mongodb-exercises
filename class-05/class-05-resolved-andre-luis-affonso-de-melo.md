# MongoDB - Aula 03 - Exercício

#1. Importar a Collection restaurantes e pokemons
```
	mongoimport --host 127.0.0.1 --db be-mean-instagram --collection pokemons --drop --file pokemons.json 
    2015-12-24T21:42:14.235-0200    connected to: 127.0.0.1
    2015-12-24T21:42:14.236-0200    dropping: be-mean-instagram.pokemons
    2015-12-24T21:42:14.255-0200    imported 620 documents

    mongoimport --host 127.0.0.1 --db be-mean-instagram --collection restaurantes --drop --file restaurantes.json 
    2015-12-24T21:38:43.860-0200    connected to: 127.0.0.1
    2015-12-24T21:38:43.861-0200    dropping: be-mean-instagram.restaurantes
    2015-12-24T21:38:45.250-0200    imported 25359 documents

```

#2. Distinct por "cuisine" por types na pokemons
```
> db.restaurantes.distinct("cuisine")
[
        "Bakery",
        "Hamburgers",
        "Irish",
        "American ",
        "Jewish/Kosher",
        "Delicatessen",
        "Ice Cream, Gelato, Yogurt, Ices",
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
        "Other",
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

#3. Distinct por "types" na pokemons
```
> db.pokemons.distinct("types")
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
>
```

#4. Paginar pokemons de 5 em 5

```
> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5*0)
{ "name" : "Rattata" }
{ "name" : "Charmander" }
{ "name" : "Charmeleon" }
{ "name" : "Wartortle" }
{ "name" : "Blastoise" }

> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5*1)
{ "name" : "Caterpie" }
{ "name" : "Metapod" }
{ "name" : "Butterfree" }
{ "name" : "Spearow" }
{ "name" : "Kakuna" }

> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5*2)
{ "name" : "Farfetchd" }
{ "name" : "Magnemite" }
{ "name" : "Magneton" }
{ "name" : "Doduo" }
{ "name" : "Seel" }

```

#5. Group ou aggregate com qual a quantidade de pokemons de um certo tipo
> db.pokemons.group({
... initial:{total: 0},
... reduce: function(curr, result){
... curr.types.forEach(function(type){
... if(result[type]){
... result[type]++;
... }else{
... result[type] = 1;
... }
... result.total++;});
... }
...  });
[
        {
                "total" : 915,
                "normal" : 78,
                "fire" : 47,
                "water" : 105,
                "bug" : 61,
                "flying" : 77,
                "poison" : 54,
                "steel" : 37,
                "electric" : 40,
                "ice" : 24,
                "ghost" : 34,
                "fighting" : 38,
                "psychic" : 62,
                "grass" : 75,
                "ground" : 51,
                "fairy" : 28,
                "rock" : 46,
                "dark" : 38,
                "dragon" : 20
        }


# 6. Realizar três counts na pokemons
> db.pokemons.count()
610
> db.pokemons.count({types: "fire"})
47
> db.pokemons.count({defense:{$gt:  70}})
250
>