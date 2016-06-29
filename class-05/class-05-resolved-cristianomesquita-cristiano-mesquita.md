# MongoDB - Aula 05 - Exercício
autor: Cristiano Mesquita

## Importar as collections restaurantes e pokemons

##                          Pokemons

cristianomesquita@ubuntu:~$ mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file '/home/cristianomesquita/pokemons.json' 
connected to: 127.0.0.1
2016-06-01T18:30:35.893-0300 dropping: be-mean.pokemons
2016-06-01T18:30:36.503-0300 check 9 610
2016-06-01T18:30:36.503-0300 imported 610 objects

##                          Restaurantes

cristianomesquita@ubuntu:~$ mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file '/home/cristianomesquita/restaurantes.json' 
connected to: 127.0.0.1
2016-06-01T18:32:18.399-0300 dropping: be-mean.restaurantes
2016-06-01T18:32:19.661-0300 check 9 25359
2016-06-01T18:32:19.773-0300 imported 25359 objects


## Distinct por 'cuisine' na restaurantes

ubuntu(mongod-2.6.10) be-mean> var query = 'cuisine'
ubuntu(mongod-2.6.10) be-mean> db.restaurantes.distinct(query)
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



## Distinct por 'types' na pokemons

ubuntu(mongod-2.6.10) be-mean> var query = 'types'
ubuntu(mongod-2.6.10) be-mean> db.pokemons.distinct(query)
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


## As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)

##                      Página 1

ubuntu(mongod-2.6.10) be-mean> db.pokemons.find({},{name:1,_id:0}).limit(5).skip(5 * 0)
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
Fetched 5 record(s) in 66ms

##                      Página 2

ubuntu(mongod-2.6.10) be-mean> db.pokemons.find({},{name:1,_id:0}).limit(5).skip(5 * 1)
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

##                      Página 3

ubuntu(mongod-2.6.10) be-mean> db.pokemons.find({},{name:1,_id:0}).limit(5).skip(5 * 2)
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
Fetched 5 record(s) in 2ms

## Group ou aggregate contando a quantidade de pokemons de cada tipo

ubuntu(mongod-2.6.10) be-mean> db.pokemons.group({
...   initial:{total:0},
...   reduce:function(curr,result){
...       curr.types.forEach(function(type){
...         if(result[type]){
...           result[type]++;
...         }else {
...           result[type] = 1;
...         }
...         result.total++;
...       });
...   }
... });
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

## Realizar 3 counts na pokemons

##-> .count -- todos
ubuntu(mongod-2.6.10) be-mean> db.pokemons.count()
610

##-> .count -- só do tipo fogo
ubuntu(mongod-2.6.10) be-mean> db.pokemons.count({types:'fire'})
47

##-> .count -- só de quantos tem a defesa maior que 70
ubuntu(mongod-2.6.10) be-mean> var query = {defense:{$gt:70}}
ubuntu(mongod-2.6.10) be-mean> db.pokemons.count(query)
250




