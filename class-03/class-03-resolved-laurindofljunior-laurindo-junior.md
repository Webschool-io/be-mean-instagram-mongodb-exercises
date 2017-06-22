# MongoDB - Aula 03 - Exercício
autor: Laurindo Ferreira Lucio Junior

## Liste todos Pokemons com a altura **menor que** 0.5;
```javascript
var query = {height: {$lt: 0.5}}
db.pokemons.find(query)
{
    "_id": 10,
    "name": "Caterpie",
    "description": "Caterpie has a voracious appetite. It can devour leaves bigger than its body right before your eyes. From its antenna, this Pokémon releases a terrifically strong odor.",
    "type": "bug",
    "attack": 30,
    "height": 0.3
}
{
    "_id": 25,
    "name": "Pikachu",
    "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge.",
    "type": "eletric",
    "attack": 55,
    "height": 0.4
}
Fetched 2 record(s) in 43ms
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```javascript
var query = {height: {$gte: 0.5}}
db.pokemons.find(query)
{
    "_id": 7,
    "name": "Squirtle",
    "description": "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
    "type": "water",
    "attack": 48,
    "height": 0.5
}
{
    "_id": 58,
    "name": "Growlithe",
    "description": "Growlithe has a superb sense of smell. Once it smells anything, this Pokémon won't forget the scent, no matter what. It uses its advanced olfactory sense to determine the emotions of other living things.",
    "type": "fire",
    "attack": 70,
    "height": 0.7
}
{
    "_id": 1,
    "name": "Bulbasaur",
    "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
    "type": "grass",
    "attack": 49,
    "height": 0.7
}
{
    "_id": 131,
    "name": "Lapras",
    "description": "People have driven Lapras almost to the point of extinction. In the evenings, this Pokémon is said to sing plaintively as it seeks what few others of its kind still remain.",
    "type": "water",
    "attack": 85,
    "height": 2.5
}
{
    "_id": 18,
    "name": "Pidgeot",
    "description": "This Pokémon has a dazzling plumage of beautifully glossy feathers. Many Trainers are captivated by the striking beauty of the feathers on its head, compelling them to choose Pidgeot as their Pokémon.",
    "type": "flying",
    "attack": 80,
    "height": 1.5
}
{
    "_id": 4,
    "name": "Charmander",
    "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
    "type": "fire",
    "attack": 52,
    "height": 0.6
}
{
    "_id": 54,
    "name": "Psyduck",
    "description": "Psyduck uses a mysterious power. When it does so, this Pokémon generates brain waves that are supposedly only seen in sleepers. This discovery spurred controversy among scholars.",
    "type": "water",
    "attack": 52,
    "height": 0.8
}
{
    "_id": 20,
    "name": "Raticate",
    "description": "Raticate's sturdy fangs grow steadily. To keep them ground down, it gnaws on rocks and logs. It may even chew on the walls of houses.",
    "type": "normal",
    "attack": 81,
    "height": 0.7
}
Fetched 8 record(s) in 40ms
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
var query = {$and: [{height: {$lte: 0.5}}, {type: /grass/}]}
db.pokemons.find(query)
Fetched 0 record(s) in 1ms

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
var query = {$or: [ {name: /Pikachu/i}, {attack: {$lte: 0.5}} ]}
db.pokemons.find(query)
{
    "_id": 25,
    "name": "Pikachu",
    "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge.",
    "type": "eletric",
    "attack": 55,
    "height": 0.4
}
Fetched 1 record(s) in 10ms

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
var query = {$and: [{attack: {$gte: 48}}, {height:{$lte: 0.5}}]}
db.pokemons.find(query)
{
    "_id": 7,
    "name": "Squirtle",
    "description": "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
    "type": "water",
    "attack": 48,
    "height": 0.5
}
{
    "_id": 25,
    "name": "Pikachu",
    "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge.",
    "type": "eletric",
    "attack": 55,
    "height": 0.4
}
Fetched 2 record(s) in 52ms