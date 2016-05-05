# MongoDB - Aula 04 - Exercício
autor: Gustavo Gomes da Fé 

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
var query = {$or: [{name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbassaur/i}, {name: /charmander/i}]};
var mod = {$pushAll: {moves: ['investida','fire']}};
var options = {multi: true};
db.pokemons.update(query, mod, options);

Gustavos-Air(mongod-3.2.0) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 3 existing record(s) in 3ms
WriteResult({
  "nMatched": 3,
  "nUpserted": 0,
  "nModified": 3
})

```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

```
var query = {};
var mod = {$push:{moves: 'desvio'}};
var options = {multi: true};
db.pokemons.update(query, mod, options);

Gustavos-Air(mongod-3.2.0) be-mean-pokemons> db.pokemons.update(query, mod, options);
Updated 9 existing record(s) in 2ms
WriteResult({
  "nMatched": 9,
  "nUpserted": 0,
  "nModified": 9
})

```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

```
var query = {name: /AindaNaoExisteMon/i};
var mod = {$setOnInsert: {name: 'AindaNaoExisteMon', attack: null, height: null, defense: null, type: null, moves: []}};
var options = {upsert: true};
Gustavos-Air(mongod-3.2.0) be-mean-pokemons> db.pokemons.update(query, mod, options);
Updated 1 new record(s) in 1ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("5694521910a06f5c62e1e759")
})

```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

```
var query = {moves: {$in: ['investida', 'desvio']}};

Gustavos-Air(mongod-3.2.0) be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("564db3c7ceae3cae710a86d3"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, its evidence that this Pokémon mistook the intensity of its charge.",
  "attack": 90,
  "defense": 90,
  "height": 0.4,
  "moves": [
    "bomb",
    "fire",
    "desvio"
  ]
}
{
  "_id": ObjectId("564db3c7ceae3cae710a86d4"),
  "name": "Squirtle",
  "description": "Squirtles shell is not merely used for protection. The shells rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
  "attack": 90,
  "defense": 90,
  "height": 0.5,
  "moves": [
    "bomb",
    "fire",
    "desvio"
  ]
}
{
  "_id": ObjectId("564db3c7ceae3cae710a86d6"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
  "attack": 95,
  "defense": 90,
  "height": 0.6,
  "moves": [
    "bomb",
    "fire",
    "desvio"
  ]
}
Fetched 3 record(s) in 4ms

```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

```
var query = {moves: {$in: ['bomb', 'fire']}};
Gustavos-Air(mongod-3.2.0) be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("564db3c7ceae3cae710a86d3"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, its evidence that this Pokémon mistook the intensity of its charge.",
  "attack": 90,
  "defense": 90,
  "height": 0.4,
  "moves": [
    "bomb",
    "fire",
    "desvio"
  ]
}
{
  "_id": ObjectId("564db3c7ceae3cae710a86d4"),
  "name": "Squirtle",
  "description": "Squirtles shell is not merely used for protection. The shells rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
  "attack": 90,
  "defense": 90,
  "height": 0.5,
  "moves": [
    "bomb",
    "fire",
    "desvio"
  ]
}
{
  "_id": ObjectId("564db3c7ceae3cae710a86d6"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
  "attack": 95,
  "defense": 90,
  "height": 0.6,
  "moves": [
    "bomb",
    "fire",
    "desvio"
  ]
}
Fetched 3 record(s) in 3ms

```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

```
var query = {type: {$ne: 'elétrico'}};

Gustavos-Air(mongod-3.2.0) be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("56447e617fe9cee4a5bc8adc"),
  "name": "Blastoise",
  "description": "Blastoise has water spouts that protrude from its shell. The water spouts are very accurate. They can shoot bullets of water with enough accuracy to strike empty cans from a distance of over 160 feet.",
  "attack": 60,
  "defense": 80,
  "height": 1.6,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56447e617fe9cee4a5bc8add"),
  "name": "Charizard",
  "description": "Charizard flies around the sky in search of powerful opponents. It breathes fire of such great heat that it melts anything. However, it never turns its fiery breath on any opponent weaker than itself.",
  "attack": 70,
  "defense": 50,
  "height": 1.7,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56447e617fe9cee4a5bc8ade"),
  "name": "Venusaur",
  "description": "There is a large flower on Venusaur back. The flower is said to take on vivid colors if it gets plenty of nutrition and sunlight. The flowers aroma soothes the emotions of people.",
  "attack": 50,
  "defense": 80,
  "height": 2,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56447e617fe9cee4a5bc8adf"),
  "name": "Pidgeot",
  "description": "This Pokémon has a dazzling plumage of beautifully glossy feathers. Many Trainers are captivated by the striking beauty of the feathers on its head, compelling them to choose Pidgeot as their Pokémon.",
  "attack": 75,
  "defense": 50,
  "height": 1.5,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56447e617fe9cee4a5bc8ae0"),
  "name": "Golduck",
  "description": "Description updated",
  "attack": 90,
  "defense": 70,
  "height": 1.7,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564db3c7ceae3cae710a86d3"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, its evidence that this Pokémon mistook the intensity of its charge.",
  "attack": 90,
  "defense": 90,
  "height": 0.4,
  "moves": [
    "bomb",
    "fire",
    "desvio"
  ]
}
{
  "_id": ObjectId("564db3c7ceae3cae710a86d4"),
  "name": "Squirtle",
  "description": "Squirtles shell is not merely used for protection. The shells rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
  "attack": 90,
  "defense": 90,
  "height": 0.5,
  "moves": [
    "bomb",
    "fire",
    "desvio"
  ]
}
{
  "_id": ObjectId("564db3c7ceae3cae710a86d5"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the suns rays, the seed grows progressively larger.",
  "attack": 80,
  "defense": 70,
  "height": 0.7,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564db3c7ceae3cae710a86d6"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
  "attack": 95,
  "defense": 90,
  "height": 0.6,
  "moves": [
    "bomb",
    "fire",
    "desvio"
  ]
}
{
  "_id": ObjectId("564db6b498d8f9b11a7eb00c"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "height": null,
  "defense": null,
  "type": null,
  "moves": [ ]
}
Fetched 10 record(s) in 6ms

```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

```
var query = { $and: [ {moves: { $in: ['investida'] }}, {defence: { $not: { $lte: 49 }  }  } ]  }
Gustavos-Air(mongod-3.2.0) be-mean-pokemons> db.pokemons.find(query);
Fetched 0 record(s) in 0ms

```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
var query = {$and: [{type: /água/i}, {attack: {$lt: 50}}]};

Gustavos-Air(mongod-3.2.0) be-mean-pokemons> db.pokemons.find(query);
Removed 0 record(s) in 1ms
WriteResult({
  "nRemoved": 0
})

```

## Esse item não está no vídeo e se você fizer significa que você lê as coisas, nesse exercício demonstre qual a diferença entre os operadores `$ne` e `$not`.

```
$ne: Seleciona os documentos onde o valor do campo não é igual ao valor especificado. Esse não aceita regex expression

$not: Seleciona os documentos que não correspondem ao operador. Esse aceita regex expressions

Ambos incluem documentos que não contêm o campo.

```