## MongoDB - Aula 02 - Exercício  
Autor: Gabriel Kalani


1. Criar database
--------------------

```
gkal19:~/workspace $ mongo be-mean-pokemons
MongoDB shell version: 2.6.11
connecting to: be-mean-pokemons
Mongo-Hacker 0.0.9
gkal19-aula-bemean-2468380(mongod-2.6.11) be-mean-pokemons> 
```


2. Listar databases
----------------------

```
be-mean-pokemons> show dbs
db      → 0.078GB
local   → 0.078GB
be-mean → 0.078GB
test    → 0.078GB
admin   → (empty)
```


3. Listando collections
---------------------------

```
be-mean-pokemons> show collections
```


4. Inserir os Pokémons
-----------------------------------

```
be-mean-pokemons> db.pokemons.insert({name:'Metagross',description:'Esse cara é tão esperto quanto o mizeravi',type:'esperto',attack:135,defense:130,height:1.6})  
Inserted 1 record(s) in 187ms
WriteResult({
  "nInserted": 1
})  

be-mean-pokemons> db.pokemons.insert({'name':'Pikachu','description':'Um hamster/rato bem fofo e foda','type':'Electric','attack': 58,'height': 0.4})
Inserted 1 record(s) in 15ms
WriteResult({
  "nInserted": 1
})

be-mean-pokemons> db.pokemons.insert({'name':'Mewtwo','description':'Uma "cobaia de laboratório" hahah ','type':'Psychic','attack': 60,'height': 2.0})
Inserted 1 record(s) in 9ms
WriteResult({
  "nInserted": 1
})

be-mean-pokemons> db.pokemons.insert({'name':'Suissa','description':'Esse pokemon tem ideias fodas "bagarai" que vão trazer muito dinheiro e acabar com o capitalismo','type':'fodao','attack': 100,'height': 2.0})
Inserted 1 record(s) in 4ms
WriteResult({
  "nInserted": 1
})

be-mean-pokemons> db.pokemons.insert({'name':'Charmander','description':'Pra quem procura fazer um churrasco no final de semana, o Charmander é uma boa opção','type':'fogo','attack': 46,'height': 0.9})
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})
```

5. Listar os Pokemons
----------------------------------

```
be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("56a90483529091c469c87feb"),
  "name": "Metagross",
  "description": "Esse cara é tão esperto quanto o mizeravi",
  "type": "esperto",
  "attack": 135,
  "defense": 130,
  "height": 1.6
}
{
  "_id": ObjectId("56a90674529091c469c87fec"),
  "name": "Pikachu",
  "description": "Um hamster/rato bem fofo e foda",
  "type": "raio",
  "attack": 58,
  "height": 0.9
}
{
  "_id": ObjectId("56a906fe529091c469c87fed"),
  "name": "Mewtwo",
  "description": "Uma \"cobaia de laboratório\" hahah ",
  "type": "fdp",
  "attack": 78,
  "height": 1
}
{
  "_id": ObjectId("56a907dd529091c469c87fee"),
  "name": "Suissa",
  "description": "Esse pokemon tem ideias fodas \"bagarai\" que vão trazer muito dinheiro",
  "type": "fodao",
  "attack": 100,
  "height": 2
}
{
  "_id": ObjectId("56a907fd529091c469c87fef"),
  "name": "Suissa",
  "description": "Esse pokemon tem ideias fodas \"bagarai\" que vão trazer muito dinheiro e acabar com o capitalismo",
  "type": "fodao",
  "attack": 100,
  "height": 2
}
{
  "_id": ObjectId("56a908fc529091c469c87ff0"),
  "name": "Charmander",
  "description": "Pra quem procura fazer um churrasco no final de semana, o Charmander é uma boa opção",
  "type": "fogo",
  "attack": 46,
  "height": 0.9
}
Fetched 6 record(s) in 187ms
```

6. Buscar um Pokémon
-----------------------


```
be-mean-pokemons> var query = {name:'Suissa'} 
be-mean-pokemons> var poke = db.pokemons.findOne(query)
be-mean-pokemons> poke
{
  "_id": ObjectId("56a907dd529091c469c87fee"),
  "name": "Suissa",
  "description": "Esse pokemon tem ideias fodas \"bagarai\" que vão trazer muito dinheiro",
  "type": "fodao",
  "attack": 100,
  "height": 2
}  
```


7. Modificando description e salvar
-------------------------------------------

```
be-mean-pokemons> poke.description = 'Esse vai destruir o Capitalismo ehuehuehu'
Esse vai destruir o Capitalismo ehuehuehu
gkal19-aula-bemean-2468380(mongod-2.6.11) be-mean-pokemons> poke
{
  "_id": ObjectId("56a907dd529091c469c87fee"),
  "name": "Suissa",
  "description": "Esse vai destruir o Capitalismo ehuehuehu",
  "type": "fodao",
  "attack": 100,
  "height": 2
}

```

````
be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 179ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

```

````
be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("56a90483529091c469c87feb"),
  "name": "Metagross",
  "description": "Esse cara é tão esperto quanto o mizeravi",
  "type": "esperto",
  "attack": 135,
  "defense": 130,
  "height": 1.6
}
{
  "_id": ObjectId("56a90674529091c469c87fec"),
  "name": "Pikachu",
  "description": "Um hamster/rato bem fofo e foda",
  "type": "raio",
  "attack": 58,
  "height": 0.9
}
{
  "_id": ObjectId("56a906fe529091c469c87fed"),
  "name": "Mewtwo",
  "description": "Uma \"cobaia de laboratório\" hahah ",
  "type": "fdp",
  "attack": 78,
  "height": 1
}
{
  "_id": ObjectId("56a907dd529091c469c87fee"),
  "name": "Suissa",
  "description": "Esse vai destruir o Capitalismo ehuehuehu",
  "type": "fodao",
  "attack": 100,
  "height": 2
}
{
  "_id": ObjectId("56a907fd529091c469c87fef"),
  "name": "Suissa",
  "description": "Esse pokemon tem ideias fodas \"bagarai\" que vão trazer muito dinheiro e acabar com o capitalismo",
  "type": "fodao",
  "attack": 100,
  "height": 2
}
{
  "_id": ObjectId("56a908fc529091c469c87ff0"),
  "name": "Charmander",
  "description": "Pra quem procura fazer um churrasco no final de semana, o Charmander é uma boa opção",
  "type": "fogo",
  "attack": 46,
  "height": 0.9
}
Fetched 6 record(s) in 82ms
```