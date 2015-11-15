 # MongoDB - Aula 01 - Exercicio
 autor: William Dias Vargas

 ##Importando os restaurantes

 williamdias@HP:~/JetBrainsProjects/WebstormProjects/exercises$ mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json
 2015-11-13T14:06:56.089-0300	connected to: 127.0.0.1
 2015-11-13T14:06:56.090-0300	dropping: be-mean.restaurantes
 2015-11-13T14:06:58.666-0300	imported 25359 documents

 ##Contando os restaurantes

  db.restaurantes.find({}).count()
 25359
