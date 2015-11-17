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

'''
juntarPalavras("guarda", "chuva");
'''

Se pensarmos numa linguagem interpretada, que vá executando o código conforme vai "lendo", linha a linha, ao chegar nesta função, teremos um erro, pois esta função não foi definida ainda, é como se você estivesse tentando executar algo que ainda não existe!

Declarar funções no início do programa resolveu o problema por um tempo, pois todas as funções e variáveis eram declaradas antes de serem usadas, sendo assim não se tinha erros de referência.

E para que isto não ocorra, é onde surgiu o conceito de Hosting no Javascript, com o tempo pensaram em uma maneira mais amigável e fácil de ler. Por que não deixar as definições em qualquer lugar do código, e usá-las em qualquer lugar que queira? Agora, os compiladores ou até mesmo linguagens runtime leem todo o programa para saber que funções e variáveis você declarou no código. Após isso, a execução real acontece e ele já sabe onde está cada coisa. JavaScript faz exatamente isso. Isto é Hoisting!!!

Vamos a alguns exemplos:

'''
> nome = 'Jean';
> console.log(nome);
Jean
>

'''

Até aqui tranquilo, vamos mudar um pouco as coisas:

'''
> var nome = meunome;
> console.log(nome);
undefined
//ReferenceError: meunome is not defined
'''
Seguindo o conceito explicado acima, como vamos atribuir nome, com o valor de meunome se esta variável não existe?

Agora mudando um pouco:

'''

> var meunome;
> console.log(nome);
> var nome = meunome;
undefined
>
'''

Agora apresentou UNDEFINED!!!

Isso acontece porque o JavaScript não obriga você a declarar variáveis, permite que você defina as funções em qualquer lugar que você queira, o que lhe permite usar uma função antes de sua definição. O nome hoisting, elevação ou até mesmo içamento, é só um termo especificado, pois ele arranca as declarações até o topo do seu escopo.

Agora o que ficou confuso é a questão da declaração e a inicialização!!!

Declarar a variável meunome:
'''
> var meunome;
undefined
>
'''

Agora o que é iniciar o conteúdo Jean:

'''
> meunome = 'Jean';
'Jean'
>
'''

Agora com uma função:
'''
console.log(multiplicaNumero(10,10));
var multiplicaNumero = function(a,b) {
  return a*b;
}

//TypeError: undefined is not a function

'''
Ele elevou a declaração var multiplicaNumero, mas como chamamos antes de ele ser iniciado recebemos um erro.

E agora se mudarmos para isto:
'''
console.log(multiplicaNumero(10,10));
multiplicaNumero = function(a,b) {
  return a*b;
}


//ReferenceError: multiplicaNumero is not defined

'''
Nesse caso, o erro foi que o multiplicaNumero não foi declarado!

E agora se transformarmos em uma função?? (Não sei por que, mas isso me lembrou do JavaScript Funcional!!!!)

'''
console.log(multiplicaNumero(10,10));
function multiplicaNumero (a,b) {
  return a*b;
}

//100
'''

TADA!!!!

Agora o código executou sem erro porque toda declaração de função não anônima é elevada para o topo do escopo.

Com isso aprendemos que é uma boa prática declarar e/ou iniciar variáveis e funções no início do escopo. E outra, utilizarmos funções não anônimas, e utilizando sempre o conceito de reaproveitamento! :)






### Closure

Explique o que é, o porquê acontece e como usar. Cite situações que você usaria.

Variável Global

Explique como se usa uma var Global dentro de uma função.

Variável por parâmetro

Explique o que acontece dentro da função qnd um parâmetro é passado e também explique quando uma GLOBAL é passada por parâmetro.

Instanciação usando uma IIFE

Explique como uma variável pode receber um valor de uma IIFE. Explique como passar uma variável por parâmetro para a IIFE e acontece com ela dentro da função.

Considerações

Quanto mais explicado melhor.

Lembre que isso fará parte do seu currículo como aluno e será disponilizado no sistema de vagas, ou seja, o contratante poderá ver todos seus projetos e trabalhos feitos nesse curso.

Boa sorte.
