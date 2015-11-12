# Artigo
**autor**: Rodrigo Alves Guerra

**Prazo**: até dia 18 de Novembro de 2015

Explique, com teoria e código, nesse artigo como o JavaScript cria e instancia as variáveis, seguindo os seguintes tópicos.

## Hoisting

Explique o que é, o porquê acontece e como acontece com variável e função.

Tendo em vista que as variáveis são processadas antes que o código seja executado, 
e são movidas para o inicio da função ou do código global.
Declarar uma variável em qualquer parte do seu código é equivalente a declarar no início.
Até mesmo é possível utilizar uma variável antes dela ser declarada.

Ex.

var x;

x = 4;

y = 3;

alert(x + y); 

var y;

// È o mesmo que !

var x;
var y;

x = 4;

y = 3;

alert(x + y); 

Referência .: https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/var

## Closure

Explique o que é, o porquê acontece e como usar. 
Cite situações que você usaria.

## Variável Global

Explique como se usa uma var Global dentro de uma função.

## Variável por parâmetro

Explique o que acontece dentro da função qnd um parâmetro é passado e também explique quando uma GLOBAL é passada por parâmetro.


## Instanciação usando uma IIFE

Explique como uma variável pode receber um valor de uma IIFE.
Explique como passar uma variável por parâmetro para a IIFE e acontece com ela dentro da função.


## Considerações

Quanto mais explicado melhor.

Lembre que isso fará parte do seu currículo como aluno e será disponilizado no sistema de vagas, ou seja, o contratante poderá ver todos seus projetos e trabalhos feitos nesse curso.

Boa sorte.

# Envio

1. Fork [esse repositório](https://github.com/Webschool-io/be-mean-instagram-artigos/) 
2. Nomeie seu artigo usando o seguinte padrão: artigo-instanciacao-githubuser-nome-completo.md
3. Adicione seu exercício aqui na Pasta Variables
4. Faça um Pull Requst enviando seu artigo.
