# MongoDB - Aula 02 - Exercício
autor: Edison Magalhães Rocha


### 1. Crie uma database chamada be-mean-pokemons;
```
njinga(mongod-3.2.6) be-mean-instagram> use be-mean-pokemons
switched to db be-mean-pokemons
```

### 2. Liste quais databases você possui nesse servidor
```
njinga(mongod-3.2.6) be-mean-pokemons> show dbs
be-mean           → 0.005GB
be-mean-instagram → 0.000GB
local             → 0.000GB
njinga(mongod-3.2.6) be-mean-pokemons> 
```

### 3. Liste quais coleções você possui nessa database;
```
njinga(mongod-3.2.6) be-mean-pokemon> show collections
njinga(mongod-3.2.6) be-mean-pokemon>
```

### 4. Insira pelo menos 5 pokemons A SUA ESCOLHA utilizando o mesmo padrão de campos utilizado: name, description, attack, defense e height;
```
var insertpoke = [{'name':'Fraxure','description': 'Bixo feio pra caralho que tem dois chifes na boca','type':'Dragon', attack: 70, defense: 43, height: 1.0}, {'name':'Drifloon','description': 'Bixo meio fofo, mas meio diabólico. Não tem boca','type':'Ghost', attack: 35, defense: 23, height: 0.4}, {'name':'Croconaw','description': 'Tem moicano de Punk','type':'Water', attack: 49, defense: 32, height: 1.1}, {'name':'Furfrou','description':'Poodle de madame com cara de drogado','type':'Normal', attack: 47, defense: 38, height: 1.2}, {'name':'Scizor','description':'Parece uma mistura de carangueijo com robô','type':'Bug', attack: 78, defense: 52, height: 1.8 }]

njinga(mongod-3.2.6) be-mean-pokemon> db.pokemons.insert(insertpoke)
Inserted 1 record(s) in 18ms
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
njinga(mongod-3.2.6) be-mean-pokemon> 
```

### 5. Liste os pokemons existentes na sua coleção;
```
njinga(mongod-3.2.6) be-mean-pokemon> db.pokemons.find()
{
  "_id": ObjectId("5753bf28aeca16bc0382fc14"),
  "name": "Fraxure",
  "description": "Bixo feio pra caralho que tem dois chifes na boca",
  "type": "Dragon",
  "attack": 70,
  "defense": 43,
  "height": 1
}
{
  "_id": ObjectId("5753bf28aeca16bc0382fc15"),
  "name": "Drifloon",
  "description": "Bixo meio fofo, mas meio diabólico. Não tem boca",
  "type": "Ghost",
  "attack": 35,
  "defense": 23,
  "height": 0.4
}
{
  "_id": ObjectId("5753bf28aeca16bc0382fc16"),
  "name": "Croconaw",
  "description": "Tem moicano de Punk",
  "type": "Water",
  "attack": 49,
  "defense": 32,
  "height": 1.1
}
{
  "_id": ObjectId("5753bf28aeca16bc0382fc17"),
  "name": "Furfrou",
  "description": "Poodle de madame com cara de drogado",
  "type": "Normal",
  "attack": 47,
  "defense": 38,
  "height": 1.2
}
{
  "_id": ObjectId("5753bf28aeca16bc0382fc18"),
  "name": "Scizor",
  "description": "Parece uma mistura de carangueijo com robô",
  "type": "Bug",
  "attack": 78,
  "defense": 52,
  "height": 1.8
}
Fetched 5 record(s) in 5ms
njinga(mongod-3.2.6) be-mean-pokemon> 
```

### 6. Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada `poke`
```
njinga(mongod-3.2.6) be-mean-pokemon> var query = {name: 'Furfrou'}
njinga(mongod-3.2.6) be-mean-pokemon> var p = db.pokemons.findOne(query)
njinga(mongod-3.2.6) be-mean-pokemon> p
{
  "_id": ObjectId("5753bf28aeca16bc0382fc17"),
  "name": "Furfrou",
  "description": "Poodle de madame com cara de drogado",
  "type": "Normal",
  "attack": 47,
  "defense": 38,
  "height": 1.2
}
njinga(mongod-3.2.6) be-mean-pokemon> 
```

### 7. Modifique sua `description` e salvê-o
```
njinga(mongod-3.2.6) be-mean-pokemon> p.description = "Muda description"
Muda description
njinga(mongod-3.2.6) be-mean-pokemon> db.pokemons.save(p)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
njinga(mongod-3.2.6) be-mean-pokemon> 
```