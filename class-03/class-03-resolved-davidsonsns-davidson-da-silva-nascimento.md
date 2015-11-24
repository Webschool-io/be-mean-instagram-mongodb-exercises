# MongoDB - Aula 03 - Exercício
autor: Davidson da Silva Nascimento
#### Foi inserido o Pikachu, para melhor demonstração
```js
> db.pokemons.insert({name: "Pikachu", attack: 55, defense: 40, height: 0.4})
WriteResult({ "nInserted" : 1 })
>
```
## Liste todos Pokemons com a altura **menor que** 0.5
```js
> var query = {height: {$lt: 0.5}}
> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("5652f5aae73644cad08260c8"),
        "name" : "Pikachu",
        "attack" : 55,
        "defense" : 40,
        "height" : 0.4
}
>
```
## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```js
> var query = {height: {$gte: 0.5}}
> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("565222b99a8f50a878c10890"),
        "name" : "Mewtwo",
        "description" : "Pokemon sangue nu ZÓI",
        "attack" : 110,
        "defense" : 90,
        "height" : 2
}
{
        "_id" : ObjectId("565222b99a8f50a878c10891"),
        "name" : "Charizard",
        "description" : "Cospe fogo que é quente o suficiente para derreter rochas. Conhecido por causar incêndios florestais sem querer.",
        "attack" : 84,
        "defense" : 78,
        "height" : 1.7
}
{
        "_id" : ObjectId("565222b99a8f50a878c10892"),
        "name" : "Yveltal",
        "description" : "Quando sua vida chega ao fim, ele absorve a energia davida de todos os seres vivos e se transforma em um casulo mais uma vez.",
        "attack" : 131,
        "defense" : 95,
        "height" : 5.8
}
{
        "_id" : ObjectId("565222b99a8f50a878c10893"),
        "name" : "Alakazam",
        "description" : "Um aroma sedutor exala de sua flor. A fragrância deixacalmo seus oponentes em uma batalha.",
        "attack" : 50,
        "defense" : 45,
        "height" : 1.5
}
{
        "_id" : ObjectId("565222b99a8f50a878c10894"),
        "name" : "Zoroark",
        "description" : "Eles protegem seu covil com cenário ilusório.",
        "attack" : 105,
        "defense" : 60,
        "height" : 1.6
}
{
        "_id" : ObjectId("565222b99a8f50a878c10895"),
        "name" : "Zubat",
        "description" : "Quando ela cresce, ela lança a pele, cobre-se com seda, e torna-se um casulo.",
        "attack" : 45,
        "defense" : 35,
        "height" : 0.8
}
{
        "_id" : ObjectId("565222b99a8f50a878c10896"),
        "name" : "Aggron",
        "description" : "Suas balas de água pode pregar precisamente latas de uma distância de mais de 160 pés.",
        "attack" : 110,
        "defense" : 180,
        "height" : 2.1
}
>
```
## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```js
> var query = {$and: [{height: {$lte: 0.5}}, {type: /grama/i}]}
> db.pokemons.find(query)
>
```
## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```js
> var query = {$or: [{name: 'Pikachu'}, {attack: {$lte: 0.5}}]}
> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("5652f5aae73644cad08260c8"),
        "name" : "Pikachu",
        "attack" : 55,
        "defense" : 40,
        "height" : 0.4,
        "type" : "Elétrico"
}
>
```
## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```js
> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("5652f5aae73644cad08260c8"),
        "name" : "Pikachu",
        "attack" : 55,
        "defense" : 40,
        "height" : 0.4,
        "type" : "Elétrico"
}
>
```