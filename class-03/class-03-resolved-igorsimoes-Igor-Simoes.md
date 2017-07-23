# MongoDB - Aula 03 - Exercício

autor: Igor Simões de Oliveira Lima

## Observações
   ```
   1. O campo altura(height) dos meus objetos são inteiros
   2. Meus objetos não tem campo tipo(type)
   3. Mesmo não retornando nada, não deixa de estar certo :)

   ```

### 1 Listar pokemons com altura(height) MENOR que 0.5
    ```
    ubuntu-igor(mongod-3.0.7) be-mean-pokemons> var query = {height:{$lt:0.5}}
    ubuntu-igor(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
    Fetched 0 record(s) in 1ms
    ```
### 2 Listar pokemons com altura(height) MAIOR OU IGUAL a 0.5
    ```
    ubuntu-igor(mongod-3.0.7) be-mean-pokemons> var query = {height:{$gte:0.5}}
    ubuntu-igor(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
    {
      "_id": ObjectId("5645eb0af5c1f5d1e52aec29"),
      "name": "Mewtwo",
      "description": "Zica modafoca psiquico",
      "attack": 110,
      "defense": 90,
      "height": 20
    }
    {
      "_id": ObjectId("5645eb0af5c1f5d1e52aec2a"),
      "name": "Diglett",
      "description": "Cava buraco",
      "attack": 55,
      "defense": 25,
      "height": 2
    }
    {
      "_id": ObjectId("5645eb0af5c1f5d1e52aec2b"),
      "name": "Dodrio",
      "description": "Ave zica",
      "attack": 110,
      "defense": 70,
      "height": 18
    }
    {
      "_id": ObjectId("5645eb0af5c1f5d1e52aec2c"),
      "name": "Muk",
      "description": "Zica do pântano",
      "attack": 105,
      "defense": 75,
      "height": 12
    }
    {
      "_id": ObjectId("5645eb0af5c1f5d1e52aec2d"),
      "name": "Sandshrew",
      "description": "Rato da terra",
      "attack": 75,
      "defense": 85,
      "height": 6
    }
    Fetched 5 record(s) in 2ms
    ```

### 3 Listar pokemons com altura(height) MENOR OU IGUAL a 0.5 E tipo "Grama"
    ```
    ubuntu-igor(mongod-3.0.7) be-mean-pokemons> var query = {$and:[{height:{$lte:0.5}}, {type:"grama"}]}
    ubuntu-igor(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
    Fetched 0 record(s) in 1ms
    ```

### 4 Listar pokemons com nome(name) "pikachu" OU attack MENOR OU IGUAL 0.5
    ```
    ubuntu-igor(mongod-3.0.7) be-mean-pokemons> var query = {$or:[{nome:"Pikachu"}, {attack:{$lte:0.5}}]}
    ubuntu-igor(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
    Fetched 0 record(s) in 26ms
    ```

### 5 Listar pokemons com ataque(attack) MAIOR OU IGUAL que 48 E com altura(height) MENOR OU IGUAL que 0.5
    ```
    ubuntu-igor(mongod-3.0.7) be-mean-pokemons> var query = {$and:[{attack:{$gte:48}}, {height: {$lte:0.5}}]}
    ubuntu-igor(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
    Fetched 0 record(s) in 0ms
    ```
