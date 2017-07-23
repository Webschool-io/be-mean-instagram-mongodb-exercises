# MongoDB - Aula 03 - Exercício
Autor: Evellyn Montalvão

## Liste pokémons com altura menor que 0.5

```
use be-mean-pokemons
switched to db be-mean-pokemons
var query = {height: {$lt: 0.5}}
query
{
"height": {
"$lt": 0.5
}
}
db.pokemons.find(query)
{
"_id": ObjectId("57afe7fdef96c0ea464330de"),
"nome": "eevee",
"description": "The pokemon that has my name",
"attack": 30,
"defense": 20,
"height": 0.3
}
Fetched 1 record(s) in 2ms
	
```
## Liste todos os pokémons com altura maior ou igual a 0.5

``` 
var query = {height: {$gte: 0.5}}
db.pokemons.find(query)
{
"_id": ObjectId("57afe503ef96c0ea464330d5"),
"nome": "dragonair",
"description": "Dragonair stores an enormous amount of energy inside its body",
"attack": 40,
"defense": 30,
"height": 4
}
{
"_id": ObjectId("57afe680ef96c0ea464330d6"),
"nome": "aurorus",
"description": "The diamond-shaped crystals body",
"attack": 40,
"defense": 30,
"height": 2.4
}
{
"_id": ObjectId("57afe737ef96c0ea464330d7"),
"nome": "reshiram",
"description": "This legendary Pokémon can scorch the world with fire",
"attack": 60,
"defense": 40,
"height": 3.2
}
{
"_id": ObjectId("57afe73eef96c0ea464330d8"),
"nome": "archeops",
"description": "They are intelligent and will cooperate to catch prey",
"attack": 70,
"defense": 30,
"height": 1.4
}
{
"_id": ObjectId("57afe745ef96c0ea464330d9"),
"nome": "liepard",
"description": "They run silently in the night.",
"attack": 50,
"defense": 20,
"height": 1.1
}
{
"_id": ObjectId("57afe74eef96c0ea464330da"),
"nome": "emboar",
"description": "It cares deeply about its friends.",
"attack": 60,
"defense": 30,
"height": 1.6
}
{
"_id": ObjectId("57afe75cef96c0ea464330db"),
"nome": "tangrowth",
"description": "It ensnares prey by extending arms made of vines. ",
"attack": 50,
"defense": 50,
"height": 2
}
{
"_id": ObjectId("57afe7edef96c0ea464330dc"),
"nome": "margmortar",
"description": "It blasts fireballs of over 3,600 degrees Fahrenheit ",
"attack": 50,
"defense": 30,
"height": 1.6
}
{
"_id": ObjectId("57afe7f6ef96c0ea464330dd"),
"nome": "weavile",
"description": "It lives in snowy regions",
"attack": 60,
"defense": 30,
"height": 1.1
}
Fetched 9 record(s) in 3ms

```

## Liste todos os pokémons com altura menor ou igual a 0.5 E ataque maior que 10 (Troquei pois não coloquei tipo nos meus)
	
```
var query = {$and: [{height: {$lte: 0.5}},{attack: {$gt: 10}}]}
db.pokemons.find(query)
{
"_id": ObjectId("57afe7fdef96c0ea464330de"),
"nome": "eevee",
"description": "The pokemon that has my name",
"attack": 30,
"defense": 20,
"height": 0.3
}
Fetched 1 record(s) in 1ms

```

## Liste todos os pokémons com o nome 'Dragonair' OU com ataque menor ou igual a 40

```
var query = {$or: [{nome: 'dragonair'},{attack: {$lt: 40}}]}
db.pokemons.find(query)
{
"_id": ObjectId("57afe503ef96c0ea464330d5"),
"nome": "dragonair",
"description": "Dragonair stores an enormous amount of energy inside its body",
"attack": 40,
"defense": 30,
"height": 4
}
{
"_id": ObjectId("57afe7fdef96c0ea464330de"),
"nome": "eevee",
"description": "The pokemon that has my name",
"attack": 30,
"defense": 20,
"height": 0.3
}

```


## Liste todos os pokémons com ataque maior ou igual a 48 E com height menor ou igual a 0.5

```
var query = {$and: [{attack:{$gte: 48}},{height:{$lte: 0.5}}]}
db.pokemons.find(query)
Fetched 0 record(s) in 2ms

```
