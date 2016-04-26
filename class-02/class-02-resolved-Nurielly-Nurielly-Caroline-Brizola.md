# MongoDB - Aula 02 - Exercício
autor: Nurielly Caroline Brizola

# Crie uma database chamada be-mean-pokemons
```
mongo be-mean-pokemons
```

# Liste quais databases você possui nesse servidor
```
show dbs
be-mean-instagram  0.078GB
be_mean            0.078GB
local              0.078GB
teste              0.078GB
```

# Liste quais coleções você possui nessa database
```
show collections
pokemons
system.indexes
```

# Insira pelo menos 5 pokemons A SUA ESCOLHA utilizando o mesmo padrão de campos utilizado: name, description, attack, defense e height
```
var pikachu = {"name":"Pikachu","description":"Rato elétrico bem fofinho","type": "elétrico", attack: 55, height: 0.4 }
var bulbassauro = {"name":"Bulbassauro","description":"Chicote de trepadeira","type": "grama", "attack": 49, height: 0.4 }
var charmander = {"name":"Charmander","description":"Esse é o cão chupando manga de fofinho","type": "fogo", "attack": 52, height: 0.6 }
var squirtle = {"name":"Squirtle","description":"Ejeta água que passarinho não bebe","type": "água", "attack": 48, height: 0.5 }
var caterpie = {"name":"Caterpie","description":"Larva lutadora","type": "inseto", attack: 30, height: 0.3 }
var chespin = {"name":"Chespin","description":"Cabeça de chifre","type": "grama", attack: 61, height: 0.5 }
var sharpedo = {"name":"Sharpedo","description":"valentão do mar","type": "água", attack: 120, height: 1.8 }
var onix = {"name":"Onix","description":"valentão do mar","type": "chão", attack: 45, height: 8.8 }
var minun = {"name":"Minun","description":"chuveiros de faísca","type": "elétrico", attack: 40, height: 0.4}
var zangoose = {"name":"Zangoose","description":"cover do Kratos","type": "normal", attack: 115, height: 1.3}
var arcanine = {"name":"Arcanine ","description":"mistura de cachorro e gato","type": "fogo", attack: 110, height: 1.9}
var staryu = {"name":"Staryu","description":"estrelinha","type": "água", attack: 45, height: 0.8}
var riolu = {"name":"Riolu","description":"cachorro fresco","type": "combate", attack: 70, height: 0.7}
var serperior = {"name":"Serperior","description":"cobra que se acha","type": "grama", attack: 75, height: 3.3}
var umbreon = {"name":"Umbreon","description":"cachorro preto","type": "escuro", attack: 65, height: 1.0}

var pokemons = [pikachu, bulbassauro, charmander, squirtle, caterpie, chespin, sharpedo, onix, minun, zangoose, arcanine, staryu, riolu, serperior, umbreon]

db.pokemons.insert(pokemons)
BulkWriteResult({
        "writeErrors" : [ ],
        "writeConcernErrors" : [ ],
        "nInserted" : 15,
        "nUpserted" : 0,
        "nMatched" : 0,
        "nModified" : 0,
        "nRemoved" : 0,
        "upserted" : [ ]
})

```

# Liste os pokemons existentes na sua coleção
```
db.pokemons.find()
{ "_id" : ObjectId("56ae56f1d45f835ef1c80830"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "elétrico", "attack" : 55, "height" : 0.4 }
{ "_id" : ObjectId("56ae56f1d45f835ef1c80831"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }
{ "_id" : ObjectId("56ae56f1d45f835ef1c80832"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6 }
{ "_id" : ObjectId("56ae56f1d45f835ef1c80833"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5 }
{ "_id" : ObjectId("56ae56f1d45f835ef1c80834"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3 }
{ "_id" : ObjectId("56ae56f1d45f835ef1c80835"), "name" : "Chespin", "description" : "Cabeça de chifre", "type" : "grama", "attack" : 61, "height" : 0.5 }
{ "_id" : ObjectId("56ae56f1d45f835ef1c80836"), "name" : "Sharpedo", "description" : "valentão do mar", "type" : "água", "attack" : 120, "height" : 1.8 }
{ "_id" : ObjectId("56ae56f1d45f835ef1c80837"), "name" : "Onix", "description" : "valentão do mar", "type" : "chão", "attack" : 45, "height" : 8.8 }
{ "_id" : ObjectId("56ae56f1d45f835ef1c80838"), "name" : "Minun", "description" : "chuveiros de faísca", "type" : "elétrico", "attack" : 40, "height" : 0.4 }
{ "_id" : ObjectId("56ae56f1d45f835ef1c80839"), "name" : "Zangoose", "description" : "cover do Kratos", "type" : "normal", "attack" : 115, "height" : 1.3 }
{ "_id" : ObjectId("56ae56f1d45f835ef1c8083a"), "name" : "Arcanine ", "description" : "mistura de cachorro e gato", "type" : "fogo", "attack" : 110, "height" : 1.9 }
{ "_id" : ObjectId("56ae56f1d45f835ef1c8083b"), "name" : "Staryu", "description" : "estrelinha", "type" : "água", "attack" : 45, "height" : 0.8 }
{ "_id" : ObjectId("56ae56f1d45f835ef1c8083c"), "name" : "Riolu", "description" : "cachorro fresco", "type" : "combate", "attack" : 70, "height" : 0.7 }
{ "_id" : ObjectId("56ae56f1d45f835ef1c8083d"), "name" : "Serperior", "description" : "cobra que se acha", "type" : "grama", "attack" : 75, "height" : 3.3 }
{ "_id" : ObjectId("56ae56f1d45f835ef1c8083e"), "name" : "Umbreon", "description" : "cachorro preto", "type" : "escuro", "attack" : 65, "height" : 1 }

```

# Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada `poke`
```
var query = {"name":"Zangoose"}
var poke = db.pokemons.findOne(query)
poke
{
        "_id" : ObjectId("56ae56f1d45f835ef1c80839"),
        "name" : "Zangoose",
        "description" : "cover do Kratos",
        "type" : "normal",
        "attack" : 115,
        "height" : 1.3
}

```

# Modifique sua `description` e salvê-o
```
var query = {"name":"Zangoose"}
var poke = db.pokemons.findOne(query)

poke.description = 'Pokemon do Kratos'
Pokemon do Kratos

db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
```
