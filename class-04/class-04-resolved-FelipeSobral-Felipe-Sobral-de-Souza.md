# MongoDB - Aula 02 - Exercício
Autor: Felipe Sobral

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Blastoise, Rattata, Heatmor e Boldore.
```
felipe-pc(mongod-3.0.7) be-mean-pokemon> var query = { $or: [ {name: /blastoise/i}, {name: /rattata/i}, {name: /heatmor/i}, {name: /boldore/i} ]};
felipe-pc(mongod-3.0.7) be-mean-pokemon> var mod = { $pushAll: { moves: ['esquiva','investida']}};
felipe-pc(mongod-3.0.7) be-mean-pokemon> var options= {multi:true};
felipe-pc(mongod-3.0.7) be-mean-pokemon> db.pokemons.update(query,mod,options);
Updated 4 existing record(s) in 75ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})


```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```
felipe-pc(mongod-3.0.7) be-mean-pokemon> var query = {};
felipe-pc(mongod-3.0.7) be-mean-pokemon> var mod ={$push:{moves:'desvio'}};
felipe-pc(mongod-3.0.7) be-mean-pokemon> var options= {multi:true};
felipe-pc(mongod-3.0.7) be-mean-pokemon> db.pokemons.update(query,mod,options);
Updated 5 existing record(s) in 1ms
WriteResult({
  "nMatched": 5,
  "nUpserted": 0,
  "nModified": 5
})


```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
felipe-pc(mongod-3.0.7) be-mean-pokemon> var query = { name: /AindaNaoExisteMon/i };
felipe-pc(mongod-3.0.7) be-mean-pokemon> var mod = { $setOnInsert: {name: "AindaNaoExisteMon", attack: null, height: null, defense: null, moves: [], description: "Sem maiores informações"}};
felipe-pc(mongod-3.0.7) be-mean-pokemon> var options = {upsert: true};
felipe-pc(mongod-3.0.7) be-mean-pokemon> db.pokemons.update(query,mod,options);
Updated 1 new record(s) in 0ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564d984fca1501860248bd95")
})

```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
felipe-pc(mongod-3.0.7) be-mean-pokemon> var query = { moves: { $in: ['investida', 'esquiva'] }};
felipe-pc(mongod-3.0.7) be-mean-pokemon> db.pokemons.find(query)
{
  "_id": ObjectId("56433350342f68f460c236b5"),
  "name": "Blastoise",
  "description": "Blastoise has water spouts that protrude from its shell. The water spouts are very accurate. They can shoot bullets of water with enough accuracy to strike empty cans from a distance of over 160 feet.",
  "type": "Water",
  "attack": 83,
  "defense": 100,
  "height": 16,
  "moves": [
    "esquiva",
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56433350342f68f460c236b6"),
  "name": "Rattata",
  "description": "Rattata is cautious in the extreme. Even while it is asleep, it constantly listens by moving its ears around. It is not picky about where it lives—it will make its nest anywhere.",
  "type": "Normal",
  "attack": 56,
  "defense": 35,
  "height": 3,
  "moves": [
    "esquiva",
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56433350342f68f460c236b8"),
  "name": "Boldore",
  "description": "Pokemon Boladão",
  "type": "Rock",
  "attack": 105,
  "defense": 105,
  "height": 9,
  "moves": [
    "esquiva",
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56433350342f68f460c236b7"),
  "name": "Heatmor",
  "description": "Using their very hot, flame-covered tongues, they burn through Durants steel bodies and consume their insides.",
  "type": "Fire",
  "attack": 97,
  "defense": 66,
  "height": 14,
  "moves": [
    "esquiva",
    "investida",
    "desvio"
  ]
}
Fetched 4 record(s) in 33ms


```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```
felipe-pc(mongod-3.0.7) be-mean-pokemon> var query = { moves: { $in: ['esquiva'] }};
felipe-pc(mongod-3.0.7) be-mean-pokemon> db.pokemons.find(query)
{
  "_id": ObjectId("56433350342f68f460c236b5"),
  "name": "Blastoise",
  "description": "Blastoise has water spouts that protrude from its shell. The water spouts are very accurate. They can shoot bullets of water with enough accuracy to strike empty cans from a distance of over 160 feet.",
  "type": "Water",
  "attack": 83,
  "defense": 100,
  "height": 16,
  "moves": [
    "esquiva",
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56433350342f68f460c236b6"),
  "name": "Rattata",
  "description": "Rattata is cautious in the extreme. Even while it is asleep, it constantly listens by moving its ears around. It is not picky about where it lives—it will make its nest anywhere.",
  "type": "Normal",
  "attack": 56,
  "defense": 35,
  "height": 3,
  "moves": [
    "esquiva",
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56433350342f68f460c236b8"),
  "name": "Boldore",
  "description": "Pokemon Boladão",
  "type": "Rock",
  "attack": 105,
  "defense": 105,
  "height": 9,
  "moves": [
    "esquiva",
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56433350342f68f460c236b7"),
  "name": "Heatmor",
  "description": "Using their very hot, flame-covered tongues, they burn through Durants steel bodies and consume their insides.",
  "type": "Fire",
  "attack": 97,
  "defense": 66,
  "height": 14,
  "moves": [
    "esquiva",
    "investida",
    "desvio"
  ]
}
Fetched 4 record(s) in 1ms


```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```
felipe-pc(mongod-3.0.7) be-mean-pokemon> var query = {type:{$ne:'eletric'}}
felipe-pc(mongod-3.0.7) be-mean-pokemon> db.pokemons.find()
{
  "_id": ObjectId("56433350342f68f460c236b4"),
  "name": "Ivysaur",
  "description": "There is a bud on this Pokémons back. To support its weight, Ivysaurs legs and trunk grow thick and strong. If it starts spending more time lying in the sunlight, its a sign that the bud will bloom into a large flower soon.",
  "type": "Poison",
  "attack": 62,
  "defense": 63,
  "height": 10,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56433350342f68f460c236b5"),
  "name": "Blastoise",
  "description": "Blastoise has water spouts that protrude from its shell. The water spouts are very accurate. They can shoot bullets of water with enough accuracy to strike empty cans from a distance of over 160 feet.",
  "type": "Water",
  "attack": 83,
  "defense": 100,
  "height": 16,
  "moves": [
    "esquiva",
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56433350342f68f460c236b6"),
  "name": "Rattata",
  "description": "Rattata is cautious in the extreme. Even while it is asleep, it constantly listens by moving its ears around. It is not picky about where it lives—it will make its nest anywhere.",
  "type": "Normal",
  "attack": 56,
  "defense": 35,
  "height": 3,
  "moves": [
    "esquiva",
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56433350342f68f460c236b8"),
  "name": "Boldore",
  "description": "Pokemon Boladão",
  "type": "Rock",
  "attack": 105,
  "defense": 105,
  "height": 9,
  "moves": [
    "esquiva",
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56433350342f68f460c236b7"),
  "name": "Heatmor",
  "description": "Using their very hot, flame-covered tongues, they burn through Durants steel bodies and consume their insides.",
  "type": "Fire",
  "attack": 97,
  "defense": 66,
  "height": 14,
  "moves": [
    "esquiva",
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564d984fca1501860248bd95"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "height": null,
  "defense": null,
  "moves": [ ],
  "description": "Sem maiores informações"
}

```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```
felipe-pc(mongod-3.0.7) be-mean-pokemon> var query = {$and:[{moves:{$in:['investida']},defense:{$not:{$lte:49}}}]}
felipe-pc(mongod-3.0.7) be-mean-pokemdb.pokemons.find(query)
{
  "_id": ObjectId("56433350342f68f460c236b5"),
  "name": "Blastoise",
  "description": "Blastoise has water spouts that protrude from its shell. The water spouts are very accurate. They can shoot bullets of water with enough accuracy to strike empty cans from a distance of over 160 feet.",
  "type": "Water",
  "attack": 83,
  "defense": 100,
  "height": 16,
  "moves": [
    "esquiva",
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56433350342f68f460c236b8"),
  "name": "Boldore",
  "description": "Pokemon Boladão",
  "type": "Rock",
  "attack": 105,
  "defense": 105,
  "height": 9,
  "moves": [
    "esquiva",
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56433350342f68f460c236b7"),
  "name": "Heatmor",
  "description": "Using their very hot, flame-covered tongues, they burn through Durants steel bodies and consume their insides.",
  "type": "Fire",
  "attack": 97,
  "defense": 66,
  "height": 14,
  "moves": [
    "esquiva",
    "investida",
    "desvio"
  ]
}
Fetched 3 record(s) in 241ms


```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
felipe-pc(mongod-3.0.7) be-mean-pokemon> var query = {$and:[{type:'water'},{attack:{$lt:50}}]}
felipe-pc(mongod-3.0.7) be-mean-pokemon> db.pokemons.remove(query)
Removed 0 record(s) in 35ms
WriteResult({
  "nRemoved": 0
})


```
