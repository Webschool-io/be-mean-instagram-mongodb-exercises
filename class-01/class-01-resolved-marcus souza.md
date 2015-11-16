MongoDB - Aula 01 - Exercício
autor: Marcus Vinicius Silva de Souza

Importando os restaurantes

marcus@CSPDEV002 /c/Program Files/MongoDB/Server/3.0/bin
$ mongoimport --db be-mean --collection restarantes --host=127.0.0.1 --drop --file 'C:\Users\marcus\Desktop\Be Mean Ins
tagram\be-mean-instagram-mongodb\Excercises\restaurantes.json'
2015-11-16T12:30:52.508-0200    connected to: 127.0.0.1
2015-11-16T12:30:52.527-0200    dropping: be-mean.restarantes
2015-11-16T12:30:53.836-0200    imported 25359 documents

Contando os restaurantes

> db.restaurantes.find({}).count()
25359
