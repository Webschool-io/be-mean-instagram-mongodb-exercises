# MongoDB - Aula 02 - Exercício
autor: Anderson Lemos

## Crie uma database chamada be-mean-pokemons

```
cerberus(mongod-2.6.11) test> use be-mean-pokemons
switched to db be-mean-pokemons
```
## Liste quais databases você possui nesse servidor

```
cerberus(mongod-2.6.11) be-mean-pokemons> show dbs
admin             → (empty)
be-mean           → 0.078GB
be-mean-instagram → 0.078GB
be-mean-pokemons  → 0.078GB
be-mean-teste     → 0.078GB
local             → 0.078GB

```

## Liste quais coleções você possui nessa database

```
cerberus(mongod-2.6.11) be-mean-pokemons> show collections
pokemons       → 0.000MB / 0.008MB
system.indexes → 0.000MB / 0.008MB
```

## Insira pelo menos 5 pokemons A SUA ESCOLHA utilizando o mesmo padrão de campos -utilizado: name, description, attack, defense e height;

```
cerberus(mongod-2.6.11) be-mean-pokemons> var pokemon = {'name':'Charmeleon','description':'  Charmeleon mercilessly destroys its foes using its sharp claws. If it encounters a strong foe, it turns aggressive. In this excited state, the flame at the tip of its tail flares with a bluish white color. ', attack:30, defense: 30 , height:1.1}

cerberus(mongod-2.6.11) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 4ms

cerberus(mongod-2.6.11) be-mean-pokemons> var pokemon = {'name':'Butterfree','description':'   Butterfree has a superior ability to search for delicious honey from flowers. It can even search out, extract, and carry honey from flowers that are blooming over six miles from its nest. ', attack:20, defense: 20 , height:1.1}

cerberus(mongod-2.6.11) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 11ms

cerberus(mongod-2.6.11) be-mean-pokemons> var pokemon = {'name':'Butterfree','description':'   Butterfree has a superior ability to search for delicious honey from flowers. It can even search out, extract, and carry honey from flowers that are blooming over six miles from its nest. ', attack:20, defense: 20 , height:1.1}

cerberus(mongod-2.6.11) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 3ms

cerberus(mongod-2.6.11) be-mean-pokemons> var pokemon = {'name':'Charizard','description':'    Charizard flies around the sky in search of powerful opponents. It breathes fire of such great heat that it melts anything. However, it never turns its fiery breath on any opponent weaker than itself. ', attack:40, defense: 30 , height:1.7}

cerberus(mongod-2.6.11) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 0ms

cerberus(mongod-2.6.11) be-mean-pokemons> var pokemon = {'name':'Arbok','description':'This Pokémon is terrifically strong in order to constrict things with its body. It can even flatten steel oil drums. Once Arbok wraps its body around its foe, escaping its crunching embrace is impossible. ', attack:40, defense: 30 , height:3.5}

cerberus(mongod-2.6.11) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 0ms
```
## Liste os pokemons existentes na sua coleção

```
cerberus(mongod-2.6.11) be-mean-pokemons> db.pokemons.find()
{-
  "_id": ObjectId("56c73b9ccfefc8bd001c3502"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, its evidence that this Pokémon mistook the intensity of its charge.",
  "attack": 30,
  "defense": 20,
  "height": 0.4
}
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
Fetched 6 record(s) in 4ms
```
## Busque o pickachu e armazene-o em uma variável chamada poke

```
cerberus(mongod-2.6.11) be-mean-pokemons> var query = {name:"Pikachu"}
cerberus(mongod-2.6.11) be-mean-pokemons> poke = db.pokemons.findOne(query)
{
  "_id": ObjectId("56c73b9ccfefc8bd001c3502"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, its evidence that this Pokémon mistook the intensity of its charge.",
  "attack": 30,Augusto Ody - MongoDB - Exercicio 01, 02, 03 e 04 resolvido
  "defense": 20,
  "height": 0.4
}
```
## Modifique sua description e salve-o

```
cerberus(mongod-2.6.11) be-mean-pokemons> poke.description = "Own"
Own

cerberus(mongod-2.6.11) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 3ms

cerberus(mongod-2.6.11) be-mean-pokemons> poke
{
  "_id": ObjectId("56c73b9ccfefc8bd001c3502"),
  "name": "Pikachu",
  "description": "Own",
  "attack": 30,
  "defense": 20,
  "height": 0.4
}
```
