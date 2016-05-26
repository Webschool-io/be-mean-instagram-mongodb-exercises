# MongoDb - Aula 02 - Exercício
autor: Maicon Giovani LC Ferreira

## Crie uma database chamada be-mean-pokemons;

```
> use be-mean-pokemons
switched to db be-mean-pokemons

```
## Liste quais databases você possui nesse servidor;

```
> show dbs
be-mean            0.004GB
be-mean-instagram  0.000GB
be-mean-pokemons   0.000GB
local              0.000GB
test               0.000GB

```
## Liste quais coleções você possui nessa database;

```
>show collections
>

```

## Insira pelo menos 5 pokemons A SUA ESCOLHA;

```
var pokemon = [
	{'name':'Trevenant', 'description': 'It can control trees at will. It will trap people who harm the forest, so they can never leave.', 'type':'Ghost', 'attack': 110, 'defense': 76, 'height': 4.11},
	{'name':'Yveltal', 'description': 'When this legendary Pokémons wings and tail feathers spread wide and glow red, it absorbs the life force of living creatures.', 'type':'Dark', 'attack': 131, 'defense': 95, 'height': 19.00},
	{'name':'Steelix', 'description': 'Steelix lives even further underground than Onix. This Pokémon is known to dig toward the earths core. There are records of this Pokémon reaching a depth of over six-tenths of a mile underground.', 'type':'Steel', "attack": 85, "defense": 200, "height": 30.05},
	{'name':'Marowak', 'description': 'Marowak is the evolved form of a Cubone that has overcome its sadness at the loss of its mother and grown tough. This Pokémons tempered and hardened spirit is not easily broken.', 'type':'Ground', "attack": 80, "defense": 110, "height": 3.03},
	{'name':'Kadabra', 'description': 'Kadabra emits a peculiar alpha wave if it develops a headache. Only those people with a particularly strong psyche can hope to become a Trainer of this Pokémon.', 'type':'Psychic', "attack": 35, "defense": 30, "height": 4.03}]

	> db.pokemons.insert(pokemon)
	BulkWriteResult({
		"writeErrors" : [ ],
		"writeConcernErrors" : [ ],
		"nInserted" : 5,
		"nUpserted" : 0,
		"nMatched" : 0,
		"nModified" : 0,
		"nRemoved" : 0,
		"upserted" : [ ]
	})

```

## Liste os pokemons existentes na sua coleção;

```
> db.pokemons.find()
{ "_id" : ObjectId("57362f9b1bd514b027750cdb"), "name" : "Trevenant", "description" : "It can control trees at will. It will trap people who harm the forest, so they can never leave.", "type" : "Ghost", "attack" : 110, "defense" : 76, "height" : 4.11 }
{ "_id" : ObjectId("57362f9b1bd514b027750cdc"), "name" : "Yveltal", "description" : "When this legendary Pokémons wings and tail feathers spread wide and glow red, it absorbs the life force of living creatures.", "type" : "Dark", "attack" : 131, "defense" : 95, "height" : 19 }
{ "_id" : ObjectId("57362f9b1bd514b027750cdd"), "name" : "Steelix", "description" : "Steelix lives even further underground than Onix. This Pokémon is known to dig toward the earths core. There are records of this Pokémon reaching a depth of over six-tenths of a mile underground.", "type" : "Steel", "attack" : 85, "defense" : 200, "height" : 30.05 }
{ "_id" : ObjectId("57362f9b1bd514b027750cde"), "name" : "Marowak", "description" : "Marowak is the evolved form of a Cubone that has overcome its sadness at the loss of its mother and grown tough. This Pokémons tempered and hardened spirit is not easily broken.", "type" : "Ground", "attack" : 80, "defense" : 110, "height" : 3.03 }
{ "_id" : ObjectId("57362f9b1bd514b027750cdf"), "name" : "Kadabra", "description" : "Kadabra emits a peculiar alpha wave if it develops a headache. Only those people with a particularly strong psyche can hope to become a Trainer of this Pokémon.", "type" : "Psychic", "attack" : 35, "defense" : 30, "height" : 4.03 }

```

## Busque o pokemon da sua escolha, pelo nome, e armazene-o em uma variável chamada poke;

```
> var name = {'name':'Yveltal'}
> var poke = db.pokemons.findOne(name)
> poke
{
	"_id" : ObjectId("57362f9b1bd514b027750cdc"),
	"name" : "Yveltal",
	"description" : "When this legendary Pokémons wings and tail feathers spread wide and glow red, it absorbs the life force of living creatures.",
	"type" : "Dark",
	"attack" : 131,
	"defense" : 95,
	"height" : 19
}

```

## Modifique sua description e salvê-o;

```
> poke.description = 'Pokémon fadaum que avua e eu nunca peguei '
> db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })

```

