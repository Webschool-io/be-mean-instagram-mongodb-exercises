# MongoDB - Aula 03 - Exercício
Autor: Jefferson William Machado

## Liste todos Pokemons com a altura menor que 0.5
```
var query = {height: {$lt: 0.5}}
db.pokemons.find(query)

```

## Liste todos Pokemons com a altura maior ou igual que 0.5
```
var query = {height: {$gte: 0.5}}
db.pokemons.find(query)
{
	"_id": ObjectId("5644abe70db0460bf34c31ee"),
	"name": "Raticate",
	"description": "Raticate's sturdy fangs grow steadily. To keep them ground down, it gnaws on rocks and logs. It may even chew on the walls of houses.",
	"attack": 81,
	"defense": 60,
	"height": 7
}
{
	"_id": ObjectId("5644abf10db0460bf34c31ef"),
	"name": "Spearow",
	"description": "Spearow has a very loud cry that can be heard over half a mile away. If its high, keening cry is heard echoing all around, it is a sign that they are warning each other of danger.",
	"attack": 60,
	"defense": 30,
	"height": 3
}
{
	"_id": ObjectId("5644abfa0db0460bf34c31f0"),
	"name": "Fearow",
	"description": "Fearow is recognized by its long neck and elongated beak. They are conveniently shaped for catching prey in soil or water. It deftly moves its long and skinny beak to pluck prey.",
	"attack": 90,
	"defense": 65,
	"height": 12
}
{
	"_id": ObjectId("5644ac000db0460bf34c31f1"),
	"name": "Ekans",
	"description": "Ekans curls itself up in a spiral while it rests. Assuming this position allows it to quickly respond to a threat from any direction with a glare from its upraised head.",
	"attack": 60,
	"defense": 44,
	"height": 20
}
{
	"_id": ObjectId("5644ac050db0460bf34c31f2"),
	"name": "Arbok",
	"description": "This Pokémon is terrifically strong in order to constrict things with its body. It can even flatten steel oil drums. Once Arbok wraps its body around its foe, escaping its crunching embrace is impossible.",
	"attack": 85,
	"defense": 69,
	"height": 35
}
{
	"_id": ObjectId("5644ac090db0460bf34c31f3"),
	"name": "Pikachu",
	"description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge.",
	"attack": 55,
	"defense": 40,
	"height": 4
}
```

## Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama
```
var query = {$and: [{height: {$lte: 0.5}}, {type: "grama"}]}
db.pokemons.find(query)

```

## Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5
```
var query = {$or: [{name: "Pikachu"}, {attack: {$lte: 0.5}}]}
db.pokemons.find(query)
{
	"_id": ObjectId("5644ac090db0460bf34c31f3"),
	"name": "Pikachu",
	"description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge.",
	"attack": 55,
	"defense": 40,
	"height": 4
}
```

## Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5
```
var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
db.pokemons.find(query)

```