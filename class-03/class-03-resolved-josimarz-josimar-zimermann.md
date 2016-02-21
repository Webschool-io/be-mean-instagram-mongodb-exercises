# MongoDB - Aula 03 - Exercício
**Autor**: Josimar Zimermann - [josimarz](https://github.com/josimarz)

## Listar todos os Pokemon com a altura menor que 0.5

	nightwolf(mongod-3.2.1) be-mean-pokemons> var query = {height: {$lt: .5}}
	nightwolf(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("56c89884dcd3b02a4c0cca65"),
	  "name": "Mew",
	  "description": "Mew is said to possess the genetic composition of all Pokémon. It is capable of making itself invisible at will, so it entirely avoids notice even if it approaches people.",
	  "type": "Psychic",
	  "attack": 50,
	  "defense": 40,
	  "height": 0.4
	}
	{
	  "_id": ObjectId("56c918b5e20aaf7ac2f541c6"),
	  "name": "Pikachu",
	  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge.",
	  "type": "Electric",
	  "attack": 30,
	  "defense": 20,
	  "height": 0.4
	}
	Fetched 2 record(s) in 2ms
	nightwolf(mongod-3.2.1) be-mean-pokemons>

## Listar todos os Pokemon com a altura maior que ou igual a 0.5

	nightwolf(mongod-3.2.1) be-mean-pokemons> var query = {height: {$gte: .5}}
	nightwolf(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("56c89817dcd3b02a4c0cca56"),
	  "name": "Sandslash",
	  "description": "Sandslash's body is covered by tough spikes, which are hardened sections of its hide. Once a year, the old spikes fall out, to be replaced with new spikes that grow out from beneath the old ones.",
	  "type": "Ground",
	  "attack": 50,
	  "defense": 50,
	  "height": 1
	}
	{
	  "_id": ObjectId("56c89823dcd3b02a4c0cca57"),
	  "name": "Clefairy",
	  "description": "On every night of a full moon, groups of this Pokémon come out to play. When dawn arrives, the tired Clefairy return to their quiet mountain retreats and go to sleep nestled up against each other.",
	  "type": "Fairy",
	  "attack": 20,
	  "defense": 20,
	  "height": 0.6
	}
	{
	  "_id": ObjectId("56c8982adcd3b02a4c0cca58"),
	  "name": "Parasect",
	  "description": "Parasect is known to infest large trees en masse and drain nutrients from the lower trunk and roots. When an infested tree dies, they move onto another tree all at once.",
	  "type": "Grass",
	  "attack": 50,
	  "defense": 40,
	  "height": 1
	}
	{
	  "_id": ObjectId("56c89831dcd3b02a4c0cca59"),
	  "name": "Golduck",
	  "description": "The webbed flippers on its forelegs and hind legs and the streamlined body of Golduck give it frightening speed. This Pokémon is definitely much faster than even the most athletic swimmer.",
	  "type": "Water",
	  "attack": 40,
	  "defense": 30,
	  "height": 1.7
	}
	{
	  "_id": ObjectId("56c8983adcd3b02a4c0cca5a"),
	  "name": "Arcanine",
	  "description": "Arcanine is known for its high speed. It is said to be capable of running over 6,200 miles in a single day and night. The fire that blazes wildly within this Pokémon's body is its source of power.",
	  "type": "Fire",
	  "attack": 60,
	  "defense": 40,
	  "height": 1.9
	}
	{
	  "_id": ObjectId("56c89842dcd3b02a4c0cca5b"),
	  "name": "Kadabra",
	  "description": "Kadabra emits a peculiar alpha wave if it develops a headache. Only those people with a particularly strong psyche can hope to become a Trainer of this Pokémon.",
	  "type": "Psychic",
	  "attack": 20,
	  "defense": 20,
	  "height": 1.3
	}
	{
	  "_id": ObjectId("56c8984adcd3b02a4c0cca5c"),
	  "name": "Bellsprout",
	  "description": "Bellsprout's thin and flexible body lets it bend and sway to avoid any attack, however strong it may be. From its mouth, this Pokémon spits a corrosive fluid that melts even iron.",
	  "type": "Grass",
	  "attack": 40,
	  "defense": 20,
	  "height": 0.7
	}
	{
	  "_id": ObjectId("56c8984fdcd3b02a4c0cca5d"),
	  "name": "Slowpoke",
	  "description": "Slowpoke uses its tail to catch prey by dipping it in water at the side of a river. However, this Pokémon often forgets what it's doing and often spends entire days just loafing at water's edge.",
	  "type": "Water",
	  "attack": 30,
	  "defense": 30,
	  "height": 1.2
	}
	{
	  "_id": ObjectId("56c89858dcd3b02a4c0cca5e"),
	  "name": "Magneton",
	  "description": "Magneton emits a powerful magnetic force that is fatal to mechanical devices. As a result, large cities sound sirens to warn citizens of large-scale outbreaks of this Pokémon.",
	  "type": "Electric",
	  "attack": 30,
	  "defense": 40,
	  "height": 1
	}
	{
	  "_id": ObjectId("56c8985fdcd3b02a4c0cca5f"),
	  "name": "Kingler",
	  "description": "Kingler has an enormous, oversized claw. It waves this huge claw in the air to communicate with others. However, because the claw is so heavy, the Pokémon quickly tires.",
	  "type": "Water",
	  "attack": 70,
	  "defense": 50,
	  "height": 1.3
	}
	{
	  "_id": ObjectId("56c89865dcd3b02a4c0cca60"),
	  "name": "Marowak",
	  "description": "Marowak is the evolved form of a Cubone that has overcome its sadness at the loss of its mother and grown tough. This Pokémon's tempered and hardened spirit is not easily broken.",
	  "type": "Ground",
	  "attack": 70,
	  "defense": 50,
	  "height": 1
	}
	{
	  "_id": ObjectId("56c8986bdcd3b02a4c0cca61"),
	  "name": "Scyther",
	  "description": "Scyther is blindingly fast. Its blazing speed enhances the effectiveness of the twin scythes on its forearms. This Pokémon's scythes are so effective, they can slice through thick logs in one wicked stroke.",
	  "type": "Bug",
	  "attack": 60,
	  "defense": 40,
	  "height": 1.5
	}
	{
	  "_id": ObjectId("56c89871dcd3b02a4c0cca62"),
	  "name": "Electabuzz",
	  "description": "When a storm arrives, gangs of this Pokémon compete with each other to scale heights that are likely to be stricken by lightning bolts. Some towns use Electabuzz in place of lightning rods.",
	  "type": "Electric",
	  "attack": 40,
	  "defense": 30,
	  "height": 1.1
	}
	{
	  "_id": ObjectId("56c89876dcd3b02a4c0cca63"),
	  "name": "Magmar",
	  "description": "In battle, Magmar blows out intensely hot flames from all over its body to intimidate its opponent. This Pokémon's fiery bursts create heat waves that ignite grass and trees in its surroundings.",
	  "type": "Fire",
	  "attack": 50,
	  "defense": 30,
	  "height": 1.3
	}
	{
	  "_id": ObjectId("56c8987edcd3b02a4c0cca64"),
	  "name": "Gyarados",
	  "description": "When Magikarp evolves into Gyarados, its brain cells undergo a structural transformation. It is said that this transformation is to blame for this Pokémon's wildly violent nature.",
	  "type": "Water",
	  "attack": 60,
	  "defense": 30,
	  "height": 6.5
	}
	Fetched 15 record(s) in 7ms
	nightwolf(mongod-3.2.1) be-mean-pokemons>

##Listar todos os Pokemon com a altura menor que ou igual a 0.5 e do tipo grama

	nightwolf(mongod-3.2.1) be-mean-pokemons> var query = {$and: [{type: "Grass"}, {height: {$lte: .5}}]}
	nightwolf(mongod-3.2.1) be-mean-pokemons> query
	{
	  "$and": [
	    {
	      "type": "Grass"
	    },
	    {
	      "height": {
	        "$lte": 0.5
	      }
	    }
	  ]
	}
	nightwolf(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("56c91ad0e20aaf7ac2f541c7"),
	  "name": "Oddish",
	  "description": "During the daytime, Oddish buries itself in soil to absorb nutrients from the ground using its entire body. The more fertile the soil, the glossier its leaves become.",
	  "type": "Grass",
	  "attack": 30,
	  "defense": 30,
	  "height": 0.5
	}
	Fetched 1 record(s) in 1ms
	nightwolf(mongod-3.2.1) be-mean-pokemons>

## Listar todos os Pokemon com `name` igual a 'Pikachu' ou com `attack` menor que ou igual a 0.5

	nightwolf(mongod-3.2.1) be-mean-pokemons> var query = {$or: [{name: "Pikachu"}, {attack: {$lte: .5}}]}
	nightwolf(mongod-3.2.1) be-mean-pokemons> query
	{
	  "$or": [
	    {
	      "name": "Pikachu"
	    },
	    {
	      "attack": {
	        "$lte": 0.5
	      }
	    }
	  ]
	}
	nightwolf(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("56c918b5e20aaf7ac2f541c6"),
	  "name": "Pikachu",
	  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge.",
	  "type": "Electric",
	  "attack": 30,
	  "defense": 20,
	  "height": 0.4
	}
	Fetched 1 record(s) in 2ms
	nightwolf(mongod-3.2.1) be-mean-pokemons>

## Listar todos os Pokemon com `attack` maior que ou igual a 48 e com `height` menor que ou igual a 0.5

	nightwolf(mongod-3.2.1) be-mean-pokemons> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: .5}}]}
	nightwolf(mongod-3.2.1) be-mean-pokemons> query
	{
	  "$and": [
	    {
	      "attack": {
	        "$gte": 48
	      }
	    },
	    {
	      "height": {
	        "$lte": 0.5
	      }
	    }
	  ]
	}
	nightwolf(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("56c89884dcd3b02a4c0cca65"),
	  "name": "Mew",
	  "description": "Mew is said to possess the genetic composition of all Pokémon. It is capable of making itself invisible at will, so it entirely avoids notice even if it approaches people.",
	  "type": "Psychic",
	  "attack": 50,
	  "defense": 40,
	  "height": 0.4
	}
	Fetched 1 record(s) in 1ms
	nightwolf(mongod-3.2.1) be-mean-pokemons>