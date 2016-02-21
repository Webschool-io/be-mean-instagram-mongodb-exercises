1:
BlackArch(mongod-3.2.1) test> use be-mean-pokemons

2:

BlackArch(mongod-3.2.1) be-mean-pokemons> show dbs
be-mean-instagram → 0.000GB
be-mean-pokemons  → 0.000GB
be_mean           → 0.002GB
local             → 0.000GB
test              → 0.000GB

3:

BlackArch(mongod-3.2.1) be-mean-pokemons> show collections
pokemon  → 0.000MB / 0.031MB
pokemons → 0.001MB / 0.035MB

4:

BlackArch(mongod-3.2.1) be-mean-pokemons> db.pokemons.find()
{
      "_id": ObjectId("56c64b4304e657a13e0cd708"),
        "name": "darkrai",
          "attack": 200,
            "defense": 120,
              "height": 10,
                "description": "Melhor pokemon ever"
}
{
      "_id": ObjectId("56c64b6904e657a13e0cd709"),
        "name": "charizard",
          "attack": 150,
            "defense": 50,
              "height": 89
}
{
      "_id": ObjectId("56c64baa04e657a13e0cd70c"),
        "name": "umbreon",
          "attack": 77,
            "defense": 55,
              "height": 44
}
{
      "_id": ObjectId("56c64bde04e657a13e0cd70d"),
        "name": "vaporeon",
          "attack": 87,
            "defense": 29,
              "height": 54
}
{
      "_id": ObjectId("56c64bf304e657a13e0cd70e"),
        "name": "mew",
          "attack": 200,
            "defense": 209,
              "height": 4
}
{
      "_id": ObjectId("56c64c0404e657a13e0cd70f"),
        "name": "mewtwo",
          "attack": 300,
            "defense": 290,
              "height": 40
}
{
      "_id": ObjectId("56c64c2904e657a13e0cd710"),
        "name": "arceus",
          "attack": 400,
            "defense": 390,
              "height": 400
}
{
      "_id": ObjectId("56c64cca04e657a13e0cd711"),
        "name": "darkrai"
}
Fetched 8 record(s) in 2ms

6:

BlackArch(mongod-3.2.1) be-mean-pokemons> var query = {"name":"darkrai"}
BlackArch(mongod-3.2.1) be-mean-pokemons> var poke = db.pokemons.findOne(query)

7:

BlackArch(mongod-3.2.1) be-mean-pokemons> poke.description = "Melhor pokemon ever"
Melhor pokemon ever
BlackArch(mongod-3.2.1) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 1ms
WriteResult({
      "nMatched": 1,
        "nUpserted": 0,
          "nModified": 0
})

