# MongoDB - Aula 03 - Exercício
autor: Natália Nascimento de Ávila

# 1. Liste todos Pokemons com a altura menor que 0.5;

```
var poke = {height: {$lt: 0.5}}

poke
"height" : { "$lt" : 0.5 } }
 
db.pokemons.find(poke)
"_id" : ObjectId("57058674a89457f8db006ce3"), "name" : "Chespin", "description" : "mega proteção na cabeça e costas", "type" : "grass", "attack" : 3, "defense" : 3, "height" : 0.4 }
"_id" : ObjectId("57058674a89457f8db006ce4"), "name" : "Fennekin", "description" : "curte fogo e odeia agua", "type" : "fire", "attack" : 2, "defense" : 2, "height" : 0.4 }
"_id" : ObjectId("57058674a89457f8db006ce5"), "name" : "Froakie", "description" : "é um sapinho que curte agua", "type" : "fire", "attack" : 30, "defense" : 20, "height" : 0.3 }

```

# 2. Liste todos Pokemons com a altura maior ou igual que 0.5;

```
var poke = {height: {$gte:0.5}}

poke
{ "height" : { "$gte" : 0.5 } }

db.pokemons.find(poke)
{ "_id" : ObjectId("570cfc63887690aa1846c4d6"), "name" : "Wartortle", "description" : "Turtle Pokemon", "type" : "água", "attack" : 63, "defense" : 80, "height" : 0.9 }
{ "_id" : ObjectId("570cfc64887690aa1846c4d7"), "name" : "Beedrill", "description" : "Esse é venenoso", "type" : "buge poison", "attack" : 150, "defense" : 40, "height" : 1.4 }
{ "_id" : ObjectId("570cfc64887690aa1846c4d8"), "name" : "Venusaur", "description" : "esse é calminho", "type" : "grasse poison", "attack" : 82, "defense" : 83, "height" : 2 }
{ "_id" : ObjectId("570cfc64887690aa1846c4d9"), "name" : "Jigglypuff", "description" : "canta para deixar os inimigos lentos", "type" : "normal e fairy", "attack" : 45, "defense" : 20, "height" : 0.5 }
{ "_id" : ObjectId("570cfc64887690aa1846c4da"), "name" : "Butterfree", "description" : "transporta mel e flores em longa distancia", "type" : "bug e flying", "attack" : 45, "defense" : 50, "height" : 1 }
{ "_id" : ObjectId("570cfc7a887690aa1846c4db"), "name" : "Wartortle", "description" : "Turtle Pokemon", "type" : "água", "attack" : 63, "defense" : 80, "height" : 0.9 }
{ "_id" : ObjectId("570cfc82887690aa1846c4dc"), "name" : "Beedrill", "description" : "Esse é venenoso", "type" : "buge poison", "attack" : 150, "defense" : 40, "height" : 1.4 }
{ "_id" : ObjectId("570cfc88887690aa1846c4dd"), "name" : "Venusaur", "description" : "esse é calminho", "type" : "grasse poison", "attack" : 82, "defense" : 83, "height" : 2 }
{ "_id" : ObjectId("570cfc8f887690aa1846c4de"), "name" : "Jigglypuff", "description" : "canta para deixar os inimigos lentos", "type" : "normal e fairy", "attack" : 45, "defense" : 20, "height" : 0.5 }
{ "_id" : ObjectId("570cfc94887690aa1846c4df"), "name" : "Butterfree", "description" : "transporta mel e flores em longa distancia", "type" : "bug e flying", "attack" : 45, "defense" : 50, "height" : 1 }
{ "_id" : ObjectId("570d013e887690aa1846c4e4"), "name" : "Binacle", "description" : "pedra aquatica de duas cabeças", "type" : "rock", "attack" : 50, "defense" : 50, "height" : 0.5 }

```

# 3. Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama;

```
var poke = {$and: [{type:'grass'}, {height:{$lte: 0.5}}]}

db.pokemons.find(poke)
{ "_id" : ObjectId("570d013e887690aa1846c4e1"), "name" : "Chespin", "description" : "mega proteção na cabeça e costas",
"type" : "grass", "attack" : 3, "defense" : 3, "height" : 0.4 }

```

# 4. Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5;

```
var poke = { $or: [{name: /pikachu/i},{attack: { $lte: 0.5} }]}

db.pokemons.find(poke)
{ "_id" : ObjectId("570d4510887690aa1846c4e5"), "name" : "Pikachu", "description" : "esse é pokemon pop", "type" : "elet
ric", "attack" : 50, "defense" : 40, "height" : 0.4 }

```

# 5. Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5;

```
var poke = {$and:[{attack:{$gte:48}},{height:{$lte: 0.5}}]}

db.pokemons.find(poke)
{ "_id" : ObjectId("570d013e887690aa1846c4e4"), "name" : "Binacle", "description" : "pedra aquatica de duas cabeças", "t
ype" : "rock", "attack" : 50, "defense" : 50, "height" : 0.5 }
{ "_id" : ObjectId("570d4510887690aa1846c4e5"), "name" : "Pikachu", "description" : "esse é pokemon pop", "type" : "elet
ric", "attack" : 50, "defense" : 40, "height" : 0.4 }

```