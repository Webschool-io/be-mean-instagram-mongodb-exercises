# MongoDB - Aula 02 - Exercício
autor: Renato Galvão

## Criando banco de pokemons

```
Renatos-Mac-Pro(mongod-3.2.0) test> use be-mean-pokemons
switched to db be-mean-pokemons

```

## Mostrando bancos

```
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> show dbs
be-mean-instagram → 0.004GB
local             → 0.000GB

```

## Mostrando coleções

```
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> show collections

```

## Adicionando pokemons

```

Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> var pokemon = {'name':'mewtwo','description':'bichão fodão','type':'psychic','attack':110,height:20}
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> pokemon
{
  "name": "mewtwo",
  "description": "bichão fodão",
  "type": "psychic",
  "attack": 110,
  "height": 20
}
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 152ms
WriteResult({
  "nInserted": 1
})
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> var pokemon = {'name':'dragonite','description':'dragão que só voa a noite','type':'dragon','attack':134,height:22}
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> var pokemon = {'name':'dragonite','description':'chocante','type':'electric','attack':13,height:22}
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> var pokemon = {'name':'dragonite','description':'chocante','type':'electric','attack':83,height:11}
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> db.pokemons.save(pokemon)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> var pokemon = {'name':'magmar','description':'queeeeeeente','type':'fire','attack':95,height:13}
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> db.pokemons.save(pokemon)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> var pokemon = {'name':'staryu','description':'estrelinha','type':'water','attack':45,height:8}
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> db.pokemons.save(pokemon)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})

```

### Listando pokemons da minha collection

```
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("56c1ce9965d70c166a207adf"),
  "name": "mewtwo",
  "description": "bichão fodão",
  "type": "psychic",
  "attack": 110,
  "height": 20
}
{
  "_id": ObjectId("56c1cf1965d70c166a207ae0"),
  "name": "dragonite",
  "description": "dragão que só voa a noite",
  "type": "dragon",
  "attack": 134,
  "height": 22
}
{
  "_id": ObjectId("56c1d02f65d70c166a207ae1"),
  "name": "dragonite",
  "description": "chocante",
  "type": "electric",
  "attack": 83,
  "height": 11
}
{
  "_id": ObjectId("56c1d05b65d70c166a207ae2"),
  "name": "magmar",
  "description": "queeeeeeente",
  "type": "fire",
  "attack": 95,
  "height": 13
}
{
  "_id": ObjectId("56c1d09165d70c166a207ae3"),
  "name": "staryu",
  "description": "estrelinha",
  "type": "water",
  "attack": 45,
  "height": 8
}
Fetched 5 record(s) in 2ms

```

### Procurando pelo mewtwo utilizando o nome

```
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> db.pokemons.find({name:'mewtwo'})
{
  "_id": ObjectId("56c1ce9965d70c166a207adf"),
  "name": "mewtwo",
  "description": "bichão fodão",
  "type": "psychic",
  "attack": 110,
  "height": 20
}
Fetched 1 record(s) in 6ms

```

### Mudando description do mewtwo
```
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> var poke = db.pokemons.findOne({name:'mewtwo'})
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> poke
{
  "_id": ObjectId("56c1ce9965d70c166a207adf"),
  "name": "mewtwo",
  "description": "bichão fodão",
  "type": "psychic",
  "attack": 110,
  "height": 20
}
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> poke.description = 'bichão fodão psicótico'
bichão fodão psicótico
Renatos-Mac-Pro(mongod-3.2.0) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

```
