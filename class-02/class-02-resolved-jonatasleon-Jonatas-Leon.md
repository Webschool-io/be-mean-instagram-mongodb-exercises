# MongoDB - Aula 02 - Exercício
Autor: Jonatas Leon

## Criar database chamada be-mean-pokemons
```
lucy(mongod-3.0.12) test> use be-mean-pokemons
switched to db be-mean-pokemons
```

## Listar databases
```
lucy(mongod-3.0.12) be-mean-pokemons> show dbs
Loc8r             → 0.078GB
be-mean           → 0.078GB
be-mean-instagram → 0.078GB
bears-express     → 0.078GB
local             → 0.078GB
test              → 0.078GB
```

## Listar coleções
```
lucy(mongod-3.0.12) be-mean-pokemons> show collections
```

## Inserir no minímo 5 pokemons usando o padrão mostrado na aula (name, description, attack, defense e height)
```
lucy(mongod-3.0.12) be-mean-pokemons> db.pokemons.insert([
...   {
...     "attack": 110,
...     "defense": 70,
...     "height": "18",
...     "name": "Dodrio",
...     "type": "flying",
...     "description": "Bichão zica de 3 cabeças feio pra casseta"
...   }, {
...     "attack": 52,
...     "defense": 48,
...     "height": "8",
...     "name": "Psyduck",
...     "type": "water",
...     "description": "Patão chapado"
...   }, {
...     "attack": 105,
...     "defense": 90,
...     "height": "4",
...     "name": "Krabby",
...     "type": "water",
...     "description": "Caranguejo boladão"
...   }, {
...     "attack": 110,
...     "defense": 90,
...     "height": "20",
...     "name": "Mewtwo",
...     "type": "psychic",
...     "description": "Vem monstro, vem monstro! Bichão criado em laboratório pra destruir todas essas árvores do Parque Ibirapuera"
...   }, {
...     "attack": 120,
...     "defense": 120,
...     "height": "32",
...     "name": "Arceus",
...     "type": "normal",
...     "description": "According to the legends of Sinnoh, this Pokémon emerged from an egg and shaped all there is in this world."
...   }, {
...     "attack": 150,
...     "defense": 50,
...     "height": "17",
...     "name": "Deoxys",
...     "type": "psychic",
...     "description": "The DNA of a space virus underwent a sudden mutation upon exposure to a laser beam and resulted in Deoxys. The crystalline organ on this Pokémon's chest appears to be its brain."
...   }
... ])
Inserted 1 record(s) in 88ms
BulkWriteResult({
  "writeErrors": [ ],
  "writeConcernErrors": [ ],
  "nInserted": 6,
  "nUpserted": 0,
  "nMatched": 0,
  "nModified": 0,
  "nRemoved": 0,
  "upserted": [ ]
})
```

## Listar os pokemons na collection
```
lucy(mongod-3.0.12) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("579d7fc3cf09c5720e50ef15"),
  "attack": 110,
  "defense": 70,
  "height": "18",
  "name": "Dodrio",
  "type": "flying",
  "description": "Bichão zica de 3 cabeças feio pra casseta"
}
{
  "_id": ObjectId("579d7fc3cf09c5720e50ef16"),
  "attack": 52,
  "defense": 48,
  "height": "8",
  "name": "Psyduck",
  "type": "water",
  "description": "Patão chapado"
}
{
  "_id": ObjectId("579d7fc3cf09c5720e50ef17"),
  "attack": 105,
  "defense": 90,
  "height": "4",
  "name": "Krabby",
  "type": "water",
  "description": "Caranguejo boladão"
}
{
  "_id": ObjectId("579d7fc3cf09c5720e50ef18"),
  "attack": 110,
  "defense": 90,
  "height": "20",
  "name": "Mewtwo",
  "type": "psychic",
  "description": "Vem monstro, vem monstro! Bichão criado em laboratório pra destruir todas essas árvores do Parque Ibirapuera"
}
{
  "_id": ObjectId("579d7fc3cf09c5720e50ef19"),
  "attack": 120,
  "defense": 120,
  "height": "32",
  "name": "Arceus",
  "type": "normal",
  "description": "According to the legends of Sinnoh, this Pokémon emerged from an egg and shaped all there is in this world."
}
{
  "_id": ObjectId("579d7fc3cf09c5720e50ef1a"),
  "attack": 150,
  "defense": 50,
  "height": "17",
  "name": "Deoxys",
  "type": "psychic",
  "description": "The DNA of a space virus underwent a sudden mutation upon exposure to a laser beam and resulted in Deoxys. The crystalline organ on this Pokémon's chest appears to be its brain."
}
Fetched 6 record(s) in 3ms
```

## Buscar pelo nome um pokemon a sua escolha e armazena-lo em uma váriavel chamada "poke"
```
lucy(mongod-3.0.12) be-mean-pokemons> var query = {name: "Deoxys"}
lucy(mongod-3.0.12) be-mean-pokemons> var poke = db.pokemons.findOne(query)
lucy(mongod-3.0.12) be-mean-pokemons> poke
{
  "_id": ObjectId("579d7fc3cf09c5720e50ef1a"),
  "attack": 150,
  "defense": 50,
  "height": "17",
  "name": "Deoxys",
  "type": "psychic",
  "description": "The DNA of a space virus underwent a sudden mutation upon exposure to a laser beam and resulted in Deoxys. The crystalline organ on this Pokémon's chest appears to be its brain."
}
```

## Modificar sua description e salvar
```
lucy(mongod-3.0.12) be-mean-pokemons> poke.description = "Pokemon pika, não Pikachu, mas pika das galaxia mesmo!"
Pokemon pika, não Pikachu, mas pika das galaxia mesmo!
lucy(mongod-3.0.12) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 9ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```
