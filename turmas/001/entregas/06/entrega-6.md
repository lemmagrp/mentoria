## Definições

**Axioma da extensão.**
$$
x = y \quad \iff \quad \forall z \big( (z \in x) \leftrightarrow (z \in y) \big).
$$
Equivalentemente, $x = y$ exatamente quando $p_x(z)$ e $p_y(z)$ têm o mesmo valor de verdade
para todo $z$.

**Axioma da regularidade.**
Todo conjunto não vazio $S$ possui um elemento $m$ minimal para a relação de pertinência, isto é,
nenhum elemento de $m$ pertence a $S$.

A regularidade é usada uma única vez, na Proposição 3.

**Enumeração.** Para um conjunto indexador qualquer $I$ e uma família $(x_i)_{i \in I}$, $x = \{x_i\}_{i \in I}$ é
notação para $p_x(z) \equiv \exists i \in I\,(z = x_i)$.

## Conjuntos não possuem elementos repetidos

**Proposição 1.** Se $y \in x$, então $x \cup \{y\} = x$.

*Demonstração.* Para $z$ arbitrário,
$$
z \in x \cup \{y\} \iff (z \in x) \vee (z = y).
$$
Escreva $A :\equiv (z \in x)$ e $B :\equiv (z = y)$. De $y \in x$ segue $B \Rightarrow A$, e portanto
$(A \vee B) \leftrightarrow A$. Pelo axioma da extensão, $x \cup \{y\} = x$. $\blacksquare$

## Conjuntos não dependem da ordem

**Proposição 2.** Sejam $x = \{x_i\}_{i \in I}$ e $\sigma : I \to I$ uma permutação. Se $y = \{x_{\sigma(i)}\}_{i \in I}$,
então $x = y$.

*Demonstração.* Seja $z$ arbitrário.
Se $z = x_{\sigma(i)}$ para algum $i$, tome $j := \sigma(i)$, e então $z \in x$.
Se $z = x_j$ para algum $j$, a sobrejetividade de $\sigma$ dá $i$ com $\sigma(i) = j$, e então $z \in y$.
Logo $p_x \leftrightarrow p_y$, e o axioma da extensão conclui. $\blacksquare$

## Comutatividade de produto e coproduto

### Pares ordenados

Um par ordenado $(a,b)$ é definido como o conjunto $\{a, \{b\}\}$. Também, fixe $0 := \varnothing$ e $1 := \{\varnothing\}$, de modo que $0 \neq 1$ e $\{0\} = 1$.

**Observação (pares ordenados).** Essa definição não determina as coordenadas. Para quaisquer conjuntos
$b$ e $d$,
$$
(\{d\},\, b) = \big\{\{d\},\{b\}\big\} = \big\{\{b\},\{d\}\big\} = (\{b\},\, d),
$$
e tomando $b := 0$ e $d := 1$, com $\{0\} = 1$, isso dá $(\{1\},\, 0) = (1,\, 1)$ com
$\{1\} \neq 1$ e $0 \neq 1$. Portanto $(a,b) = (c,d)$ não força $a = c$ e $b = d$, e cada uso de
pares adiante precisa de um argumento próprio: a Proposição 3 apela à regularidade, e o Lema 1
trata à mão o caso dos índices $0$ e $1$.

### Produto

**Proposição 3.** $x \times y = y \times x$ se, e somente se, $x = y$ ou $x = \varnothing$ ou $y = \varnothing$.

*Demonstração.* $(\Leftarrow)$ Para $x = y$ é trivial. Se $x = \varnothing$, os predicados de ambos os lados são sempre
falsos, e o axioma da extensão dá $x \times y = \varnothing = y \times x$. O caso $y = \varnothing$ é simétrico.

$(\Rightarrow)$ Por contraposição. Sejam $x \neq y$ ambos não vazios, e suponha $x \times y = y \times x$.
Pelo axioma da extensão existe elemento em exatamente um dos dois, e como a hipótese é simétrica em
$x$ e $y$ podemos supor que ele está em $x$. Assim $S := x \setminus y$ é não vazio.

*Passo 1.* Sejam $a \in S$ e $b \in y$ quaisquer. Como $(a,b) \in x \times y = y \times x$,
existem $b' \in y$ e $a' \in x$ com $\{a,\{b\}\} = \{b',\{a'\}\}$. De $a \in \{b',\{a'\}\}$ segue
$a = b' \in y$, excluído por $a \in S$, ou $a = \{a'\}$ com $a' \in x$. De $\{b\} \in \{b',\{a'\}\}$
segue $\{b\} = b' \in y$, ou $\{b\} = \{a'\}$, isto é, $b = a'$. Neste último subcaso
$a = \{a'\} = \{b\}$, de modo que o lado esquerdo é $\{a,\{b\}\} = \{a\}$ e o direito é
$\{b',\{a'\}\} = \{b',a\}$, forçando $b' = a$ e portanto $a \in y$, excluído. Concluímos que todo
$a \in S$ é da forma $a = \{a'\}$ com $a' \in x$, e que $y$ é fechado por singletons.

*Passo 2.* Esse $a'$ não pertence a $y$. Caso contrário o fechamento do Passo 1 daria
$\{a'\} = a \in y$, contra $a \in S$. Logo $a' \in S$ e $a' \in a$.

*Passo 3.* Pelo axioma da regularidade tome $m$ minimal em $S$. Os dois passos anteriores dão
$m = \{m'\}$ com $m' \in S$ e $m' \in m$, contradizendo a minimalidade de $m$. $\blacksquare$

**Observação.** A regularidade entra aqui porque, pela observação sobre pares ordenados acima,
de $\{a,\{b\}\} = \{b',\{a'\}\}$ não se conclui $a = b'$, e o Passo 1 sozinho não fecha o argumento. Uma alternativa é supor que
nenhum elemento de $x \cup y$ seja o singleton de outro, hipótese que elimina de saída o caso
$a = \{a'\}$. Com a definição de Kuratowski, $(a,b) := \{\{a\},\{a,b\}\}$, nada disso é necessário.

### Coproduto

Com $0$ e $1$ como acima, para quaisquer conjuntos $x$ e $y$ defina
$$
x \sqcup y := \{(0,a) : a \in x\} \cup \{(1,b) : b \in y\}.
$$

**Lema 1.** Para quaisquer conjuntos $a$ e $b$:
(i) $(0,a) \neq (1,b)$;
(ii) $(t,a) = (t,b) \Rightarrow a = b$, para $t \in \{0,1\}$.

*Demonstração.* (i) De $\{0,\{a\}\} = \{1,\{b\}\}$ segue $0 = 1$, falso por construção, ou $0 = \{b\}$, falso pois
$\varnothing$ não tem elementos.

(ii) Para $t = 0$: de $\{a\} \in \{0,\{b\}\}$ segue $\{a\} = 0$, impossível, ou $\{a\} = \{b\}$, que
dá $a = b$. Para $t = 1$: de $\{a\} \in \{1,\{b\}\}$ segue $\{a\} = \{b\}$, que conclui, ou
$\{a\} = \{\varnothing\}$, isto é, $a = \varnothing$. Nesse subcaso o lado esquerdo é
$\{1,\{\varnothing\}\} = \{1\}$, e então $\{b\} = 1 = \{\varnothing\}$, ou seja, $b = \varnothing = a$. $\blacksquare$

**Proposição 4.** $x \sqcup y = y \sqcup x$ se, e somente se, $x = y$.

*Demonstração.* $(\Leftarrow)$ Imediato.

$(\Rightarrow)$ Por contraposição. Se $x \neq y$, digamos $a \in x$ com $a \notin y$, então
$(0,a) \in x \sqcup y$. Os elementos de $y \sqcup x$ são $(0,b)$ com $b \in y$, ou $(1,c)$ com
$c \in x$. No primeiro caso, o Lema 1(ii) daria $a = b \in y$, contradição. O segundo
é impossível pelo Lema 1(i). O caso $a \in y \setminus x$ é simétrico. $\blacksquare$

Aqui nem o caso vazio salva a igualdade: para $y \neq \varnothing$,
$\varnothing \sqcup y = \{(1,b) : b \in y\}$ e $y \sqcup \varnothing = \{(0,b) : b \in y\}$ diferem pelo
Lema 1(i). A bijeção canônica que troca os índices dá comutatividade a menos de um isomorfismo.

**Proposição 5.** $\displaystyle x \sqcup \varnothing = \{(0,a) : a \in x\} = \big\{\, \{\varnothing,\{a\}\} : a \in x \,\big\} = \{0\} \times x$.

*Demonstração.* O predicado do segundo termo, $\exists b\,(b \in \varnothing \wedge w = (1,b))$, é sempre falso.
Como $P \vee \bot \leftrightarrow P$, o axioma da extensão conclui. $\blacksquare$
