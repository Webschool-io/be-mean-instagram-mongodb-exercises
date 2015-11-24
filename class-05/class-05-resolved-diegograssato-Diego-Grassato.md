# MongoDB - Aula 05 - Exercício
autor: Diego Pereira Grassato


### Importar as collections restaurantes e pokemons

```javascript

mongoimport -d be-mean -c restaurantes --drop --file restaurantes.json
connected to: 127.0.0.1
Mon Nov  9 23:46:38.679 dropping: be-mean.restaurantes
Mon Nov  9 23:46:39.752 check 9 25359
Mon Nov  9 23:46:40.097 imported 25359 objects

```

### Distinct por `cuisine` na restaurantes

```javascript

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

### Distinct por `types` na pokemons

```javascript

db.pokemons.distinct('types')
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

### As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)

```javascript

db.pokemons.find({},{ name:1, _id:0 }).limit(5).skip(5 * 0)
{
  "name": "Pikachu"
}
{
  "name": "Bulbassauro"
}
{
  "name": "Charmander"
}
{
  "name": "Squirtle"
}
{
  "name": "Caterpie"
}

db.pokemons.find({},{ name:1, _id:0 }).limit(5).skip(5 * 1)
{
  "name": "Testemon"
}


db.pokemons.find({},{ name:1, _id:0 }).limit(5).skip(5 * 2)
Fetched 0 record(s) in 0ms

```

### Group ou Aggregate contando a quantidade de pokemons de cada tipo

```javascript

db.pokemons.group({
    initial: { total: 0 },
    reduce:  function(cur, result) {
        cur.type.forEach(function(t) {
            if (result[t]) {
                result[t]++;
            } else {
                result[t] = 1;
            }
            result.total++;
        });
    }
});

// ou

db.pokemons.aggregate([
  {$unwind: '$type'},
  {$group: {
    _id: '$type',
    total: {$sum: 1}
  }}
]);


```

### Realizar 3 counts na pokemons.

```javascript

// todos
> db.pokemons.count()
6

// tipo fogo
db.pokemons.count({ type: 'fire'  })
1

//quantos tem a defesa maior que 70
db.pokemons.count({ defense: {$gt: 70} })
1

```
