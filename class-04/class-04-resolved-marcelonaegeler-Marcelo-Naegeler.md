# MongoDB - Aula 04 - Exercício
autor: Marcelo André Naegeler

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokémons: Pikachu, Squirtle, Bulbasaur e Charizard.
```
var query = { $or: [ { name: /pikachu/i }, { name: /squirtle/i }, { name: /bulbasaur/i }, { name: /charizard/i } ] };
var mod = { $pushAll: { moves: [ 'dodge', 'throw sand' ] } };
var opts = { multi: true };
db.pokemons.update( query, mod, opts );
Updated 4 existing record(s) in 20ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
```

## **Adicionar** 1 movimento em todos os pokémons: `avoid`.##
```
var query = {};
var mod = { $push: { moves: 'avoid' } };
var opts = { multi: true };
db.pokemons.update( query, mod, opts );
Updated 4 existing record(s) in 9ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
```

## **Adicionar** o pokémon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
var query = { name: /aindanaoexistemon/i };
var mod = { $setOnInsert: {
  name: "AindaNaoExisteMon"
  , attack: null
  , height: null
  , defense: null
  , moves: []
  , description: 'Sem maiores informações'
} };
var opts = { upsert: true };
db.pokemons.update( query, mod, opts );
Updated 1 new record(s) in 10ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564be9c6fe48e9e114ad323c")
})
```

## Pesquisar todos o pokémons que possuam o ataque `dodge` e mais um que você adicionou, escolha seu pokémon favorito.##
```
var query = { moves: { $in: [ /dodge/i, /thunder shock/i ] } };
> db.pokemons.find( query ).pretty();
{
  "_id" : ObjectId("56448fcf8d9cce899a4271c4"),
  "name" : "Pikachu",
  "description" : "Awesome eletric pokémon",
  "attack" : 20,
  "defense" : 5,
  "height" : 45,
  "type" : "electric",
  "moves" : [
    "dodge",
    "throw sand",
    "thunder shock"
  ]
}
{
  "_id" : ObjectId("56448fcf8d9cce899a4271c5"),
  "name" : "Bulbasaur",
  "description" : "Grass pokémon",
  "attack" : 18,
  "defense" : 15,
  "height" : 60,
  "type" : "grass",
  "moves" : [
    "dodge",
    "throw sand"
  ]
}
{
  "_id" : ObjectId("56448fcf8d9cce899a4271c6"),
  "name" : "Charizard",
  "description" : "Fire pokémon",
  "attack" : 25,
  "defense" : 10,
  "height" : 100,
  "type" : "fire",
  "moves" : [
    "dodge",
    "throw sand"
  ]
}
{
  "_id" : ObjectId("56448fcf8d9cce899a4271c7"),
  "name" : "Squirtle",
  "description" : "Water pokémon",
  "attack" : 15,
  "defense" : 8,
  "height" : 45,
  "type" : "water",
  "moves" : [
    "dodge",
    "throw sand"
  ]
}
```

## Pesquisar **todos** os pokemons que não são do tipo `electric`.##
```
var query = { type: { $ne: 'electric' } };
> db.pokemons.find( query ).pretty()
{
  "_id" : ObjectId("56448fcf8d9cce899a4271c5"),
  "name" : "Bulbasaur",
  "description" : "Grass pokémon",
  "attack" : 18,
  "defense" : 15,
  "height" : 60,
  "type" : "grass",
  "moves" : [
    "dodge",
    "throw sand"
  ]
}
{
  "_id" : ObjectId("56448fcf8d9cce899a4271c6"),
  "name" : "Charizard",
  "description" : "Fire pokémon",
  "attack" : 25,
  "defense" : 10,
  "height" : 100,
  "type" : "fire",
  "moves" : [
    "dodge",
    "throw sand"
  ]
}
{
  "_id" : ObjectId("56448fcf8d9cce899a4271c7"),
  "name" : "Squirtle",
  "description" : "Water pokémon",
  "attack" : 15,
  "defense" : 8,
  "height" : 45,
  "type" : "water",
  "moves" : [
    "dodge",
    "throw sand"
  ]
}
{
  "_id" : ObjectId("56448fcf8d9cce899a4271c8"),
  "name" : "Caterpie",
  "description" : "Bug pokémon",
  "attack" : 0,
  "defense" : 20,
  "height" : 20,
  "type" : "bug"
}
{
  "_id" : ObjectId("565369b69d7a56c26c5d0a7a"),
  "name" : "AindaNaoExisteMon",
  "attack" : null,
  "height" : null,
  "defense" : null,
  "moves" : [ ],
  "description" : "Sem maiores informações"
}
```

## Pesquisar **todos** os pokemons que tenham o ataque `throw sand` **E** tenham a defesa **não menor ou igual** a 10.##
```
var query = { $and: [ { moves: { $in: [ /throw sand/i ] } }, { defense: { $gt: 10 } } ] };
> db.pokemons.find( query ).pretty();
{
  "_id" : ObjectId("56448fcf8d9cce899a4271c5"),
  "name" : "Bulbasaur",
  "description" : "Grass pokémon",
  "attack" : 18,
  "defense" : 15,
  "height" : 60,
  "type" : "grass",
  "moves" : [
    "dodge",
    "throw sand"
  ]
}
```

## Remova **todos** os pokemons do tipo `water` e com attack menor que 50.
```
var query = { $and: [ { type: 'water' }, { attack: { $lt: 50 } } ] };
> db.pokemons.remove( query );
WriteResult({ "nRemoved" : 1 })
```
