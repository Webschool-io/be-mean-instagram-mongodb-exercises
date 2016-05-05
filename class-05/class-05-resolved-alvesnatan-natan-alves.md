# MongoDB - Aula 05 - Exercício
autor: Natan Alves


# 1. Importar as collections restaurantes e pokemons
```
C:\Users\Natan\Documents>mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-12-13T18:23:46.397-0200    connected to: localhost
2015-12-13T18:23:46.400-0200    dropping: be-mean.restaurantes
2015-12-13T18:23:47.668-0200    imported 25359 documents

C:\Users\Natan\Documents>mongoimport --db be-mean --collection restaurantes --drop --file pokemons.json
2015-12-13T18:24:01.732-0200    connected to: localhost
2015-12-13T18:24:01.734-0200    dropping: be-mean.restaurantes
2015-12-13T18:24:01.760-0200    imported 610 documents
```

# 2. Distinct por 'cuisine' na restaurantes
```
natan-stark(mongod-3.0.7) be-mean> db.restaurantes.distinct('cuisine').sort()
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

# 3. Distinct por 'types' na pokemons
```
natan-stark(mongod-3.0.7) be-mean> db.pokemons.distinct( 'types' );
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
    "psychic",
    "fighting",
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
natan-stark(mongod-3.0.7) be-mean> db.pokemons.find({}, { name: 1 }).limit(5).skip(5 * 0)
{
    "_id": ObjectId("564b1dad25337263280d047b"),
    "name": "Charmeleon"
}
{
    "_id": ObjectId("564b1dad25337263280d047a"),
    "name": "Charmander"
}
{
    "_id": ObjectId("564b1dad25337263280d0479"),
    "name": "Rattata"
}
{
    "_id": ObjectId("564b1dad25337263280d047d"),
    "name": "Blastoise"
}
{
    "_id": ObjectId("564b1dad25337263280d047c"),
    "name": "Wartortle"
}

natan-stark(mongod-3.0.7) be-mean> db.pokemons.find({}, { name: 1 }).limit(5).skip(5 * 1)
{
    "_id": ObjectId("564b1dad25337263280d047e"),
    "name": "Caterpie"
}
{
    "_id": ObjectId("564b1dad25337263280d047f"),
    "name": "Metapod"
}
{
    "_id": ObjectId("564b1dad25337263280d0480"),
    "name": "Butterfree"
}
{
    "_id": ObjectId("564b1dad25337263280d0481"),
    "name": "Spearow"
}
{
    "_id": ObjectId("564b1dad25337263280d0482"),
    "name": "Kakuna"
}

natan-stark(mongod-3.0.7) be-mean> db.pokemons.find({}, { name: 1 }).limit(5).skip(5 * 2)
{
    "_id": ObjectId("564b1dae25337263280d0483"),
    "name": "Farfetchd"
}
{
    "_id": ObjectId("564b1dae25337263280d0484"),
    "name": "Magnemite"
}
{
    "_id": ObjectId("564b1dae25337263280d0485"),
    "name": "Magneton"
}
{
    "_id": ObjectId("564b1dae25337263280d0486"),
    "name": "Doduo"
}
{
    "_id": ObjectId("564b1dae25337263280d0487"),
    "name": "Seel"
}
```

# 5. Group ou Aggregate contando a quantidade de pokemons de cada tipo
```
natan-stark(mongod-3.0.7) be-mean> db.pokemons.group({
   initial: { total: 0 },
   reduce: function(curr, result) {
     curr.types.forEach(function(type) {
     if(result[type]) {
       result[type]++;
     }
     else {
       result[type] = 1;
     }
     result.total++;
   });
 }});
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
        "psychic": 62,
        "fighting": 38,
        "grass": 75,
        "ground": 51,
        "fairy": 28,
        "rock": 46,
        "dark": 38,
        "dragon": 20
    }
]
```

# 6. Realizar 3 counts na pokemons.
```
-> count -- todos
natan-stark(mongod-3.0.7) be-mean> db.pokemons.count({})
610

-> count -- só tipo fogo
natan-stark(mongod-3.0.7) be-mean> db.pokemons.count({ types: 'fire'})
47

-> count -- só de quantos tem a defesa maior que 70
natan-stark(mongod-3.0.7) be-mean> db.pokemons.count({ defense: { $gt: 70 }})
250
```