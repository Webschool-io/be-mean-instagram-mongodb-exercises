# MongoDB - Aula 02 - Exercício
autor: Natália Nascimento de Ávila

# Crie uma database chamada be-mean-pokemons

```
use be-mean-pokemons

```

# Liste quais databases você possui nesse servidor

```
show dbs
be-mean-instagram        0.078GB
be-mean-pokemons         0.078GB
local                    0.078GB

```

# Liste quais coleções você possui nessa database

```
show collections
pokemons
system.indexes

```

# Insira pelo menos 5 pokemons a sua escolha utilizando o mesmo padrão de campos utilizado: name, description, attack, defense e height

```
var pokemon = {'name':'Wartortle','description':'Turtle Pokemon','type': 'água', attack: 63, defense: 80, height: 0.9 }
db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })

var pokemon = {'name':'Beedrill','description':'Esse é venenoso','type': 'buge poison', attack: 150, defense:40, height: 1.4 }
db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })

var pokemon = {'name':'Venusaur','description':'esse é calminho','type': 'grass e poison', attack: 82, defense:83, height: 2.0 }
db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })

var pokemon = {'name':'Jigglypuff','description':'canta para deixar os inimigos lentos','type': 'normal e fairy', attack: 45, defense:20, height: 0.5 }
db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })

var pokemon = {'name':'Butterfree','description':'transporta mel e flores em longa distancia','type': 'bug e flying', attack: 45, defense:50, height: 1.0 }
db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })

```

# Liste os pokemons existentes na sua coleção

```
db.pokemons.find()

{ "_id" : ObjectId("56eac32253b8908cf365b069"), "name" : "Wartortle", "description" : "Turtle Pokemon", "type" : "água", "attack" : 63, "defense" : 80, "height" : 0.9 }

{ "_id" : ObjectId("56eac32253b8908cf365b06a"), "name" : "Beedrill", "description" : "Esse é venenoso", "type" : "buge poison", "attack" : 150, "defense" : 40,"height" : 1.4 }

{ "_id" : ObjectId("56eac32253b8908cf365b06b"), "name" : "Venusaur", "description" : "esse é calminho", "type" : "grass e poison", "attack" : 82, "defense" : 83, "height" : 2 }

{ "_id" : ObjectId("56eac32253b8908cf365b06c"), "name" : "Jigglypuff", "description" : "canta para deixar os inimigos lentos", "type" : "normal e fairy", "attack" : 45, "defense" : 20, "height" : 0.5 }

{ "_id" : ObjectId("56eac32253b8908cf365b06d"), "name" : "Butterfree", "description" : "transporta mel e flores em longa distancia", "type" : "bug e flying", "attack" : 45, "defense" : 50, "height" : 1 }

```

# Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada poke

```
var poke = {name:"Wartortle"}

db.pokemons.findOne(poke)

{ "_id" : ObjectId("56eac32253b8908cf365b069"), "name" : "Wartortle", "description" : "Turtle Pokemon", "type" : "água", "attack" : 63, "defense" : 80, "height" : 0.9 }


```

# Modifique sua description e salvê-o

```
poke.description = "pokemon tartaruga"
pokemon tartaruga

poke
{ "name" : "Wartortle", "description" : "pokemon tartaruga" }

db.pokemons.save(poke)
WriteResult({ "nInserted" : 1 })

db.pokemons.find(poke)
{ "_id" : ObjectId("56eb244453b8908cf365b06e"), "name" : "Wartortle", "description" :"pokemon tartaruga" }

```