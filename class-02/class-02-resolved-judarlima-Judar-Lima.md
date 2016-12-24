# MongoDb - Aula 02 - Exercício
autor: Judar Lima

## 1 - Crie uma database chamada be-mean-pokemons;

```
➜  ~ mongo be-mean-pokemons
MongoDB shell version: 3.2.6
connecting to: be-mean-pokemons
Mongo-Hacker 0.0.13

```

## 2 - Liste quais databases você possui nesse servidor;

```
z10n(MONGOD-3.2.6) be-mean-pokemons> show dbs
be-mean-instagram   → 0.005GB
be-mean-open-orders → 0.000GB
local               → 0.000GB

```
## 3 - Liste quais coleções você possui nessa database;

```
z10n(MONGOD-3.2.6) be-mean-pokemons> show collections
z10n(MONGOD-3.2.6) be-mean-pokemons>

```
## 4 - Insira pelo menos 5 pokemons A SUA ESCOLHA;

```
z10n(MONGOD-3.2.6) be-mean-pokemons> var butter = {'name': 'Butterfree', 'description': 'Borboletinha cabulosa', 'type': 'inseto', attack: 20, height: 0.3}
z10n(MONGOD-3.2.6) be-mean-pokemons> db.pokemons.save(butter)
Inserted 1 record(s) in 30ms
WriteResult({
  "nInserted": 1
})
z10n(MONGOD-3.2.6) be-mean-pokemons> var p = {'name': 'Arbok', 'description': 'Cobra naja gigante', 'type': 'poison', attack: 85, height: 11.6}
z10n(MONGOD-3.2.6) be-mean-pokemons> db.pokemons.save(p)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
z10n(MONGOD-3.2.6) be-mean-pokemons> var p = {'name': 'Sandshrew', 'description': 'Tatu bola mucho loko', 'type': 'terra', attack: 75, height: 2.0}
z10n(MONGOD-3.2.6) be-mean-pokemons> db.pokemons.save(p)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
z10n(MONGOD-3.2.6) be-mean-pokemons> var p = {'name': 'Jigglypuff', 'description': 'Melhor que a MC Mellody', 'type': 'fada', attack: 45, height: 1.8}
z10n(MONGOD-3.2.6) be-mean-pokemons> db.pokemons.save(p)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})
z10n(MONGOD-3.2.6) be-mean-pokemons> var p = {'name': 'Hypno', 'description': 'O Fabio Puentes versão pokemon', 'type': 'psíquico', attack: 73, height: 5.3}

z10n(MONGOD-3.2.6) be-mean-pokemons> db.pokemons.save(p)
Inserted 1 record(s) in 0ms
WriteResult({
  "nInserted": 1
})

```

## 5 - Liste os pokemons existentes na sua coleção;

```
z10n(MONGOD-3.2.6) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("5772ffcf54c202b7d67f797c"),
  "name": "Butterfree",
  "description": "Borboletinha cabulosa",
  "type": "inseto",
  "attack": 20,
  "height": 0.3
}
{
  "_id": ObjectId("577300ca54c202b7d67f797d"),
  "name": "Arbok",
  "description": "Cobra naja gigante",
  "type": "poison",
  "attack": 85,
  "height": 11.6
}
{
  "_id": ObjectId("5773010c54c202b7d67f797e"),
  "name": "Sandshrew",
  "description": "Tatu bola mucho loko",
  "type": "terra",
  "attack": 75,
  "height": 2
}
{
  "_id": ObjectId("5773015754c202b7d67f797f"),
  "name": "Jigglypuff",
  "description": "Melhor que a MC Mellody",
  "type": "fada",
  "attack": 45,
  "height": 1.8
}
{
  "_id": ObjectId("577301cf54c202b7d67f7980"),
  "name": "Hypno",
  "description": "O Fabio Puentes versão pokemon",
  "type": "psíquico",
  "attack": 73,
  "height": 5.3
}
Fetched 5 record(s) in 2ms

```

## 6 - Busque o pokemon da sua escolha, pelo nome, e armazene-o em uma variável chamada poke;

```

z10n(MONGOD-3.2.6) be-mean-pokemons> var query = {name: 'Hypno'}
z10n(MONGOD-3.2.6) be-mean-pokemons> query
{
  "name": "Hypno"
}
z10n(MONGOD-3.2.6) be-mean-pokemons> var poke = db.pokemons.findOne(query)
z10n(MONGOD-3.2.6) be-mean-pokemons> poke
{
  "_id": ObjectId("577301cf54c202b7d67f7980"),
  "name": "Hypno",
  "description": "O Fabio Puentes versão pokemon",
  "type": "psíquico",
  "attack": 73,
  "height": 5.3
}

```

## 7 - Modifique sua description e salve-o;

```
z10n(MONGOD-3.2.6) be-mean-pokemons> poke.description = "Se o Hypno fosse gente ele seria o Fábio Puentes"
Se o Hypno fosse gente ele seria o Fábio Puentes
z10n(MONGOD-3.2.6) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
z10n(MONGOD-3.2.6) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("5772ffcf54c202b7d67f797c"),
  "name": "Butterfree",
  "description": "Borboletinha cabulosa",
  "type": "inseto",
  "attack": 20,
  "height": 0.3
}
{
  "_id": ObjectId("577300ca54c202b7d67f797d"),
  "name": "Arbok",
  "description": "Cobra naja gigante",
  "type": "poison",
  "attack": 85,
  "height": 11.6
}
{
  "_id": ObjectId("5773010c54c202b7d67f797e"),
  "name": "Sandshrew",
  "description": "Tatu bola mucho loko",
  "type": "terra",
  "attack": 75,
  "height": 2
}
{
  "_id": ObjectId("5773015754c202b7d67f797f"),
  "name": "Jigglypuff",
  "description": "Melhor que a MC Mellody",
  "type": "fada",
  "attack": 45,
  "height": 1.8
}
{
  "_id": ObjectId("577301cf54c202b7d67f7980"),
  "name": "Hypno",
  "description": "Se o Hypno fosse gente ele seria o Fábio Puentes",
  "type": "psíquico",
  "attack": 73,
  "height": 5.3
}
Fetched 5 record(s) in 2ms
```
