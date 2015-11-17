# Artigo
autor: Jean Martins Rito
github: http://github.com/rito

Quando recebi o desafio de escrever este artigo, a princípio torci o nariz. Se estou fazendo um curso, em tese precisaria receber a teoria e depois fazer os exercícios propostos daquele conteúdo. Legal, estava tranquilo, até surgir o desafio de escrever o artigo. Como fazer um artigo, com conceitos técnicos que não vi, e que não domino?

Legal, Bora escrever de um jeito que eu mesmo consiga entender, visto que muita informação existente na internet, são de técnicos, extremamente técnicos, que escrevem para outros técnicos, e se esquecem que nem todos entendem do que estão falando.
Um item não entendido, ou mal explicado, pode confundir ainda mais, e até fazer pensar que a linguagem é muito complicado, ou que a pessoa nunca entenderá programação. Será que este tabu realmente é verdade?

Desafio Aceito!!!


### Hoisting

Hoist em inglês significa levantar ou suspender algo através de um aparato mecânico. Em bom português, significa usar o guindaste para elevar um objeto. E é isto o que acontece em JavaScript quando declaramos uma variável ou função. Sua declaração é “elevada” para o topo do escopo.

Em outras palavras, esta "Elevação" nada mais é que trazer para o início do escopo a declaração de variáveis e funções.

Vamos usar um exemplo onde você queira usar uma função para juntar 2 palavras:

```
juntarPalavras("guarda", "chuva");
```

Se pensarmos numa linguagem interpretada, que vá executando o código conforme vai "lendo", linha a linha, ao chegar nesta função, teremos um erro, pois esta função não foi definida ainda, é como se você estivesse tentando executar algo que ainda não existe!

Declarar funções no início do programa resolveu o problema por um tempo, pois todas as funções e variáveis eram declaradas antes de serem usadas, sendo assim não se tinha erros de referência.

E para que isto não ocorra, é onde surgiu o conceito de Hosting no Javascript, com o tempo pensaram em uma maneira mais amigável e fácil de ler. Por que não deixar as definições em qualquer lugar do código, e usá-las em qualquer lugar que queira? Agora, os compiladores ou até mesmo linguagens runtime leem todo o programa para saber que funções e variáveis você declarou no código. Após isso, a execução real acontece e ele já sabe onde está cada coisa. JavaScript faz exatamente isso. Isto é Hoisting!!!

Vamos a alguns exemplos:

```
> nome = 'Jean';
> console.log(nome);
Jean
>
```


Até aqui tranquilo, vamos mudar um pouco as coisas:

```
> var nome = meunome;
> console.log(nome);
undefined
//ReferenceError: meunome is not defined
```
Seguindo o conceito explicado acima, como vamos atribuir nome, com o valor de meunome se esta variável não existe?

Agora mudando um pouco:

```

> var meunome;
> console.log(nome);
> var nome = meunome;
undefined
>
```

Agora apresentou UNDEFINED!!!

Isso acontece porque o JavaScript não obriga você a declarar variáveis, permite que você defina as funções em qualquer lugar que você queira, o que lhe permite usar uma função antes de sua definição. O nome hoisting, elevação ou até mesmo içamento, é só um termo especificado, pois ele arranca as declarações até o topo do seu escopo.

Agora o que ficou confuso é a questão da declaração e a inicialização!!!

Declarar a variável meunome:
```
> var meunome;
undefined
>
```

Agora o que é iniciar o conteúdo Jean:

```
> meunome = 'Jean';
'Jean'
>
```

Agora com uma função:
```
console.log(multiplicaNumero(10,10));
var multiplicaNumero = function(a,b) {
  return a*b;
}

//TypeError: undefined is not a function

```
Ele elevou a declaração var multiplicaNumero, mas como chamamos antes de ele ser iniciado recebemos um erro.

E agora se mudarmos para isto:
```
console.log(multiplicaNumero(10,10));
multiplicaNumero = function(a,b) {
  return a*b;
}


//ReferenceError: multiplicaNumero is not defined

```
Nesse caso, o erro foi que o multiplicaNumero não foi declarado!

E agora se transformarmos em uma função?? (Não sei por que, mas isso me lembrou do JavaScript Funcional!!!!)

```
console.log(multiplicaNumero(10,10));
function multiplicaNumero (a,b) {
  return a*b;
}

//100
```

TADA!!!!

Agora o código executou sem erro porque toda declaração de função não anônima é elevada para o topo do escopo.

Com isso aprendemos que é uma boa prática declarar e/ou iniciar variáveis e funções no início do escopo. E outra, utilizarmos funções não anônimas, e utilizando sempre o conceito de reaproveitamento! :)

Acho que ficou um pouco mais claro pra mim. E pra você?


### Closure

Agora tentar explicar de uma maneira mais clara o que é Closure...!

"Closures (fechamentos) são funções que se referem a variáveis livres (independentes)."

Show!!! #SQN
Que porra é essa?

Em outras palavras, a função definida no closure "lembra" do ambiente em que ela foi criada.

Quase... Dá pra ser mais claro?

Vamos ver se melhora com um pouco de prática pra tirarmos novas conclusões:

```
function init() {
  var name = "Rito";
  function displayName() {
    console.log(name);
  }
  displayName();
}
init();


//Rito
```

A função init() cria uma variável local chamada name, e depois define uma função chamada displayName().

displayName() é uma função aninhada (um closure) — ela é definida dentro da função init(), e está disponivel apenas dentro do corpo daquela função.
Diferente de init(), displayName() não tem variáveis locais próprias, e ao invés disso reusa a variável name declarada na função pai.

Este é um exemplo de  escopo léxico : em JavaScript, o escopo de uma variável é definido por sua localização dentro do código fonte (isto é aparentemente  léxico ) e funções aninhadas têm acesso às variáveis declaradas em seu escopo externo.

Agora outro exemplo:

```
function makeAdder(x) {
  return function(y) {
    return x + y;
  };
}

var add5 = makeAdder(5);
var add10 = makeAdder(10);

console.log(add5(2));  
console.log(add10(2));





//7
//12
```

Neste exemplo definimos a função makeAdder(x) que toma um único argumento x e retorno uma nova função. A função retornada toma então um único argumento, y, e retorna então a soma de x e de y.

Na essência o makeAdder trata-se de uma função fábrica - irá construir outras funções que podem adicionar um determinado valor específico a seu argumento. No exemplo acima usamos a fábrica de funções para criar duas novas funções - uma que adiciona 5 ao argumento, e outra que adiciona 10.

Ambas as funções add5 e add10   são closures. Compartilham o mesmo corpo de definição de função mas armazenam diferentes ambientes. No ambiente da add5, por exemplo, x equivale a 5, enquanto na add10 o valor de x é 10.

Esta é a teoria — mas closures são realmente úteis? Vamos considerar suas aplicações práticas. Uma closure deixa você associar dados (do ambiente) com uma função que trabalha estes dados. Isto está diretamente ligado com programação orientada a objetos, onde objetos nos permitem associar dados (as propriedades do objeto) utilizando um ou mais métodos.

Consequentemente, você pode utilizar uma closure em qualquer lugar onde você normalmente utilizaria um objeto de único método.

Situações onde você poderia utilizar isto são comuns em ambientes web. Muitos códigos escrito em JavaScript para web são baseados em eventos - nós definimos algum comportamento e então, o atribuimos a um evento que será disparado pelo usuário (quando uma tecla for pressionada, por exemplo). Nosso código normalmente é utilizado como callback: uma função que será executada como resposta ao evento.

Um exemplo prático: suponha que queremos adicionar alguns botões para ajustar o tamanho do texto de uma página. Um jeito de fazer seria especificar o tamanho da fonte no elemento body e então definir o tamanho dos outros elementos da página (os cabeçalhos, por exemplo) utilizando a unidade relativa em:

```
body {
  font-family: Helvetica, Arial, sans-serif;
  font-size: 12px;
}

h1 {
  font-size: 1.5em;
}
h2 {
  font-size: 1.2em;
}
```

Nossos botões interativos de tamanho de texto podem alterar a propriedade font-size do elemento body, e os ajustes serão refletidos em outros elementos graças à unidade relativa.

O código JavaScript:

```
function makeSizer(size) {
  return function() {
    document.body.style.fontSize = size + 'px';
  };
}

var size12 = makeSizer(12);
var size14 = makeSizer(14);
var size16 = makeSizer(16);
```

size12, size14 e size16 agora são funções que devem redimensionar o texto do elemento body para 12.14 e 16 pixels respectivamente. Nós podemos designá-las à botões (neste caso, links) como feito a seguir:

```
document.getElementById('size-12').onclick = size12;
document.getElementById('size-14').onclick = size14;
document.getElementById('size-16').onclick = size16;
```

```
<a href="#" id="size-12">12</a>
<a href="#" id="size-14">14</a>
<a href="#" id="size-16">16</a>
```

Entendido?

### Variável Global

Todas as variáveis declaradas fora de uma função estão no escopo global.
Qualquer variável declarada ou inicializada fora de uma função é uma variável global, e estará portanto disponível para toda a aplicação. Por exemplo:

```
var myName = "Jean";
```

ou
```
firstName = "Richard";
```
ou
```
var name;
name;
```

Se uma variável é inicializada (atribuída com um valor) sem primeiro ser declarada com a palavra chave var, ela é automaticamente adicionada ao contexto global sendo assim portanto uma variável global:

```
function showAge() {
    //age é uma variável global porque ela não foi declarada com a palavra chave var dentro da função
    age = 90;
    console.log(age);
}

showAge();


//age está no contexto global, então está disponível aqui, também
console.log(age);


//90
//90
```

Demonstração de variáveis que estão no Escopo Global mesmo que pareça o contrário:

```
//Ambas variáveis firstName estão no escopo global, mesmo que a segunda esteja dentro do bloco {}
var firstName = "Jean";
{
    var firstName = "Rito";
}

//Para reiterar: JavaScript não tem escopo por nível de bloco
//A segunda declaração ou firstName simplesmente redeclara e sobrescreve a primeira

console.log (firstName);


//Rito
```



### Variável por parâmetro

Explique o que acontece dentro da função qnd um parâmetro é passado e também explique quando uma GLOBAL é passada por parâmetro.

### Instanciação usando uma IIFE

Explique como uma variável pode receber um valor de uma IIFE. Explique como passar uma variável por parâmetro para a IIFE e acontece com ela dentro da função.

Considerações

Quanto mais explicado melhor.

Lembre que isso fará parte do seu currículo como aluno e será disponilizado no sistema de vagas, ou seja, o contratante poderá ver todos seus projetos e trabalhos feitos nesse curso.

Boa sorte.



### Referências Bibliográficas
http://tableless.com.br/elevacao-ou-javascript-hoisting/
http://loopinfinito.com.br/2014/10/29/hoisting-e-escopo-em-javascript/
https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Guide/Closures
http://javascriptbrasil.com/2013/10/11/escopo-de-variavel-e-hoisting-no-javascript-explicado/
