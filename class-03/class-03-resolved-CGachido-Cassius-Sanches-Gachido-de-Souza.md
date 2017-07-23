# MongoDB - Aula 03 - Exercício
autor: Cassius Sanches Gachido de Souza

## 1) Liste todos Pokemons com a altura menor que 0.5;
```
> use be-mean-pokemons
switched to db be-mean-pokemons
> var query = {'height':{$lt:0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("564271699d8b71065c81a8fc"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinha", "type" : "electrict", "attack" : 100, "height" : 0.4 }
{ "_id" : ObjectId("564272919d8b71065c81a8fd"), "name" : "Caterpie", "description" : "larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35 }
```

## 2) Liste todos Pokemons com a altura maior ou igual que 0.5;
```
> var query = {'height':{$gte:0.5}}
> db.pokemons.find(query)
{ "_id" : ObjectId("5642808e3d9018dc6050b58f"), "name" : "Mewtwo", "description" : "Because its battle abilities were raised to the ultimate level, it thinks only of de feating its foes.", "type" : "psychic", "attack" : 110, "defense" : 90, "height" : 20 }
{ "_id" : ObjectId("564280cf3d9018dc6050b590"), "name" : "Dragonite", "description" : "It can fly in spite of its big and bulky physique. It circles the globe in just 16 hours.", "type" : "dragon", "attack" : 134, "defense" : 95, "height" : 22 }
{ "_id" : ObjectId("564280d93d9018dc6050b591"), "name" : "Dragonair", "description" : "A mystical POKMON that exudes a gentle aura. Has the ability to change climate conditions.", "type" : "dragon", "attack" : 84, "defense" : 65, "height" : 40 }
{ "_id" : ObjectId("564280e03d9018dc6050b592"), "name" : "Swinub", "description" : "It loves eating mushrooms that grow under dead grass. It also finds hot springs while foraging.", "type" : "ice", "attack" : 50, "defense" : 40, "height" : 4 }
{ "_id" : ObjectId("564280e83d9018dc6050b593"), "name" : "Milotic", "description" : "\"Its said that a glimpse of a MILOTIC and its beauty will calm any hostile emotions youre feeling.", "type" : "water", "attack" : 60, "defense" : 79, "height" : 62 }
```

## 3) Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama;
```
> var query = {'height':{$lte:0.5}, $and:[{'type': 'grama'}]}
> db.pokemons.find(query)
```

## 4) Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5;
```
> var query = {$or:[{'name':'Pikachu'}, {attack: {$lte:0.5 }}]}
> db.pokemons.find(query)
{ "_id" : ObjectId("564271699d8b71065c81a8fc"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinha", "type" : "electrict", "attack" : 100, "height" : 0.4 }
>
```

## 5) Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5;
```
> var query = {$and:[ {attack: {$gte:48}},{'height':{$lte:0.5}}]}
> db.pokemons.find(query)
```