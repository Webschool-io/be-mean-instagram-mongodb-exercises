****** Usando 1 campo (Name)*******
> db.pokemons.find({"name" : "Muk"}).explain('executionStats').executionStats.totalDocsExamined
610
> db.pokemons.find({"name" : "Muk"}).explain('executionStats').executionStats.executionTimeMillis
0

#Indice com apenas um campo da database Pokemons
> db.pokemons.createIndex({name : 1})
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 1,
        "numIndexesAfter" : 2,
        "ok" : 1
}
> db.pokemons.find({"name" : "Muk"})
{ "_id" : ObjectId("564b1dae25337263280d048c"), "attack" : 105, "created" : "2013-11-03T15:05:41.452237", "defense" : 75, "height" : "12", "hp" : 105, "name" : "Muk", "speed" : 50, "types" : [ "poison" ] }
> db.pokemons.find({"name" : "Muk"}).explain('executionStats').executionStats.executionTimeMillis
0
> db.pokemons.find({"name" : "Muk"}).explain('executionStats').executionStats.totalDocsExamined
1

*****Usando 2 campos (Attack e HP)******

> db.pokemons.find({"attack" : "25", "hp": "45"}).explain('executionStats').executionStats.totalDocsExamined
610
> db.pokemons.find({"attack" : 25, "hp": 45}).explain('executionStats').executionStats.executionTimeMillis
0

#Agora criar o indice com dois campos da database pokemons
> db.pokemons.createIndex({attack : 1, hp : 1})
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 2,
        "numIndexesAfter" : 3,
        "ok" : 1
}
> db.pokemons.find({"attack" : 25, "hp": 45}).explain('executionStats').executionStats.executionTimeMillis
0
> db.pokemons.find({"attack" : 25, "hp": 45}).explain('executionStats').executionStats.totalDocsExamined
1
