# MongoDB - Aula 03 - Exercício
autor: Anderson Lemos

## Liste Todos os Pokemons com a altura **Menor que** 0,5
```
cerberus(mongod-2.6.11) be-mean-pokemons> var query = {height:{$lt:0.5}}
cerberus(mongod-2.6.11) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56c73b9ccfefc8bd001c3502"),
  "name": "Pikachu",
  "description": "Own",
  "attack": 30,
  "defense": 20,
  "height": 0.4
}
{
  "_id": ObjectId("56cb4fa5fffdadaf81d003d1"),
  "name": "Pikachu",
  "description": "Litlle electric rat",
  "type": "Electric",
  "attack": 55,
  "defense": 40,
  "height": 0.4
}
{
  "_id": ObjectId("56cb4fa5fffdadaf81d003d3"),
  "name": "Ignotum",
  "description": "???",
  "type": "God",
  "attack": 9999,
  "defense": 9999,
  "height": 0.3
}
{
  "_id": ObjectId("56cb4fa5fffdadaf81d003d4"),
  "name": "Green Monkey",
  "description": "A green monkey",
  "type": "Grama",
  "attack": 15,
  "defense": 10,
  "height": 0.4
}
Fetched 4 record(s) in 2ms
```
## Liste todos Pokemons com a altura **Maior ou igual que** 0.5
```
cerberus(mongod-2.6.11) be-mean-pokemons> var query = {height:{$gte:0.5}}
cerberus(mongod-2.6.11) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56c73d93cfefc8bd001c3503"),
  "name": "Charmeleon",
  "description": "  Charmeleon mercilessly destroys its foes using its sharp claws. If it encounters a strong foe, it turns aggressive. In this excited state, the flame at the tip of its tail flares with a bluish white color. ",
  "attack": 30,
  "defense": 30,
  "height": 1.1
}
{
  "_id": ObjectId("56c73e3309e0167957d7d0d7"),
  "name": "Butterfree",
  "description": "   Butterfree has a superior ability to search for delicious honey from flowers. It can even search out, extract, and carry honey from flowers that are blooming over six miles from its nest. ",
  "attack": 20,
  "defense": 20,
  "height": 1.1
}
{
  "_id": ObjectId("56c73e6909e0167957d7d0d8"),
  "name": "Butterfree",
  "description": "   Butterfree has a superior ability to search for delicious honey from flowers. It can even search out, extract, and carry honey from flowers that are blooming over six miles from its nest. ",
  "attack": 20,
  "defense": 20,
  "height": 1.1
}
{
  "_id": ObjectId("56c73e9c09e0167957d7d0d9"),
  "name": "Charizard",
  "description": "    Charizard flies around the sky in search of powerful opponents. It breathes fire of such great heat that it melts anything. However, it never turns its fiery breath on any opponent weaker than itself. ",
  "attack": 40,
  "defense": 30,
  "height": 1.7
}
{
  "_id": ObjectId("56c73ec609e0167957d7d0da"),
  "name": "Arbok",
  "description": "This Pokémon is terrifically strong in order to constrict things with its body. It can even flatten steel oil drums. Once Arbok wraps its body around its foe, escaping its crunching embrace is impossible. ",
  "attack": 40,
  "defense": 30,
  "height": 3.5
}
{
  "_id": ObjectId("56cb4fa5fffdadaf81d003d2"),
  "name": "CrazyCrazy",
  "description": "WTF?",
  "type": "Unknown",
  "attack": 0.2,
  "defense": 1000,
  "height": 10
}
Fetched 6 record(s) in 4ms
```
## Liste todos os Pokemons com as altura **Menor ou igual que** 0.5 **E** do tipo grama
```
cerberus(mongod-2.6.11) be-mean-pokemons> var query = {$and: [{type:"Grama"},{height:{$lte:0.5}}]}
cerberus(mongod-2.6.11) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56cb4fa5fffdadaf81d003d4"),
  "name": "Green Monkey",
  "description": "A green monkey",
  "type": "Grama",
  "attack": 15,
  "defense": 10,
  "height": 0.4
}
Fetched 1 record(s) in 1ms
```
## Liste todos os Pokemons com o name Pikachu **OU**  com o attack **menor ou igual que** 0.5
```
cerberus(mongod-2.6.11) be-mean-pokemons> var query = {$or: [{name:"Pikachu"},{attack:{$lte:0.5}}]}
cerberus(mongod-2.6.11) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56c73b9ccfefc8bd001c3502"),
  "name": "Pikachu",
  "description": "Own",
  "attack": 30,
  "defense": 20,
  "height": 0.4
}
{
  "_id": ObjectId("56cb4fa5fffdadaf81d003d1"),
  "name": "Pikachu",
  "description": "Litlle electric rat",
  "type": "Electric",
  "attack": 55,
  "defense": 40,
  "height": 0.4
}
{
  "_id": ObjectId("56cb4fa5fffdadaf81d003d2"),
  "name": "CrazyCrazy",
  "description": "WTF?",
  "type": "Unknown",
  "attack": 0.2,
  "defense": 1000,
  "height": 10
}
Fetched 3 record(s) in 2ms
```
## Liste todos os Pokemons com o attack **maior ou igual que** 48 **E** com height **menor ou igual que** 0.5
```
cerberus(mongod-2.6.11) be-mean-pokemons> var query = {$and:[{attack:{$gte:48}},{height:{$lte:0.5}}]}
cerberus(mongod-2.6.11) be-mean-pokemons> db.pokemons.find(query)
{
"_id": ObjectId("56c894f4df2db116b3534bc1"),
"name": "Butterfree",
"description": "   Butterfree has a superior ability to search for delicious honey from flowers. It can even search out, extract, and carry honey from flowers that are blooming over six miles from its nest. ",
"attack": 50,
"defense": 20,
"height": 0.5
}
{
"_id": ObjectId("56c897d1df2db116b3534bc5"),
"name": "Pikachu",
"description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, its evidence that this Pokémon mistook the intensity of its charge.",
"attack": 49,
"defense": 40,
"height": 0.4
}
Fetched 2 record(s) in 5ms

```
