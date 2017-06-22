# MongoDb - Aula 03 - Exercício

autor: Judar Lima

## 1 - Liste todos os Pokemons com a altura menor que 0.5;

```

z10n(MONGOD-3.2.6) be-mean-pokemons> var query = {height: {$lt: 0.5}}
z10n(MONGOD-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5772ffcf54c202b7d67f797c"),
  "name": "Butterfree",
  "description": "Borboletinha cabulosa",
  "type": "inseto",
  "attack": 20,
  "height": 0.3
}
Fetched 1 record(s) in 1ms
```

## 2 - Liste todos os Pokemons com a altura maior ou igual a 0.5;

```
z10n(MONGOD-3.2.6) be-mean-pokemons> var query = {height: {$gte: 0.5}}
z10n(MONGOD-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("577300ca54c202b7d67f797d"),
  "name": "Arbok",
  "description": "Cobra naja gigante",
  "type": "poison",
  "attack": 85,
  "height": 11.6
}
{
  "_id": ObjectId("5773010c54c202b7d67f797e"),
  "name": "Sandshrew",
  "description": "Tatu bola mucho loko",
  "type": "terra",
  "attack": 75,
  "height": 2
}
{
  "_id": ObjectId("5773015754c202b7d67f797f"),
  "name": "Jigglypuff",
  "description": "Melhor que a MC Mellody",
  "type": "fada",
  "attack": 45,
  "height": 1.8
}
{
  "_id": ObjectId("577301cf54c202b7d67f7980"),
  "name": "Hypno",
  "description": "Se o Hypno fosse gente ele seria o Fábio Puentes",
  "type": "psíquico",
  "attack": 73,
  "height": 5.3
}
Fetched 4 record(s) in 3ms
```

## 3 - Liste todos os Pokemons com a altura menor ou igual a 0.5 e do tipo grama;

```
z10n(MONGOD-3.2.6) be-mean-pokemons> var query = {$and: [{height: {$lte: 0.5}}, {type: 'grama'}]}
z10n(MONGOD-3.2.6) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```

## 4 - Liste todos os Pokemons com o nome 'Pikachu' ou com attack menor ou igual a 0.5;

```
var query = {$or: [{name: 'Pikachu'}, {attack: {$lte: 0.5}}]}
z10n(MONGOD-3.2.6) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```

## 5 - Liste todos os Pokemons com o attack maior ou igual a 48 e com height menor ou igual a 0.5;

```
z10n(MONGOD-3.2.6) be-mean-pokemons> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
z10n(MONGOD-3.2.6) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```
