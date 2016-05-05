## 1. Importar as collections restaurantes e pokemons
```
***IMPORTE DA COLEÇÃO RESTAURANTES***
mick@Vostro-3500:~/Documents/Repos/be-mean-instagram-mongodb/data$ mongoimport -d be-mean-william -c restaurantes --drop --file restaurantes.json
connected to: 127.0.0.1
2015-12-02T11:38:42.059-0200 dropping: be-mean-william.restaurantes
2015-12-02T11:38:43.096-0200 check 9 25359
2015-12-02T11:38:43.141-0200 imported 25359 objects

***IMPORTE DA COLEÇÃO POKEMONS***
mick@Vostro-3500:~/Documents/Repos/be-mean-instagram-mongodb/data$ mongoimport -d be-mean-william -c pokemons --drop --file pokemons-william.json
connected to: 127.0.0.1
2015-12-02T11:40:20.111-0200 dropping: be-mean-william.pokemons
2015-12-02T11:40:20.135-0200 check 9 610
2015-12-02T11:40:20.135-0200 imported 610 objects

```
## 2. Distinct por `cuisine` na restaurantes
```
> db.restaurantes.distinct('cuisine')
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
## 3. Distinct por `types` na pokemons
```
Vostro-3500(mongod-2.6.10) be-mean-william> db.pokemons.distinct('types')
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
## 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)
```
Vostro-3500(mongod-2.6.10) be-mean-william> db.pokemons.find().limit(5).skip(2*0)
Vostro-3500(mongod-2.6.10) be-mean-william> db.pokemons.find().limit(5).skip(2*1)
Vostro-3500(mongod-2.6.10) be-mean-william> db.pokemons.find().limit(5).skip(2*2)
```
## 5 . Group ou Aggregate contando a quantidade de pokemons de cada tipo
```
db.pokemons.group({
  initial: {total: 0},
  reduce: function(curr, result){
    curr.types.forEach(function(type) {
      if (result[type]) {
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

## 6. Realizar 3 counts na pokemons.

# -> .count -- todos
```
Vostro-3500(mongod-2.6.10) be-mean-william> db.pokemons.find().count()
610
```
# -> .count -- só tipo fogo
```
Vostro-3500(mongod-2.6.10) be-mean-william> db.pokemons.find({types: 'fire'}).count()
47
```
# -> .count -- só de quantos tem a defesa maior que 70
```
Vostro-3500(mongod-2.6.10) be-mean-william> var query = {defense: {$gt: 70}}
Vostro-3500(mongod-2.6.10) be-mean-william> query
{
  "defense": {
    "$gt": 70
  }
}
Vostro-3500(mongod-2.6.10) be-mean-william> db.pokemons.find(query).count()
250
```
