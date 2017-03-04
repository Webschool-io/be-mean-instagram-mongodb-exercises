# MongoDB - Aula 01 - Exercício
Autor: Oracy Martos

Be-mean


# Importando os restaurantes:

```
oracy@oracy-X555UB:~/Documentos/bemean/be-mean-instagram-mongodb! mongoimport --db bemean --collection restaurantes --drop --file data.json
2017-03-03T18:23:15.072-0300	connected to: localhost
2017-03-03T18:23:15.072-0300	dropping: bemean.restaurantes
2017-03-03T18:23:15.596-0300	imported 11282 documents
```

# Restaurantes importados

#Contando os restaurantes

```
oracy@oracy-X555UB:~/Documentos/be-mean-instagram-mongodb! mongo
MongoDB shell version: 2.6.10
connecting to: test
$ db.restaurantes.find({}).count()
0
$ use bemean
switched to db bemean
$ db.restaurantes.find({}).count()
11282
```

# Contagem feita