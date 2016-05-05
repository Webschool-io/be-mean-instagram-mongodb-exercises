# MongoDB - Aula 05 - Exercício
Autor: Elvisley Souza Pereira


## Importar as collections restaurantes e pokemons

```
> mongoimport  --db be-mean-pokemons --collection pokemons --drop --file BEMEAN/pokemons.json
> connected to: 127.0.0.1
> 2015-11-23T20:07:49.199-0200 dropping: be-mean-pokemons.pokemons
> 2015-11-23T20:07:49.255-0200 check 9 610
> 2015-11-23T20:07:49.255-0200 imported 610 objects


> mongoimport  --db be-mean --collection restaurantes --drop --file restaurantes.json
> connected to: 127.0.0.1
> 2015-11-23T20:19:10.067-0200 dropping: be-mean.restaurantes
> 2015-11-23T20:19:12.566-0200 check 9 25359
> 2015-11-23T20:19:12.566-0200 imported 25359 objects

```


## Distinct por cuisine na collection restaurante

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
 "Other",
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


## Distinct por types na collection pokemons

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

```


## As primeiras 3 páginas com .limit() e .skip() de pokemons (de 5 em 5)



```
> var query = {};
> var options = {name : 1 , _id : 0};
> db.pokemons.find(query , options ).limit(5).skip(5 * 0);

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
  "name": "Wartortle"
}
{
  "name": "Blastoise"
}
> Fetched 5 record(s) in 3ms

> db.pokemons.find(query , options ).limit(5).skip(5 * 1);

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
> Fetched 5 record(s) in 2ms

> db.pokemons.find(query , options ).limit(5).skip(5 * 2);

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
  "name": "Doduo"
}
{
  "name": "Seel"
}
Fetched 5 record(s) in 3ms

```


## Group ou Aggregate contando a quantidade de pokemons de cada tipo

```

> db.pokemons.group({
      initial : {total : 0}, //Variavel disponivel na funcao reduce
      reduce : function(curr , result){
        curr.types.forEach(function(type){
          if(result[type]){
            result[type]++;
          }else{
            result[type] = 1;
          }
          result.total++;
        });
      }
  });

> [
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

```

## Realizar 3 counts na collection pokemons

### .count -> todos

```
>  db.pokemons.count({})
> 610
```


### .count -> só tipo fogo

```
> db.pokemons.count({types: "fire"})
> 47
```


### .count -> só de quantos tem a defesa maior que 70

```
> db.pokemons.count({defense: {$gt : 70}} )
> 250
```
