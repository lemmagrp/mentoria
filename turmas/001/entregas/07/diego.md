# Entrega 07

Fixe um conjunto $S$ e sejam $a, b, c$ elementos dele. Uma *relação binária* em $S$ é um subconjunto
$R \subseteq S \times S$. Escreve-se $aRb$ para $(a,b) \in R$. Ou seja, $R$ é um predicado de
duas variáveis, ambas percorrendo o mesmo conjunto. Com isso podemos comparar elementos de $S$ entre
si, e não apenas verificar se são iguais.

Escreva
$$
\Delta := \{(a,a) : a \in S\}
$$
para a *diagonal*, a relação que só liga cada elemento a si mesmo. Escreva ainda
$$
R^{-1} := \{(b,a) : (a,b) \in R\}
$$
para o *converso* de $R$, que troca a ordem de cada par. Inverter duas vezes devolve $R$, inverter
preserva inclusões, e $\Delta^{-1} = \Delta$.

Dadas relações $R$ e $T$ em $S$, a *composição* $T \circ R$ é definida por
$$
T \circ R := \{(a,c) \in S \times S : \exists b \in S \text{ com } aRb \text{ e } bTc\}.
$$
Como na composição de funções, lê-se da direita para a esquerda, ou seja, $T \circ R$ percorre
primeiro $R$ e depois $T$. Em particular, $R \circ R$ liga $a$ a $c$ quando há um caminho de dois
passos de $a$ até $c$ dentro de $R$.

Igualdade e inclusão se aplicam a conjuntos. Para tratá-las como relações binárias no sentido acima
tomamos $\mathcal{P}(S)$ como conjunto ambiente, já que o paradoxo de Russell impede um conjunto de
todos os conjuntos. A escolha não é arbitrária: $\mathcal{P}(S)$ é fechado por baixo sob inclusão,
pois $y \subseteq x \subseteq S$ dá $y \subseteq S$, e nenhuma comparação interna se perde. Tudo o
que segue vale com $\mathcal{P}(S)$ no lugar de $S$. Chamamos os conjuntos comparados de $x, y$ e
mantemos $a, b, c$ para elementos de $S$.

## Propriedades

**Reflexiva.** Todo elemento se relaciona consigo mesmo.
$$
\Delta \subseteq R.
$$

**Simétrica.** A ordem dos elementos é irrelevante.
$$
R^{-1} \subseteq R.
$$

**Antissimétrica.** Se dois elementos se relacionam nos dois sentidos, então são o mesmo elemento.
$$
R \cap R^{-1} \subseteq \Delta.
$$

**Transitiva.** A relação absorve a própria composição.
$$
R \circ R \subseteq R.
$$

Fixe $R$ e faça o ambiente crescer, de $S$ para algum $S' \supseteq S$. Das quatro propriedades, só
a reflexividade depende dessa mudança, já que pede $\Delta \subseteq R$. O mesmo vale para a
totalidade, usada adiante, que pede $S \times S \subseteq R \cup R^{-1}$. As duas exigem que certos
pares estejam em $R$, e a exigência cresce com $S$. Simetria, antissimetria e transitividade são
condições sobre pares que já estão em $R$, e por isso não mudam.

Uma relação reflexiva e transitiva é chamada de *pré-ordem*. Se ela também é simétrica, temos uma *relação
de equivalência*, que agrupa elementos indistinguíveis. Se em vez disso é antissimétrica, temos uma
*ordem parcial*, e os elementos ficam hierarquizados, ainda que dois deles nem sempre sejam
comparáveis.

**Observação.** Simetria e antissimetria podem valer ao mesmo tempo, e o caso em que isso acontece é
exatamente este:
$$
R \text{ é simétrica e antissimétrica} \iff R \subseteq \Delta.
$$
De fato, invertendo os dois lados de $R^{-1} \subseteq R$ e usando que inverter duas vezes devolve
$R$, a simetria dá também $R \subseteq R^{-1}$, logo $R = R^{-1}$ e $R = R \cap R^{-1}$. A
antissimetria põe isso dentro de $\Delta$. Na volta, todo $R \subseteq \Delta$ é seu próprio
converso, já que inverter $(a,a)$ devolve $(a,a)$, e então $R \cap R^{-1} = R \subseteq \Delta$.

## Igualdade

O axioma da extensão define a igualdade por
$$
x = y \;:\iff\; \forall a \big( p_x(a) \iff p_y(a) \big),
$$
isto é, a igualdade entre conjuntos é o $\iff$ entre os predicados que os definem. Suas propriedades
são, portanto, herdadas das propriedades de $\iff$ entre valores de verdade, e daí saem
reflexividade, simetria e transitividade. A antissimetria é gratuita, já que a conclusão exigida,
$x = y$, é a própria hipótese.

Logo $=$ é uma relação de equivalência, e é ao mesmo tempo simétrica e antissimétrica. Pela
observação acima está contida na diagonal, e a reflexividade dá a inclusão oposta. Em
$\mathcal{P}(S)$ a igualdade coincide com a diagonal.

**Proposição.** $R$ é reflexiva, simétrica e antissimétrica se, e somente se, $R = \Delta$.

*Demonstração.* $(\Rightarrow)$ A reflexividade dá $\Delta \subseteq R$, e a observação dá
$R \subseteq \Delta$. $(\Leftarrow)$ A diagonal tem as três propriedades. $\blacksquare$

Note que a transitividade não entra na lista porque é consequência. Das três propriedades sai
$R = \Delta$, que é transitiva. A reflexividade sozinha já dá $\Delta \subseteq R$ para toda $R$
reflexiva, ou seja, a igualdade é a menor de todas. Como equivalência ela é também a mais fina, no
sentido de que distingue tudo o que se pode distinguir.

## Ser subconjunto de

$$
x \subseteq y \;:\iff\; \forall a \big( (a \in x) \implies (a \in y) \big).
$$

A inclusão está para $\implies$ assim como a igualdade está para $\iff$, e herda as propriedades do
conectivo. Reflexividade e transitividade saem de $P \implies P$ e da composição de implicações. A
antissimetria é o axioma da extensão, dado que $(P \implies Q) \wedge (Q \implies P)$ é $P \iff Q$,
isto é, $x = y$ exatamente quando $x \subseteq y$ e $y \subseteq x$. Simetria não vale assim que há
o que comparar: se $a \in S$, então $\varnothing$ e $\{a\}$ estão em $\mathcal{P}(S)$, com
$\varnothing \subseteq \{a\}$ e $\{a\} \not\subseteq \varnothing$.

Então $\subseteq$ é uma ordem parcial em $\mathcal{P}(S)$. Se $S$ tem dois elementos distintos $a$ e
$b$, ela não é total, já que $\{a\}$ e $\{b\}$ são incomparáveis. A hipótese é necessária. Com $S$
vazio ou unitário, $\mathcal{P}(S)$ se reduz a $\varnothing$ e ao próprio $S$, e a inclusão vale
entre eles, ou seja, a ordem é total. E como toda ordem parcial, $\subseteq$ deixa de ser simétrica
tão logo haja algo a ordenar. Pela observação acima, uma ordem parcial simétrica está contida na
diagonal, e a reflexividade a torna igual à diagonal, o caso degenerado em que nada se compara além
de consigo mesmo. Para a inclusão isso dá
$$
\subseteq \text{ é simétrica em } \mathcal{P}(S) \iff S = \varnothing,
$$
já que $\mathcal{P}(\varnothing) = \{\varnothing\}$ e, para $S$ não vazio, o contraexemplo acima
resolve.

## Resumo

Cada relação abaixo é lida no seu próprio ambiente. Nas duas primeiras linhas ele é $\mathcal{P}(S)$
com $S \neq \varnothing$, e na última é
$A := \{\varnothing, \{\varnothing\}, \{\{\varnothing\}\}\}$, que contém os três conjuntos do
contraexemplo adiante.

| $R$ | reflexiva | simétrica | antissimétrica | transitiva |
|-|-|-|-|-|
| $=$ em $\mathcal{P}(S)$ | sim | sim | sim | sim |
| $\subseteq$ em $\mathcal{P}(S)$ | sim | não | sim | sim |
| $\leq$ em $\mathbb{N}$ | sim | não | sim | sim |
| $<$ em $\mathbb{N}$ | não | não | sim | sim |
| $\in$ em $A$ | não | não | sim | não |

A igualdade é uma equivalência e a inclusão é uma ordem parcial. As duas só discordam na coluna da
simetria, o que era de esperar, já que $\iff$ é simétrico e $\implies$ não é.

Nas duas últimas linhas a antissimetria vale por vacuidade, já que $R \cap R^{-1} = \varnothing$, ou
seja, a hipótese $aRb \wedge bRa$ nunca se realiza. Para $<$ isso é imediato. Para $\in$ é o axioma
da regularidade, pois de $a \in b$ e $b \in a$ o conjunto $\{a,b\}$ não teria elemento minimal
para a pertinência. A mesma regularidade dá a não reflexividade de $\in$: aplicada a $\{a\}$, o
único elemento minimal possível é $a$, logo nenhum elemento de $a$ pertence a $\{a\}$, e em
particular $a \notin a$. E $\in$ não é transitiva, como mostra
$\varnothing \in \{\varnothing\} \in \{\{\varnothing\}\}$ com $\varnothing \notin \{\{\varnothing\}\}$.
