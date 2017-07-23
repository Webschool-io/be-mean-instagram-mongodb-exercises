# MongoDB - Aula 03 - Exercício
autor: Nurielly Caroline Brizola


# Liste todos Pokemons com a altura menor que 0.5
```
var query = {"height":{$lt:0.5}}

db.pokemons.find(query)
{ "_id" : ObjectId("56ae56f1d45f835ef1c80830"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "elétrico", "attack" : 55, "height" : 0.4 }
{ "_id" : ObjectId("56ae56f1d45f835ef1c80831"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }
{ "_id" : ObjectId("56ae56f1d45f835ef1c80834"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3 }
{ "_id" : ObjectId("56ae56f1d45f835ef1c80838"), "name" : "Minun", "description" : "chuveiros de faísca", "type" : "elétrico", "attack" : 40, "height" : 0.4 }

```
# Liste todos Pokemons com a altura maior ou igual que 0.5
```
var query = {height:{$gte:0.5}}

db.pokemons.find(query)
{ "_id" : ObjectId("56ae56f1d45f835ef1c80832"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6 }
{ "_id" : ObjectId("56ae56f1d45f835ef1c80833"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5 }
{ "_id" : ObjectId("56ae56f1d45f835ef1c80835"), "name" : "Chespin", "description" : "Cabeça de chifre", "type" : "grama", "attack" : 61, "height" : 0.5 }
{ "_id" : ObjectId("56ae56f1d45f835ef1c80836"), "name" : "Sharpedo", "description" : "valentão do mar", "type" : "água", "attack" : 120, "height" : 1.8 }
{ "_id" : ObjectId("56ae56f1d45f835ef1c80837"), "name" : "Onix", "description" : "valentão do mar", "type" : "chão", "attack" : 45, "height" : 8.8 }
{ "_id" : ObjectId("56ae56f1d45f835ef1c80839"), "name" : "Zangoose", "description" : "Pokemon do Kratos", "type" : "normal", "attack" : 115, "height" : 1.3 }
{ "_id" : ObjectId("56ae56f1d45f835ef1c8083a"), "name" : "Arcanine ", "description" : "mistura de cachorro e gato", "type" : "fogo", "attack" : 110, "height" : 1.9 }
{ "_id" : ObjectId("56ae56f1d45f835ef1c8083b"), "name" : "Staryu", "description" : "estrelinha", "type" : "água", "attack" : 45, "height" : 0.8 }
{ "_id" : ObjectId("56ae56f1d45f835ef1c8083c"), "name" : "Riolu", "description" : "cachorro fresco", "type" : "combate", "attack" : 70, "height" : 0.7 }
{ "_id" : ObjectId("56ae56f1d45f835ef1c8083d"), "name" : "Serperior", "description" : "cobra que se acha", "type" : "grama", "attack" : 75, "height" : 3.3 }
{ "_id" : ObjectId("56ae56f1d45f835ef1c8083e"), "name" : "Umbreon", "description" : "cachorro preto", "type" : "escuro", "attack" : 65, "height" : 1 }

```
# Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama
```
var query = ({ $and: [{height: {$lte:0.5}}, {type: 'grama'}]})
db.pokemons.find(query)

{ "_id" : ObjectId("56ae56f1d45f835ef1c80831"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }
{ "_id" : ObjectId("56ae56f1d45f835ef1c80835"), "name" : "Chespin", "description" : "Cabeça de chifre", "type" : "grama", "attack" : 61, "height" : 0.5 }

```
# Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5
```
var query = ( { $or:[{name:'Pikachu'}, {attack: {$lt:0.5}}]})

db.pokemons.find(query)
{ "_id" : ObjectId("56ae56f1d45f835ef1c80830"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "elétrico", "attack" : 55, "height" : 0.4 }


```
# Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5
```
query = ({ $and: [{attack:{$gte:48}}, {height: {$lte:0.5}}] })

db.pokemons.find(query)
{ "_id" : ObjectId("56ae56f1d45f835ef1c80830"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "elétrico", "attack" : 55, "height" : 0.4 }
{ "_id" : ObjectId("56ae56f1d45f835ef1c80831"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }
{ "_id" : ObjectId("56ae56f1d45f835ef1c80833"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5 }
{ "_id" : ObjectId("56ae56f1d45f835ef1c80835"), "name" : "Chespin", "description" : "Cabeça de chifre", "type" : "grama", "attack" : 61, "height" : 0.5 }
```

