# Linguagens Formais

**Núcleo**. Uma linguagem formal é um conjunto de cadeias sobre um alfabeto, definido por regras matemáticas puramente sintáticas e desprovido de semântica (significado).

**Síntese**. Dado um alfabeto finito Σ, uma linguagem é qualquer subconjunto de Σ* (todas as cadeias possíveis). O interesse está em como descrever esses conjuntos finitamente: por gramáticas (regras que geram cadeias) ou por máquinas reconhecedoras (que determinam se uma cadeia pertence a uma linguagem). A correspondência entre o poder gerativo das gramáticas e o poder computacional das máquinas é o eixo central da teoria.

---
# Computabilidade

**Núcleo**. Há um limite para o que qualquer algoritmo pode resolver: existem problemas bem definidos que nenhum procedimento mecânico resolve, por mais tempo que se dê.

**Síntese**. Computabilidade estuda quais problemas admitem solução por algoritmo. A tese de Church-Turing identifica "algoritmo" com máquina de Turing (equivalente a funções recursivas e ao cálculo lambda). Um problema é decidível se há uma máquina que sempre para com sim ou não, e semidecidível se ela para apenas nos casos positivos. O problema da parada é o exemplo canônico de não decidível, e reduções transferem essa impossibilidade a outros problemas.

---
# Teoremas da Incompletude de Gödel

**Núcleo**. Todo sistema formal consistente e forte o bastante para expressar a aritmética contém afirmações verdadeiras que ele próprio não consegue provar.

**Síntese**. Uma teoria de primeira ordem efetivamente axiomatizável e capaz de expressar a aritmética não pode ser consistente e completa ao mesmo tempo. Se for consistente, deixa sentenças verdadeiras sem demonstração e portanto é incompleta. Se for completa, prova contradições e é inconsistente. A capacidade de representar aritmética implica essa escolha.

---
# Problema da Parada

**Núcleo**. Não existe algoritmo capaz de decidir, para todo programa e toda entrada, se aquele programa eventualmente para ou roda para sempre.

**Síntese**. O problema da parada pergunta se existe uma máquina de Turing H que, recebendo a descrição de um programa P e uma entrada x, decide corretamente se P(x) para. Turing (1936) provou que H não pode existir. A prova é por diagonalização: supondo H, constrói-se um programa que pergunta a H sobre si mesmo e faz o oposto da resposta, gerando contradição. Historicamente, foi um dos primeiros problemas provados indecidíveis, o que o torna relevante: ele mostrou que a computação tem limites intrínsecos, independentes de habilidade ou método.

Dois limites importantes emergem desse resultado:
- *A indecidibilidade não impede resolver casos específicos.* Para muitos programas concretos, dizer se param é trivial. *O que não existe é um procedimento único que funcione para todos.*
- *O problema é semidecidível*: pode-se confirmar a parada simplesmente executando, mas não confirmar o laço infinito em tempo finito.

---
# Apêndice
## Definições

**Tese de Church-Turing.** Uma função sobre os naturais pode ser calculada por um método efetivo se e somente se for computável por uma máquina de Turing.

**Computabilidade vs. Decidibilidade.** Computabilidade pergunta se uma função pode ser calculada por algum algoritmo. Decidibilidade é o caso particular em que a função responde sim ou não e o algoritmo sempre para. Decidir um conjunto é computar sua função característica com parada garantida.
---
## Desenvolvimento do Conceito de Computabilidade

O campo nasce na década de 1930, quando três pesquisadores formalizaram independentemente a noção de "calculável":
- **Turing**: máquinas de Turing
- **Church**: cálculo lambda
- **Kleene**: funções recursivas de Gödel-Herbrand

A coincidência dessas três definições, somada à ausência de qualquer modelo que as supere em poder, é a evidência empírica que suporta a tese de Church-Turing. 

A estrutura central separa dois níveis:
- **Conjuntos recursivos (decidíveis)**: têm função característica computável.
- **Conjuntos recursivamente enumeráveis (semidecidíveis)**: têm um reconhecedor que aceita os membros mas pode não parar nos não membros.

Um conjunto é decidível se e somente se ele e seu complemento são r.e. O problema da parada é r.e. mas não recursivo, o que torna seu complemento nem sequer r.e.

---
## Esboço das Demonstrações

### Problema da Parada
A demonstração formaliza um argumento autorreferente por contradição. Suponha que exista um decisor total H(P, x) que retorna "para" ou "não para". Defina D(P) a partir de H(P, P):
- Se H diz "para": D entra em laço infinito.
- Se H diz "não para": D para imediatamente.

Avaliando D(D):
- Se D(D) para, então H(D, D) disse "para", mas por construção D entra em laço; contradição.
- Se D(D) não para, então H(D, D) disse "não para", mas D para; contradição.

Logo H não pode existir.

### Teoremas de Incompletude de Gödel
Gödel codifica a sintaxe do sistema em números (numeração de Gödel), construindo uma sentença G que afirma de si mesma "eu não sou demonstrável". Se o sistema é consistente, G não pode ser provada nem refutada: está fora do alcance dedutivo, embora seja verdadeira. Esse é o primeiro teorema. O segundo decorre diretamente: o próprio argumento "se o sistema é consistente, então G é indemonstrável" pode ser formalizado dentro dele, portanto provar a própria consistência implicaria provar G, o que o primeiro teorema proíbe. Logo, tal sistema não consegue provar a própria consistência.