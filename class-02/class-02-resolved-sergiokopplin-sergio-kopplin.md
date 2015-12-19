MongoDB - Aula 02 - Exercício
autor: Sérgio Kopplin - sergiokopplin

## Usando outro db (passo 1)

```
Sergios-MacBook-Pro(mongod-3.0.7) be-mean> use be-mean-pokemons
switched to db be-mean-pokemons
```

## Listagem das databases (passo 2)

```
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> show dbs
be-mean  0.078GB
```

## Listagem das coleções (passo 3)

```
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> show collections
[empty]
```

## Cadastro dos pokemons (passo 4)

```
var pok1 = {
    "name": "Venusaur",
    "description": "There is a large flower on Venusaur's back",
    "type": "Seed",
    "attack": "40",
    "height": "2.0"
};

var pok2 = {
    "name": "Charizard",
    "description": "Charizard flies around the sky in search of powerful opponents",
    "type": "Flame",
    "attack": "40",
    "height": "1.7"
};

var pok3 = {
    "name": "Blastoise",
    "description": "Blastoise has water spouts that protrude from its shell",
    "type": "Shellfish",
    "attack": "40",
    "height": "1.6"
};

var pok4 = {
    "name": "Nidoking",
    "description": "Nidoking's thick tail packs enormously destructive power",
    "type": "Drill",
    "attack": "50",
    "height": "1.4"
};

var pok5 = {
    "name": "Nidoqueen",
    "description": "Nidoqueen's body is encased in extremely hard scales",
    "type": "Drill",
    "attack": "50",
    "height": "1.3"
};
```

```
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(pok1)
Inserted 1 record(s) in 192ms
WriteResult({
  "nInserted": 1
})

Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(pok2)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})

Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(pok3)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})

Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(pok4)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})

Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(pok5)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
```

## Lista dos pokemons (passo 5)

```
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("564756bd17c5d4b60e935cbb"),
  "name": "Venusaur",
  "description": "There is a large flower on Venusaur's back",
  "type": "Seed",
  "attack": "40",
  "height": "2.0"
}
{
  "_id": ObjectId("5647574f17c5d4b60e935cbc"),
  "name": "Charizard",
  "description": "Charizard flies around the sky in search of powerful opponents",
  "type": "Flame",
  "attack": "40",
  "height": "1.7"
}
{
  "_id": ObjectId("5647575817c5d4b60e935cbd"),
  "name": "Blastoise",
  "description": "Blastoise has water spouts that protrude from its shell",
  "type": "Shellfish",
  "attack": "40",
  "height": "1.6"
}
{
  "_id": ObjectId("5647575e17c5d4b60e935cbe"),
  "name": "Nidoking",
  "description": "Nidoking's thick tail packs enormously destructive power",
  "type": "Drill",
  "attack": "50",
  "height": "1.4"
}
{
  "_id": ObjectId("5647576a17c5d4b60e935cbf"),
  "name": "Nidoqueen",
  "description": "Nidoqueen's body is encased in extremely hard scales",
  "type": "Drill",
  "attack": "50",
  "height": "1.3"
}
Fetched 5 record(s) in 5ms
```

## Pikachu (passo 6)
```
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> var query = { "name": "Blastoise" };
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(query);
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> poke
{
  "_id": ObjectId("5647575817c5d4b60e935cbd"),
  "name": "Blastoise",
  "description": "Blastoise has water spouts that protrude from its shell",
  "type": "Shellfish",
  "attack": "40",
  "height": "1.6"
}
```

## Atualização do Pikachu (passo 6)
```
Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> poke.description = "Blastoise has water spouts that protrude from its shell. The water spouts are very accurate. They can shoot bullets of water with enough accuracy to strike empty cans from a distance of over 160 feet."

Sergios-MacBook-Pro(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
```
