# MongoDB - Aula 02 - Exercício
autor: Amanda Vilela

## Crie uma database chamada be-mean-pokemons

```
amanda-Inspiron-7520(mongod-2.4.9) be-mean> use be-mean-pokemons
switched to db be-mean-pokemons
```
## Liste quais databases você possui nesse servidor

```
amanda-Inspiron-7520(mongod-2.4.9) be-mean-pokemons> show dbs
be-mean → 0.203GB
local   → 0.078GB

```

## Liste quais coleções você possui nessa database

```
show collections
pokemons       → 0.002MB / 0.020MB
system.indexes → 0.000MB / 0.008MB
```

## Insira pelo menos 5 pokemons A SUA ESCOLHA utilizando o mesmo padrão de campos utilizado: name, description, attack, defense e height;

```
amanda-Inspiron-7520(mongod-2.4.9) be-mean-pokemons> var pokemon = {'name':'Charmeleon','description':'  Charmeleon mercilessly destroys its foes using its sharp claws. If it encounters a strong foe, it turns aggressive. In this excited state, the flame at the tip of its tail flares with a bluish white color. ', attack:30, defense: 30 , height:1.1}

amanda-Inspiron-7520(mongod-2.4.9) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 119ms

amanda-Inspiron-7520(mongod-2.4.9) be-mean-pokemons> var pokemon = {'name':'Butterfree','description':'   Butterfree has a superior ability to search for delicious honey from flowers. It can even search out, extract, and carry honey from flowers that are blooming over six miles from its nest. ', attack:20, defense: 20 , height:1.1}

amanda-Inspiron-7520(mongod-2.4.9) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 0ms

amanda-Inspiron-7520(mongod-2.4.9) be-mean-pokemons> var pokemon = {'name':'Charizard','description':'    Charizard flies around the sky in search of powerful opponents. It breathes fire of such great heat that it melts anything. However, it never turns its fiery breath on any opponent weaker than itself. ', attack:40, defense: 30 , height:1.7}

amanda-Inspiron-7520(mongod-2.4.9) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 0ms

amanda-Inspiron-7520(mongod-2.4.9) be-mean-pokemons> var pokemon = {'name':'Arbok','description':'This Pokémon is terrifically strong in order to constrict things with its body. It can even flatten steel oil drums. Once Arbok wraps its body around its foe, escaping its crunching embrace is impossible. ', attack:40, defense: 30 , height:3.5}

amanda-Inspiron-7520(mongod-2.4.9) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 0ms

```

## Liste os pokemons existentes na sua coleção


```
amanda-Inspiron-7520(mongod-2.4.9) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("5651fd6e2b465aac30102ff0"),
  "name": "Charmeleon",
  "description": "  Charmeleon mercilessly destroys its foes using its sharp claws. If it encounters a strong foe, it turns aggressive. In this excited state, the flame at the tip of its tail flares with a bluish white color. ",
  "attack": 30,
  "defense": 30,
  "height": 1.1
}
{
  "_id": ObjectId("5651fd7a2b465aac30102ff1"),
  "name": "Butterfree",
  "description": "   Butterfree has a superior ability to search for delicious honey from flowers. It can even search out, extract, and carry honey from flowers that are blooming over six miles from its nest. ",
  "attack": 20,
  "defense": 20,
  "height": 1.1
}
{
  "_id": ObjectId("5651fd882b465aac30102ff2"),
  "name": "Charizard",
  "description": "    Charizard flies around the sky in search of powerful opponents. It breathes fire of such great heat that it melts anything. However, it never turns its fiery breath on any opponent weaker than itself. ",
  "attack": 40,
  "defense": 30,
  "height": 1.7
}
{
  "_id": ObjectId("5651fd942b465aac30102ff3"),
  "name": "Arbok",
  "description": "This Pokémon is terrifically strong in order to constrict things with its body. It can even flatten steel oil drums. Once Arbok wraps its body around its foe, escaping its crunching embrace is impossible. ",
  "attack": 40,
  "defense": 30,
  "height": 3.5
}
{
  "_id": ObjectId("5651fddc2b465aac30102ff4"),
  "name": "Arbok",
  "description": "This Pokémon is terrifically strong in order to constrict things with its body. It can even flatten steel oil drums. Once Arbok wraps its body around its foe, escaping its crunching embrace is impossible.",
  "attack": 40,
  "defense": 30,
  "height": 3.5
}
Fetched 5 record(s) in 5ms

```

## Busque o pickachu e armazene-o em uma variável chamada poke

### Inserindo o Pikachu

```
amanda-Inspiron-7520(mongod-2.4.9) be-mean-pokemons> var pokemon = {'name':'Pikachu','description':'Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, its evidence that this Pokémon mistook the intensity of its charge.', attack:30, defense:20, height:0.4}

amanda-Inspiron-7520(mongod-2.4.9) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 0ms
```
### Buscando o Pikachu

```
amanda-Inspiron-7520(mongod-2.4.9) be-mean-pokemons> var query = {name:"Pikachu"}
amanda-Inspiron-7520(mongod-2.4.9) be-mean-pokemons> poke = db.pokemons.findOne(query)
{
  "_id": ObjectId("5651ffcd2b465aac30102ff5"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, its evidence that this Pokémon mistook the intensity of its charge.",
  "attack": 30,
  "defense": 20,
  "height": 0.4
}
```

## Modifique sua description e salvê-o

```
amanda-Inspiron-7520(mongod-2.4.9) be-mean-pokemons> poke.description = "Very cute"
Very cute

amanda-Inspiron-7520(mongod-2.4.9) be-mean-pokemons> poke.description
Very cute

amanda-Inspiron-7520(mongod-2.4.9) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 0ms

amanda-Inspiron-7520(mongod-2.4.9) be-mean-pokemons> poke
{
  "_id": ObjectId("5651ffcd2b465aac30102ff5"),
  "name": "Pikachu",
  "description": "Very cute",
  "attack": 30,
  "defense": 20,
  "height": 0.4
}

```

Augusto Ody - MongoDB - Exercicio 01, 02, 03 e 04 resolvido
