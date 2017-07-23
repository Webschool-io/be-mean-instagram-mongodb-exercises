# MongoDB - Aula 03 - Exercício
autor: Fábio de Carvalho

## Liste todos Pokemons com a altura menor que 0.5; (passo 1)
```
> var query = {height: {$lt: 0.5}}
> db.pokemons.find(query)
>
```

## Liste todos Pokemons com a altura maior ou igual que 0.5; (passo 2)

```
> var query = {height: {$gte: 0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("5642a225b313f9771f455cf0"), "name" : "Blastoise", "description" : "Tartaruga mal encarada com canhões de água", "type" : "Water", "attack" : 83, "height" : 16 }
{ "_id" : ObjectId("5642a231b313f9771f455cf1"), "name" : "Vulpix", "description" : "Um \"Kyuubi wannabe\" do caralho\"", "type" : "Fire", "attack" : 41, "height" : 6 }
{ "_id" : ObjectId("5642a23fb313f9771f455cf2"), "name" : "Kadabra", "description" : "Neo do mundo pokemon", "type" : "Psychic", "attack" : 35, "height" : 13, "defense" : 30 }
{ "_id" : ObjectId("5642a249b313f9771f455cf3"), "name" : "Hitmonlee", "description" : "O da voadora com os dois pés na cara", "type" : "Fighting", "attack" : 120, "height" : 15 }
{ "_id" : ObjectId("5642a254b313f9771f455cf4"), "name" : "Hitmonchan", "description" : "Soquinho, soquinho, soquinho...", "type" : "Fighting", "attack" : 105, "height" : 14 }
```
## Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama; (passo 3)

```
> var query = {$and: [{ height: {$gte: 0.5 }}, { type: 'Fighting'} ]}
> db.pokemons.find(query)
{ "_id" : ObjectId("5642a249b313f9771f455cf3"), "name" : "Hitmonlee", "description" : "O da voadora com os dois pés na cara", "type" : "Fighting", "attack" : 120, "height" : 15 }
{ "_id" : ObjectId("5642a254b313f9771f455cf4"), "name" : "Hitmonchan", "description" : "Soquinho, soquinho, soquinho...", "type" : "Fighting", "attack" : 105, "height" : 14 }
```

## Liste todos Pokemons com name 'Pikachu' OU com attack menor ou igual que 0.5 (passo 4)

```
> var query = {$or: [{ name: 'Pikachu'}, { attack: {$lte: 0.5}} ]}
> db.pokemons.find(query)
>
```

## Liste todos Pokemons com attack maior ou igual que 48 E com height menor ou igual que 0.5 (passo 5)

```
> var query = {$and: [{ attack: {$gte: 48}}, { height: {$lte: 15}} ]}
> db.pokemons.find(query)
{ "_id" : ObjectId("5642a249b313f9771f455cf3"), "name" : "Hitmonlee", "description" : "O da voadora com os dois pés na cara", "type" : "Fighting", "attack" : 120, "height" : 15 }
{ "_id" : ObjectId("5642a254b313f9771f455cf4"), "name" : "Hitmonchan", "description" : "Soquinho, soquinho, soquinho...", "type" : "Fighting", "attack" : 105, "height" : 14 }
```


