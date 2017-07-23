# MongoDB - Aula 03 - Exercício
Autor: Jackson de Fraga
Github: https://github.com/jacksonfraga/

## Listando todos os pokemons com altura menor que 0.5

```
var query = { height : { $lt: 0.5 }}
db.pokemons.find(query)
```

## Listando todos os pokemons com altura maior ou igual que 0.5

```
var query = { height : { $gte: 0.5 }}
db.pokemons.find(query)
```

## Listando todos os pokemons com altura menor ou igual que 0.5 e tipo grama

```

var query = { $and : [ { height: { $lte : 0.5 } }, { type: 'grama' } ] }
db.pokemons.find(query)
```

## Listando todos os pokemons com nome 'Pikachu' ou com attack menor ou igual que 0.5

```
var query = { $or : [ { attack: { $lte : 0.5 } }, { name: 'Pikachu' } ] }
db.pokemons.find(query)
```

## Listando todos os pokemons attack maior ou igual que 48 e com height menor ou igual que 0.5

```
var query = { $or : [ { attack: { $gte : 48 } }, { height: { $lte : 0.5 } } ] }
db.pokemons.find(query)
```
