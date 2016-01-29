# MongoDB - Aula 05 - Exercício
autor: Alex Farias

## 1. Importar as collections restaurantes e pokemons. ##

```
    //Importando JSON pokemons
    mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file pokemons.json 
    2015-12-09T15:47:43.879-0200    connected to: 127.0.0.1
    2015-12-09T15:47:43.880-0200    dropping: be-mean.pokemons
    2015-12-09T15:47:44.034-0200    imported 620 documents 

    //Importando JSON restaurantes
    mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file restaurantes.json 
    2015-12-09T15:48:48.329-0200    connected to: 127.0.0.1
    2015-12-09T15:48:48.330-0200    dropping: be-mean.restaurantes
```



## 2. Distinct por `cuisine` na restaurantes.##

```
    be-mean> db.restaurantes.distinct('cuisine')
    [
      "Hamburgers",
      "Bakery",
      "American ",
      "Irish",
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

## 3. Distinct por `types` na pokemons.##

```
   be-mean> db.pokemons.distinct('types')
   [
     "bug",
     "poison",
     "flying",
     "normal",
     "electric",
     "water",
     "psychic",
     "fighting",
     "grass",
     "fairy",
     "fire",
     "rock",
     "ice",
     "ground",
     "steel",
     "ghost",
     "dark",
     "dragon"
   ]
```

## 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)##

```
    //Pag1
    be-mean> db.pokemons.find({},{name:1, _id:0}).limit(5).skip(5*0)
    {
      "name": "Beedrill"
    }
    {
      "name": "Pidgey"
    }
    {
      "name": "Pidgeotto"
    }
    {
      "name": "Pidgeot"
    }
    {
      "name": "Raticate"
    }
    Fetched 5 record(s) in 1ms

    //Pag2
    be-mean> db.pokemons.find({},{name:1, _id:0}).limit(5).skip(5*1)
    {
      "name": "Fearow"
    }
    {
      "name": "Pikachu"
    }
    {
      "name": "Ekans"
    }
    {
      "name": "Raichu"
    }
    {
      "name": "Arbok"
    }
    Fetched 5 record(s) in 1ms

    //Pag3
    be-mean> db.pokemons.find({},{name:1, _id:0}).limit(5).skip(5*2)
    {
      "name": "Poliwag"
    }
    {
      "name": "Poliwhirl"
    }
    {
      "name": "Abra"
    }
    {
      "name": "Poliwrath"
    }
    {
      "name": "Machop"
    }
    Fetched 5 record(s) in 1ms    
```

## 5 . Group ou Aggregate contando a quantidade de pokemons de cada tipo ##

```
    db.pokemons.group({ 
        initial:{total:0}, 
        reduce: function(curr, result){ 
            curr.types.forEach(function(type){ 
                if (result[type]){ 
                        result[type]++; 
                    } else { 
                        result[type]=1; 
                    } 
                    result.total++; 
            }); 
        } 
    });
   
```

## 6. Realizar 3 counts na pokemons. ##

```
    //Total
    be-mean> db.pokemons.count()
    620
    //Tipo fogo
    be-mean> db.pokemons.count({types:'fire'})
    53
    //Defesa >70
    be-mean> db.pokemons.count({defense: {$gt: 70}})
    263
```