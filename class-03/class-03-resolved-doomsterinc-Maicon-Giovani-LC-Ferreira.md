# MongoDb - Aula 03 - Exercício
autor: Maicon Giovani LC Ferreira

## Liste todos Pokemons com a altura menor que 0.5;

```
> var query = {height:{$lt:0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("573a26e91bd514b027750ce1"), "name" : "Paras", "description" : "Small Pokemon", "type" : "Grass", "attack" : 35, "defense" : 55, "height" : 0.3 }
{ "_id" : ObjectId("573a26e91bd514b027750ce2"), "name" : "Exeggcute", "description" : "Small Small Pokemon", "type" : "Grass", "attack" : 60, "defense" : 80, "height" : 0.4 }

```
## Liste todos Pokemons com a altura maior ou igual que 0.5;

```
> var query = {height:{$gte:0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("57362f9b1bd514b027750cdb"), "name" : "Trevenant", "description" : "It can control trees at will. It will trap people who harm the forest, so they can never leave.", "type" : "Ghost", "attack" : 110, "defense" : 76, "height" : 4.11 }
{ "_id" : ObjectId("57362f9b1bd514b027750cdc"), "name" : "Yveltal", "description" : "Pokémon fodaum que avua e eu nunca peguei ", "type" : "Dark", "attack" : 131, "defense" : 95, "height" : 19 }
{ "_id" : ObjectId("57362f9b1bd514b027750cdd"), "name" : "Steelix", "description" : "Steelix lives even further underground than Onix. This Pokémon is known to dig toward the earths core. There are records of this Pokémon reaching a depth of over six-tenths of a mile underground.", "type" : "Steel", "attack" : 85, "defense" : 200, "height" : 30.05 }
{ "_id" : ObjectId("57362f9b1bd514b027750cde"), "name" : "Marowak", "description" : "Marowak is the evolved form of a Cubone that has overcome its sadness at the loss of its mother and grown tough. This Pokémons tempered and hardened spirit is not easily broken.", "type" : "Ground", "attack" : 80, "defense" : 110, "height" : 3.03 }
{ "_id" : ObjectId("57362f9b1bd514b027750cdf"), "name" : "Kadabra", "description" : "Kadabra emits a peculiar alpha wave if it develops a headache. Only those people with a particularly strong psyche can hope to become a Trainer of this Pokémon.", "type" : "Psychic", "attack" : 35, "defense" : 30, "height" : 4.03 }
{ "_id" : ObjectId("573a26e91bd514b027750ce3"), "name" : "Voltorb", "description" : "Pokemon ugly small", "type" : "Eletric", "attack" : 40, "defense" : 50, "height" : 0.5 }

```
## Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama;

```
> var query = {$and: [{height:{$lte:0.5}},{type:'Grass'}]}
> db.pokemons.find(query)
{ "_id" : ObjectId("573a26e91bd514b027750ce1"), "name" : "Paras", "description" : "Small Pokemon", "type" : "Grass", "attack" : 35, "defense" : 55, "height" : 0.3 }
{ "_id" : ObjectId("573a26e91bd514b027750ce2"), "name" : "Exeggcute", "description" : "Small Small Pokemon", "type" : "Grass", "attack" : 60, "defense" : 80, "height" : 0.4 }

```

## Liste todos Pokemons com o name Pikachu OU com attack menor ou igual que 0.5;

```
> var query = {$or: [{name:'Pikachu'},{attack:{$lte:0.5}}]}
> db.pokemons.find(query)
> 

```

## Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com height menor ou igual que 0.5;

```
> var query = {$and: [{attack:{$gte:48}},{height:{$lte:0.5}}]}
> db.pokemons.find(query)
{ "_id" : ObjectId("573a26e91bd514b027750ce2"), "name" : "Exeggcute", "description" : "Small Small Pokemon", "type" : "Grass", "attack" : 60, "defense" : 80, "height" : 0.4 }

```

