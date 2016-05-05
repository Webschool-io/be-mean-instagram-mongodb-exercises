# MongoDB - Aula 03 - Exercício
Autor: Abel Neto

## Pokémons com altura menor que 0.5

```
be-mean-pokemons> var query = { height: { $lt: 0.5 } }
be-mean-pokemons> db.pokemons.find(query);
```

## Pokémons com altura maior ou igual a 0.5

```
be-mean-pokemons> var query = { height: { $gte: 0.5 } }
be-mean-pokemons> db.pokemons.find(query);
```

## Pokémons com altura maior ou igual a 0.5

```
be-mean-pokemons> var query = { $and: [{ height: { $lte: 0.5 } }, { type: 'grass' }] }
be-mean-pokemons> db.pokemons.find(query);
```

## Pokémons com nome 'Pikachu' ou com attack menor ou igual a 0.5

```
be-mean-pokemons> var query = { $or: [{ attack: { $lte: 0.5 } }, { name: 'Pikachu' }] }
be-mean-pokemons> db.pokemons.find(query);
```

## Pokémons com nome attack maior ou igual a 48 e altura menor ou igual a 0.5

```
be-mean-pokemons> var query = { $and: [{ attack: { $gte: 48 } }, { height: { $lte: 0.5 } }] }
be-mean-pokemons> db.pokemons.find(query);
```
