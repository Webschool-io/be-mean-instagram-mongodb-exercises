# MongoDB - Aula 05 - Exercício
autor: Rafael Ferreira Vianna

## 1 - Importar as collections restaurantes e pokemons.;

  ```  
  C:\Users\Rafael\Documents\projetos\be-mean-instagram-mongodb-exercises>mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file restaurantes.json
  2016-11-05T13:04:37.558-0200    connected to: 127.0.0.1
  2016-11-05T13:04:37.559-0200    dropping: be-mean.restaurantes
  2016-11-05T13:04:38.987-0200    imported 25359 documents


  C:\Users\Rafael\Documents\projetos\be-mean-instagram-mongodb-exercises>mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file pokemons.json
  2016-11-05T13:07:08.266-0200    connected to: 127.0.0.1
  2016-11-05T13:07:08.267-0200    dropping: be-mean.restaurantes
  2016-11-05T13:07:08.476-0200    imported 610 documents

  ```

## 2 - Distinct por cuisine na restaurantes;

  ```
  > db.restaurantes.distinct('cuisine')
[
        "American ",
        "Delicatessen",
        "Bakery",
        "Ice Cream, Gelato, Yogurt, Ices",
        "Chinese",
        "Jewish/Kosher",
        "Irish",
        "Hamburgers",
        "Chicken",
        "Turkish",
        "Caribbean",
        "Donuts",
        "Bagels/Pretzels",
        "Continental",
        "Sandwiches/Salads/Mixed Buffet",
        "Pizza",
        "Italian",
        "Steak",
        "Polish",
        "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
        "German",
        "Pizza/Italian",
        "French",
        "Mexican",
        "Spanish",
        "Café/Coffee/Tea",
        "Tex-Mex",
        "Soul Food",
        "Pancakes/Waffles",
        "Seafood",
        "Hotdogs",
        "Greek",
        "Not Listed/Not Applicable",
        "African",
        "Japanese",
        "Indian",
        "Thai",
        "Armenian",
        "Chinese/Cuban",
        "Mediterranean",
        "Korean",
        "Bottled beverages, including water, sodas, juices, etc.",
        "Russian",
        "Eastern European",
        "Asian",
        "Middle Eastern",
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

## 3 - Distinct por types na pokemon;

  ```
  > db.pokemons.distinct('types')
  [
          "fire",
          "normal",
          "water",
          "bug",
          "flying",
          "poison",
          "ghost",
          "ice",
          "fighting",
          "psychic",
          "grass",
          "electric",
          "steel",
          "ground",
          "fairy",
          "rock",
          "dark",
          "dragon"
  ]
  >

  ```

## 4 - As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5);

   ```
   > db.pokemons.find({}).limit(5).skip(0 * 5)

    { "_id" : ObjectId("564b1dad25337263280d047a"), "attack" : 52, "created" : "2013-11-03T15:05:41.271082", "defense" : 43, "height" : "6", "hp" : 39, "name" : "Charmander", "speed" : 65, "types" : [ "fire" ] }
    { "_id" : ObjectId("564b1dad25337263280d0479"), "attack" : 56, "created" : "2013-11-03T15:05:41.305777", "defense" : 35, "height" : "3", "hp" : 30, "name" : "Rattata", "speed" : 72, "types" : [ "normal" ] }
    { "_id" : ObjectId("564b1dad25337263280d047b"), "attack" : 64, "created" : "2013-11-03T15:05:41.273462", "defense" : 58, "height" : "11", "hp" : 58, "name" : "Charmeleon", "speed" : 80, "types" : [ "fire" ] }
    { "_id" : ObjectId("564b1dad25337263280d047c"), "attack" : 63, "created" : "2013-11-03T15:05:41.280718", "defense" : 80, "height" : "10", "hp" : 59, "name" : "Wartortle", "speed" : 58, "types" : [ "water" ] }
    { "_id" : ObjectId("564b1dad25337263280d047d"), "attack" : 83, "created" : "2013-11-03T15:05:41.282985", "defense" : 100, "height" : "16", "hp" : 79, "name" : "Blastoise", "speed" : 78, "types" : [ "water" ] }


   > db.pokemons.find({}).limit(5).skip(1 * 5)

    { "_id" : ObjectId("564b1dad25337263280d047f"), "attack" : 20, "created" : "2013-11-03T15:05:41.288107", "defense" : 55, "height" : "7", "hp" : 50, "name" : "Metapod", "speed" : 30, "types" : [ "bug" ] }
    { "_id" : ObjectId("564b1dad25337263280d0480"), "attack" : 45, "created" : "2013-11-03T15:05:41.290411", "defense" : 50, "height" : "11", "hp" : 60, "name" : "Butterfree", "speed" : 70, "types" : [ "flying", "bug" ] }
    { "_id" : ObjectId("564b1dad25337263280d0481"), "attack" : 60, "created" : "2013-11-03T15:05:41.310402", "defense" : 30, "height" : "3", "hp" : 40, "name" : "Spearow", "speed" : 70, "types" : [ "normal", "flying" ] }
    { "_id" : ObjectId("564b1dad25337263280d047e"), "attack" : 30, "created" : "2013-11-03T15:05:41.285736", "defense" : 35, "height" : "3", "hp" : 45, "name" : "Caterpie", "speed" : 45, "types" : [ "bug" ] }
    { "_id" : ObjectId("564b1dad25337263280d0482"), "attack" : 25, "created" : "2013-11-03T15:05:41.294947", "defense" : 50, "height" : "6", "hp" : 45, "name" : "Kakuna", "speed" : 35, "types" : [ "poison", "bug" ] }


   > db.pokemons.find({}).limit(5).skip(2 * 5)

    { "_id" : ObjectId("564b1dae25337263280d048a"), "attack" : 35, "created" : "2013-11-03T15:05:41.457865", "defense" : 30, "height" : "13", "hp" : 30, "name" : "Gastly", "speed" : 80, "types" : [ "poison", "ghost" ] }
    { "_id" : ObjectId("564b1dae25337263280d048b"), "attack" : 95, "created" : "2013-11-03T15:05:41.456387", "defense" : 180, "height" : "15", "hp" : 50, "name" : "Cloyster", "speed" : 70, "types" : [ "water", "ice" ] }
    { "_id" : ObjectId("564b1dae25337263280d0486"), "attack" : 85, "created" : "2013-11-03T15:05:41.441502", "defense" : 45, "height" : "14", "hp" : 35, "name" : "Doduo", "speed" : 75, "types" : [ "normal", "flying" ] }
    { "_id" : ObjectId("564b1dae25337263280d048c"), "attack" : 105, "created" : "2013-11-03T15:05:41.452237", "defense" : 75, "height" : "12", "hp" : 105, "name" : "Muk", "speed" : 50, "types" : [ "poison" ] }
    { "_id" : ObjectId("564b1daf25337263280d048d"), "attack" : 50, "created" : "2013-11-03T15:05:41.388462", "defense" : 40, "height" : "6", "hp" : 40, "name" : "Poliwag", "speed" : 90, "types" : [ "water" ] }
    >

   ```

## 5 - Um group ou aggregate contando a quantidade de pokemons de cada tipo;

  ```
  > db.pokemons.group({
      initial: {total: 0},
      reduce: function(curr, result) {
        curr.types.forEach(function(type) {
          if(result[type]) {
            result[type]++;
            } else {
              result[type] = 1;
            }
            result.total++;
          });
      }
    });
    [
        {
                "total" : 915,
                "fire" : 47,
                "normal" : 78,
                "water" : 105,
                "bug" : 61,
                "flying" : 77,
                "poison" : 54,
                "ghost" : 34,
                "ice" : 24,
                "fighting" : 38,
                "psychic" : 62,
                "grass" : 75,
                "steel" : 37,
                "electric" : 40,
                "ground" : 51,
                "fairy" : 28,
                "rock" : 46,
                "dark" : 38,
                "dragon" : 20
        }
  ]
  >

  ```

## 6 - Realizar 3 counts na pokemons;

  ```
  >   var query = {types: /fire/i}
  >   db.pokemons.count(query);
  47

  >   var query = {attack: {$gt: 40}}
  >   db.pokemons.count(query);
  534
  >

  >   var query = {attack: {$lt: 100}}
  >   db.pokemons.count(query);
  484
  >
  
  ```
