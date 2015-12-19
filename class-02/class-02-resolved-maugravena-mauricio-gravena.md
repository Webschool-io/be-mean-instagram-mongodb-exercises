# MongoDB - Aula 02 - Exercício
autor: Mauricio Gravena de Oliveira

## Criando database be-mean-pokemons

```
mau-desktop(mongod-3.0.7) be-mean-instagram> use be-mean-pokemons
switched to db be-mean-pokemons
mau-desktop(mongod-3.0.7) be-mean-pokemons>
```

## Listando databases

```
mau-desktop(mongod-3.0.7) be-mean-pokemons> show dbs
local             → 0.078GB
be-mean           → 0.078GB
be-mean-instagram → 0.078GB
```

## Listando coleções

```
mau-desktop(mongod-3.0.7) be-mean-pokemons> db.teste.insert({'nome': 'Mauricio', 'idade': '24'})
Inserted 1 record(s) in 817ms
WriteResult({
  "nInserted": 1
})
mau-desktop(mongod-3.0.7) be-mean-pokemons> show collections
system.indexes → 0.000MB / 0.008MB
teste          → 0.000MB / 0.008MB
```

## Listando pokemons

```
mau-desktop(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("564b44333af557c773f61d0c"),
  "name": "Chimchar",
  "description": "Macaco de fogo",
  "type": "fogo",
  "attack": 45,
  "heigth": 0.5,
  "defense": 47
}
{
  "_id": ObjectId("564b44e73af557c773f61d0d"),
  "name": "Shinx",
  "description": "Ele brilha quando está em dificuldades.",
  "type": "electric",
  "attack": 40,
  "heigth": 0.5,
  "defense": 41
}
{
  "_id": ObjectId("564b45a23af557c773f61d0e"),
  "name": "Eevee",
  "description": "Eevee tem uma composição genética instável que de repente se transforma devido ao ambiente em que vive.",
  "type": "normal",
  "attack": 33,
  "heigth": 0.3,
  "defense": 39
}
{
  "_id": ObjectId("564b46293af557c773f61d0f"),
  "name": "Aipom",
  "description": "Utiliza sua calda como principal arma.",
  "type": "normal",
  "attack": 39,
  "heigth": 0.8,
  "defense": 38
}
{
  "_id": ObjectId("564b46fb3af557c773f61d10"),
  "name": "Cubone",
  "description": "Vendo a semelhança de sua mãe na lua cheia, ele chora.",
  "type": "ground",
  "attack": 43,
  "heigth": 0.4,
  "defense": 47
}
{
  "_id": ObjectId("564b47863af557c773f61d11"),
  "name": "Drowzee",
  "description": "Comedor de sonhos.",
  "type": "psychic",
  "attack": 46,
  "heigth": 1,
  "defense": 50
}
{
  "_id": ObjectId("564b47eb3af557c773f61d12"),
  "name": "Gastly",
  "description": "Gastly é em grande parte é composto de matéria gasosa.",
  "type": "ghost, poison",
  "attack": 50,
  "heigth": 1.3,
  "defense": 51
}
{
  "_id": ObjectId("564b48473af557c773f61d13"),
  "name": "Charmander",
  "description": "A chama que arde na ponta de sua cauda é uma indicação de suas emoções.",
  "type": "fire",
  "attack": 46,
  "heigth": 0.6,
  "defense": 44
}
{
  "_id": ObjectId("564b48ae3af557c773f61d14"),
  "name": "Meowth",
  "description": "este Pokémon ama moedas brilhantes que brilham com a luz.",
  "type": "normal",
  "attack": 43,
  "heigth": 0.4,
  "defense": 41
}
{
  "_id": ObjectId("564b497c3af557c773f61d15"),
  "name": "Mankey",
  "description": "é impossível para qualquer um de fugir a sua ira.",
  "type": "fighting",
  "attack": 48,
  "heigth": 0.5,
  "defense": 45
}
```

## Buscando pokemon pelo nome e armagenando na variável "poke"

```
mau-desktop(mongod-3.0.7) be-mean-pokemons> var query = {name: 'Gastly'}
mau-desktop(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.find(query)
mau-desktop(mongod-3.0.7) be-mean-pokemons> poke
{
  "_id": ObjectId("564b47eb3af557c773f61d12"),
  "name": "Gastly",
  "description": "Gastly é em grande parte é composto de matéria gasosa.",
  "type": "ghost, poison",
  "attack": 50,
  "heigth": 1.3,
  "defense": 51
}
```

## Modificando sua "description" e salvando

```
mau-desktop(mongod-3.0.7) be-mean-pokemons> poke.description
Gastly é em grande parte é composto de matéria gasosa.
mau-desktop(mongod-3.0.7) be-mean-pokemons> poke.description = "Gastly é em grande parte composto de matéria gasosa."
Gastly é em grande parte composto de matéria gasosa.
mau-desktop(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 18ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 0
})
```
