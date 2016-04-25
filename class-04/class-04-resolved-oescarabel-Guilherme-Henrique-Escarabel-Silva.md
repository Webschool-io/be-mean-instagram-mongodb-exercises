# MongoDB - Aula 04 - Exercício
autor: Guilherme Henrique Escarabel Silva

## Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
oescarabel(mongod-3.2.4) be-mean-pokemons>var query = {
	$or: [
		{name: /Pikachu/i}, 
		{name: /Squirtle/i}, 
		{name: /Bulbassauro/i},
		{name: /Charmander/i}
	]
};
oescarabel(mongod-3.2.4) be-mean-pokemons>var mod = {
	$set: {
		moves: ["Ragnarok","Meteoro de Chesus"]
	}
};
oescarabel(mongod-3.2.4) be-mean-pokemons>var options = {multi: true};
oescarabel(mongod-3.2.4) be-mean-pokemons> db.pokemons.update(query,mod,options);
Updated 4 existing record(s) in 4ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
```

## Adicionar 1 movimento em todos os pokemons: 'desvio'
```
oescarabel(mongod-3.2.4) be-mean-pokemons> var query = {};
oescarabel(mongod-3.2.4) be-mean-pokemons> var mod = { $push: { moves: 'Desvio' } };
oescarabel(mongod-3.2.4) be-mean-pokemons> db.pokemons.update(query,mod,options);
Updated 15 existing record(s) in 4ms
WriteResult({
  "nMatched": 15,
  "nUpserted": 0,
  "nModified": 15
})
```

## Adicionar o pokemon 'AindaNaoExisteMon' caso ele não exista com todos os dados com o valor 'null' e a descrição: "Sem maiores informações"
```
oescarabel(mongod-3.2.4) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i};
oescarabel(mongod-3.2.4) be-mean-pokemons> var mod = {
    $setOnInsert: {
        name:"AindaNaoExisteMon", 
        attack: null, 
        description: "Sem Maiores Informações",
        type: null, 
        defense: null, 
        velocity: null, 
        category: null, 
        height: null, 
        moves: []
    }
};
oescarabel(mongod-3.2.4) be-mean-pokemons> var options = {upsert:true};
oescarabel(mongod-3.2.4) be-mean-pokemons> db.pokemons.update(query,mod,options);
Updated 1 new record(s) in 191ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("5718f94508202f17587839e3")
})
```

## Pesquisar todos os pokemons que possuam o ataque 'investida' e mais um que você adicionou, escolha seu pokemon favorito
```
oescarabel(mongod-3.2.4) be-mean-pokemons> var query = {$or: [{moves: /investida/i},{moves: /Meteoro de Chesus/i}]};
oescarabel(mongod-3.2.4) be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("57177bee79b2f16330764cbb"),
  "name": "Squirtle",
  "description": "Tartaruga brilhante",
  "type": "Tartaruga",
  "attack": 30,
  "defense": 30,
  "velocity": 20,
  "category": "Água",
  "height": 0.5,
  "moves": [
    "Ragnarok",
    "Meteoro de Chesus",
    "Desvio"
  ]
}

```

## Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito
```
oescarabel(mongod-3.2.4) be-mean-pokemons> var query = {$or: [{moves: /desvio/i},{moves: /Meteoro de Chesus/i},{moves: /Ragnarok/i}]};
oescarabel(mongod-3.2.4) be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("570fd80a2ce32ca4a32b0ddc"),
  "name": "Eevee",
  "description": "Não preciso nem me mexer para te dominar",
  "type": "Normal",
  "attack": 30,
  "defense": 20,
  "velocity": 30,
  "category": "Evolution",
  "height": 6.5,
  "active": false,
  "moves": [
    "Desvio"
  ]
}
```

## Pesquisar todos os pokemons que não são do tipo 'elétrico'
```
oescarabel(mongod-3.2.4) be-mean-pokemons> var query = {type: {$ne: "Elétric"}};
oescarabel(mongod-3.2.4) be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("570fb2562ce32ca4a32b0dd7"),
  "name": "Seadra",
  "description": "Sniper Russo",
  "type": "water",
  "attack": 30,
  "defense": 40,
  "velocity": 50,
  "category": "dragon",
  "height": 25,
  "active": false,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("570fb47c2ce32ca4a32b0dd8"),
  "name": "Surskit",
  "description": "Aranha Galática",
  "type": "bug",
  "attack": 20,
  "defense": 20,
  "velocity": 30,
  "category": "Pond Skater",
  "height": 1.7,
  "active": false,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("570fb4912ce32ca4a32b0dd9"),
  "name": "shuppet",
  "description": "Rouba lençois para se vestir",
  "type": "Ghost",
  "attack": 40,
  "defense": 20,
  "velocity": 30,
  "category": "Puppet",
  "height": 2.3,
  "active": false,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("570fb5902ce32ca4a32b0dda"),
  "name": "Entei",
  "description": "Corpo de Tigre, rosto de Gavião e rabo de nuvem",
  "type": "Fire",
  "attack": 60,
  "defense": 40,
  "velocity": 50,
  "category": "Volcano",
  "height": 198,
  "active": false,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("570fd6c12ce32ca4a32b0ddb"),
  "name": "Gengar",
  "description": "Típico demônio",
  "type": "Ghost",
  "attack": 30,
  "defense": 30,
  "velocity": 60,
  "category": "Shadow",
  "height": 40.5,
  "active": false,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("570fd80a2ce32ca4a32b0ddc"),
  "name": "Eevee",
  "description": "Não preciso nem me mexer para te dominar",
  "type": "Normal",
  "attack": 30,
  "defense": 20,
  "velocity": 30,
  "category": "Evolution",
  "height": 6.5,
  "active": false,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("570fd8ea2ce32ca4a32b0ddd"),
  "name": "Bunnelby",
  "description": "Coelho com sprite errada, os pés são as orelhas",
  "type": "Normal",
  "attack": 20,
  "defense": 20,
  "velocity": 30,
  "category": "Digging",
  "height": 5,
  "active": false,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("571058142ce32ca4a32b0ddf"),
  "name": "Gramatildo",
  "description": "Comedor de alho poró",
  "type": "Grama",
  "attack": 100,
  "height": 0.4,
  "active": false,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("57118b1d3358e0529965de11"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8003,
  "active": false,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("57163dfdcd67f416d70328b9"),
  "active": false,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("57163f6acd67f416d70328ba"),
  "active": false,
  "name": "NãoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações",
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("57177b2679b2f16330764cba"),
  "name": "Bulbassauro",
  "description": "Sapo com flor nas costas",
  "type": "grama",
  "attack": 30,
  "defense": 20,
  "velocity": 30,
  "category": "Semente",
  "height": 0.7,
  "moves": [
    "Ragnarok",
    "Meteoro de Chesus",
    "Desvio"
  ]
}
{
  "_id": ObjectId("57177bee79b2f16330764cbb"),
  "name": "Squirtle",
  "description": "Tartaruga brilhante",
  "type": "Tartaruga",
  "attack": 30,
  "defense": 30,
  "velocity": 20,
  "category": "Água",
  "height": 0.5,
  "moves": [
    "Ragnarok",
    "Meteoro de Chesus",
    "Desvio"
  ]
}
{
  "_id": ObjectId("57177c6279b2f16330764cbc"),
  "name": "Charmander",
  "description": "Largarto del Fuego",
  "type": "Fogo",
  "attack": 30,
  "defense": 20,
  "velocity": 40,
  "category": "Lagarto",
  "height": 0.6,
  "moves": [
    "Ragnarok",
    "Meteoro de Chesus",
    "Desvio"
  ]
}
{
  "_id": ObjectId("5718f94508202f17587839e3"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "description": "Sem Maiores Informações",
  "type": null,
  "defense": null,
  "velocity": null,
  "category": null,
  "height": null,
  "moves": [ ]
}
Fetched 15 record(s) in 14ms
```

## Pesquisar todos os pokemons que tenham o ataque 'investida' e tenham a defesa não menor ou igual a 49
```
oescarabel(mongod-3.2.4) be-mean-pokemons> var query = {
    $and:
        [{
            moves: /desvio/i
        },
        {
            defense:
            {
                $not:
                {
                    $lte:49
                }
            }
        }]
};
oescarabel(mongod-3.2.4) be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("571058142ce32ca4a32b0ddf"),
  "name": "Gramatildo",
  "description": "Comedor de alho poró",
  "type": "Grama",
  "attack": 100,
  "height": 0.4,
  "active": false,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("57118b1d3358e0529965de11"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8003,
  "active": false,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("57163dfdcd67f416d70328b9"),
  "active": false,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("57163f6acd67f416d70328ba"),
  "active": false,
  "name": "NãoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações",
  "moves": [
    "Desvio"
  ]
}
Fetched 4 record(s) in 77ms
```

## Remova todos os pokemons do tipo água e com attack menor que 50.
```
oescarabel(mongod-3.2.4) be-mean-pokemons> var options = {multi: true};
oescarabel(mongod-3.2.4) be-mean-pokemons> var query = {
    $and: 
        [
            {
                type: "water"
            }, 
            {
                attack: 
                {
                    $lt: 50
                }
            }
        ]
};
oescarabel(mongod-3.2.4) be-mean-pokemons> db.pokemons.remove(query,options);
Removed 1 record(s) in 3ms
WriteResult({
  "nRemoved": 1
})

```