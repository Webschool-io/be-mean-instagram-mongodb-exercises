#MongoDB - Aula 06 - Exercícios
autor: Angelo Rogério Rubin

##1. Fazer uma query para o campo `name` utilizando `explain` para ver o resultado da busca

```
db
.getCollection('pokemons')
.find({ name: /rattata/i })
.explain('executionStats')
.executionStats
.totalDocsExamined
610
```

##2. Criar um `index` para o campo `name`

```
db
.getCollection('pokemons')
.createIndex({ name: 1 })

db
.getCollection('pokemons')
.getIndexes()
/* 1 */
{
    "0" : {
        "v" : 1,
        "key" : {
            "_id" : 1
        },
        "name" : "_id_",
        "ns" : "be-mean.pokemons"
    },
    "1" : {
        "v" : 1,
        "key" : {
            "name" : 1.0000000000000000
        },
        "name" : "name_1",
        "ns" : "be-mean.pokemons"
    }
}
```

##3. Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca

```
db
.getCollection('pokemons')
.find({ name: /rattata/i })
.explain('executionStats')
.executionStats
.totalDocsExamined
1

db
.getCollection('pokemons')
.find({ name: /rattata/i })
.explain('executionStats')
.executionStats
.executionTimeMillis
1
```

##4. Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca

```
db
.getCollection('pokemons')
.find({ $and:[ { defense: { $gt: 60 } }, { speed: { $gt: 50 } } ] })
.explain('executionStats')
.executionStats
.totalDocsExamined
610

db
.getCollection('pokemons')
.find({ $and:[ { defense: { $gt: 60 } }, { speed: { $gt: 50 } } ] })
.explain('executionStats')
.executionStats
.executionTimeMillis
0

```

##5. Criar um `index` para esses dois campos juntos
```
db
.getCollection('pokemons')
.createIndex({ defense: 1, speed: 1 })
Inserted 1 record(s) in 30ms

db
.getCollection('pokemons')
.getIndexes()

/* 1 */
{
    "0" : {
        "v" : 1,
        "key" : {
            "_id" : 1
        },
        "name" : "_id_",
        "ns" : "be-mean.pokemons"
    },
    "1" : {
        "v" : 1,
        "key" : {
            "name" : 1.0000000000000000
        },
        "name" : "name_1",
        "ns" : "be-mean.pokemons"
    },
    "2" : {
        "v" : 1,
        "key" : {
            "defense" : 1.0000000000000000,
            "speed" : 1.0000000000000000
        },
        "name" : "defense_1_speed_1",
        "ns" : "be-mean.pokemons"
    }
}
```

##6. Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca
```
db
.getCollection('pokemons')
.find({ $and:[ { defense: { $gt: 60 } }, { speed: { $gt: 50 } } ] })
.explain('executionStats')
.executionStats
.totalDocsExamined
236

db
.getCollection('pokemons')
.find({ $and:[ { defense: { $gt: 60 } }, { speed: { $gt: 50 } } ] })
.explain('executionStats')
.executionStats
.executionTimeMillis
0
```