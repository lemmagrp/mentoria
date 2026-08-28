# Linguagens formais

Linguagens formais são linguagens artificiais, incrivelmente mais simples que a linguagem natural e com menor expressividade. Em contrapartida, são significativamente mais precisas para propósitos lógicos e matemáticos.

Uma linguagem formal é construída a partir de dois elementos fundamentais:
-   Alfabeto: um conjunto de símbolos primitivos.
-   Regras de formação: regras que permitem construir fórmulas a partir desses símbolos, distinguindo enunciados sintaticamente corretos dos incorretos.

As regras de formação nos permitem distinguir um enunciado sintaticamente correto na linguagem de um enunciado sintaticamente incorreto. Logo, pode-se dizer que as regras de formação são a "gramática" de uma linguagem formal.

O cálculo proposicional é um exemplo de linguagem formal. Seus símbolos são organizados em três categorias:

Símbolos lógicos
L={¬,∧,∨,→,↔}

Símbolos não-lógicos (variáveis proposicionais)
P={p,q,r,s,…}

Símbolos auxiliares
S={(,)}

# Computabilidade

Computabilidade é um conceito que se originou principalmente no século XX, com os trabalhos de Kurt Godel, Alonzo Church e Alan Turing. 

Inicialmente, a definição de algoritmo era uma noção informal e utilizada sem muitos problemas ao longo da história da matemática. Porém, no aspecto de fundamentação da matemática, a definição precisa do que é um algoritmo se tornou fundamental para a busca última de fundamentação completa, consistente e decidível da matemática, especificamente para o Entscheidungsproblem (problema da decisão): existe um procedimento mecânico capaz de decidir a verdade ou falsidade de qualquer enunciado matemático? Nesse aspecto, três propostas foram apresentadas, e todas elas são equivalentes.

A primeira proposta é a noção de recursidade, onde podemos definir computabilidade a partir de funções recursivas gerais, pois todas elas tem a característica de serem computáveis. Logo, podemos dizer que uma função é computável se e somente se existe uma função recursiva geral correspondente.

A segunda proposta é o cálculo lambda (λ-cálculo), desenvolvido por Alonzo Church. O cálculo lambda (λ-cálculo) representa toda função computável como uma abstração. É a base teórica das linguagens de programação funcionais.

A terceira proposta é a Máquina de Turing, desenvolvida por Alan Turing no mesmo ano. Uma Máquina de Turing é um modelo abstrato de computação composto por um conjunto finito de estados, uma fita infinita de leitura e escrita, e uma função de transição que dita seu comportamento a cada passo. Uma função é computável se e somente se existe uma Máquina de Turing capaz de calculá-la.

A equivalência entre as três propostas acima fundamenta Tese de Church-Turing:

> Toda função efetivamente computável no sentido intuitivo é computável por uma Máquina de Turing.


# Teoremas da Incompletude de Godel

Os Teoremas da Incompletude de Gödel são dois resultados fundamentais que revelam os limites intrínsecos dos sistemas formais. Para qualquer sistema formal suficientemente expressivo, capaz de conter a aritmética e representar todas as relações computáveis, tal sistema formal é incompleto. Ou seja, existe sempre uma sentença G (sentença de Godel), que é verdadeira, mas não pode ser demonstrada sintáticamente, ou seja, não possui prova.

O método de demonstração desses resultados utiliza-se de duas técnicas essenciais:

 - Numeração de Godel, ou Aritmetização da Sintaxe.
 - Lema da Diagonal, também chamado de Lema do Ponto Fixo.

Podemos utilizar os codificar fórmulas por meio dos números naturais. Existem algumas formas de fazer isso, sendo o teorema fundamental da aritmética, por meio de números primos, a forma mais utilizada.

Podemos codificar fórmulas usando números, e usar esses mesmos números em nossas próprias fórmulas construídas, criando uma forma que nos permite falar sobre as próprias sentenças.

Outro do teorema da incompletude se refere à impossibilidade de um sistema com essas propriedades de provar sua própria consistência. Ele conseguirá provar sua consistência, se e somente se, for inconsistente.

Abaixo, tem-se os devidos enunciados dos teoremas de Godel:

- Primeiro Teorema da Incompletude:Se F é um sistema formal consistente e suficientemente expressivo para conter a aritmética de Peano, então existe uma sentença G​ na linguagem de F tal que nem G nem ¬GF​ são demonstráveis em F.

- Segundo Teorema da Incompletude: Se F é um sistema formal consistente e satisfaz as condições do primeiro teorema, então a sentença que expressa a consistência de F, denotada Cons(F), não é demonstrável em F.
