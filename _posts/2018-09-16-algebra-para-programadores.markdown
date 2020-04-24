---
layout: post
title:  "Álgebra para Programadores"
date:   2018-09-16 14:03:22 -0300
categories: math algebra programming
---
# Álgebra para Programadores

Agenda:
- História
- Conceitos Iniciais
    - Estruturas Algébricas
    - Axiomas Algébricos
- Semigrupos e Monoids
- Grupos e Anéis
- Referências
 

*Disclaimer: esse post introdutório e é baseado no livro "A Book of Abstract Algebra - Charles C. Pinter"[1] e nas experiências pessoais do autor.*

## História

Há um consenso entre os matemáticos e historiadores de que a Álgebra tem o seu marco inicial com o nosso querido Al Khwarizmi[2](780 - 850), matemático, astrônomo e mais um monte de coisa, que vivia em Bagdá. Nessa época a principal função da Álgebra era de encontrar métodos bem definidos para resolver equações do tipo ```ax + b = 0``` ou mesmo equações do segundo grau ```ax² + bx + c = 0```. Porém, foi somente no século XVI (era renascentista), na Itália, que métodos para resolver equações de terceiro, e até mesmo quarto graus, foram definidos. Vale a pena estudar a história de figuras como Tartaglia e Cardan, que foram os grandes nomes de suas épocas. Apesar de todo o avanço alcançado, ainda restavam dúvidas: *como resolver equações de grau 5, 6, ...?* Essa pergunta, entretanto, só foi respondida 200 anos depois por um matemático prodígio norueguês chamado Niels Abel. Abel mostrou que ***não existe uma fórmula para encontrar as raízes de equações de grau cinco ou superior***. Essa descoberta, portanto, põe um fim à era clássica da álgebra, como a ciência de resolver equações, e estabelece um limite para essas "técnicas". A partir desse momento, começam a surgir diversas "álgebras" que não tem relação com "resolver equações". Por isso, questões mais profundas e fundamentais a respeito das álgebras, que se estabelece como um ramo importante da Matemática, são feitas. Exemplos de álgebras que surgiram no séc. 19 foram a Álgebra de Matrizes e a Álgebra Booleana, que tem aplicações diversas como a eletrônica digital e computação. Algumas questões que surgiram foram:
- O que todas essas álgebras têm em comum?
- O que faz com que uma estrutura seja uma álgebra?


## Conceitos iniciais

*Disclaimer: o autor assume que o leitor tenha um conhecimento básico de Teoria dos Conjuntos.

### Estrutura Algébrica

Em termos gerais uma álgebra consiste em um *conjunto* (um conjunto de matrizes, um conjunto de números, etc) e uma ou mais operações sobre esse conjunto. Uma *operação* é uma simples maneira de combinar dois itens desse conjunto cujo resultado da operação ***é um elemento unívoco desse mesmo conjunto***. Essa, portanto, é a definição de estrutura álgebrica: um conjunto com uma ou mais operações definidas sobre o mesmo. Qualquer estrutura que obedece essa definição é uma ***estrutura algébrica***. Um exemplo de estrutura algébrica é você pensar no conjunto de **todas as possíveis cores** e uma operação que mistura duas cores, produzindo uma nova cor. Geralmente, a estrutura algébrica é apresentada pela tupla ```⟨S,⊕⟩```, onde S é um conjunto e ⊕ é uma operação com as propriedades descritas acima. Quando temos uma operação que combina dois elementos de um conjunto e o resultado dessa operação pertence ao mesmo conjunto, dizemos que a operação é ***fechada*** naquele conjunto, ex.: se somarmos dois números Naturais, o resultado é outro número natural, portanto a soma é fechada no conjunto dos Naturais.

Em uma linguagem estaticamente tipada (fictícia) teríamos o seguinte:
```typescript
function combine(a: A, b: A): A { 
    // combine the two elements here 
}
```

### Axiomas Algébricos

A partir de agora vamos assumir que ```A``` é um conjunto qualquer e ```⊕``` é uma operação fechada nesse conjunto.

```a ⊕ b = b ⊕ a```

Se a equação acima for verdadeira para quaisquer dois elementos de ```a``` e ```b``` de ```A```, nós dizemos que a operação ```⊕``` é ***comutativa***. Ou seja, não importa a ordem da operação, o resultado será sempre o mesmo.

```a ⊕ (b ⊕ c) = (a ⊕ b) ⊕ c```

Se a equação acima for verdadeira para quaisquer três elementos ```a, b, c ∈ A```, nós dizemos que a operação é ***associativa***. Ou seja, nós podemos combinar três elementos (sem mudar a ordem) de maneiras diferentes e o resultado será o mesmo. Ex.: ```1 + (2 + 3) = (1 + 2) + 3```

Existem um elemento ```e``` em ```A```, tal que:

```e ⊕ a``` e ```a ⊕ e``` para todo ```a ∈ A```

Se tal elemento ```e``` existir em ```A```, nós o chamamos de ***elemento identidade*** para a operação ```⊕```. Ele também é conhecido como ***elemento neutro***. Ex.: o zero é o elemento neutro da soma pois: ```x + 0 = x```.

Para todo elemento ```a``` em ```A```, existe um elemento a<sup>-1</sup> (inverso), tal que:

a ⊕ a<sup>-1</sup> = ```e```  
a<sup>-1</sup> ⊕ a = ```e```

Se a equação acima for verdadeira, nós dizemos que o elemento a possui inverso com respeito à operação ⊕. A combinação de dois elementos inversos resulta no elemento neutro. Se considerarmos a estrutura ```⟨ℤ,+⟩```, ou seja, os Inteiros com soma, podemos ver que: ```1 + (-1) = 0```.

Vamos assumir agora que ```A``` tem uma segunda operação ```×```, além da ```⊕```:

```a × (b ⊕ c) = (a × b) ⊕ (a × c)```

Se a equação acima for verdadeira para quaisquer três elementos de A, dizemos que ```×``` é distributiva sobre ```⊕```

Esses são os ***axiomas algébricos*** mais comuns.

## Semigrupos e Monoids

São duas estruturas algébricas muito simples que tem relação com à programação de computadores.

### Semigrupo

Consiste em um conjunto S e uma operação fechada em S com as seguintes propriedades:
- Associatividade


### Monoid

Consiste em um Semigrupo com um elemento identidade. Você pode me perguntar, "é só isso?". Eu respondo: é!
Mas qual é a relação disso com o mundo real? Thats the question.

O Monoid representa uma espécie de acumulador, que parte de um elemento neutro (identidade) e "acumula valores" através de uma operação que junta dois elementos do mesmo tipo. Isso te lembra alguma operação? Como bom programador, você vai fazer a ligação do Monoid com a nossa querida função ***fold***, muitas vezes chamada de ***reduce***, que é responsável por "acumular" valores a partir de uma lista. Então os Monoids são naturalmente *foldable* e sua associatividade permite paralelizar as operações (map/reduce). Mais ainda, a definição de uma única função ```fold``` funcionará para todos os Monoids.


#### Exemplos

Seja ⊕ a operação concatenação. Ex.: ```"a" ⊕ "b" = "ab"```, ```[1,2] ⊕ [3,4] = [1,2,3,4]```
```<String, ⊕>```: Esse é um dos monoids mais comuns, O Conjunto das Strings pode ser representado pelo seu Tipo String, a operação é a de concatenação e o elemento neutro é a String vazia ```""```.

Vamos testar se a operação de concatenação obedece às regras do Monoid:
- Fechamento:
    - Se eu concatenar duas Strings, o resultado sempre será uma String
    - Checked
- Associatividade: 
    - ```"a" ⊕ ("b" ⊕ "c") == abc == ("a" ⊕ "b") ⊕ "c"``` ? 
    - ⊕ é associativa
- Elemento Identidade:
    - ```("" ⊕ "a") == "a" == ("a" ⊕ "")``` ?
    - Sim, ```""``` é o elemento neutro
Então essa estrutura algébrica formada por String e ⊕ formam, ou são, um Monoid.


```<List[A], ⊕>```: praticamente igual ao monoid anterior, com o elemento neutro sendo a lista vazia ```[]```

```<Bool, AND>```: Monoid Booleano com operador AND, novamente vamos testar as regras:
- Fechamento:
    - AND recebe dois valores booleanos e o seu resultado sempre é Verdadeiro ou Falso
    - Checked
- Associatividade:
    - ```a AND (b AND c) == (a AND b) AND c``` ? 
    - Checked
- Identidade do AND:
    - A identidade do AND é o valor True
    - ```True and True = True```
    - ```False and True = False```
    - Checked

Existe um Monoid de funções. Se uma função possui como domínio e contradomínio o mesmo conjunto/type, podemos formar um monoid cujo conjunto é o conjunto de TODAS as funções de ```A -> A``` com a operação de composição de funções. ```<A->A, ∘>``` forma um Monoid, vejamos:
- Fechamento:
    - A composição recebe duas funções e retorna uma outra função: Checked
- Associatividade:
    - A composição é sabidamente associativa.
- Identidade da composição:
    - A função identidade ```f(x)=x``` é a identidade da composição. 


## Conclusões

Os exemplos acima tem um cunho educacional, porém, eles servem para mostrar que, sem percebermos, essas estruturas matemáticas estão entranhadas nos códigos que produzimos ao longo da vida. Você pode se perguntar como esse conhecimento afetará no seu dia-a-dia de programador. A resposta é simples: não sei. Porém, ele pode te ajudar a identificar Monoids nos projetos que você trabalha e ganhar, "theorems for free", e uma estrutura ***foldable***. No mais, se um dia você se deparar com uma operação que junta dois elementos do seu domínio em um novo elemento desse mesmo domínio (componentes react, por ex.), provavelmente você estará lidando com um semigrupo (associatividade é necessária), e se possuir um elemento neutro, você terá um Monoid. Outro ponto importante é que essas estruturas fazem mais sentido quando estamos usando linguagens estaticamente tipadas, nas quais podemos expressar esses tipos de primeira e segunda ordem. De todo modo, os monoids existem mas estão implícitos nas linguagens dinamicamente tipadas. 


## Referências
1. A Book of Abstract Algebra. Charles C. Pinter - Dover Editora
2. https://www.famousscientists.org/muhammad-ibn-musa-al-khwarizmi/
