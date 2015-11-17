# Artigo
**autor**: Michel Mattos

**Prazo**: até dia 18 de Novembro de 2015

Explique, com teoria e código, nesse artigo como o JavaScript cria e instancia as variáveis, seguindo os seguintes tópicos.

## Hoisting

Hoisting é uma característica do JavaScript onde as variáveis e funções estão disponíveis para todo o escopo onde foram declaradas, independente da ordem em que foram declaradas.

Vamos ver alguns exemplos.

```javascript
// hoisting_01.js
console.log(a); // Dispara um erro do tipo ReferenceError
```
```javascript
// hoisting_02.js
console.log(a); // Retorna undefined, e não mais um erro

var a;
```
No primeiro exemplo, um `ReferenceError` é disparado pois a variável `a` não foi declarada previamente. Isso pode ser solucionado colocando um `var a;` no início do arquivo, mas graças ao hoisting, essa declaração pode ficar em qualquer lugar *daquele escopo*.


```javascript
// hoisting_03.js
console.log(a); // Retorna undefined

var a = 1;
```
O código acima continua retornando `undefined`. O motivo é que apenas a declaração da variável fica disponível, e não a sua atribuição. Isso acontece porque o compilador javascript divide a declaração `var a = 1;` em duas: `var a;` e `a = 1;`. Então a variável `a` estará disponível para todo o escopo onde ela foi declarada, mas o valor só será atribuido à variável depois daquele ponto.


```javascript
// hoisting_04.js
log('Teste'); // Funciona

function log(texto) {
  console.log(texto);
}
```
```javascript
// hoisting_05.js
log('Teste'); // Não funciona, retorna TypeError

var log = function (texto) {
  console.log(texto);
}
```
Com funções, o funcionamento é o mesmo. O primeiro funciona porque a função é definida de forma *declarativa*. Porém, no segundo exemplo, um erro do tipo `TypeError` é retornado, pois apenas a declaração `log` com o valor inicial `undefined` está disponível naquele momento (por isso o erro do tipo `TypeError` é disparado, pois `undefined` não é uma `Function`).


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
