# MongoDB - Aula 02 - Exercício
autor: Laércio Bernardo

## Crie uma database chamada be-mean-prokemons

```
    use be-mean-pokemons
switched to db be-mean-pokemons

```

## Liste quais databases você possui nesse servidor

```
    show databases
be-mean           → 0.078GB
be-mean-instagram → 0.078GB
local             → 0.078GB
local-40          → 0.203GB
m101              → 0.078GB
test              → 0.078GB
video             → 0.078GB

```

## Liste quais coleções você possui nessa database;

```
    show collections

```

## Insira pelo menos 5 pokemons A SUA ESCOLHA utilizando o mesmo padrão de campos utilizado: name, description, attack, defense e height

```
   var pokemons = [
   {
    "name": "Eevee",
    "description": "Eevee has an unstable genetic makeup that suddenly mutates due to the environment in which it lives. Radiation from various stones causes this Pokémon to evolve.",
    "attack": 55,
    "defense": 50,
    "height": 0.3
  },
  {
    "name": "Charizard",
    "description": "Charizard flies around the sky in search of powerful opponents. It breathes fire of such great heat that it melts anything. However, it never turns its fiery breath on any opponent weaker than itself.",
    "attack": 84,
    "defense": 78,
    "height": 1.7
  },
  {
    "name": "Blastoise",
    "description": "Blastoise has water spouts that protrude from its shell. The water spouts are very accurate. They can shoot bullets of water with enough accuracy to strike empty cans from a distance of over 160 feet.",
    "attack": 83,
    "defense": 100,
    "height": 1.6
  },
  {
    "name": "Venusaur",
    "description": "There is a large flower on Venusaur's back. The flower is said to take on vivid colors if it gets plenty of nutrition and sunlight. The flower's aroma soothes the emotions of people.",
    "attack": 82,
    "defense": 83,
    "height": 6.7
  },
  {
    "name": "Mewtwo",
    "description": "Mewtwo is a Pokémon that was created by genetic manipulation. However, even though the scientific power of humans created this Pokémon's body, they failed to endow Mewtwo with a compassionate heart.",
    "attack": 110,
    "defense": 90,
    "height": 2
  }
];

db.pokemons.save(pokemons)

Inserted 1 record(s) in 75ms

BulkWriteResult({
  "writeErrors": [ ],
  "writeConcernErrors": [ ],
  "nInserted": 5,
  "nUpserted": 0,
  "nMatched": 0,
  "nModified": 0,
  "nRemoved": 0,
  "upserted": [ ]
})
 
```
## liste os pokemons existentes na sua coleção

```
db.pokemons.find()

{
  "_id": ObjectId("56e1ae3ee776552d53a1c2d5"),
  "name": "Eevee",
  "description": "Eevee has an unstable genetic makeup that suddenly mutates due to the environment in which it lives. Radiation from various stones causes this Pokémon to evolve.",
  "attack": 55,
  "defense": 50,
  "height": 0.3
}
{
  "_id": ObjectId("56e1ae3ee776552d53a1c2d6"),
  "name": "Charizard",
  "description": "Charizard flies around the sky in search of powerful opponents. It breathes fire of such great heat that it melts anything. However, it never turns its fiery breath on any opponent weaker than itself.",
  "attack": 84,
  "defense": 78,
  "height": 1.7
}
{
  "_id": ObjectId("56e1ae3ee776552d53a1c2d7"),
  "name": "Blastoise",
  "description": "Blastoise has water spouts that protrude from its shell. The water spouts are very accurate. They can shoot bullets of water with enough accuracy to strike empty cans from a distance of over 160 feet.",
  "attack": 83,
  "defense": 100,
  "height": 1.6
}
{
  "_id": ObjectId("56e1ae3ee776552d53a1c2d8"),
  "name": "Venusaur",
  "description": "There is a large flower on Venusaur's back. The flower is said to take on vivid colors if it gets plenty of nutrition and sunlight. The flower's aroma soothes the emotions of people.",
  "attack": 82,
  "defense": 83,
  "height": 6.7
}
{
  "_id": ObjectId("56e1ae3ee776552d53a1c2d9"),
  "name": "Mewtwo",
  "description": "Mewtwo is a Pokémon that was created by genetic manipulation. However, even though the scientific power of humans created this Pokémon's body, they failed to endow Mewtwo with a compassionate heart.",
  "attack": 110,
  "defense": 90,
  "height": 2
}

Fetched 5 record(s) in 6ms

```

## Busque o pokemon a sua escolha, pelo nome, e armazene-o em uma variável chamada `poke`;

```
var query = {name:"Charizard"}

bernardo-pc(mongod-3.0.8) be-mean-pokemons> var poke = db.pokemons.findOne(query)

bernardo-pc(mongod-3.0.8) be-mean-pokemons> poke

{
  "_id": ObjectId("56e1ae3ee776552d53a1c2d6"),
  "name": "Charizard",
  "description": "Charizard flies around the sky in search of powerful opponents. It breathes fire of such great heat that it melts anything. However, it never turns its fiery breath on any opponent weaker than itself.",
  "attack": 84,
  "defense": 78,
  "height": 1.7
}

```
## Modifiique sua `description` e salve-o

```
poke.description = "Ah como eu queria ter um la em casa!"
Ah como eu queria ter um la em casa!

bernardo-pc(mongod-3.0.8) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 4ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

bernardo-pc(mongod-3.0.8) be-mean-pokemons> query
{
  "name": "Charizard"
}

bernardo-pc(mongod-3.0.8) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56e1ae3ee776552d53a1c2d6"),
  "name": "Charizard",
  "description": "Ah como eu queria ter um la em casa!",
  "attack": 84,
  "defense": 78,
  "height": 1.7
}

Fetched 1 record(s) in 2ms

```