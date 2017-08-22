#MongoDB - Aula 06 - Exercício
autor: Carlos Henrique Ribeiro

##1. Fazer uma query para o campo `name` utilizando `explain` para ver o resultado da busca

```
> db.pokemons.find({ name: "Mewtwo" }).explain('executionStats').executionStats;
{
        "executionSuccess" : true,
        "nReturned" : 1,
        "executionTimeMillis" : 23,
        "totalKeysExamined" : 0,
        "totalDocsExamined" : 610,
        "executionStages" : {
                "stage" : "COLLSCAN",
                "filter" : {
                        "name" : {
                                "$eq" : "Mewtwo"
                        }
                },
                "nReturned" : 1,
                "executionTimeMillisEstimate" : 30,
                "works" : 612,
                "advanced" : 1,
                "needTime" : 610,
                "needFetch" : 0,
                "saveState" : 5,
                "restoreState" : 5,
                "isEOF" : 1,
                "invalidates" : 0,
                "direction" : "forward",
                "docsExamined" : 610
        }
}

> db.pokemons.find({ name: "Mewtwo" }).explain('executionStats').executionStats.totalDocsExamined;
610

> db.pokemons.find({ name: "Mewtwo" }).explain('executionStats').executionStats.executionTimeMillis;
0

```

##2. Criar um `index` um para o campo `name`

```
> db.pokemons.createIndex({ name: 1 });
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 1,
        "numIndexesAfter" : 2,
        "ok" : 1
}

```

##3. Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca

```
> db.pokemons.find({ name: "Mewtwo" }).explain('executionStats').executionStats.totalDocsExamined;
1

> db.pokemons.find({ name: "Mewtwo" }).explain('executionStats').executionStats.executionTimeMillis;
0

```

##4. Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca

```
> db.pokemons.find({ $and: [ { attack: { $lt: 50 } }, { height: { $gt: 0.5 } } ] }).explain('executionStats').executionStats.totalDocsExamined;
610

> db.pokemons.find({ $and: [ { attack: { $lt: 50 } }, { height: { $gt: 0.5 } } ] }).explain('executionStats').executionStats.executionTimeMillis;
0

```

##5. Criar um `index` para esses dois campos juntos

```
> db.pokemons.createIndex({ attack: 1, height: 1 });
{
        "createdCollectionAutomatically" : false,
        "numIndexesBefore" : 2,
        "numIndexesAfter" : 3,
        "ok" : 1
}
```

##6. Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca

```
> db.pokemons.find({ $and: [ { attack: { $lt: 50 } }, { height: { $gt: 0.5 } } ] }).explain('executionStats').executionStats.totalDocsExamined;
0

> db.pokemons.find({ $and: [ { attack: { $lt: 50 } }, { height: { $gt: 0.5 } } ] }).explain('executionStats').executionStats.executionTimeMillis;
0
```
