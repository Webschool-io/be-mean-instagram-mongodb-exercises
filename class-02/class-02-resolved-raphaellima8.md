# MongoDB - Aula 02 - Exercício
autor: Raphael Lima

## Crie uma database chamada be-mean-pokemons

    ```
    use be-mean-pokemons
    switched to db be-mean-pokemons
    debian(mongod-3.0.7) be-mean-pokemons>

    ```

## Liste quais databases você possui nesse servidor

    ```
    debian(mongod-3.0.7) be-mean-pokemons> show dbs
    local             → 0.078GB
    test              → 0.078GB
    be-mean-instagram → 0.078GB
    be-mean           → 0.078GB
    debian(mongod-3.0.7) be-mean-pokemons>

    ```

## Listagem das coleções (passo 3)

    ```
    debian(mongod-3.0.7) be-mean-pokemons> show collections
    pokemons       → 0.000MB / 0.008MB
    system.indexes → 0.000MB / 0.008MB
    ```

## Insira pelo menos 5 pokemons A SUA ESCOLHA utilizando o mesmo padrão de campos utilizado: name, description, attack, defense e height

    ```
    var blastoise = {'name':'Blastoise','description': 'Blastoise has water spouts that protrude from its shell','type': 'water', 'attack': 85, height: 16 }

    var charizard = {'name':'Charizard','description': 'Charizard flies around the sky in search of powerful opponents','type': 'fire', 'attack': 109, height: 17 }

    var beedrill = {'name':'Beedrill','description': 'Beedrill is extremely territorial','type': 'flying', 'attack': 45, height: 10 }

    var scizor = {name: "Scizor", description: "Scizor is a bipedal, insectoid Pokémon with a red, metallic exoskeleton. It has gray, retractable forewings and hind wings with simple, curved venation", attack: 999, defense: 999, height: 33.33}

    var raticate = {'name':'Raticate','description': 'Raticates sturdy fangs grow steadily','type': 'normal', 'attack': 50, height: 7 }

    ```
## Liste os pokemons existentes na sua coleção

    ```
    debian(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
"_id": ObjectId("5647fad53b616ac39c6286dc"),
"name": "Blastoise",
"description": "Blastoise has water spouts that protrude from its shell",
"type": "water",
"attack": 85,
"height": 16
}
{
"_id": ObjectId("5647fb2f3b616ac39c6286dd"),
"name": "Charizard",
"description": "Charizard flies around the sky in search of powerful opponents",
"type": "fire",
"attack": 109,
"height": 17
}
{
"_id": ObjectId("5647fb363b616ac39c6286de"),
"name": "Beedrill",
"description": "Beedrill is extremely territorial",
"type": "flying",
"attack": 45,
"height": 10
}
{
"_id": ObjectId("5647fb3c3b616ac39c6286df"),
"name": "Scizor",
"description": "Scizor is a bipedal, insectoid Pokémon with a red, metallic exoskeleton. It has gray, retractable forewings and hind wings with simple, curved venation",
"attack": 999,
"defense": 999,
"height": 33.33
}
{
"_id": ObjectId("5647fb413b616ac39c6286e0"),
"name": "Raticate",
"description": "Raticates sturdy fangs grow steadily",
"type": "normal",
"attack": 50,
"height": 7
}
Fetched 5 record(s) in 5ms

    ```
## Busque o pokemon a sua escolha, pelo nome, e armazene-o em uma variável chamada "poke"
  ```
  debian(mongod-3.0.7) be-mean-pokemons> var query = {name:'Raticate'}
  debian(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(query)
  ```


## Modifique sua `description` e salvê-o

    ```
    debian(mongod-3.0.7) be-mean-pokemons> poke.description = "Mudança da descrição para atender o exercício"
    Mudança da descrição para atender o exercício
    debian(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
    Updated 1 existing record(s) in 3ms
    WriteResult({
    "nMatched": 1,
    "nUpserted": 0,
    "nModified": 1
    })
    debian(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
    {
    "_id": ObjectId("5647fb413b616ac39c6286e0"),
    "name": "Raticate",
    "description": "Mudança da descrição para atender o exercício",
    "type": "normal",
    "attack": 50,
    "height": 7
    }
    Fetched 1 record(s) in 1ms
    ```
