# Exercício 05
# Autor: Guilherme Pendezza de Sousa

# 1 - Importar as collections restaurantes e pokemons

#Importando os pokemons
guilherme@guilherme-notebook:~/desenvolvimento/estudo/be-mean/mongo/be-mean-instagram-mongodb-excercises$ mongoimport --host 127.0.0.1 --file pokemons.json --db be-mean --collection pokemons --drop
2015-12-09T16:42:45.895-0200	connected to: 127.0.0.1
2015-12-09T16:42:45.896-0200	dropping: be-mean.pokemons
2015-12-09T16:42:45.924-0200	imported 610 documents
guilherme@guilherme-notebook:~/desenvolvimento/estudo/be-mean/mongo/be-mean-instagram-mongodb-excercises$

#Importando os restaurantes
$ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-11-10T16:04:38.818-0200    connected to: localhost
2015-11-10T16:04:38.819-0200    dropping: be-mean.restaurantes
2015-11-10T16:04:40.488-0200    imported 25359 documents

# 2 - Distinct por 'cuisine' na restaurantes
guilherme-notebook(mongod-3.0.7) be-mean> db.restaurantes.distinct('cuisine')
[
  "Irish",
  "Hamburgers",
  "American ",
  "Bakery",
  "Jewish/Kosher",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Delicatessen",
  "Chinese",
  "Other",
  "Caribbean",
  "Chicken",
  "Turkish",
  "Donuts",
  "Sandwiches/Salads/Mixed Buffet",
  "Bagels/Pretzels",
  "Continental",
  "Pizza",
  "Steak",
  "Italian",
  "Polish",
  "French",
  "German",
  "Pizza/Italian",
  "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
  "Mexican",
  "Spanish",
  "Café/Coffee/Tea",
  "Tex-Mex",
  "Pancakes/Waffles",
  "Soul Food",
  "Hotdogs",
  "Seafood",
  "Not Listed/Not Applicable",
  "Greek",
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
guilherme-notebook(mongod-3.0.7) be-mean>

# 3 - Distinct por types na pokemons
guilherme-notebook(mongod-3.0.7) be-mean> db.pokemons.distinct('types')
[
  "fire",
  "water",
  "bug",
  "normal",
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
guilherme-notebook(mongod-3.0.7) be-mean>


# 4 - As primeiras páginas com .limit() e .skip() de pokemons
guilherme-notebook(mongod-3.0.7) be-mean> db.pokemons.find({}).limit(5).skip(5 * 0)
{
  "_id": ObjectId("564b1dad25337263280d047b"),
  "attack": 64,
  "created": "2013-11-03T15:05:41.273462",
  "defense": 58,
  "height": "11",
  "hp": 58,
  "name": "Charmeleon",
  "speed": 80,
  "types": [
    "fire"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d047c"),
  "attack": 63,
  "created": "2013-11-03T15:05:41.280718",
  "defense": 80,
  "height": "10",
  "hp": 59,
  "name": "Wartortle",
  "speed": 58,
  "types": [
    "water"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d047e"),
  "attack": 30,
  "created": "2013-11-03T15:05:41.285736",
  "defense": 35,
  "height": "3",
  "hp": 45,
  "name": "Caterpie",
  "speed": 45,
  "types": [
    "bug"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d0479"),
  "attack": 56,
  "created": "2013-11-03T15:05:41.305777",
  "defense": 35,
  "height": "3",
  "hp": 30,
  "name": "Rattata",
  "speed": 72,
  "types": [
    "normal"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d047f"),
  "attack": 20,
  "created": "2013-11-03T15:05:41.288107",
  "defense": 55,
  "height": "7",
  "hp": 50,
  "name": "Metapod",
  "speed": 30,
  "types": [
    "bug"
  ]
}
Fetched 5 record(s) in 2ms
guilherme-notebook(mongod-3.0.7) be-mean> db.pokemons.find({}).limit(5).skip(5 * 1)
{
  "_id": ObjectId("564b1dad25337263280d0481"),
  "attack": 60,
  "created": "2013-11-03T15:05:41.310402",
  "defense": 30,
  "height": "3",
  "hp": 40,
  "name": "Spearow",
  "speed": 70,
  "types": [
    "normal",
    "flying"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d0482"),
  "attack": 25,
  "created": "2013-11-03T15:05:41.294947",
  "defense": 50,
  "height": "6",
  "hp": 45,
  "name": "Kakuna",
  "speed": 35,
  "types": [
    "poison",
    "bug"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d047a"),
  "attack": 52,
  "created": "2013-11-03T15:05:41.271082",
  "defense": 43,
  "height": "6",
  "hp": 39,
  "name": "Charmander",
  "speed": 65,
  "types": [
    "fire"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d0483"),
  "attack": 65,
  "created": "2013-11-03T15:05:41.439497",
  "defense": 55,
  "height": "8",
  "hp": 52,
  "name": "Farfetchd",
  "speed": 60,
  "types": [
    "normal",
    "flying"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d047d"),
  "attack": 83,
  "created": "2013-11-03T15:05:41.282985",
  "defense": 100,
  "height": "16",
  "hp": 79,
  "name": "Blastoise",
  "speed": 78,
  "types": [
    "water"
  ]
}
Fetched 5 record(s) in 25ms
guilherme-notebook(mongod-3.0.7) be-mean> db.pokemons.find({}).limit(5).skip(5 * 2)
{
  "_id": ObjectId("564b1dae25337263280d0484"),
  "attack": 35,
  "created": "2013-11-03T15:05:41.435237",
  "defense": 70,
  "height": "3",
  "hp": 25,
  "name": "Magnemite",
  "speed": 45,
  "types": [
    "steel",
    "electric"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d0487"),
  "attack": 45,
  "created": "2013-11-03T15:05:41.445749",
  "defense": 55,
  "height": "11",
  "hp": 65,
  "name": "Seel",
  "speed": 45,
  "types": [
    "water"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d0488"),
  "attack": 110,
  "created": "2013-11-03T15:05:41.443720",
  "defense": 70,
  "height": "18",
  "hp": 60,
  "name": "Dodrio",
  "speed": 100,
  "types": [
    "normal",
    "flying"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d0489"),
  "attack": 70,
  "created": "2013-11-03T15:05:41.447897",
  "defense": 80,
  "height": "17",
  "hp": 90,
  "name": "Dewgong",
  "speed": 70,
  "types": [
    "water",
    "ice"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d048a"),
  "attack": 35,
  "created": "2013-11-03T15:05:41.457865",
  "defense": 30,
  "height": "13",
  "hp": 30,
  "name": "Gastly",
  "speed": 80,
  "types": [
    "poison",
    "ghost"
  ]
}
Fetched 5 record(s) in 3ms
guilherme-notebook(mongod-3.0.7) be-mean>

# 5 - Group ou aggregate contando a quantidade de pokemons de cada tipo
db.pokemons.aggregate([
  {$unwind: "$types"},
  {
    $group: {
      _id: '$types',
      count: {$sum: 1}
    }
  },
  {$project: { _id: 0, tipo: "$_id", count: 1 } }
]);

db.pokemons.group({
    initial: { total: 0},
    reduce: function(curr, result){
      result.total++;
      curr.types.forEach(function(type){
        if(result[type]){
          result[type] += 1;
        } else {
          result[type] = 1;
        }
      })
    }
});


# 6 - Realizar 3 counts na pokemons
#   -> todos
guilherme-notebook(mongod-3.0.7) be-mean> db.pokemons.count({})
610
guilherme-notebook(mongod-3.0.7) be-mean>

#   -> só tipo fogo
guilherme-notebook(mongod-3.0.7) be-mean> db.pokemons.count({types: 'fire'})
47
guilherme-notebook(mongod-3.0.7) be-mean>

#   -> só de quantos tem a defesa maior que 70
guilherme-notebook(mongod-3.0.7) be-mean> db.pokemons.count({defense: {$gt: 70}})
250
guilherme-notebook(mongod-3.0.7) be-mean>
