Last login: Thu Nov 26 10:08:42 on ttys004
erackson:be-mean-instagram-mongodb-excercises erackson$ mongo be-mean-pokemons
MongoDB shell version: 3.0.3
connecting to: be-mean-pokemons
Mongo-Hacker 0.0.8
Server has startup warnings:
2015-11-26T10:33:18.427-0300 I CONTROL  [initandlisten]
2015-11-26T10:33:18.427-0300 I CONTROL  [initandlisten] ** WARNING: soft rlimits too low. Number of files is 256, should be at least 1000
Eracksons-MacBook-Pro(mongod-3.0.3) be-mean-pokemons> show dbs
be-mean-instagram → 0.078GB
be-mean           → 0.078GB
local             → 0.078GB
test              → 0.078GB
Eracksons-MacBook-Pro(mongod-3.0.3) be-mean-pokemons> show collections
Eracksons-MacBook-Pro(mongod-3.0.3) be-mean-pokemons> var pokemons = [
...   {
...     'name':'Exeggcute',
...     'description':'Ex ovo fofinho',
...     type:'grass/psychic',
...     'attack': 40,
...     'defense':80,
...     'height':4
...   },
...   {
...     'name':'Lickitung',
...     'description':'Cronista popular',
...     type:'norml',
...     'attack': 55,
...     'defense':75,
...     'height':12
...   },
...   {
...     'name':'Mr. Mime',
...     'description':'mmmm mmmmm mmm',
...     type:'psychic/fairy',
...     'attack': 45,
...     'defense':65,
...     'height':13
...   },
...   {
...     'name':'Snorlax',
...     'description':'Gato preguiçoso do Shaka',
...     type:'normal',
...     'attack': 110,
...     'defense':65,
...     'height':21
...   },
...   {
...     'name':'Dragonite',
...     'description':'Dragão fofinho do caralho',
...     type:'dragon/flying',
...     'attack': 134,
...     'defense':95,
...     'height':22
...   },
...   {
...     'name':'Wigglytuff',
...     'description':'High School Musical',
...     type:'normal/fairy',
...     'attack': 70,
...     'defense':45,
...     'height':10
...   },
...   {
...     'name':'Diglett',
...     'description':'Falo',
...     type:'ground',
...     'attack': 55,
...     'defense': 25,
...     'height':2
...   }
... ]
Eracksons-MacBook-Pro(mongod-3.0.3) be-mean-pokemons> db
DB(               DBCollection(     DBCommandCursor(  DBExplainQuery(   DBPointer(        DBQuery(          DBRef(            db
Eracksons-MacBook-Pro(mongod-3.0.3) be-mean-pokemons> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 1909ms
BulkWriteResult({
  "writeErrors": [ ],
  "writeConcernErrors": [ ],
  "nInserted": 7,
  "nUpserted": 0,
  "nMatched": 0,
  "nModified": 0,
  "nRemoved": 0,
  "upserted": [ ]
})
Eracksons-MacBook-Pro(mongod-3.0.3) be-mean-pokemons> show collections
pokemons       → 0.002MB / 0.008MB
system.indexes → 0.000MB / 0.008MB
Eracksons-MacBook-Pro(mongod-3.0.3) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("5659e32ada8ad0dfec4f8eba"),
  "name": "Exeggcute",
  "description": "Ex ovo fofinho",
  "type": "grass/psychic",
  "attack": 40,
  "defense": 80,
  "height": 4
}
{
  "_id": ObjectId("5659e32ada8ad0dfec4f8ebb"),
  "name": "Lickitung",
  "description": "Cronista popular",
  "type": "norml",
  "attack": 55,
  "defense": 75,
  "height": 12
}
{
  "_id": ObjectId("5659e32ada8ad0dfec4f8ebc"),
  "name": "Mr. Mime",
  "description": "mmmm mmmmm mmm",
  "type": "psychic/fairy",
  "attack": 45,
  "defense": 65,
  "height": 13
}
{
  "_id": ObjectId("5659e32ada8ad0dfec4f8ebd"),
  "name": "Snorlax",
  "description": "Gato preguiçoso do Shaka",
  "type": "normal",
  "attack": 110,
  "defense": 65,
  "height": 21
}
{
  "_id": ObjectId("5659e32ada8ad0dfec4f8ebe"),
  "name": "Dragonite",
  "description": "Dragão fofinho do caralho",
  "type": "dragon/flying",
  "attack": 134,
  "defense": 95,
  "height": 22
}
{
  "_id": ObjectId("5659e32ada8ad0dfec4f8ebf"),
  "name": "Wigglytuff",
  "description": "High School Musical",
  "type": "normal/fairy",
  "attack": 70,
  "defense": 45,
  "height": 10
}
{
  "_id": ObjectId("5659e32ada8ad0dfec4f8ec0"),
  "name": "Diglett",
  "description": "Falo",
  "type": "ground",
  "attack": 55,
  "defense": 25,
  "height": 2
}
Fetched 7 record(s) in 4ms
Eracksons-MacBook-Pro(mongod-3.0.3) be-mean-pokemons> var poke = db.pokemons.findOne({name: 'Exeggcute'})
Eracksons-MacBook-Pro(mongod-3.0.3) be-mean-pokemons> poke
{
  "_id": ObjectId("5659e32ada8ad0dfec4f8eba"),
  "name": "Exeggcute",
  "description": "Ex ovo fofinho",
  "type": "grass/psychic",
  "attack": 40,
  "defense": 80,
  "height": 4
}
Eracksons-MacBook-Pro(mongod-3.0.3) be-mean-pokemons> poke.
poke._id                    poke.defense                poke.height                 poke.toLocaleString(        poke.valueOf(
poke.attack                 poke.description            poke.name                   poke.toString(
poke.constructor            poke.hasOwnProperty(        poke.propertyIsEnumerable(  poke.type
Eracksons-MacBook-Pro(mongod-3.0.3) be-mean-pokemons> poke.description = 'Ex ovo fofinho.. sacou?? :P'
Ex ovo fofinho.. sacou?? :P
Eracksons-MacBook-Pro(mongod-3.0.3) be-mean-pokemons> poke
{
  "_id": ObjectId("5659e32ada8ad0dfec4f8eba"),
  "name": "Exeggcute",
  "description": "Ex ovo fofinho.. sacou?? :P",
  "type": "grass/psychic",
  "attack": 40,
  "defense": 80,
  "height": 4
}
Eracksons-MacBook-Pro(mongod-3.0.3) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 40ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
Eracksons-MacBook-Pro(mongod-3.0.3) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("5659e32ada8ad0dfec4f8eba"),
  "name": "Exeggcute",
  "description": "Ex ovo fofinho.. sacou?? :P",
  "type": "grass/psychic",
  "attack": 40,
  "defense": 80,
  "height": 4
}
{
  "_id": ObjectId("5659e32ada8ad0dfec4f8ebb"),
  "name": "Lickitung",
  "description": "Cronista popular",
  "type": "norml",
  "attack": 55,
  "defense": 75,
  "height": 12
}
{
  "_id": ObjectId("5659e32ada8ad0dfec4f8ebc"),
  "name": "Mr. Mime",
  "description": "mmmm mmmmm mmm",
  "type": "psychic/fairy",
  "attack": 45,
  "defense": 65,
  "height": 13
}
{
  "_id": ObjectId("5659e32ada8ad0dfec4f8ebd"),
  "name": "Snorlax",
  "description": "Gato preguiçoso do Shaka",
  "type": "normal",
  "attack": 110,
  "defense": 65,
  "height": 21
}
{
  "_id": ObjectId("5659e32ada8ad0dfec4f8ebe"),
  "name": "Dragonite",
  "description": "Dragão fofinho do caralho",
  "type": "dragon/flying",
  "attack": 134,
  "defense": 95,
  "height": 22
}
{
  "_id": ObjectId("5659e32ada8ad0dfec4f8ebf"),
  "name": "Wigglytuff",
  "description": "High School Musical",
  "type": "normal/fairy",
  "attack": 70,
  "defense": 45,
  "height": 10
}
{
  "_id": ObjectId("5659e32ada8ad0dfec4f8ec0"),
  "name": "Diglett",
  "description": "Falo",
  "type": "ground",
  "attack": 55,
  "defense": 25,
  "height": 2
}
Fetched 7 record(s) in 3ms
Eracksons-MacBook-Pro(mongod-3.0.3) be-mean-pokemons>
