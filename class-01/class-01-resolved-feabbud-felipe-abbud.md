# MongoDB - Aula 01 - Exercício
autor: Felipe Ricardo Silveira Abbud

## Importando os restaurantes

felipe@felipe-VPCEG13EB:~/be-mean-instagram-mongodb-excercises$  mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
connected to: 127.0.0.1
Sat Nov 21 18:09:14.437 dropping: be-mean.restaurantes
Sat Nov 21 18:09:15.376 check 9 25359
Sat Nov 21 18:09:15.400 imported 25359 objects



## Contando os restaurantes 
felipe@felipe-VPCEG13EB:~$ mongo
MongoDB shell version: 2.4.9
connecting to: test
> use be-mean
switched to db be-mean
> db.restaurantes.find({}).count()
25359

