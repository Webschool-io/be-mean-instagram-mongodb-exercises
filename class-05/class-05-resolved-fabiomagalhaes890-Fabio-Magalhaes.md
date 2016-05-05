
# 1. Importar as collections restaurantes e pokemons
```
C:\mongodb>mongoimport --db be-mean --collection pokemons --drop --file pokemons.json
2015-12-09T21:07:07.110-0200    connected to: localhost
2015-12-09T21:07:07.127-0200    dropping: be-mean.pokemons
2015-12-09T21:07:07.160-0200    imported 610 documents

C:\mongodb>mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-12-09T21:11:15.451-0200    connected to: localhost
2015-12-09T21:11:15.452-0200    dropping: be-mean.restaurantes
2015-12-09T21:11:16.227-0200    imported 25359 documents

```
# 2. Distinct por `cuisine` na restaurantes 
```
> db.restaurantes.distinct('cuisine');
[
        "Hamburgers",
        "Bakery",
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
        "Continental",
        "Pizza",
        "Steak",
        "Italian",
        "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
        "German",
        "Polish",
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
# 3. Distinct por `types` na pokemons
```
> db.pokemons.distinct('types');
[
        "water",
        "normal",
        "fire",
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
# 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)
```
> db.pokemons.find({}, { name: 1, _id: 0} ).limit(5).skip(5 * 0).pretty();
{ "name" : "Wartortle" }
{ "name" : "Rattata" }
{ "name" : "Charmander" }
{ "name" : "Blastoise" }
{ "name" : "Charmeleon" }
> db.pokemons.find({}, { name: 1, _id: 0} ).limit(5).skip(5 * 1).pretty();
{ "name" : "Caterpie" }
{ "name" : "Metapod" }
{ "name" : "Butterfree" }
{ "name" : "Kakuna" }
{ "name" : "Spearow" }
> db.pokemons.find({}, { name: 1, _id: 0} ).limit(5).skip(5 * 2).pretty();
{ "name" : "Farfetchd" }
{ "name" : "Magnemite" }
{ "name" : "Magneton" }
{ "name" : "Doduo" }
{ "name" : "Seel" }
```
# 5. Group ou Aggregate contando a quantidade de cada tipo
```
> db.pokemons.group({
... initial: { total: 0 },
... reduce: function(curr, result) {
... curr.types.forEach(function(type) {
... if(result[type]) {
... result[type]++;
... }
... else {
... result[type] = 1;
... }
... result.total++;
... });
... }});
[
        {
                "total" : 915,
                "water" : 105,
                "normal" : 78,
                "fire" : 47,
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
]
```
# 6. Realizar 3 counts na pokemons - count - count tipo fogo - count defesa maior que 70
```
> db.pokemons.count({});
610
> db.pokemons.count({'types':'fire'});
47
> db.pokemons.count({defense:{$gt: 70}});
250
```