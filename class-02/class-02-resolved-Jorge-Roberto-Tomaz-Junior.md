# MongoDB - Aula 02 - Exercício
autor: Jorge Roberto Tomaz Junior

## Listagem das databases (passo 2)

        jorge@dev:~$ mongo
        MongoDB shell version: 3.0.7
        connecting to: test
        Server has startup warnings: 
        2015-12-04T21:36:58.204-0200 I CONTROL  [initandlisten] 
        2015-12-04T21:36:58.204-0200 I CONTROL  [initandlisten] ** WARNING: /sys/kernel/mm/transparent_hugepage/enabled is 'always'.
        2015-12-04T21:36:58.204-0200 I CONTROL  [initandlisten] **        We suggest setting it to 'never'
        2015-12-04T21:36:58.204-0200 I CONTROL  [initandlisten] 
        2015-12-04T21:36:58.204-0200 I CONTROL  [initandlisten] ** WARNING: /sys/kernel/mm/transparent_hugepage/defrag is 'always'.
        2015-12-04T21:36:58.204-0200 I CONTROL  [initandlisten] **        We suggest setting it to 'never'
        2015-12-04T21:36:58.204-0200 I CONTROL  [initandlisten] 
        > use users
        switched to db users
        > show dbs;
        local  0.078GB

## Listagem das coleções (passo 3)
        > show collections
        >

## Cadastro de usuarios (passo 4)
        > show collections;
        >   var users = [{name : "Jorge Roberto", job: "Programmer"}]
        > 
        > db.users.insert(users)
        BulkWriteResult({
          "writeErrors" : [ ],
          "writeConcernErrors" : [ ],
          "nInserted" : 1,
          "nUpserted" : 0,
          "nMatched" : 0,
          "nModified" : 0,
          "nRemoved" : 0,
          "upserted" : [ ]
        })


## Lista dos pokemons (passo 5)
        > db.users.find().pretty()
        {
          "_id" : ObjectId("56622612f78609733094c745"),
          "name" : "Jorge Roberto",
          "job" : "Programmer"
        }
> 

## Pokemon (passo 6)
        > var query = {"name" : "Jorge Roberto"};
        > var user = db.users.findOne(query)
        > user
        {
          "_id" : ObjectId("56622612f78609733094c745"),
          "name" : "Jorge Roberto",
          "job" : "Programmer"
        }
        > 

## Atualização do Pokemon (passo 7)
        > user.job = "Programmer web";
        Programmer web
        > db.users.save(user)
        WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
        > db.users.findOne(query)
        {
          "_id" : ObjectId("56622612f78609733094c745"),
          "name" : "Jorge Roberto",
          "job" : "Programmer web"
        }
        > 
