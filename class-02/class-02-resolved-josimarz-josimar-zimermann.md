# MongoDB - Aula 02 - Exercício
autor: Josimar Zimermann

## Criar banco de dados denominado 'be-mean-pokemons'

	```
	nightwolf(mongod-3.2.1) be-mean-instagram> use be-mean-pokemons
	switched to db be-mean-pokemons
	nightwolf(mongod-3.2.1) be-mean-pokemons>
	```

## Listar todos os bancos de dados presentes no servidor

	```
	nightwolf(mongod-3.2.1) be-mean-pokemons> show dbs
	Loc8r             → 0.000GB
	be-mean           → 0.004GB
	be-mean-instagram → 0.000GB
	local             → 0.000GB
	mean-dev          → 0.000GB
	nightwolf(mongod-3.2.1) be-mean-pokemons>
	```

## Listar todas as coleções do banco de dados 'be-mean-pokemons'

	```
	nightwolf(mongod-3.2.1) be-mean-pokemons> show collections
	nightwolf(mongod-3.2.1) be-mean-pokemons>
	```

## Inserir Pokemons (pelo menos 5)

	```
	nightwolf(mongod-3.2.1) be-mean-pokemons> var pokemon = {
	... name: "Sandslash",
	... description: "Sandslash's body is covered by tough spikes, which are hardened sections of its hide. Once a year, the old spikes fall out, to be replaced with new spikes that grow out from beneath the old ones.",
	... type: "Ground",
	... attack: 50,
	... defense: 50,
	... height: 1
	... }
	nightwolf(mongod-3.2.1) be-mean-pokemons> db.pokemons.insert(pokemon)
	Inserted 1 record(s) in 23ms
	WriteResult({
	  "nInserted": 1
	})
	nightwolf(mongod-3.2.1) be-mean-pokemons> var pokemon = {
	... name: "Clefairy",
	... description: "On every night of a full moon, groups of this Pokémon come out to play. When dawn arrives, the tired Clefairy return to their quiet mountain retreats and go to sleep nestled up against each other.",
	... type: "Fairy",
	... attack: 20,
	... defense: 20,
	... height: 0.6
	... }
	nightwolf(mongod-3.2.1) be-mean-pokemons> db.pokemons.insert(pokemon)
	Inserted 1 record(s) in 1ms
	WriteResult({
	  "nInserted": 1
	})
	nightwolf(mongod-3.2.1) be-mean-pokemons> var pokemon = {
	... name: "Parasect",
	... description: "Parasect is known to infest large trees en masse and drain nutrients from the lower trunk and roots. When an infested tree dies, they move onto another tree all at once.",
	... type: "Grass",
	... attack: 50,
	... defense: 40,
	... height: 1
	... }
	nightwolf(mongod-3.2.1) be-mean-pokemons> db.pokemons.insert(pokemon)
	Inserted 1 record(s) in 2ms
	WriteResult({
	  "nInserted": 1
	})
	nightwolf(mongod-3.2.1) be-mean-pokemons> var pokemon = {
	... name: "Golduck",
	... description: "The webbed flippers on its forelegs and hind legs and the streamlined body of Golduck give it frightening speed. This Pokémon is definitely much faster than even the most athletic swimmer.",
	... type: "Water",
	... attack: 40,
	... defense: 30,
	... height: 1.7
	... }
	nightwolf(mongod-3.2.1) be-mean-pokemons> db.pokemons.insert(pokemon)
	Inserted 1 record(s) in 3ms
	WriteResult({
	  "nInserted": 1
	})
	nightwolf(mongod-3.2.1) be-mean-pokemons> var pokemon = {
	... name: "Arcanine",
	... description: "Arcanine is known for its high speed. It is said to be capable of running over 6,200 miles in a single day and night. The fire that blazes wildly within this Pokémon's body is its source of power.",
	... type: "Fire",
	... attack: 60,
	... defense: 40,
	... height: 1.9
	... }
	nightwolf(mongod-3.2.1) be-mean-pokemons> db.pokemons.insert(pokemon)
	Inserted 1 record(s) in 1ms
	WriteResult({
	  "nInserted": 1
	})
	nightwolf(mongod-3.2.1) be-mean-pokemons> var pokemon = {
	... name: "Kadabra",
	... description: "Kadabra emits a peculiar alpha wave if it develops a headache. Only those people with a particularly strong psyche can hope to become a Trainer of this Pokémon.",
	... type: "Psychic",
	... attack: 20,
	... defense: 20,
	... height: 1.3
	... }
	nightwolf(mongod-3.2.1) be-mean-pokemons> db.pokemons.insert(pokemon)
	Inserted 1 record(s) in 1ms
	WriteResult({
	  "nInserted": 1
	})
	nightwolf(mongod-3.2.1) be-mean-pokemons> var pokemon = {
	... name: "Bellsprout",
	... description: "Bellsprout's thin and flexible body lets it bend and sway to avoid any attack, however strong it may be. From its mouth, this Pokémon spits a corrosive fluid that melts even iron.",
	... type: "Grass",
	... attack: 40,
	... defense: 20,
	... height: 0.7
	... }
	nightwolf(mongod-3.2.1) be-mean-pokemons> db.pokemons.insert(pokemon)
	Inserted 1 record(s) in 1ms
	WriteResult({
	  "nInserted": 1
	})
	nightwolf(mongod-3.2.1) be-mean-pokemons> var pokemon = {
	... name: "Slowpoke",
	... description: "Slowpoke uses its tail to catch prey by dipping it in water at the side of a river. However, this Pokémon often forgets what it's doing and often spends entire days just loafing at water's edge.",
	... type: "Water",
	... attack: 30,
	... defense: 30,
	... height: 1.2
	... }
	nightwolf(mongod-3.2.1) be-mean-pokemons> db.pokemons.insert(pokemon)
	Inserted 1 record(s) in 1ms
	WriteResult({
	  "nInserted": 1
	})
	nightwolf(mongod-3.2.1) be-mean-pokemons> var pokemon = {
	... name: "Magneton",
	... description: "Magneton emits a powerful magnetic force that is fatal to mechanical devices. As a result, large cities sound sirens to warn citizens of large-scale outbreaks of this Pokémon.",
	... type: "Electric",
	... attack: 30,
	... defense: 40,
	... height: 1
	... }
	nightwolf(mongod-3.2.1) be-mean-pokemons> db.pokemons.insert(pokemon)
	Inserted 1 record(s) in 1ms
	WriteResult({
	  "nInserted": 1
	})
	nightwolf(mongod-3.2.1) be-mean-pokemons> var pokemon = {
	... name: "Kingler",
	... description: "Kingler has an enormous, oversized claw. It waves this huge claw in the air to communicate with others. However, because the claw is so heavy, the Pokémon quickly tires.",
	... type: "Water",
	... attack: 70,
	... defense: 50,
	... height: 1.3
	... }
	nightwolf(mongod-3.2.1) be-mean-pokemons> db.pokemons.insert(pokemon)
	Inserted 1 record(s) in 2ms
	WriteResult({
	  "nInserted": 1
	})
	nightwolf(mongod-3.2.1) be-mean-pokemons> var pokemon = {
	... name: "Marowak",
	... description: "Marowak is the evolved form of a Cubone that has overcome its sadness at the loss of its mother and grown tough. This Pokémon's tempered and hardened spirit is not easily broken.",
	... type: "Ground",
	... attack: 70,
	... defense: 50,
	... height: 1
	... }
	nightwolf(mongod-3.2.1) be-mean-pokemons> db.pokemons.insert(pokemon)
	Inserted 1 record(s) in 2ms
	WriteResult({
	  "nInserted": 1
	})
	nightwolf(mongod-3.2.1) be-mean-pokemons> var pokemon = {
	... name: "Scyther",
	... description: "Scyther is blindingly fast. Its blazing speed enhances the effectiveness of the twin scythes on its forearms. This Pokémon's scythes are so effective, they can slice through thick logs in one wicked stroke.",
	... type: "Bug",
	... attack: 60,
	... defense: 40,
	... height: 1.5
	... }
	nightwolf(mongod-3.2.1) be-mean-pokemons> db.pokemons.insert(pokemon)
	Inserted 1 record(s) in 1ms
	WriteResult({
	  "nInserted": 1
	})
	nightwolf(mongod-3.2.1) be-mean-pokemons> var pokemon = {
	... name: "Electabuzz",
	... description: "When a storm arrives, gangs of this Pokémon compete with each other to scale heights that are likely to be stricken by lightning bolts. Some towns use Electabuzz in place of lightning rods.",
	... type: "Electric",
	... attack: 40,
	... defense: 30,
	... height: 1.1
	... }
	nightwolf(mongod-3.2.1) be-mean-pokemons> db.pokemons.insert(pokemon)
	Inserted 1 record(s) in 1ms
	WriteResult({
	  "nInserted": 1
	})
	nightwolf(mongod-3.2.1) be-mean-pokemons> var pokemon = {
	... name: "Magmar",
	... description: "In battle, Magmar blows out intensely hot flames from all over its body to intimidate its opponent. This Pokémon's fiery bursts create heat waves that ignite grass and trees in its surroundings.",
	... type: "Fire",
	... attack: 50,
	... defense: 30,
	... height: 1.3
	... }
	nightwolf(mongod-3.2.1) be-mean-pokemons> db.pokemons.insert(pokemon)
	Inserted 1 record(s) in 2ms
	WriteResult({
	  "nInserted": 1
	})
	nightwolf(mongod-3.2.1) be-mean-pokemons> var pokemon = {
	... name: "Gyarados",
	... description: "Proin vulputate enim nec diam facilisis ultrices. Phasellus tempor dui ut leo maximus, ac euismod libero hendrerit. Curabitur sed ornare justo. Duis finibus orci massa, et fermentum diam varius eget. Pellentesque vitae mi porttitor arcu consequat dictum. Morbi interdum ac sapien vitae posuere. Duis dapibus ex et augue iaculis, a viverra mi volutpat.",
	... type: "Water",
	... attack: 60,
	... defense: 30,
	... height: 6.5
	... }
	nightwolf(mongod-3.2.1) be-mean-pokemons> db.pokemons.insert(pokemon)
	Inserted 1 record(s) in 1ms
	WriteResult({
	  "nInserted": 1
	})
	nightwolf(mongod-3.2.1) be-mean-pokemons> var pokemon = {
	... name: "Mew",
	... description: "Mew is said to possess the genetic composition of all Pokémon. It is capable of making itself invisible at will, so it entirely avoids notice even if it approaches people.",
	... type: "Psychic",
	... attack: 50,
	... defense: 40,
	... height: 0.4
	... }
	nightwolf(mongod-3.2.1) be-mean-pokemons> db.pokemons.insert(pokemon)
	Inserted 1 record(s) in 2ms
	WriteResult({
	  "nInserted": 1
	})
	nightwolf(mongod-3.2.1) be-mean-pokemons>
	```

## Listar todos os Pokemons na coleção 'pokemons'

	```
	nightwolf(mongod-3.2.1) be-mean-pokemons> db.pokemons.find()
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
	  "description": "Proin vulputate enim nec diam facilisis ultrices. Phasellus tempor dui ut leo maximus, ac euismod libero hendrerit. Curabitur sed ornare justo. Duis finibus orci massa, et fermentum diam varius eget. Pellentesque vitae mi porttitor arcu consequat dictum. Morbi interdum ac sapien vitae posuere. Duis dapibus ex et augue iaculis, a viverra mi volutpat.",
	  "type": "Water",
	  "attack": 60,
	  "defense": 30,
	  "height": 6.5
	}
	{
	  "_id": ObjectId("56c89884dcd3b02a4c0cca65"),
	  "name": "Mew",
	  "description": "Mew is said to possess the genetic composition of all Pokémon. It is capable of making itself invisible at will, so it entirely avoids notice even if it approaches people.",
	  "type": "Psychic",
	  "attack": 50,
	  "defense": 40,
	  "height": 0.4
	}
	Fetched 16 record(s) in 7ms
	nightwolf(mongod-3.2.1) be-mean-pokemons>
	```

## Selecionar um Pokemon e guardar na variável 'poke'

	```
	nightwolf(mongod-3.2.1) be-mean-pokemons> var query = {name: 'Gyarados'}
	nightwolf(mongod-3.2.1) be-mean-pokemons> var poke = db.pokemons.findOne(query)
	nightwolf(mongod-3.2.1) be-mean-pokemons> poke
	{
	  "_id": ObjectId("56c8987edcd3b02a4c0cca64"),
	  "name": "Gyarados",
	  "description": "Proin vulputate enim nec diam facilisis ultrices. Phasellus tempor dui ut leo maximus, ac euismod libero hendrerit. Curabitur sed ornare justo. Duis finibus orci massa, et fermentum diam varius eget. Pellentesque vitae mi porttitor arcu consequat dictum. Morbi interdum ac sapien vitae posuere. Duis dapibus ex et augue iaculis, a viverra mi volutpat.",
	  "type": "Water",
	  "attack": 60,
	  "defense": 30,
	  "height": 6.5
	}
	nightwolf(mongod-3.2.1) be-mean-pokemons>
	```

## Atualizar a descrição do Pokemon armazenado na variável 'poke' e salvar na coleção

	```
	nightwolf(mongod-3.2.1) be-mean-pokemons> poke.description = "When Magikarp evolves into Gyarados, its brain cells undergo a structural transformation. It is said that this transformation is to blame for this Pokémon's wildly violent nature."
	When Magikarp evolves into Gyarados, its brain cells undergo a structural transformation. It is said that this transformation is to blame for this Pokémon's wildly violent nature.
	nightwolf(mongod-3.2.1) be-mean-pokemons> db.pokemons.save(poke)
	Updated 1 existing record(s) in 1ms
	WriteResult({
	  "nMatched": 1,
	  "nUpserted": 0,
	  "nModified": 1
	})
	nightwolf(mongod-3.2.1) be-mean-pokemons>
	```