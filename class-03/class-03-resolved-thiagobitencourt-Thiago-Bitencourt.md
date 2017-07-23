# MongoDB - Aula 03 - Exercício
autor: Thiago R. M. Bitencourt

## 1. Pokemons com altura menor que 0.5
```
> var query = {height: {$lt: 0.5}}
> db.pokemons.find(query).pretty()
{
	"_id" : ObjectId("5779c658ebea693787997606"),
	"name" : "Vulpix",
	"description" : "Fofo porém mortal",
	"type" : "fogo",
	"attack" : 41,
	"height" : 0.4
}
{
	"_id" : ObjectId("577b1901fe6950263ad63a64"),
	"name" : "Butterfree",
	"description" : "In battle, it flaps its wings at high speed to release highly toxic dust into the air.",
	"type" : "inseto",
	"attack" : 45,
	"defense" : 50,
	"height" : 0.3,
	"heigth" : 0.3
}
{
	"_id" : ObjectId("577b1901fe6950263ad63a66"),
	"name" : "Ninetales",
	"description" : "Its nine tails are said to be imbued with a mystic power. It can live for a thousand years.",
	"type" : "fogo",
	"attack" : 76,
	"defense" : 75,
	"height" : 0.3
}
{
	"_id" : ObjectId("577b1901fe6950263ad63a67"),
	"name" : "Grimer",
	"description" : "Appears in filthy areas. Thrives by sucking up polluted sludge that is pumped out of factories.",
	"type" : "veneno",
	"attack" : 80,
	"defense" : 50,
	"height" : 0.2
}
{
	"_id" : ObjectId("577b1901fe6950263ad63a68"),
	"name" : "Dewgong",
	"description" : "Stores thermal energy in its body. Swims at a steady 8 knots even in intensely cold waters.",
	"type" : "água",
	"attack" : 70,
	"defense" : 80,
	"height" : 0.4
}
{
	"_id" : ObjectId("577b1901fe6950263ad63a69"),
	"name" : "Beedrill",
	"description" : "It can take down any opponent with its powerful poi son stingers.",
	"type" : "inseto",
	"attack" : 90,
	"defense" : 40,
	"height" : 0.2
}
{
	"_id" : ObjectId("577b1901fe6950263ad63a6a"),
	"name" : "Nidorina",
	"description" : "When NIDORINA are with their friends or family, they keep their barbs tucked away to prevent hurting each other.",
	"type" : "veneno",
	"attack" : 62,
	"defense" : 67,
	"height" : 0.2
}
```

## 2. Pokemons com a altura maior ou igual que 0.5
```
> var query = {height: {$gte : 0.5}}
> db.pokemons.find(query).pretty()
{
	"_id" : ObjectId("5779c63eebea693787997603"),
	"name" : "Charizard",
	"description" : "Pokemon massa de fogo",
	"type" : "fogo",
	"attack" : 77,
	"height" : 1.7
}
{
	"_id" : ObjectId("5779c64bebea693787997604"),
	"name" : "Pidgeot",
	"description" : "Voador dos bons",
	"type" : "voador",
	"attack" : 69,
	"height" : 1.5
}
{
	"_id" : ObjectId("5779c650ebea693787997605"),
	"name" : "Persian",
	"description" : "Gatinho mortal",
	"type" : "Fancy cat",
	"attack" : 94,
	"height" : 1.1
}
{
	"_id" : ObjectId("5779c65debea693787997607"),
	"name" : "Zubat",
	"description" : "Parente distante do batman",
	"type" : "Batman",
	"attack" : 38,
	"height" : 0.8
}
{
	"_id" : ObjectId("577b1901fe6950263ad63a65"),
	"name" : "Arbok",
	"description" : "The frightening patterns on its belly have been studied. Six variations have been confirmed.",
	"type" : "veneno",
	"attack" : 85,
	"defense" : 69,
	"height" : 0.9
}
```

## 3. Pokemons com a altura maior ou igual que 0.5 e do tipo grama
```
> var query = {$end: [{height: {$gte : 0.5}}, {type: "grama"}]}
> db.pokemons.find(query)
>
```

## 4. Pokemons com o name 'Pikachu' ou com attack menor ou igual que 50;
```
> var query = {$or: [{name: "Pikachu"}, {attack: {$lte: 50}}]}
> db.pokemons.find(query).pretty()
{
	"_id" : ObjectId("5779c658ebea693787997606"),
	"name" : "Vulpix",
	"description" : "Fofo porém mortal",
	"type" : "fogo",
	"attack" : 41,
	"height" : 0.4
}
{
	"_id" : ObjectId("5779c65debea693787997607"),
	"name" : "Zubat",
	"description" : "Parente distante do batman",
	"type" : "Batman",
	"attack" : 38,
	"height" : 0.8
}
{
	"_id" : ObjectId("577b1901fe6950263ad63a64"),
	"name" : "Butterfree",
	"description" : "In battle, it flaps its wings at high speed to release highly toxic dust into the air.",
	"type" : "inseto",
	"attack" : 45,
	"defense" : 50,
	"height" : 0.3,
	"heigth" : 0.3
}
```

## 5. Pokemons com attack MAIOR OU IGUAL QUE 48 E com height menor ou igual que 0.5
```
> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
> db.pokemons.find(query).pretty()
{
	"_id" : ObjectId("577b1901fe6950263ad63a66"),
	"name" : "Ninetales",
	"description" : "Its nine tails are said to be imbued with a mystic power. It can live for a thousand years.",
	"type" : "fogo",
	"attack" : 76,
	"defense" : 75,
	"height" : 0.3
}
{
	"_id" : ObjectId("577b1901fe6950263ad63a67"),
	"name" : "Grimer",
	"description" : "Appears in filthy areas. Thrives by sucking up polluted sludge that is pumped out of factories.",
	"type" : "veneno",
	"attack" : 80,
	"defense" : 50,
	"height" : 0.2
}
{
	"_id" : ObjectId("577b1901fe6950263ad63a68"),
	"name" : "Dewgong",
	"description" : "Stores thermal energy in its body. Swims at a steady 8 knots even in intensely cold waters.",
	"type" : "água",
	"attack" : 70,
	"defense" : 80,
	"height" : 0.4
}
{
	"_id" : ObjectId("577b1901fe6950263ad63a69"),
	"name" : "Beedrill",
	"description" : "It can take down any opponent with its powerful poi son stingers.",
	"type" : "inseto",
	"attack" : 90,
	"defense" : 40,
	"height" : 0.2
}
{
	"_id" : ObjectId("577b1901fe6950263ad63a6a"),
	"name" : "Nidorina",
	"description" : "When NIDORINA are with their friends or family, they keep their barbs tucked away to prevent hurting each other.",
	"type" : "veneno",
	"attack" : 62,
	"defense" : 67,
	"height" : 0.2
}
```
