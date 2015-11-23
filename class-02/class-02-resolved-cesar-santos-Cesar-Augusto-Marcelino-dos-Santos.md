# MongoDB - Aula 02 - Exercício
autor: César Augusto Marcelino dos Santos

## Crie uma database chamada be-mean-pokemons
cesinha@vilaDoChaves:~$ mongo be-mean-pokemons
MongoDB shell version: 3.0.7
connecting to: be-mean-pokemons
Mongo-Hacker 0.0.8
Server has startup warnings: 
2015-11-19T20:12:38.034-0200 I CONTROL  [initandlisten] 
2015-11-19T20:12:38.034-0200 I CONTROL  [initandlisten] ** WARNING: /sys/kernel/mm/transparent_hugepage/enabled is 'always'.
2015-11-19T20:12:38.034-0200 I CONTROL  [initandlisten] **        We suggest setting it to 'never'
2015-11-19T20:12:38.034-0200 I CONTROL  [initandlisten] 
2015-11-19T20:12:38.034-0200 I CONTROL  [initandlisten] ** WARNING: /sys/kernel/mm/transparent_hugepage/defrag is 'always'.
2015-11-19T20:12:38.034-0200 I CONTROL  [initandlisten] **        We suggest setting it to 'never'
2015-11-19T20:12:38.034-0200 I CONTROL  [initandlisten] 

## Liste quais databases você possui nesse servidor
vilaDoChaves(mongod-3.0.7) be-mean-pokemons> show dbs
be-mean           → 0.078GB
local             → 0.078GB
be-mean-instagram → 0.078GB

## Liste quais coleções você possui nessa database
vilaDoChaves(mongod-3.0.7) be-mean-pokemons> show collections

## Insira pelo menos 5 pokémons À SUA ESCOLHA utilizando o mesmo padrão de campos utilizado: name, description, attack, defense e height
vilaDoChaves(mongod-3.0.7) be-mean-pokemons> var articuno = {"name": "articuno", "attack": 85, "defense": 100, "height": "1.7", description = "Articuno is a legendary bird Pokémon that can control ice. The flapping of its wings chills the air. As a result, it is said that when this Pokémon flies, snow will fall." }
2015-11-19T23:58:12.378-0200 E QUERY    SyntaxError: Unexpected token =
vilaDoChaves(mongod-3.0.7) be-mean-pokemons> var articuno = {"name": "articuno", "attack": 85, "defense": 100, "height": "1.7", description: "Articuno is a legendary bird Pokémon that can control ice. The flapping of its wings chills the air. As a result, it is said that when this Pokémon flies, snow will fall." }
vilaDoChaves(mongod-3.0.7) be-mean-pokemons> var zapdos = {"name": "zapdos", "attack": 90, "defense": 85, "height": "1.6", description: "Zapdos is a legendary bird Pokémon that has the ability to control electricity. It usually lives in thunderclouds. The Pokémon gains power if it is stricken by lightning bolts." }
vilaDoChaves(mongod-3.0.7) be-mean-pokemons> var moltres = {"name": "moltres", "attack": 100, "defense": 90, "height": "2.0", description: "Moltres is a legendary bird Pokémon that has the ability to control fire. If this Pokémon is injured, it is said to dip its body in the molten magma of a volcano to burn and heal itself." }
vilaDoChaves(mongod-3.0.7) be-mean-pokemons> var mewtwo = {"name": "mewtwo", "attack": 110, "defense": 90, "height": "2.0", description: "Pica das galáxias!" }
vilaDoChaves(mongod-3.0.7) be-mean-pokemons> var mew = {"name": "mew", "attack": 100, "defense": 100, "height": "0.4", description: "Mew is said to possess the genetic composition of all Pokémon. It is capable of making itself invisible at will, so it entirely avoids notice even if it approaches people." }
vilaDoChaves(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(articuno)
Inserted 1 record(s) in 656ms
WriteResult({
  "nInserted": 1
})
vilaDoChaves(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(zapdos)
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})
vilaDoChaves(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(moltres)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})
vilaDoChaves(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(mewtwo)
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})
vilaDoChaves(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(mew)
Inserted 1 record(s) in 4ms
WriteResult({
  "nInserted": 1
})

## Liste os pokémons existentes na sua coleção
vilaDoChaves(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("564e7f01b58ec32f36e2f89c"),
  "name": "articuno",
  "attack": 85,
  "defense": 100,
  "height": "1.7",
  "description": "Articuno is a legendary bird Pokémon that can control ice. The flapping of its wings chills the air. As a result, it is said that when this Pokémon flies, snow will fall."
}
{
  "_id": ObjectId("564e7f07b58ec32f36e2f89d"),
  "name": "zapdos",
  "attack": 90,
  "defense": 85,
  "height": "1.6",
  "description": "Zapdos is a legendary bird Pokémon that has the ability to control electricity. It usually lives in thunderclouds. The Pokémon gains power if it is stricken by lightning bolts."
}
{
  "_id": ObjectId("564e7f0db58ec32f36e2f89e"),
  "name": "moltres",
  "attack": 100,
  "defense": 90,
  "height": "2.0",
  "description": "Moltres is a legendary bird Pokémon that has the ability to control fire. If this Pokémon is injured, it is said to dip its body in the molten magma of a volcano to burn and heal itself."
}
{
  "_id": ObjectId("564e7f12b58ec32f36e2f89f"),
  "name": "mewtwo",
  "attack": 110,
  "defense": 90,
  "height": "2.0",
  "description": "Pica das galáxias!"
}
{
  "_id": ObjectId("564e7f15b58ec32f36e2f8a0"),
  "name": "mew",
  "attack": 100,
  "defense": 100,
  "height": "0.4",
  "description": "Mew is said to possess the genetic composition of all Pokémon. It is capable of making itself invisible at will, so it entirely avoids notice even if it approaches people."
}
Fetched 5 record(s) in 3ms

## Busque um pokémon à sua escolha, pelo nome, e armazene-o em uma variável chamada `poke`
vilaDoChaves(mongod-3.0.7) be-mean-pokemons> var q = {"name": "mewtwo"}
vilaDoChaves(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(q)
vilaDoChaves(mongod-3.0.7) be-mean-pokemons> poke
{
  "_id": ObjectId("564e7f12b58ec32f36e2f89f"),
  "name": "mewtwo",
  "attack": 110,
  "defense": 90,
  "height": "2.0",
  "description": "Pica das galáxias!"
}

## Modifique sua `description` e salve-a
vilaDoChaves(mongod-3.0.7) be-mean-pokemons> poke.description = "Mewtwo is a Pokémon that was created by genetic manipulation. However, even though the scientific power of humans created this Pokémon's body, they failed to endow Mewtwo with a compassionate heart."
Mewtwo is a Pokémon that was created by genetic manipulation. However, even though the scientific power of humans created this Pokémon's body, they failed to endow Mewtwo with a compassionate heart.
vilaDoChaves(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 3ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
vilaDoChaves(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("564e7f01b58ec32f36e2f89c"),
  "name": "articuno",
  "attack": 85,
  "defense": 100,
  "height": "1.7",
  "description": "Articuno is a legendary bird Pokémon that can control ice. The flapping of its wings chills the air. As a result, it is said that when this Pokémon flies, snow will fall."
}
{
  "_id": ObjectId("564e7f07b58ec32f36e2f89d"),
  "name": "zapdos",
  "attack": 90,
  "defense": 85,
  "height": "1.6",
  "description": "Zapdos is a legendary bird Pokémon that has the ability to control electricity. It usually lives in thunderclouds. The Pokémon gains power if it is stricken by lightning bolts."
}
{
  "_id": ObjectId("564e7f0db58ec32f36e2f89e"),
  "name": "moltres",
  "attack": 100,
  "defense": 90,
  "height": "2.0",
  "description": "Moltres is a legendary bird Pokémon that has the ability to control fire. If this Pokémon is injured, it is said to dip its body in the molten magma of a volcano to burn and heal itself."
}
{
  "_id": ObjectId("564e7f15b58ec32f36e2f8a0"),
  "name": "mew",
  "attack": 100,
  "defense": 100,
  "height": "0.4",
  "description": "Mew is said to possess the genetic composition of all Pokémon. It is capable of making itself invisible at will, so it entirely avoids notice even if it approaches people."
}
{
  "_id": ObjectId("564e7f12b58ec32f36e2f89f"),
  "name": "mewtwo",
  "attack": 110,
  "defense": 90,
  "height": "2.0",
  "description": "Mewtwo is a Pokémon that was created by genetic manipulation. However, even though the scientific power of humans created this Pokémon's body, they failed to endow Mewtwo with a compassionate heart."
}
Fetched 5 record(s) in 10ms
vilaDoChaves(mongod-3.0.7) be-mean-pokemons> 
