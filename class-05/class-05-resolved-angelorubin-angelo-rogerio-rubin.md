MongoDB - Aula 05 - Exercício
autor: Angelo Rogério Rubin

## 1. Importar as collections restaurantes e pokemons

PS C:\> mongoimport --db be-mean --collection restaurantes --drop --file data/restaurantes.json
2015-11-20T15:58:01.697-0200    connected to: localhost
2015-11-20T15:58:01.700-0200    dropping: be-mean.restaurantes
2015-11-20T15:58:02.968-0200    imported 25359 documents

PS C:\> mongoimport --db be-mean --collection pokemons --drop --file data/pokemons.json
2015-11-20T15:58:50.773-0200    connected to: localhost
2015-11-20T15:58:50.774-0200    dropping: be-mean.pokemons
2015-11-20T15:58:50.795-0200    imported 610 documents

## 2. Distinct por cuisine na restaurantes

db.restaurantes.distinct('cuisine')

/* 1 */
{
    "0" : "Bakery",
    "1" : "Hamburgers",
    "2" : "American ",
    "3" : "Irish",
    "4" : "Jewish/Kosher",
    "5" : "Delicatessen",
    "6" : "Ice Cream, Gelato, Yogurt, Ices",
    "7" : "Chinese",
    "8" : "Other",
    "9" : "Chicken",
    "10" : "Turkish",
    "11" : "Caribbean",
    "12" : "Donuts",
    "13" : "Sandwiches/Salads/Mixed Buffet",
    "14" : "Bagels/Pretzels",
    "15" : "Continental",
    "16" : "Pizza",
    "17" : "Italian",
    "18" : "Steak",
    "19" : "Polish",
    "20" : "German",
    "21" : "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
    "22" : "French",
    "23" : "Pizza/Italian",
    "24" : "Mexican",
    "25" : "Spanish",
    "26" : "Café/Coffee/Tea",
    "27" : "Tex-Mex",
    "28" : "Pancakes/Waffles",
    "29" : "Soul Food",
    "30" : "Seafood",
    "31" : "Hotdogs",
    "32" : "Greek",
    "33" : "Not Listed/Not Applicable",
    "34" : "African",
    "35" : "Japanese",
    "36" : "Indian",
    "37" : "Armenian",
    "38" : "Thai",
    "39" : "Chinese/Cuban",
    "40" : "Mediterranean",
    "41" : "Korean",
    "42" : "Bottled beverages, including water, sodas, juices, etc.",
    "43" : "Russian",
    "44" : "Eastern European",
    "45" : "Middle Eastern",
    "46" : "Asian",
    "47" : "Ethiopian",
    "48" : "Vegetarian",
    "49" : "Barbecue",
    "50" : "English",
    "51" : "Egyptian",
    "52" : "Sandwiches",
    "53" : "Portuguese",
    "54" : "Indonesian",
    "55" : "Chinese/Japanese",
    "56" : "Filipino",
    "57" : "Juice, Smoothies, Fruit Salads",
    "58" : "Brazilian",
    "59" : "Afghan",
    "60" : "Vietnamese/Cambodian/Malaysia",
    "61" : "CafÃ©/Coffee/Tea",
    "62" : "Soups & Sandwiches",
    "63" : "Tapas",
    "64" : "Moroccan",
    "65" : "Pakistani",
    "66" : "Peruvian",
    "67" : "Bangladeshi",
    "68" : "Czech",
    "69" : "Salads",
    "70" : "Creole",
    "71" : "Fruits/Vegetables",
    "72" : "Iranian",
    "73" : "Cajun",
    "74" : "Scandinavian",
    "75" : "Polynesian",
    "76" : "Soups",
    "77" : "Australian",
    "78" : "Hotdogs/Pretzels",
    "79" : "Southwestern",
    "80" : "Nuts/Confectionary",
    "81" : "Hawaiian",
    "82" : "Creole/Cajun",
    "83" : "Californian",
    "84" : "Chilean"
}

## 3. Distinct por types na pokemons

db.pokemons.distinct('types')

/* 1 */
{
    "0" : "normal",
    "1" : "fire",
    "2" : "water",
    "3" : "bug",
    "4" : "flying",
    "5" : "poison",
    "6" : "electric",
    "7" : "steel",
    "8" : "ghost",
    "9" : "ice",
    "10" : "fighting",
    "11" : "psychic",
    "12" : "grass",
    "13" : "ground",
    "14" : "fairy",
    "15" : "rock",
    "16" : "dark",
    "17" : "dragon"
}

## 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)

db.pokemons.find( {}, { name : 1, _id : 0 } ).limit(5).skip(5 * 0)

/* 1 */
{
    "name" : "Rattata"
}

/* 2 */
{
    "name" : "Charmeleon"
}

/* 3 */
{
    "name" : "Charmander"
}

/* 4 */
{
    "name" : "Blastoise"
}

/* 5 */
{
    "name" : "Caterpie"
}

db.pokemons.find( {}, { name : 1, _id : 0 } ).limit(5).skip(5 * 1)

/* 1 */
{
    "name" : "Metapod"
}

/* 2 */
{
    "name" : "Butterfree"
}

/* 3 */
{
    "name" : "Spearow"
}

/* 4 */
{
    "name" : "Kakuna"
}

/* 5 */
{
    "name" : "Farfetchd"
}

db.pokemons.find( {}, { name : 1, _id : 0 } ).limit(5).skip(5 * 2)

/* 1 */
{
    "name" : "Magneton"
}

/* 2 */
{
    "name" : "Magnemite"
}

/* 3 */
{
    "name" : "Doduo"
}

/* 4 */
{
    "name" : "Seel"
}

/* 5 */
{
    "name" : "Dodrio"
}

## 5 . Group ou Aggregate contando a quantidade de pokemons de cada tipo

db.pokemons.aggregate(
    [
        {
            $unwind: "$types"
        },
        {
            $group : 
            {
                '_id' : '$types',
                'total' : { '$sum' : 1 }
            }
        }
    ]
);

/* 1 */
{
    "result" : [ 
        {
            "_id" : "fairy",
            "total" : 28.0000000000000000
        }, 
        {
            "_id" : "psychic",
            "total" : 62.0000000000000000
        }, 
        {
            "_id" : "fighting",
            "total" : 38.0000000000000000
        }, 
        {
            "_id" : "dark",
            "total" : 38.0000000000000000
        }, 
        {
            "_id" : "ground",
            "total" : 51.0000000000000000
        }, 
        {
            "_id" : "grass",
            "total" : 75.0000000000000000
        }, 
        {
            "_id" : "electric",
            "total" : 40.0000000000000000
        }, 
        {
            "_id" : "steel",
            "total" : 37.0000000000000000
        }, 
        {
            "_id" : "rock",
            "total" : 46.0000000000000000
        }, 
        {
            "_id" : "flying",
            "total" : 77.0000000000000000
        }, 
        {
            "_id" : "fire",
            "total" : 47.0000000000000000
        }, 
        {
            "_id" : "ice",
            "total" : 24.0000000000000000
        }, 
        {
            "_id" : "bug",
            "total" : 61.0000000000000000
        }, 
        {
            "_id" : "poison",
            "total" : 54.0000000000000000
        }, 
        {
            "_id" : "ghost",
            "total" : 34.0000000000000000
        }, 
        {
            "_id" : "dragon",
            "total" : 20.0000000000000000
        }, 
        {
            "_id" : "water",
            "total" : 105.0000000000000000
        }, 
        {
            "_id" : "normal",
            "total" : 78.0000000000000000
        }
    ],
    "ok" : 1.0000000000000000
}

## 6. Realizar 3 counts na pokemons.

#### count - todos os pokemons
db.pokemons.count() // 610

#### count - só do tipo fogo
db.pokemons.count({ types: 'fire' }) // 47

#### count -- só de quantos tem a defesa maior que 70
db.pokemons.count({ defense: { $gte : 70 } }) // 295