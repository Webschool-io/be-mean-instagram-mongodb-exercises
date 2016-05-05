# MongoDB - Aula 04 - Exercício
autor: Lucas de Oliveira

1 - **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```js
lucas-Vostro-14-5480(mongod-2.4.9) be-mean-pokemons> var query = {name: {$in: [/pikachu/i, /squirtle/i, /bulbassauro/i, /charmander/i]}}
lucas-Vostro-14-5480(mongod-2.4.9) be-mean-pokemons> var mod = { $pushAll: { moves: ['Voadora alemã', 'Dragão branco'] }}
lucas-Vostro-14-5480(mongod-2.4.9) be-mean-pokemons> var options = { multi: true }
lucas-Vostro-14-5480(mongod-2.4.9) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 1ms
lucas-Vostro-14-5480(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56427d3334289cd2f8f7c21e"),
  "attack": 55,
  "description": "Rato elétrico bem fofinho",
  "height": 0.4,
  "moves": [
    "Voadora alemã",
    "Dragão branco"
  ],
  "name": "Pikachu",
  "type": "electric"
}
{
  "_id": ObjectId("56427d7534289cd2f8f7c21f"),
  "attack": 49,
  "description": "Chicote de trepadeira",
  "height": 0.4,
  "moves": [
    "Voadora alemã",
    "Dragão branco"
  ],
  "name": "Bulbassauro",
  "type": "grama"
}
{
  "_id": ObjectId("56427d8734289cd2f8f7c220"),
  "attack": 52,
  "description": "Esse é o cão chupando manga de fofinho",
  "height": 0.6,
  "moves": [
    "Voadora alemã",
    "Dragão branco"
  ],
  "name": "Charmander",
  "type": "fogo"
}
{
  "_id": ObjectId("56427e8634289cd2f8f7c223"),
  "attack": 48,
  "description": "Ejeta água que passarinho não bebe",
  "height": 0.5,
  "moves": [
    "Voadora alemã",
    "Dragão branco"
  ],
  "name": "Squirtle",
  "type": "água"
}
Fetched 4 record(s) in 2ms
```

2 - **Adicionar** 1 movimento em todos os pokemons: `desvio`.

```js
lucas-Vostro-14-5480(mongod-2.4.9) be-mean-pokemons> var query = {}
lucas-Vostro-14-5480(mongod-2.4.9) be-mean-pokemons> var mod = { $push: { moves: 'Corneta paralisadora' } }
lucas-Vostro-14-5480(mongod-2.4.9) be-mean-pokemons> var options = { multi: true }
lucas-Vostro-14-5480(mongod-2.4.9) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 9 existing record(s) in 13ms
lucas-Vostro-14-5480(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5642826f34289cd2f8f7c224"),
  "attack": 82,
  "defense": 78,
  "description": "This legendary jamaican POKEMON smokes weed everyday",
  "height": "17",
  "moves": [
    "Corneta paralisadora"
  ],
  "name": "Golduck"
}
{
  "_id": ObjectId("5642828534289cd2f8f7c225"),
  "attack": 80,
  "defense": 35,
  "description": "Extremely quick to anger. It could be docile one moment then thrashing away the next instant.",
  "height": "5",
  "moves": [
    "Corneta paralisadora"
  ],
  "name": "Mankey"
}
{
  "_id": ObjectId("5642829a34289cd2f8f7c226"),
  "attack": 105,
  "defense": 60,
  "description": "When it becomes furious, its blood circulation becomes more robust, and its muscles are made stronger. But it also becomes much less intelligent.",
  "height": "10",
  "moves": [
    "Corneta paralisadora"
  ],
  "name": "Primeape"
}
{
  "_id": ObjectId("564282b134289cd2f8f7c227"),
  "attack": 70,
  "defense": 45,
  "description": "A POKMON with a friendly nature. However, it will bark fiercely at anything invading its territory.",
  "height": "7",
  "moves": [
    "Corneta paralisadora"
  ],
  "name": "Growlithe"
}
{
  "_id": ObjectId("564282c234289cd2f8f7c228"),
  "attack": 110,
  "defense": 80,
  "description": "This legendary Chinese POKEMON is considered magnif icent. Many people are enchanted by its grand mane.",
  "height": "19",
  "moves": [
    "Corneta paralisadora"
  ],
  "name": "Arcanine"
}
{
  "_id": ObjectId("56427d3334289cd2f8f7c21e"),
  "attack": 55,
  "description": "Rato elétrico bem fofinho",
  "height": 0.4,
  "moves": [
    "Voadora alemã",
    "Dragão branco",
    "Corneta paralisadora"
  ],
  "name": "Pikachu",
  "type": "electric"
}
{
  "_id": ObjectId("56427d7534289cd2f8f7c21f"),
  "attack": 49,
  "description": "Chicote de trepadeira",
  "height": 0.4,
  "moves": [
    "Voadora alemã",
    "Dragão branco",
    "Corneta paralisadora"
  ],
  "name": "Bulbassauro",
  "type": "grama"
}
{
  "_id": ObjectId("56427d8734289cd2f8f7c220"),
  "attack": 52,
  "description": "Esse é o cão chupando manga de fofinho",
  "height": 0.6,
  "moves": [
    "Voadora alemã",
    "Dragão branco",
    "Corneta paralisadora"
  ],
  "name": "Charmander",
  "type": "fogo"
}
{
  "_id": ObjectId("56427e8634289cd2f8f7c223"),
  "attack": 48,
  "description": "Ejeta água que passarinho não bebe",
  "height": 0.5,
  "moves": [
    "Voadora alemã",
    "Dragão branco",
    "Corneta paralisadora"
  ],
  "name": "Squirtle",
  "type": "água"
}
Fetched 9 record(s) in 80ms
```

3 - **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".

```js
lucas-Vostro-14-5480(mongod-2.4.9) be-mean-pokemons> var query = { name: /aindanaoexistemon/i }
lucas-Vostro-14-5480(mongod-2.4.9) be-mean-pokemons> var mod = { $set: { active: true }, $setOnInsert: { name: "AindaNaoExisteMon", attack: null, defense: null, height: null, description: 'Sem maiores informações' }}
lucas-Vostro-14-5480(mongod-2.4.9) be-mean-pokemons> var options = { upsert: true }
lucas-Vostro-14-5480(mongod-2.4.9) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 341ms
lucas-Vostro-14-5480(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564d1b317c4cd776a0208118"),
  "active": true,
  "attack": null,
  "defense": null,
  "description": "Sem maiores informações",
  "height": null,
  "name": "AindaNaoExisteMon"
}
Fetched 1 record(s) in 145ms
```

4. Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.

```js
lucas-Vostro-14-5480(mongod-2.4.9) be-mean-pokemons> var query = { moves: { $all: ['investida', 'Voadora alemã'] } }
lucas-Vostro-14-5480(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56427d8734289cd2f8f7c220"),
  "attack": 52,
  "description": "Esse é o cão chupando manga de fofinho",
  "height": 0.6,
  "moves": [
    "Voadora alemã",
    "Dragão branco",
    "Corneta paralisadora",
    "investida"
  ],
  "name": "Charmander",
  "type": "fogo"
}
Fetched 1 record(s) in 1ms
```

5 - Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```js
lucas-Vostro-14-5480(mongod-2.4.9) be-mean-pokemons> var query = { moves: { $all: ['Corneta paralisadora', 'Voadora alemã', 'Dragão branco'] } }
lucas-Vostro-14-5480(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56427d3334289cd2f8f7c21e"),
  "attack": 55,
  "description": "Rato elétrico bem fofinho",
  "height": 0.4,
  "moves": [
    "Voadora alemã",
    "Dragão branco",
    "Corneta paralisadora"
  ],
  "name": "Pikachu",
  "type": "electric"
}
{
  "_id": ObjectId("56427d7534289cd2f8f7c21f"),
  "attack": 49,
  "description": "Chicote de trepadeira",
  "height": 0.4,
  "moves": [
    "Voadora alemã",
    "Dragão branco",
    "Corneta paralisadora"
  ],
  "name": "Bulbassauro",
  "type": "grama"
}
{
  "_id": ObjectId("56427e8634289cd2f8f7c223"),
  "attack": 48,
  "description": "Ejeta água que passarinho não bebe",
  "height": 0.5,
  "moves": [
    "Voadora alemã",
    "Dragão branco",
    "Corneta paralisadora"
  ],
  "name": "Squirtle",
  "type": "água"
}
{
  "_id": ObjectId("56427d8734289cd2f8f7c220"),
  "attack": 52,
  "description": "Esse é o cão chupando manga de fofinho",
  "height": 0.6,
  "moves": [
    "Voadora alemã",
    "Dragão branco",
    "Corneta paralisadora",
    "investida"
  ],
  "name": "Charmander",
  "type": "fogo"
}
Fetched 4 record(s) in 25ms
```

6 - Pesquisar **todos** os pokemons que não são do tipo `elétrico`.

```js
lucas-Vostro-14-5480(mongod-2.4.9) be-mean-pokemons> var query = { type: { $ne: 'elétrico' } }
lucas-Vostro-14-5480(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5642826f34289cd2f8f7c224"),
  "attack": 82,
  "defense": 78,
  "description": "This legendary jamaican POKEMON smokes weed everyday",
  "height": "17",
  "moves": [
    "Corneta paralisadora"
  ],
  "name": "Golduck"
}
{
  "_id": ObjectId("5642828534289cd2f8f7c225"),
  "attack": 80,
  "defense": 35,
  "description": "Extremely quick to anger. It could be docile one moment then thrashing away the next instant.",
  "height": "5",
  "moves": [
    "Corneta paralisadora"
  ],
  "name": "Mankey"
}
{
  "_id": ObjectId("5642829a34289cd2f8f7c226"),
  "attack": 105,
  "defense": 60,
  "description": "When it becomes furious, its blood circulation becomes more robust, and its muscles are made stronger. But it also becomes much less intelligent.",
  "height": "10",
  "moves": [
    "Corneta paralisadora"
  ],
  "name": "Primeape"
}
{
  "_id": ObjectId("564282b134289cd2f8f7c227"),
  "attack": 70,
  "defense": 45,
  "description": "A POKMON with a friendly nature. However, it will bark fiercely at anything invading its territory.",
  "height": "7",
  "moves": [
    "Corneta paralisadora"
  ],
  "name": "Growlithe"
}
{
  "_id": ObjectId("564282c234289cd2f8f7c228"),
  "attack": 110,
  "defense": 80,
  "description": "This legendary Chinese POKEMON is considered magnif icent. Many people are enchanted by its grand mane.",
  "height": "19",
  "moves": [
    "Corneta paralisadora"
  ],
  "name": "Arcanine"
}
{
  "_id": ObjectId("56427d3334289cd2f8f7c21e"),
  "attack": 55,
  "description": "Rato elétrico bem fofinho",
  "height": 0.4,
  "moves": [
    "Voadora alemã",
    "Dragão branco",
    "Corneta paralisadora"
  ],
  "name": "Pikachu",
  "type": "electric"
}
{
  "_id": ObjectId("56427d7534289cd2f8f7c21f"),
  "attack": 49,
  "description": "Chicote de trepadeira",
  "height": 0.4,
  "moves": [
    "Voadora alemã",
    "Dragão branco",
    "Corneta paralisadora"
  ],
  "name": "Bulbassauro",
  "type": "grama"
}
{
  "_id": ObjectId("56427e8634289cd2f8f7c223"),
  "attack": 48,
  "description": "Ejeta água que passarinho não bebe",
  "height": 0.5,
  "moves": [
    "Voadora alemã",
    "Dragão branco",
    "Corneta paralisadora"
  ],
  "name": "Squirtle",
  "type": "água"
}
{
  "_id": ObjectId("564d1b317c4cd776a0208118"),
  "active": true,
  "attack": null,
  "defense": null,
  "description": "Sem maiores informações",
  "height": null,
  "name": "AindaNaoExisteMon"
}
{
  "_id": ObjectId("56427d8734289cd2f8f7c220"),
  "attack": 52,
  "description": "Esse é o cão chupando manga de fofinho",
  "height": 0.6,
  "moves": [
    "Voadora alemã",
    "Dragão branco",
    "Corneta paralisadora",
    "investida"
  ],
  "name": "Charmander",
  "type": "fogo"
}
Fetched 10 record(s) in 509ms
```

7 - Pesquisar **todos** pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.

```js
lucas-Vostro-14-5480(mongod-2.4.9) be-mean-pokemons> var query = { $and: [ { moves: 'investida' }, { defense: { $not: { $lte: 49 } } } ] }
lucas-Vostro-14-5480(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56427d8734289cd2f8f7c220"),
  "attack": 52,
  "description": "Esse é o cão chupando manga de fofinho",
  "height": 0.6,
  "moves": [
    "Voadora alemã",
    "Dragão branco",
    "Corneta paralisadora",
    "investida"
  ],
  "name": "Charmander",
  "type": "fogo",
  "defense": 88
}
Fetched 1 record(s) in 1ms
```

8 - Remova **todos** os pokemons do tipo água e com attack menor que 50.

```js
lucas-Vostro-14-5480(mongod-2.4.9) be-mean-pokemons> var query = { $and: [{type: 'água'}, {attack: { $lt: 50 }}] }
lucas-Vostro-14-5480(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56427e8634289cd2f8f7c223"),
  "attack": 48,
  "description": "Ejeta água que passarinho não bebe",
  "height": 0.5,
  "moves": [
    "Voadora alemã",
    "Dragão branco",
    "Corneta paralisadora"
  ],
  "name": "Squirtle",
  "type": "água"
}
Fetched 1 record(s) in 1ms
lucas-Vostro-14-5480(mongod-2.4.9) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 47ms
```
