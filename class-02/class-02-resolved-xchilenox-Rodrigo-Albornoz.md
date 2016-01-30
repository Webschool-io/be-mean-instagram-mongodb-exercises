# MongoDB - Aula 02 - Exercício
Autor: Rodrigo Albornoz

## Criando DB (passo 1)
```
ubuntu-vm(mongod-3.0.9) test> use be-mean-pokemons
switched to db be-mean-pokemons
```

## Listando databases (passo 2)
```
ubuntu-vm(mongod-3.0.9) be-mean-pokemons> show dbs
local             → 0.078GB
be-mean-instagram → 0.078GB
```

## Listando coleções (passo 3)
```
ubuntu-vm(mongod-3.0.9) be-mean-pokemons> show collections
system.indexes → 0.000MB / 0.008MB
```

## Inserindo pokemons (passo 4)
```
ubuntu-vm(mongod-3.0.9) be-mean-pokemons> var pokemons = [
    {
        name: "Chuck Norris",
        description: "Foda-se a lógica.",
        type: "God",
        attack: 1000,
        defense: 1000,
        height: 1000
    },
    {
        name: "Misdreavus",
        description: "Não faço a mínima ideia.",
        type: "Ghost",
        attack: 60,
        defense: 60,
        height: 7
    },
    {
        name: "Vivillon",
        description: "Borboleta tosca.",
        type: "Bug",
        attack: 52,
        defense: 50,
        height: 0
    },
    {
        name: "Mudkip",
        description: "Bicho que tem um rabo na  cabeça.",
        type: "Water",
        attack: 70,
        defense: 50,
        height: 4
    },
    {
        name: "Mewtwo",
        description: "Esse é foda memo!!!",
        type: "Psychic",
        attack: 110,
        defense: 90,
        height: 20
    }
];
ubuntu-vm(mongod-3.0.9) be-mean-pokemons> db.pokemons.insert(pokemons);
Inserted 1 record(s) in 251ms
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

## Listando pokemons (passo 5)
```
ubuntu-vm(mongod-3.0.9) be-mean-pokemons> db.pokemons.find();
{
  "_id": ObjectId("56acfb586a47c323fd9dadb9"),
  "name": "Chuck Norris",
  "description": "Foda-se a lógica.",
  "type": "God",
  "attack": 1000,
  "defense": 1000,
  "height": 1000
}
{
  "_id": ObjectId("56acfb586a47c323fd9dadba"),
  "name": "Misdreavus",
  "description": "Não faço a mínima ideia.",
  "type": "Ghost",
  "attack": 60,
  "defense": 60,
  "height": 7
}
{
  "_id": ObjectId("56acfb586a47c323fd9dadbb"),
  "name": "Vivillon",
  "description": "Borboleta tosca.",
  "type": "Bug",
  "attack": 52,
  "defense": 50,
  "height": 0
}
{
  "_id": ObjectId("56acfb586a47c323fd9dadbc"),
  "name": "Mudkip",
  "description": "Bicho que tem um rabo na  cabeça.",
  "type": "Water",
  "attack": 70,
  "defense": 50,
  "height": 4
}
{
  "_id": ObjectId("56acfb586a47c323fd9dadbd"),
  "name": "Mewtwo",
  "description": "Esse é foda memo!!!",
  "type": "Psychic",
  "attack": 110,
  "defense": 90,
  "height": 20
}
Fetched 5 record(s) in 15ms
```

## Consultando um pokemon (passo 6)
```
ubuntu-vm(mongod-3.0.9) be-mean-pokemons> var query = {name: 'Chuck Norris'};
ubuntu-vm(mongod-3.0.9) be-mean-pokemons> var p = db.pokemons.findOne(query);
ubuntu-vm(mongod-3.0.9) be-mean-pokemons> p
{
  "_id": ObjectId("56acfb586a47c323fd9dadb9"),
  "name": "Chuck Norris",
  "description": "Foda-se a lógica.",
  "type": "God",
  "attack": 1000,
  "defense": 1000,
  "height": 1000
}
```

## Alterando descrição do pokemon (passo 7)
```
ubuntu-vm(mongod-3.0.9) be-mean-pokemons> p.description = 'Criatura lendária';
Criatura lendária
ubuntu-vm(mongod-3.0.9) be-mean-pokemons> db.pokemons.save(p);
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
ubuntu-vm(mongod-3.0.9) be-mean-pokemons> p
{
  "_id": ObjectId("56acfb586a47c323fd9dadb9"),
  "name": "Chuck Norris",
  "description": "Criatura lendária",
  "type": "God",
  "attack": 1000,
  "defense": 1000,
  "height": 1000
}

```
