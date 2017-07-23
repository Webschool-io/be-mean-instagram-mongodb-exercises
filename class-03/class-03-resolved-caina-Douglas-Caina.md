# MongoDB - Aula 03 - Exercício
autor: Douglas Caina

## Listando menores que 0.5

    ```
db.pokemons.find({"height":{$lt:0.5}})
{ "_id" : ObjectId("564276f8732d8896c19164c1"), "name" : "Pikachu", "description" : "Raio amarelo", "attack" : 45, "defense" : 4, "height" : 0.3 }
{ "_id" : ObjectId("564276f8732d8896c19164c2"), "name" : "Charmander", "description" : "Dragonino", "attack" : 32, "defense" : 80, "height" : 0.4 }
{ "_id" : ObjectId("564276f8732d8896c19164c4"), "name" : "Jiglipuf", "description" : "Adormece tudo", "attack" : 99, "defense" : 2, "height" : 0.1 }
{ "_id" : ObjectId("564276f8732d8896c19164c5"), "name" : "Bullbassaur", "description" : "Plana legal", "attack" : 65, "defense" : 1, "height" : 0.3 }

    ```

## Maiores que 0.5

    ```
    > db.pokemons.find({"height":{$gte:0.5}})
{ "_id" : ObjectId("564276f8732d8896c19164c3"), "name" : "Squirtle", "description" : "Lider de torcida", "attack" : 25, "defense" : 4, "height" : 0.6 }



    ```

## Menores ou iguais a 0.5 e do tipo grama
    ```
db.pokemons.find({$and:[{"height":{$lte:0.5}},{'type':'grama'}]})

    ```

## Pokemons nome = Pikachu e ataque menor que 0.5
```
> db.pokemons.find({$or:[{"atack":{$lte:0.5}},{'name':'Pikachu'}]})
{ "_id" : ObjectId("564276f8732d8896c19164c1"), "name" : "Pikachu", "description" : "Raio amarelo", "attack" : 45, "defense" : 4, "height" : 0.3 }
> 
```

## Pokemons com ataque maior que 48 e altura maior que 0.5
```
db.pokemons.find({$and:[{"atack":{$gte:48}},{'height':{"&lte":0.5}}]})
```