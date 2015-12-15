# MongoDB - Aula 04 - Exercício
autor: Jefferson Daniel (https://github.com/jeffersondanielss)

## Meus Pokemons

  ```
  > db.pokemons.find().pretty()
  {
    "_id" : ObjectId("5642aab3c72670aa4c8b3c7a"),
    "name" : "Pikachu",
    "description" : "Raio elétrico bem fofinho",
    "type" : "eletric",
    "attack" : 55,
    "height" : 4,
    "active" : false,
    "moves" : [
      "investida",
      "choque do trovao"
    ]
  }
  {
    "_id" : ObjectId("5642ad29c72670aa4c8b3c7b"),
    "name" : "Charmander",
    "description" : "cao chpando manga",
    "type" : "fogo",
    "attack" : 52,
    "height" : 0.6,
    "active" : false,
    "moves" : [
      "investida"
    ]
  }
  {
    "_id" : ObjectId("5642ad2cc72670aa4c8b3c7c"),
    "name" : "Squirtie",
    "description" : "Ejeta agua que passarinho nao bebe",
    "type" : "água",
    "attack" : 48,
    "height" : 0.5,
    "active" : false,
    "moves" : [
      "investida",
      "hidro bomba"
    ]
  }
  {
    "_id" : ObjectId("5642ad79c72670aa4c8b3c7d"),
    "name" : "Bulbassauro",
    "description" : "chicote de trepadeira",
    "type" : "grama",
    "attack" : 49,
    "height" : 0.4,
    "active" : false,
    "moves" : [
      "investida"
    ]
  }
  {
    "_id" : ObjectId("5642b1b5997c24374859600f"),
    "name" : "Caterpie",
    "description" : "larva lutadora",
    "type" : "inseto",
    "attack" : 30,
    "height" : 0.3,
    "defense" : 35,
    "active" : false,
    "moves" : [
      "investida"
    ]
  }
  {
    "_id" : ObjectId("564cca57ad2e80fc35fc6fab"),
    "active" : false,
    "name" : "NaoExisteMon",
    "attack" : null,
    "defense" : null,
    "height" : null,
    "description" : "sem maiores informações",
    "moves" : [
      "investida"
    ]
  }
  ```

## Exercício

1. **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

``` 
  var query = { 
    $or: [
      { name: /pikachu/i },
      { name: /squirtie/i },
      { name: /bulbassauro/i }
    ]
  }

  var attacks = ['spray de pimenta', 'coronhada']

  var mod = { $pushAll: { moves: attacks } }

  var options = { multi: true }

  db.pokemons.update( query, mod, options )

  WriteResult({ "nMatched" : 3, "nUpserted" : 0, "nModified" : 3 })

  db.pokemons.find( query ).pretty()

  {
    "_id" : ObjectId("5642aab3c72670aa4c8b3c7a"),
    "name" : "Pikachu",
    "description" : "Raio elétrico bem fofinho",
    "type" : "eletric",
    "attack" : 55,
    "height" : 4,
    "active" : false,
    "moves" : [
      "coque do trovao",
      "investida",
      "spray de pimenta",
      "coronhada"
    ]
  }
  {
    "_id" : ObjectId("5642ad2cc72670aa4c8b3c7c"),
    "name" : "Squirtie",
    "description" : "Ejeta agua que passarinho nao bebe",
    "type" : "água",
    "attack" : 48,
    "height" : 0.5,
    "active" : false,
    "moves" : [
      "investida",
      "hidro bomba",
      "spray de pimenta",
      "coronhada"
    ]
  }
  {
    "_id" : ObjectId("5642ad79c72670aa4c8b3c7d"),
    "name" : "Bulbassauro",
    "description" : "chicote de trepadeira",
    "type" : "grama",
    "attack" : 49,
    "height" : 0.4,
    "active" : false,
    "moves" : [
      "investida",
      "spray de pimenta",
      "coronhada"
    ]
  }
```

2. **Adicionar** 1 movimento em todos os pokemons: `desvio`.

```
  var query = {}

  var mod = { $push: { moves: 'desvio' } }

  var options = { multi: true }

  db.pokemons.update( query, mod, options )

  WriteResult({ "nMatched" : 7, "nUpserted" : 0, "nModified" : 7 })

  db.pokemons.find( query ).pretty()

  {
    "_id" : ObjectId("5642ad29c72670aa4c8b3c7b"),
    "name" : "Charmander",
    "description" : "cao chpando manga",
    "type" : "fogo",
    "attack" : 52,
    "height" : 0.6,
    "active" : false,
    "moves" : [
      "investida",
      "desvio"
    ]
  }
  {
    "_id" : ObjectId("5642ad79c72670aa4c8b3c7d"),
    "name" : "Bulbassauro",
    "description" : "chicote de trepadeira",
    "type" : "grama",
    "attack" : 49,
    "height" : 0.4,
    "active" : false,
    "moves" : [
      "investida",
      "spray de pimenta",
      "coronhada",
      "desvio"
    ]
  }
  {
    "_id" : ObjectId("5642b1b5997c24374859600f"),
    "name" : "Caterpie",
    "description" : "larva lutadora",
    "type" : "inseto",
    "attack" : 30,
    "height" : 0.3,
    "defense" : 35,
    "active" : false,
    "moves" : [
      "investida",
      "desvio"
    ]
  }
  {
    "_id" : ObjectId("564cca57ad2e80fc35fc6fab"),
    "active" : false,
    "name" : "NaoExisteMon",
    "attack" : null,
    "defense" : null,
    "height" : null,
    "description" : "sem maiores informações",
    "moves" : [
      "investida",
      "desvio"
    ]
  }
  {
    "_id" : ObjectId("564cdd43ad2e80fc35fc6fad"),
    "active" : true,
    "name" : "teste",
    "attack" : null,
    "defense" : null,
    "height" : null,
    "description" : "sem maiores informações",
    "moves" : [
      "investida",
      "coque do trovao",
      "investida",
      "desvio"
    ]
  }
  {
    "_id" : ObjectId("5642aab3c72670aa4c8b3c7a"),
    "name" : "Pikachu",
    "description" : "Raio elétrico bem fofinho",
    "type" : "eletric",
    "attack" : 55,
    "height" : 4,
    "active" : false,
    "moves" : [
      "coque do trovao",
      "investida",
      "spray de pimenta",
      "coronhada",
      "desvio"
    ]
  }
  {
    "_id" : ObjectId("5642ad2cc72670aa4c8b3c7c"),
    "name" : "Squirtie",
    "description" : "Ejeta agua que passarinho nao bebe",
    "type" : "água",
    "attack" : 48,
    "height" : 0.5,
    "active" : false,
    "moves" : [
      "investida",
      "hidro bomba",
      "spray de pimenta",
      "coronhada",
      "desvio"
    ]
  }
```

3. **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".

```
  var query = { name: /AindaNaoExisteMon/i }
  var mod = {
    $set: { active: true },
    $setOnInsert: {
      name: "AindaNaoExisteMon",
      attack: null,
      defense: null,
      height: null,
      description: 'sem maiores informações'
    }
  }

  var options = { upsert: true }
  db.pokemons.update( query, mod, options )

  WriteResult({
    "nMatched" : 0,
    "nUpserted" : 1,
    "nModified" : 0,
    "_id" : ObjectId("564cf1c0ad2e80fc35fc6fae")
  })

  db.pokemons.find( query ).pretty()

  {
    "_id" : ObjectId("564cf1c0ad2e80fc35fc6fae"),
    "active" : true,
    "name" : "AindaNaoExisteMon",
    "attack" : null,
    "defense" : null,
    "height" : null,
    "description" : "sem maiores informações"
  }
```

4. Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.

```
  var query = { moves: { $all: [ 'investida', 'spray de pimenta' ] } }
  db.pokemons.find( query ).pretty()

  {
    "_id" : ObjectId("5642ad79c72670aa4c8b3c7d"),
    "name" : "Bulbassauro",
    "description" : "chicote de trepadeira",
    "type" : "grama",
    "attack" : 49,
    "height" : 0.4,
    "active" : false,
    "moves" : [
      "investida",
      "spray de pimenta",
      "coronhada",
      "desvio"
    ]
  }
  {
    "_id" : ObjectId("5642aab3c72670aa4c8b3c7a"),
    "name" : "Pikachu",
    "description" : "Raio elétrico bem fofinho",
    "type" : "eletric",
    "attack" : 55,
    "height" : 4,
    "active" : false,
    "moves" : [
      "coque do trovao",
      "investida",
      "spray de pimenta",
      "coronhada",
      "desvio"
    ]
  }
  {
    "_id" : ObjectId("5642ad2cc72670aa4c8b3c7c"),
    "name" : "Squirtie",
    "description" : "Ejeta agua que passarinho nao bebe",
    "type" : "água",
    "attack" : 48,
    "height" : 0.5,
    "active" : false,
    "moves" : [
      "investida",
      "hidro bomba",
      "spray de pimenta",
      "coronhada",
      "desvio"
    ]
  }

```

5. Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```
  var query = { moves: { $all: [ 'coronhada', 'spray de pimenta' ] } }
  db.pokemons.find( query ).pretty()

  {
    "_id" : ObjectId("5642ad79c72670aa4c8b3c7d"),
    "name" : "Bulbassauro",
    "description" : "chicote de trepadeira",
    "type" : "grama",
    "attack" : 49,
    "height" : 0.4,
    "active" : false,
    "moves" : [
      "investida",
      "spray de pimenta",
      "coronhada",
      "desvio"
    ]
  }
  {
    "_id" : ObjectId("5642aab3c72670aa4c8b3c7a"),
    "name" : "Pikachu",
    "description" : "Raio elétrico bem fofinho",
    "type" : "eletric",
    "attack" : 55,
    "height" : 4,
    "active" : false,
    "moves" : [
      "coque do trovao",
      "investida",
      "spray de pimenta",
      "coronhada",
      "desvio"
    ]
  }
  {
    "_id" : ObjectId("5642ad2cc72670aa4c8b3c7c"),
    "name" : "Squirtie",
    "description" : "Ejeta agua que passarinho nao bebe",
    "type" : "água",
    "attack" : 48,
    "height" : 0.5,
    "active" : false,
    "moves" : [
      "investida",
      "hidro bomba",
      "spray de pimenta",
      "coronhada",
      "desvio"
    ]
  }
```

6. Pesquisar **todos** os pokemons que não são do tipo `elétrico`.

```
  var query = { type: { $not: /eletric/i } }
  db.pokemons.find( query ).pretty()

  {
    "_id" : ObjectId("5642ad29c72670aa4c8b3c7b"),
    "name" : "Charmander",
    "description" : "cao chpando manga",
    "type" : "fogo",
    "attack" : 52,
    "height" : 0.6,
    "active" : false,
    "moves" : [
      "investida",
      "desvio"
    ]
  }
  {
    "_id" : ObjectId("5642ad79c72670aa4c8b3c7d"),
    "name" : "Bulbassauro",
    "description" : "chicote de trepadeira",
    "type" : "grama",
    "attack" : 49,
    "height" : 0.4,
    "active" : false,
    "moves" : [
      "investida",
      "spray de pimenta",
      "coronhada",
      "desvio"
    ]
  }
  {
    "_id" : ObjectId("5642b1b5997c24374859600f"),
    "name" : "Caterpie",
    "description" : "larva lutadora",
    "type" : "inseto",
    "attack" : 30,
    "height" : 0.3,
    "defense" : 35,
    "active" : false,
    "moves" : [
      "investida",
      "desvio"
    ]
  }
  {
    "_id" : ObjectId("564cca57ad2e80fc35fc6fab"),
    "active" : false,
    "name" : "NaoExisteMon",
    "attack" : null,
    "defense" : null,
    "height" : null,
    "description" : "sem maiores informações",
    "moves" : [
      "investida",
      "desvio"
    ]
  }
  {
    "_id" : ObjectId("5642ad2cc72670aa4c8b3c7c"),
    "name" : "Squirtie",
    "description" : "Ejeta agua que passarinho nao bebe",
    "type" : "água",
    "attack" : 48,
    "height" : 0.5,
    "active" : false,
    "moves" : [
      "investida",
      "hidro bomba",
      "spray de pimenta",
      "coronhada",
      "desvio"
    ]
  }
  {
    "_id" : ObjectId("564cf1c0ad2e80fc35fc6fae"),
    "active" : true,
    "name" : "AindaNaoExisteMon",
    "attack" : null,
    "defense" : null,
    "height" : null,
    "description" : "sem maiores informações"
  }

```

7. Pesquisar **todos** pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.

```
var query = { $and: [ { moves: 'investida' }, { defense: { $gte: 49 } } ] }
db.pokemons.find( query ).pretty()
```

8. Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
  var query = { $and: [ { type: /água/i }, { attack: { $lte: 50 } } ] }
  db.pokemons.find( query ).pretty()

  {
    "_id" : ObjectId("5642ad2cc72670aa4c8b3c7c"),
    "name" : "Squirtie",
    "description" : "Ejeta agua que passarinho nao bebe",
    "type" : "água",
    "attack" : 48,
    "height" : 0.5,
    "active" : false,
    "moves" : [
      "investida",
      "hidro bomba",
      "spray de pimenta",
      "coronhada",
      "desvio"
    }
  }
```