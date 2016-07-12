# MongoDB - Aula 05 - Exercício
autor: Jackson Ricardo Schroeder


# Importar as collections restaurantes e pokemons

```
macminixereda:aula05 xereda$ mongoimport --db be-mean --collection restaurantes --file restaurantes.json --drop
2016-05-20T17:34:42.832-0300	connected to: localhost
2016-05-20T17:34:42.833-0300	dropping: be-mean.restaurantes
2016-05-20T17:34:45.295-0300	imported 25359 documents

macminixereda:aula05 xereda$ mongoimport --db be-mean --collection pokemons --file pokemons.json --drop
2016-05-20T17:35:37.398-0300	connected to: localhost
2016-05-20T17:35:37.399-0300	dropping: be-mean.pokemons
2016-05-20T17:35:38.279-0300	imported 610 documents
```

# Distinct por cuisine na restaurantes

```
macminixereda(mongod-3.2.0) be-mean> db.restaurantes.distinct("cuisine").sort();
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

# Distinct por types na pokemons

```
macminixereda(mongod-3.2.0) be-mean> db.pokemons.distinct("types").sort();
[
  "bug",
  "dark",
  "dragon",
  "electric",
  "fairy",
  "fighting",
  "fire",
  "flying",
  "ghost",
  "grass",
  "ground",
  "ice",
  "normal",
  "poison",
  "psychic",
  "rock",
  "steel",
  "water"
]
```

# As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)
### Pagina 1

```
macminixereda(mongod-3.2.0) be-mean> var query = {};
macminixereda(mongod-3.2.0) be-mean> var campos = { name: 1, _id: 0 };
macminixereda(mongod-3.2.0) be-mean> var qtDocumentosPag = 5;
macminixereda(mongod-3.2.0) be-mean> db.pokemons.find(query, campos).limit(qtDocumentosPag).skip(qtDocumentosPag * 0);
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
{
  "name": "Caterpie"
}
Fetched 5 record(s) in 3ms
macminixereda(mongod-3.2.0) be-mean> db.pokemons.find(query, campos).limit(qtDocumentosPag).skip(qtDocumentosPag * 1);
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
  "name": "Rattata"
}
{
  "name": "Kakuna"
}
Fetched 5 record(s) in 2ms
macminixereda(mongod-3.2.0) be-mean> db.pokemons.find(query, campos).limit(qtDocumentosPag).skip(qtDocumentosPag * 2);
{
  "name": "Farfetchd"
}
{
  "name": "Seel"
}
{
  "name": "Doduo"
}
{
  "name": "Dewgong"
}
{
  "name": "Dodrio"
}
Fetched 5 record(s) in 1ms
```

# Group ou Aggregate contando a quantidade de pokemons de cada tipo
### Com group

```
db.pokemons.group({
	initial: { total: 0 },                   // inicializa variaveis dentro do group
	reduce: function(curr, result) {         // reduce recebe uma funcao, onde o parametro curr eh o cursor e result eh o acumulado
		curr.types.forEach(function(type) {    // percorre todo os elementos da array types[]
			if (result[type]) {                  // caso já tenha iniciado o contador para o tipo corrente, incrimenta mais um
				result[type]++;                    // incrimenta
			} else {
				result[type] = 1;                  // caso for a primeira vez do type, inicializa o contador
			}
			result.total++;                      // conta quantas types tem na colecao independente da repitacao do type em varios documentos
		});
	}
});

[
  {
    "total": 915,
    "fire": 47,
    "water": 105,
    "bug": 61,
    "flying": 77,
    "normal": 78,
    "poison": 54,
    "ice": 24,
    "ghost": 34,
    "steel": 37,
    "electric": 40,
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

# Realizar 3 counts na pokemons

### Todos

```
db.pokemons.count()

610
```

### Só do tipo fire

```
db.pokemons.count({ types: "fire" })

47
```

### Só dos que tem ataque maior que 70

```
db.pokemons.count({ attack: {$gt: 70} })

310
```
