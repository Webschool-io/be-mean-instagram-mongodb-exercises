# MongoDb - Aula -1 - Exercício

autor: Wellington Pinho

## Importando os restaurantes

'''
mongodbimport --db --be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json
connected to: 127.0.0.1
2016-10-02T03:47:52.686-0300 dropping: be-mean.restaurantes
2016-10-02T03:47:53.746-0300 check 9 25359
2016-10-02T03:47:53.830-0300 imported 25359 objects

'''

##Contando os restaurantes

'''
db.restaurantes.find({}).count()
25359
'''

