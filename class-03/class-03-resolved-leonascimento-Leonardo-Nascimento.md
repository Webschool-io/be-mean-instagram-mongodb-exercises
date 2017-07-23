### 1. Liste todos Pokemons com a altura menor que 0.5;

```JS
var query = { 
  height : { $lt : 0.5 } 
};

db.pokemons.find(query);

leonardo(mongod-2.6.10) be-mean> db.pokemons.find(query);
{
  "_id": ObjectId("564d2018fe74999fe47df509"),
  "name": "Pikachu",
  "description": "Rato elétrico",
  "type": "electric",
  "attack": 100,
  "height": 0.41
}
{
  "_id": ObjectId("564d2018fe74999fe47df50a"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 50
}
Fetched 2 record(s) in 2ms
```

### 2. Liste todos Pokemons com a altura maior ou igual que 0.5;

```JS
var query = { 
  height : { $gte : 0.5 } 
};

db.pokemons.find(query);

leonardo(mongod-2.6.10) be-mean> db.pokemons.find(query);
{
  "_id": ObjectId("564d1fcefe74999fe47df505"),
  "name": "Charizard",
  "description": "Dragão feroz",
  "type": "Flame",
  "attack": 40,
  "height": 1.7
}
{
  "_id": ObjectId("564d1fcefe74999fe47df506"),
  "name": "Pidgeot",
  "description": "This Pokémon has a dazzling plumage of beautifully glossy feathers",
  "type": "Bird",
  "attack": 40,
  "height": 1.5
}
{
  "_id": ObjectId("564d1fcefe74999fe47df507"),
  "name": "Raichu",
  "description": "If the electrical sacs become excessively charged, Raichu plants its tail in the ground and discharges.",
  "type": "Mouse",
  "attack": 50,
  "height": 0.8
}
{
  "_id": ObjectId("564d1fcefe74999fe47df508"),
  "name": "Arcanine",
  "description": "Arcanine is known for its high speed. It is said to be capable of running over 6,200 miles in a single day and night. ",
  "type": "Legendary",
  "attack": 60,
  "height": 1.9
}
Fetched 4 record(s) in 3ms
```

### 3. Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama;

```JS
var query = {
  $and: [
    {
      height: {
        $lte: 0.5
      }
    },
    {
      type: /grass/
    }
  ]
};

db.pokemons.find( query );

leonardo(mongod-2.6.10) be-mean> db.pokemons.find( query );
{
  "_id": ObjectId("564e6822551a5e3d2d6c54a4"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back",
  "type": "grass",
  "attack": 30,
  "height": 0.4
}
Fetched 1 record(s) in 1ms

```

### 4. Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5;

```JS
var query = { 
  $or : [
    { 
      attack : { 
        $lte : 0.5 
      }
    },
    { 
      name : /Pikachu/i 
    },
  ]
};

db.pokemons.find( query );

leonardo(mongod-2.6.10) be-mean> db.pokemons.find( query );
{
  "_id": ObjectId("564d2018fe74999fe47df509"),
  "name": "Pikachu",
  "description": "Rato elétrico",
  "type": "electric",
  "attack": 100,
  "height": 0.41
}
Fetched 1 record(s) in 77ms

```

### 5. Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5;

```JS
var query = { 
  $and : [
    { 
      attack : { 
        $gte : 48 
      } 
    },
    { 
      height : { 
        $lte : 0.5 
      } 
    } 
  ]
};

db.pokemons.find( query );

leonardo(mongod-2.6.10) be-mean> db.pokemons.find( query  );
{
  "_id": ObjectId("564d2018fe74999fe47df509"),
  "name": "Pikachu",
  "description": "Rato elétrico",
  "type": "electric",
  "attack": 100,
  "height": 0.41
}
Fetched 1 record(s) in 4ms
```
