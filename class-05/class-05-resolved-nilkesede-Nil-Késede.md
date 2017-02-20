# MongoDB - Aula 05 - Exercício
> Autor: Nil Késede

## Importar as collections restaurantes e pokemons
```bash
➔ mongoimport --db be-mean --collection restaurantes --host=localhost --drop --file ./mongodb/data/restaurantes.json
2016-03-03T15:35:09.446-0300    connected to: localhost
2016-03-03T15:35:09.447-0300    dropping: be-mean.restaurantes
2016-03-03T15:35:10.877-0300    imported 25359 documents

➔ mongoimport --db be-mean --collection pokemons --host=localhost --drop --file ./mongodb/data/pokemons.json
2016-03-03T15:34:46.019-0300    connected to: localhost
2016-03-03T15:34:46.019-0300    dropping: be-mean.pokemons
2016-03-03T15:34:46.089-0300    imported 610 documents
```

## Distinct por `cuisines` na `restaurantes`
```js
> db.restaurantes.distinct('cuisine')
[
  "American ",
  "Bakery",
  "Hamburgers",
  "Jewish/Kosher",
  "Irish",
  "Delicatessen",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Chinese",
  "Chicken",
  "Turkish",
  "Caribbean",
  "Donuts",
  "Sandwiches/Salads/Mixed Buffet",
  "Bagels/Pretzels",
  "Pizza",
  "Continental",
  "Italian",
  "Polish",
  "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
  "German",
  "Steak",
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

## Distinct por `types` na `pokemons`
```js
> db.pokemons.distinct('types')
[
  "normal",
  "fire",
  "water",
  "bug",
  "flying",
  "poison",
  "electric",
  "steel",
  "ghost",
  "ice",
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

## As primeiras três páginas com `.limit()` e `.skip()` de `pokemons` (5 em 5)
```js
> var limit = 5
> db.pokemons.find({}, { name: 1, _id: 0}).limit(limit).skip(limit * 0)
{
  "name": "Rattata"
}
{
  "name": "Charmander"
}
{
  "name": "Charmeleon"
}
{
  "name": "Blastoise"
}
{
  "name": "Wartortle"
}
Fetched 5 record(s) in 2ms

> db.pokemons.find({}, { name: 1, _id: 0}).limit(limit).skip(limit * 1)
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
Fetched 5 record(s) in 3ms

> db.pokemons.find({}, { name: 1, _id: 0}).limit(limit).skip(limit * 2)
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
  "name": "Doduo"
}
Fetched 5 record(s) in 2ms
```

## Group ou Aggregate contando a quantidade de Pokemons de cada tipo
```js
> db.pokemons.group({
    initial: {},
    reduce: function(curr, result) {
        curr.types.forEach(function(type){
            if (result[type]) {
                result[type]++;
            } else {
                result[type] = 1;
            }
        })
    }
})

[
  {
    "normal": 78,
    "fire": 47,
    "water": 105,
    "bug": 61,
    "flying": 77,
    "poison": 54,
    "steel": 37,
    "electric": 40,
    "ghost": 34,
    "ice": 24,
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

## Realizar 3 counts na `pokemons`
```js
// Todos
> db.pokemons.count()ß
610
// Tipo Fogo
> db.pokemons.count({types: 'fire'})
47
// Quantos tem a defesa maior que  70
> db.pokemons.count({'defense': {$gt: 70}})
250
```
