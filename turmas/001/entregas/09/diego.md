# Gramáticas Formais
**Núcleo.** Uma gramática formal descreve de modo finito um conjunto de palavras que pode ser infinito.
Em lugar de enumerar a linguagem, fixam-se um símbolo inicial e um conjunto de regras de reescrita. A
linguagem é formada pelas palavras que se obtêm a partir do símbolo inicial e que não contêm mais nenhum
símbolo auxiliar.

**Síntese.** Fixado um alfabeto $A$, denotamos por $K(A) = A^*$ o fecho de Kleene de $A$, isto é, o
monoide livre sobre $A$. O comprimento $\mathrm{len}$ é o único morfismo de $K(A)$ em $(\mathbb{N}, +, 0)$
que leva cada letra em $1$, e escrevemos também $|w|$ para $\mathrm{len}(w)$. Para um conjunto finito $X$,
$|X|$ denota sua cardinalidade. Uma linguagem sobre $A$ é um subconjunto $L \subseteq K(A)$. Como $K(A)$ é
enumerável, o teorema de Cantor garante que $\mathcal{P}(K(A))$ não é. Já as gramáticas são objetos
finitos e formam um conjunto enumerável, de modo que quase nenhuma linguagem é gerada por uma gramática.
A hierarquia de Chomsky classifica as gramáticas segundo a forma de suas regras, e a cada nível
corresponde uma classe de máquinas.

## Regras de Reescrita
Uma gramática opera sobre o alfabeto $N \cup \Sigma$, em que $N$ é o conjunto das variáveis e $\Sigma$ o
dos terminais, e a linguagem que ela gera está contida em $K(\Sigma)$. Uma regra $\alpha \to \beta$, em que
$\alpha$ contém ao menos uma variável, permite reescrever $w_1 \alpha w_2$ como $w_1 \beta w_2$, o que se
denota $w_1 \alpha w_2 \Rightarrow w_1 \beta w_2$. Indicamos por $\Rightarrow^*$ o fecho reflexivo e
transitivo de $\Rightarrow$. A linguagem gerada é o conjunto das palavras $s \in K(\Sigma)$ tais que
$S \Rightarrow^* s$, isto é, das que se obtêm a partir da variável inicial $S \in N$ por um número finito
de reescritas.

Algumas observações evitam confusões comuns. Uma regra induz uma relação, e não uma função: com a regra
$X \to a$, a palavra $XX$ pode ser reescrita tanto como $aX$ quanto como $Xa$. Quando nenhuma regra se
aplica, a derivação simplesmente para, sem produzir a palavra vazia $\varepsilon$, que pertence à
linguagem somente se for derivável a partir de $S$. Por fim, as formas sentenciais intermediárias ainda contêm
variáveis, e apenas as que estão em $K(\Sigma)$ entram na linguagem.

Por exemplo, a gramática $S \to aSb \mid \varepsilon$ admite a derivação
$S \Rightarrow aSb \Rightarrow aaSbb \Rightarrow aabb$ e gera $\{a^n b^n : n \geq 0\}$.

## Hierarquia de Chomsky
A hierarquia distingue quatro tipos de gramática, conforme as restrições impostas às regras. A inclusão
entre os tipos vale apenas a menos da palavra vazia, pois o tipo 1 proíbe regras $X \to \varepsilon$, com
exceção de $S \to \varepsilon$.

### Tipo 3: gramáticas regulares
As regras têm a forma $X \to aY$, $X \to a$ ou $X \to \varepsilon$, com $X, Y \in N$ e $a \in \Sigma$. Cada
forma sentencial contém no máximo uma variável, sempre na última posição, e essa variável desempenha o
papel do estado de um autômato finito. As gramáticas lineares à esquerda, com regras $X \to Ya$, geram a
mesma classe. Misturar os dois tipos de regra, porém, pode levar para fora dela: a gramática
$S \to aT$, $T \to Sb \mid b$ gera $\{a^n b^n : n \geq 1\}$.

### Tipo 2: gramáticas livres de contexto
As regras têm a forma $X \to \beta$, com $X \in N$ e $\beta \in K(N \cup \Sigma)$. Como a reescrita de uma
variável não depende de seus vizinhos, toda derivação pode ser representada por uma árvore. Existem
linguagens inerentemente ambíguas, como
$\{a^n b^n c^m d^m\} \cup \{a^n b^m c^m d^n\}$ com $n, m \geq 1$. Para uma gramática na forma normal de
Chomsky, o algoritmo CYK decide a pertinência de uma palavra de comprimento $n$ em tempo $O(n^3)$.

### Tipo 1: gramáticas sensíveis ao contexto
As regras têm a forma $\lambda X \rho \to \lambda \gamma \rho$, com $X \in N$,
$\lambda, \rho, \gamma \in K(N \cup \Sigma)$ e $\gamma \neq \varepsilon$, admitindo-se ainda $S \to \varepsilon$
quando $S$ não ocorre no lado direito de nenhuma regra. Essas gramáticas geram a mesma classe que as
gramáticas não contráteis, cujas regras satisfazem $|\alpha| \leq |\beta|$, com a mesma exceção. A
linguagem $\{a^n b^n c^n : n \geq 1\}$, por exemplo, é gerada pela gramática não contrátil
$$
S \to aSBC \mid aBC, \quad CB \to BC, \quad aB \to ab, \quad bB \to bb, \quad bC \to bc, \quad cC \to cc.
$$
Como as formas sentenciais nunca diminuem de comprimento, para decidir se uma palavra de comprimento $n$
pertence à linguagem basta examinar as formas de comprimento no máximo $n$, que são em número finito.

### Tipo 0: gramáticas irrestritas
Não há restrição sobre as regras $\alpha \to \beta$. Como as formas sentenciais podem encolher, não existe
cota para o comprimento das formas intermediárias, e a pertinência é apenas semidecidível.

### Separando os níveis
O lema do bombeamento mostra que $\{a^n b^n\}$ não é regular, e sua versão para linguagens livres de
contexto mostra que $\{a^n b^n c^n\}$ não é livre de contexto. Os dois lemas fornecem apenas condições
necessárias. Para as linguagens regulares, uma caracterização completa é dada pelo teorema de
Myhill-Nerode. Acima do tipo 1, as separações vêm de argumentos diagonais. Enumerando as gramáticas
sensíveis ao contexto, constrói-se uma linguagem recursiva que nenhuma delas gera, e o problema da parada
é recursivamente enumerável mas não recursivo. Denotando por $\mathrm{Reg}$, $\mathrm{LC}$ e $\mathrm{SC}$
as classes das linguagens regulares, livres de contexto e sensíveis ao contexto, e por $\mathrm{Rec}$ e
$\mathrm{RE}$ as das linguagens recursivas e recursivamente enumeráveis, definidas na seção sobre
máquinas de Turing, obtém-se a cadeia de inclusões estritas
$$
\mathrm{Reg} \subsetneq \mathrm{LC} \subsetneq \mathrm{SC} \subsetneq \mathrm{Rec} \subsetneq \mathrm{RE}.
$$

---

# Autômatos
**Núcleo.** Um autômato é o correspondente reconhecedor de uma gramática. Em vez de gerar palavras, ele
lê uma palavra símbolo a símbolo e decide se ela pertence à linguagem. Os níveis da hierarquia se
distinguem pela memória de que o autômato dispõe durante a leitura.

**Síntese.** Num autômato finito determinístico com conjunto finito de estados $Q$, cada letra atua como
uma função $Q \to Q$. Assim como no
caso de $\mathrm{len}$, a propriedade universal de $K(A)$ estende essa ação a um morfismo $K(A) \to Q^Q$,
desde que a composição em $Q^Q$ siga a ordem de leitura. Segue que $L$ é regular se e somente se
$L = \varphi^{-1}(P)$ para algum morfismo $\varphi : K(A) \to M$ num monoide finito $M$ e algum
$P \subseteq M$. Os autômatos dos níveis superiores conservam o controle finito e acrescentam memória:
uma pilha, uma fita do tamanho da entrada ou uma fita ilimitada.

## Autômato finito
Num autômato finito não determinístico, a transição é uma função $\delta : Q \times A \to \mathcal{P}(Q)$,
e uma palavra é aceita quando algum caminho de computação termina num estado final. A construção dos
subconjuntos produz um autômato determinístico equivalente com no máximo $2^{|Q|}$ estados. Essa cota é
essencialmente atingida: as palavras sobre $\{a, b\}$ cujo $n$-ésimo símbolo contado a partir do fim é $a$
são reconhecidas por um autômato não determinístico com $n + 1$ estados, enquanto um determinístico
precisa de $2^n$. O não determinismo reduz, portanto, o tamanho do autômato sem alterar a classe
reconhecida, que é a das linguagens denotadas por expressões regulares.

Pelo teorema de Myhill-Nerode, se definimos $s \sim t$ quando $sw \in L \iff tw \in L$ para todo $w$, a
linguagem $L$ é regular se e somente se $\sim$ tem um número finito de classes, e esse número coincide com
o de estados do autômato determinístico mínimo. Em $\{a^k b^k\}$, as palavras $a^m$ e $a^n$ com $m \neq n$
são separadas por $b^n$, de modo que há infinitas classes.

## Autômato de pilha
Um autômato de pilha dispõe de memória ilimitada, mas tem acesso apenas ao topo da pilha. Os autômatos de
pilha não determinísticos reconhecem as linguagens livres de contexto, e a pilha acompanha uma derivação
mais à esquerda. Os determinísticos reconhecem uma classe estritamente menor. A linguagem dos palíndromos
de comprimento par $\{w w^R : w \in K(A)\}$, em que $w^R$ é a palavra $w$ lida de trás para frente e
$|A| \geq 2$, não é reconhecida por nenhum deles, pois seria
preciso adivinhar onde fica o meio da palavra.

## Autômato linearmente limitado
Um autômato linearmente limitado é uma máquina de Turing que não sai do trecho da fita ocupado pela
entrada. A versão não determinística reconhece as linguagens sensíveis ao contexto, e a determinística
reconhece uma subclasse delas. Sejam $\mathrm{DSPACE}(n)$ e $\mathrm{NSPACE}(n)$ as classes das
linguagens decididas por máquinas de Turing determinísticas e não determinísticas, respectivamente, em
espaço linear no comprimento da entrada. Decidir se as duas classes de autômatos reconhecem as mesmas
linguagens equivale a decidir se $\mathrm{DSPACE}(n) = \mathrm{NSPACE}(n)$, problema que continua em
aberto. Quando a gramática também faz parte da entrada, a pertinência para gramáticas sensíveis ao
contexto é PSPACE-completa, em que PSPACE é a classe dos problemas decidíveis em espaço polinomial.

## Máquina de Turing
Uma máquina de Turing dispõe de uma fita ilimitada, na qual lê e escreve movendo-se nos dois sentidos.
Com ou sem não determinismo, as máquinas de Turing reconhecem as linguagens recursivamente enumeráveis.
As linguagens recursivas são as reconhecidas por máquinas que param em toda entrada. O problema da parada
separa as duas classes por um argumento diagonal, no espírito de Cantor e de Russell: um decisor
hipotético para a parada, aplicado à sua própria descrição, leva a uma contradição.

## Comparação

| Tipo | Forma das regras | Autômato | Memória | Determinismo | Pertinência | Complemento |
|---|---|---|---|---|---|---|
| **3, regular** | $X \to aY \mid a \mid \varepsilon$ | Finito | Apenas o estado | Não altera a classe | Decidível em tempo linear | Fechada |
| **2, livre de contexto** | $X \to \beta$ | De pilha | Pilha, acesso ao topo | Altera a classe | Decidível em $O(n^3)$ | Não fechada |
| **1, sensível ao contexto** | $\lambda X \rho \to \lambda \gamma \rho$, $\gamma \neq \varepsilon$ | Linearmente limitado | Fita do tamanho da entrada | Problema em aberto | Decidível, PSPACE-completo em geral | Fechada |
| **0, irrestrita** | $\alpha \to \beta$ | Máquina de Turing | Fita ilimitada | Não altera a classe | Apenas semidecidível | Não fechada |

---

# Definições

## Palavras e linguagens

**Alfabeto.** Um conjunto finito e não vazio $A$, cujos elementos são chamados símbolos ou letras.

**Monoide.** Uma terna $(M, \cdot, e)$ em que $\cdot$ é uma operação associativa e $e$ é seu elemento
neutro. Um morfismo de $(M, \cdot, e)$ em $(M', \cdot, e')$ é uma função $h : M \to M'$ que satisfaz $h(x \cdot y) = h(x) \cdot h(y)$ e $h(e) = e'$.

**Monoide livre.** Um monoide $F$ munido de $\iota : A \to F$ tal que toda função $f : A \to M$ num monoide
$M$ se estende a um único morfismo $\bar f : F \to M$ com $\bar f \circ \iota = f$. O monoide livre é único a
menos de isomorfismo e pode ser construído como $K(A) = \bigcup_{n \in \mathbb{N}} A^n$ com a
concatenação. Os elementos de $A^n$ são as palavras de comprimento $n$, e $\varepsilon$ é a única palavra de
comprimento $0$. Identificamos cada letra $a$ com $\iota(a)$.

**Linguagem.** Um subconjunto $L \subseteq K(A)$. Sobre linguagens consideram-se a união, a concatenação
$L_1 L_2 = \{st : s \in L_1, t \in L_2\}$ e o fecho $L^* = \bigcup_n L^n$, em que $L^0 = \{\varepsilon\}$ e
$L^{n+1} = L^n L$.

**Expressão regular.** Um termo construído a partir de $\emptyset$, $\varepsilon$ e das letras $a \in A$
por união, concatenação e fecho, interpretado pelas operações correspondentes sobre linguagens. As
linguagens denotadas por expressões regulares são exatamente as regulares.

## Gramáticas

**Gramática.** Uma quádrupla $G = (N, \Sigma, P, S)$ em que $N$ e $\Sigma$ são conjuntos finitos e
disjuntos, $P$ é um conjunto finito de regras $\alpha \to \beta$ com $\alpha, \beta \in K(N \cup \Sigma)$ e
$\alpha$ contendo ao menos uma variável, e $S \in N$. Os tipos de 0 a 3 foram descritos na seção sobre a
hierarquia de Chomsky, e $\mathrm{Reg}$, $\mathrm{LC}$ e $\mathrm{SC}$ denotam as classes de linguagens
geradas pelos tipos 3, 2 e 1.

**Derivação.** Escrevemos $w_1 \alpha w_2 \Rightarrow w_1 \beta w_2$ sempre que $\alpha \to \beta \in P$, e
denotamos por $\Rightarrow^*$ o fecho reflexivo e transitivo dessa relação.

**Forma sentencial.** Uma palavra $u \in K(N \cup \Sigma)$ tal que $S \Rightarrow^* u$.

**Linguagem gerada.** $L(G) = \{ s \in K(\Sigma) : S \Rightarrow^* s \}$.

**Derivação mais à esquerda.** Uma derivação em que cada passo reescreve a variável mais à esquerda.

**Árvore de derivação.** Uma árvore ordenada com raiz $S$, cujos nós internos são rotulados por variáveis
e cujas folhas são rotuladas por terminais ou por $\varepsilon$, de modo que os filhos de cada nó $X$
formam, em ordem, o lado direito de uma regra $X \to \beta$. As árvores de derivação estão em bijeção com
as derivações mais à esquerda.

**Ambiguidade.** Uma gramática livre de contexto é ambígua se alguma palavra admite duas árvores de
derivação distintas. Uma linguagem é inerentemente ambígua se toda gramática livre de contexto que a gera
é ambígua.

**Forma normal de Chomsky.** Uma gramática livre de contexto cujas regras têm a forma $X \to YZ$ ou
$X \to a$.

## Autômatos

**Autômato finito determinístico.** Uma quíntupla $(Q, A, \delta, q_0, F)$ em que $Q$ é o conjunto finito
de estados, $\delta : Q \times A \to Q$ é a função de transição, $q_0 \in Q$ é o estado inicial e
$F \subseteq Q$ é o conjunto de estados finais. O autômato aceita $s$ quando
$\hat\delta(q_0, s) \in F$, em que $\hat\delta(q, \varepsilon) = q$ e
$\hat\delta(q, sa) = \delta(\hat\delta(q, s), a)$.

**Monoide de transições.** A imagem do morfismo $K(A) \to Q^Q$. Tem no máximo $|Q|^{|Q|}$ elementos.

**Autômato finito não determinístico.** Definido como o determinístico, mas com
$\delta : Q \times (A \cup \{\varepsilon\}) \to \mathcal{P}(Q)$. Aceita uma palavra quando algum caminho
termina em $F$. A eliminação das transições $\varepsilon$ não altera a classe reconhecida.

**Autômato de pilha.** Uma sétupla $(Q, A, \Gamma, \delta, q_0, Z_0, F)$ com
$\delta : Q \times (A \cup \{\varepsilon\}) \times \Gamma \to \mathcal{P}_{\mathrm{fin}}(Q \times K(\Gamma))$,
em que $\Gamma$ é o alfabeto da pilha, $Z_0 \in \Gamma$ é o símbolo inicial da pilha e
$\mathcal{P}_{\mathrm{fin}}(X)$ denota o conjunto das partes finitas de $X$. Cada transição substitui o topo da pilha por uma palavra de $K(\Gamma)$. A aceitação é por estado
final.

**Autômato de pilha determinístico.** Um autômato de pilha em que
$|\delta(q, a, Z)| + |\delta(q, \varepsilon, Z)| \leq 1$ para todos $q$, $a$ e $Z$.

**Máquina de Turing.** Uma sétupla $(Q, A, \Gamma, \delta, q_0, q_{\mathrm{ac}}, q_{\mathrm{rej}})$ em que
$\Gamma \supseteq A$ é o alfabeto da fita, o símbolo branco pertence a $\Gamma \setminus A$,
$q_{\mathrm{ac}}$ e $q_{\mathrm{rej}}$ são os estados de aceitação e de rejeição e
$\delta : (Q \setminus \{q_{\mathrm{ac}}, q_{\mathrm{rej}}\}) \times \Gamma \to Q \times \Gamma \times \{E, D\}$,
em que $E$ e $D$ indicam o movimento da cabeça para a esquerda ou para a direita. Na versão não determinística, $\delta$ toma valores em $\mathcal{P}(Q \times \Gamma \times \{E, D\})$.

**Autômato linearmente limitado.** Uma máquina de Turing que nunca ultrapassa nem sobrescreve os
marcadores que delimitam a entrada.

**Linguagem recursivamente enumerável ($\mathrm{RE}$).** Uma linguagem da forma $L(M)$ para alguma máquina
de Turing $M$, em que $L(M)$ denota o conjunto das palavras que $M$ aceita. Para entradas fora de $L$, a máquina pode rejeitar ou não parar.

**Linguagem recursiva ($\mathrm{Rec}$).** Uma linguagem aceita por alguma máquina de Turing que para em
toda entrada.
