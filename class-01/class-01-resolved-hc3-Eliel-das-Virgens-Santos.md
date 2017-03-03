MongoDB - Aula01 - Exercício

Autor : Eliel das Virgens

# Importando os restaurantes

```
hc3@darkSide:~/be-mean-mongodb-exercicios/aula01$ mongoimport --db be-mean-restaurantes --collection restaurantes --drop --file restaurantes.json 
connected to: 127.0.0.1
2016-02-07T10:03:28.894-0300 dropping: be-mean-restaurantes.restaurantes
2016-02-07T10:03:30.005-0300 check 9 25359
2016-02-07T10:03:30.059-0300 imported 25359 objects
```

# Contando os restaurantes

```
darkSide(mongod-2.6.3) be-mean-restaurantes> db.restaurantes.find({}).count()
25359
```
