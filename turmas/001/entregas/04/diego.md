# Paradoxo de Russell
**Núcleo.** O conjunto de todos os conjuntos que não pertencem a si mesmos não pode existir: se ele
pertence a si mesmo, então não pertence; se não pertence, então pertence. A contradição mostra que nem
toda propriedade bem formulada define um conjunto.

**Síntese.** Seja $R$ o conjunto definido por $R = \{x : x \notin x\}$. Perguntar se $R \in R$ produz uma
equivalência com sua própria negação, $R \in R \iff R \notin R$, portanto uma contradição, derivável já
na lógica intuicionista. A contradição vem do princípio de **compreensão irrestrita**, que garante a
existência de um conjunto para qualquer condição expressável. A definição de $R$ isolada não basta para
produzi-la. Abandonar esse princípio, restringindo a formação de conjuntos, é o preço da consistência.

## Modos de Contorno
Toda saída do paradoxo restringe a **compreensão irrestrita**: nenhuma condição pode, sozinha, formar um
conjunto. O que muda de teoria para teoria é o critério adotado, seja estratificação em
tipos, limitação de tamanho ou tipagem estrutural da pertinência. A raiz está na instanciação da
bicondicional de compreensão na própria coleção que ela define, não na negação nem na cardinalidade. É
o passo $x := R$ que toda saída bloqueia, seja tornando-o inescrevível, seja condicionando-o a uma
pertinência prévia, seja restringindo-o a argumentos que já sejam conjuntos.

### Teoria de Tipos
A resposta de Russell foi impor ao próprio sistema de formação de expressões uma disciplina de níveis.
Na versão simples dessa disciplina, que é a que basta aqui, indivíduos ocupam o tipo 0, funções
proposicionais sobre indivíduos ocupam o tipo 1, e assim por diante, de modo que a aplicação $\phi(x)$ só
é bem formada quando o tipo de $x$ é exatamente um nível abaixo do tipo de $\phi$. Sob essa restrição,
$x \in x$ é simplesmente inescrevível, o que é diferente de ser refutável. A teoria que Russell de fato
publicou é a ramificada, que estratifica também as ordens dentro de cada tipo e paga por isso com o
axioma da redutibilidade.

### Teoria dos conjuntos de Zermelo-Fraenkel (ZF)
Zermelo substitui a compreensão irrestrita pelo esquema da separação: dado um conjunto $A$ qualquer,
existe $\{x \in A : \phi(x)\}$. O argumento de Russell continua válido, mas agora só prova que
$\{x \in A : x \notin x\}$ não pertence a $A$, e daí que nenhum conjunto contém todos os conjuntos. A
estratégia difere estruturalmente da de Russell: a linguagem permanece sem tipos e $x \in x$ continua
sendo uma fórmula legítima. Deste modo, o bloqueio recai sobre a formação do conjunto, não sobre a expressão.

### Teoria dos conjuntos de Von Neumann-Bernays-Gödel (NBG)
Em ZF, nenhum termo da forma "a coleção de todos os conjuntos tais que" é objeto da teoria. Toda
formação de conjunto a partir de uma fórmula é relativa a um conjunto já dado, como subconjunto dele por
separação ou como imagem dele por substituição, e aquela coleção sobrevive apenas como abreviação
metalinguística. NBG faz o movimento oposto: mantém a compreensão quase intacta, mas paga o preço com
uma bipartição ontológica. Toda entidade da teoria é uma classe; conjunto é, por definição, uma classe
que pertence a alguma classe. A compreensão passa a valer para qualquer fórmula cujos quantificadores
percorram apenas conjuntos, e o objeto $R$ existe de fato. A diagonal continua funcionando, só que agora
o resultado é informação, e não mais contradição: se $R$ fosse conjunto, a compreensão instanciada em
$x := R$ daria $R \in R \iff R \notin R$, logo $R$ é classe própria, logo é incapaz de ser elemento, e a
bicondicional contraditória nunca chega a se concretizar.

### Universos de Grothendieck
Esta saída tem natureza diferente das anteriores. Em vez de restringir a compreensão, ela acrescenta um
axioma de existência a uma teoria já restringida. O que ela ganha é liberdade relativa: fixado um
universo, "todos os conjuntos" volta a ser uma coleção legítima, desde que "todos" signifique
"todos os que pertencem a ele".

Um universo de Grothendieck é um conjunto $U$ que satisfaz cinco condições de fechamento.
1. É transitivo: $x \in U \land y \in x \implies y \in U$.
2. É fechado sob pares não ordenados: $x, y \in U \implies \{x, y\} \in U$.
3. É fechado sob conjunto das partes: $x \in U \implies \mathcal{P}(x) \in U$.
4. É fechado sob uniões de famílias indexadas por um elemento de $U$: se $I \in U$ e $A_i \in U$ para todo $i \in I$, então $\bigcup_{i \in I} A_i \in U$.
5. Contém um conjunto infinito: $\omega \in U$.

Essas condições fazem de $U$ um modelo de ZFC: tudo que os axiomas produzem a partir de elementos de $U$
permanece em $U$. Para separação e partes isso é imediato. Para substituição é a condição 4 que faz o
trabalho, já que a imagem de $A \in U$ por uma função $f$ se escreve como $\bigcup_{a \in A} \{f(a)\}$.
A condição 5 tem peso próprio: sem ela, $V_\omega$ satisfaria as quatro primeiras e falharia justamente
o axioma do infinito. Com ela, os universos são exatamente os $V_\kappa$ com $\kappa$ fortemente
inacessível, o que situa a construção entre os axiomas de cardinais grandes.

### Topos elementares
Um topos elementar é uma categoria com limites finitos, exponenciais e um objeto que classifica
subobjetos. Essa estrutura mínima basta para reconstruir internamente a lógica e boa parte da teoria de
conjuntos, o que faz de cada topos um universo matemático alternativo. A abordagem é semelhante à que
Russell adotou na teoria de tipos. A diferença está na fundamentação: em vez de proibir a autoaplicação
por decreto sintático, o topos transforma a ausência dela em teorema. Em nenhum topos não degenerado
existe morfismo $X \to \Omega^X$ sobrejetor em pontos, pelo teorema do ponto fixo de Lawvere, do qual
Russell e Cantor são instâncias. A demonstração usa apenas que a negação $\neg : \Omega \to \Omega$ não
tem ponto fixo, que é a mesma contradição da Síntese e por isso não depende de lógica clássica.

### Comparação
As cinco saídas diferem no lugar onde interrompem a mesma cadeia.

| Saída | O que é restringido | O que acontece com $R$ | Preço |
|---|---|---|---|
| **Teoria de tipos** | A boa formação das expressões. $\phi(x)$ exige o tipo de $x$ um nível abaixo do de $\phi$ | $R$ não é definível. $x \in x$ é inescrevível, o que é diferente de ser falso | Uma hierarquia na própria linguagem, mais o axioma da redutibilidade na versão ramificada |
| **ZF** | A compreensão, que vira separação dentro de um conjunto já dado | $R$ não existe. Cada $R_A = \{x \in A : x \notin x\}$ existe, e o argumento prova $R_A \notin A$ | Não há conjunto universal. Coleções grandes só sobrevivem como abreviação |
| **NBG** | A compreensão de classes, cujos quantificadores percorrem apenas conjuntos | $R$ existe como classe própria. Não é elemento de nada, e $x := R$ nunca chega a ser instanciado | Bipartição ontológica entre classe e conjunto |
| **Universos de Grothendieck** | Nada é restringido aqui. É um axioma de existência acrescentado a uma teoria já restringida | Herda ZF. Dentro de um universo, $R_U = U$ e a conclusão de Zermelo instancia em $U \notin U$ | Força de um cardinal fortemente inacessível |
| **Topos elementar** | Nada por decreto. A tipagem é estrutural, herdada de objetos e morfismos | Não há análogo global de $R$. O papel dele cabe a $\neg : \Omega \to \Omega$, cuja ausência de ponto fixo obstrui $X \to \Omega^X$ sobrejetor em pontos | Lógica interna apenas intuicionista no caso geral |

Vista assim, a última linha deixa de ser um caso à parte. O paradoxo de Russell, o teorema de Cantor e o
primeiro teorema de incompletude são instâncias de um mesmo teorema de ponto fixo, e as quatro primeiras
linhas diferem apenas em onde cada teoria impede que a hipótese dele seja satisfeita.

---

# Numerais de von Neumann
**Núcleo.** É uma das formas de se definir os números naturais. Cada número natural é definido como um
conjunto concreto: zero é o conjunto vazio, e cada número seguinte é o anterior acrescido do próprio
anterior como novo elemento. Contar vira pertencer, e a aritmética passa a ser teorema de teoria dos
conjuntos.

**Síntese.** Toda a aritmética é recuperada a partir de dois elementos: um objeto inicial, o conjunto
vazio, e uma operação de sucessão, $S(x) = x \cup \{x\}$. O resultado é a cadeia $0 = \emptyset$,
$1 = \{0\}$, $2 = \{0, 1\}$, ..., na qual pertencer a um número é ser menor que ele. O único axioma
adicional é o do infinito, que assegura a existência de um conjunto indutivo. Tomando o menor deles,
obtém-se $\omega$ e, com ele, indução e recursão. Esse menor não vem de axioma próprio: fixado um
indutivo $N$, é a separação que produz $\omega = \{x \in N : x$ pertence a todo conjunto indutivo$\}$, e
verifica-se que $\omega$ é ele próprio indutivo.


---

# Definições

## Esquemas de formação de conjuntos

**Compreensão irrestrita.** Para toda fórmula $\phi(x)$ na qual $y$ não ocorre livre,
$$
\exists y \, \forall x \, ( x \in y \iff \phi(x) ).
$$
É o princípio refutado pelo paradoxo de Russell. A definição de $R$ em si não é o alvo da refutação.

**Esquema da separação.** Para toda fórmula $\phi(x)$ na qual $B$ não ocorre livre,
$$
\forall A \, \exists B \, \forall x \, ( x \in B \iff x \in A \land \phi(x) ).
$$
A formação é sempre relativa a um conjunto já dado.

**Esquema da substituição.** Se $\phi(x, y)$ é funcional em $A$, isto é
$\forall x \in A \, \exists ! y \, \phi(x, y)$, então existe $B$ tal que
$\forall x \in A \, \exists y \in B \, \phi(x, y)$. O conjunto imagem se obtém de $B$ por separação.

**Extensionalidade.** $\forall A \, \forall B \, ( \forall x ( x \in A \iff x \in B ) \implies A = B )$.
É o que garante unicidade ao objeto descrito por uma condição, e portanto o que faz de $R$ um objeto bem
determinado caso ele exista.

**Axioma da regularidade.** Todo conjunto não vazio tem elemento $\in$-minimal:
$$
A \neq \emptyset \implies \exists x \in A \, ( x \cap A = \emptyset ).
$$
Aplicado a $\{x\}$, ele dá $x \notin x$ para todo $x$. Sob regularidade, portanto, a condição
$x \notin x$ é universalmente satisfeita e a classe de Russell coincide com a classe de todos os
conjuntos. O paradoxo se reduz ao enunciado de que não existe conjunto universal, que é exatamente o que
a separação já provava.

## Classes

**Classe própria.** Classe que não pertence a nenhuma classe. Equivalentemente, classe que não é
conjunto no sentido de NBG. Uma classe própria é incapaz de ser instanciada em uma bicondicional de
compreensão, e é daí que vem o bloqueio.

**Fórmula predicativa.** Fórmula cujos quantificadores percorrem apenas conjuntos, admitindo classes
somente como parâmetros livres. É sob essa restrição que a compreensão de NBG vale. É também o que torna
NBG finitamente axiomatizável e conservativa sobre ZFC.

**Limitação de tamanho.** Uma classe é própria se e somente se existe bijeção entre ela e a classe de
todos os conjuntos. Adotado como axioma por von Neumann, ele implica substituição e escolha global.

## Hierarquia cumulativa e universos

**Hierarquia cumulativa.** Definida por recursão transfinita:
$$
V_0 = \emptyset, \qquad V_{\alpha + 1} = \mathcal{P}(V_\alpha), \qquad
V_\lambda = \bigcup_{\alpha < \lambda} V_\alpha \ \ (\lambda \text{ limite}).
$$
Sob regularidade, todo conjunto pertence a algum $V_\alpha$.

**Cardinal regular.** $\kappa$ é regular quando $\mathrm{cf}(\kappa) = \kappa$, ou seja, quando nenhuma
família de menos de $\kappa$ conjuntos de tamanho menor que $\kappa$ tem união de tamanho $\kappa$.

**Cardinal fortemente inacessível.** $\kappa > \omega$ regular e fechado sob exponenciação:
$\lambda < \kappa \implies 2^\lambda < \kappa$. Vale que os universos de Grothendieck não vazios são
exatamente os $V_\kappa$ com $\kappa$ inacessível. É por isso que a existência de universos não é
demonstrável em ZFC, e é nisso que consiste o preço do axioma adicional.

## Estrutura categórica

**Ponto.** Em uma categoria com objeto terminal $1$, um ponto de $X$ é um morfismo $1 \to X$.

**Exponencial.** Objeto $Y^X$ com bijeção natural em $Z$ entre morfismos $Z \times X \to Y$ e morfismos
$Z \to Y^X$. A contraparte da aplicação é a avaliação $\mathrm{ev} : Y^X \times X \to Y$.

**Classificador de subobjetos.** Mono $\top : 1 \to \Omega$ tal que todo mono $S \rightarrowtail X$ é
pullback de $\top$ ao longo de um único $\chi : X \to \Omega$. É o que substitui, internamente, a relação
de pertinência.

**Topos não degenerado.** Topos no qual $0$ e $1$ não são isomorfos, o que equivale a
$\top \neq \bot$ como pontos de $\Omega$. Em um topos degenerado toda afirmação vale e nada se conclui.

**Teorema do ponto fixo de Lawvere.** Se existe $f : A \to B^A$ fracamente sobrejetor em pontos, isto é,
tal que para todo $g : A \to B$ existe $a : 1 \to A$ com
$\mathrm{ev} \circ \langle f \circ a, x \rangle = g \circ x$ para todo ponto $x : 1 \to A$, então todo
endomorfismo de $B$ tem ponto fixo. A contrapositiva com $B = \Omega$ e o endomorfismo $\neg$ dá o
enunciado da seção sobre topos.

**Teorema de Cantor.** Não existe sobrejeção $A \to \mathcal{P}(A)$. É a instância de Lawvere obtida em
$\mathbf{Set}$ com $B = \{0, 1\}$ e o endomorfismo de troca, que também não tem ponto fixo.

## Teoria de tipos

**Tipo e função proposicional.** Na versão simples, indivíduos ocupam o tipo $0$ e funções
proposicionais cujos argumentos são de tipo $n$ ocupam o tipo $n + 1$. A aplicação $\phi(x)$ é bem
formada apenas quando $\mathrm{tipo}(\phi) = \mathrm{tipo}(x) + 1$, o que torna $x \in x$ inescrevível.

**Ordem e axioma da redutibilidade.** Na versão ramificada, funções proposicionais de um mesmo tipo
ainda se estratificam por ordem, conforme os quantificadores que empregam. O axioma da redutibilidade
postula que toda função proposicional é coextensiva a uma de ordem mínima para o seu tipo, o que
restaura a matemática clássica ao custo de anular boa parte da ramificação.

**Fórmula estratificada.** Fórmula para a qual existe atribuição de inteiros às variáveis tal que
$x \in y$ exige $\mathrm{tipo}(y) = \mathrm{tipo}(x) + 1$ e $x = y$ exige tipos iguais. A compreensão
restrita a fórmulas estratificadas é a saída de New Foundations, na qual $x \in x$ é escrevível mas
$x \notin x$ não é estratificada.

## Aritmética

**Conjunto indutivo.** $N$ é indutivo quando
$$
\emptyset \in N \land ( \forall x : x \in N \implies x \cup \{x\} \in N ).
$$

**Axioma do infinito.** Existe um conjunto indutivo.

**Ordinal de von Neumann.** Conjunto transitivo e bem ordenado estritamente por $\in$. Os numerais são
exatamente os ordinais finitos, e $\omega$ é o menor ordinal limite.

**Teorema da recursão.** Dados um conjunto $A$, um elemento $a \in A$ e uma função $g : A \to A$, existe
uma única $f : \omega \to A$ com $f(0) = a$ e $f(S(n)) = g(f(n))$. É o que legitima definir operações
aritméticas por recursão, e não decorre da indução sozinha.
