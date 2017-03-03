# MongoDB - Aula 01 - Exercício
Autor: Oracy Martos

Be-mean


# Importando os restaurantes:

oracy@oracy-X555UB:~/Documentos/be-mean-instagram-mongodb! mongoimport --db bemean --collection restaurantes --drop --file data.json

connected to: 127.0.0.1
2017-03-03T14:05:18.973-0300 dropping: bemean.restaurantes
exception:BSON representation of supplied JSON is too large: code FailedToParse: FailedToParse: Trailing number at end of input: offset:355 of:{"address": {"building": "80-08", "coord": [-73.789221, 40.726154], "street": "Surrey Place", "zipcode": "11432"}, "borough": "Queens", "cuisine": "Japanese", "grades": [{"date": {"$date": 1421020800000}, "grade": "A", "score": 11}, {"date": {"$date": 1385942400000}, "grade": "A", "score": 12}, {"date": {"$date": 1367020800000}, "grade": "A", "score": 1
2017-03-03T14:05:19.547-0300 check 9 11282
2017-03-03T14:05:19.547-0300 imported 11282 objects
encountered 1 error(s)

# Restaurantes importados

#Contando os restaurantes

oracy@oracy-X555UB:~/Documentos/be-mean-instagram-mongodb! mongo
MongoDB shell version: 2.6.10
connecting to: test
> db.restaurantes.find({}).count()
0
> use bemean
switched to db bemean
> db.restaurantes.find({}).count()
11282

# Contagem feita