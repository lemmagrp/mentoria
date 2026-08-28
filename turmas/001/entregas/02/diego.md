# Problema da parada com tempo infinito
**Núcleo.** O problema da parada H das MTTIs é semidecidível, mas indecidível pelas próprias máquinas que o formulam. Equipar uma máquina com um oráculo para H cria uma máquina estritamente mais forte, capaz de decidir o H anterior, mas que gera um novo problema da parada igualmente indecidível num nível acima.

**Síntese.** Imagine um computador que pode rodar por tempo infinito. Hamkins e Lewis chamam esta máquina de Máquina de Turing de Tempo Infinito e perguntam: esse computador consegue prever se um programa qualquer vai parar ou rodar para sempre? Estudam duas formas dela: uma geral (H), que pergunta pela parada de qualquer programa com qualquer entrada, e uma restrita (h), que só pergunta sobre a entrada vazia. A descoberta central é que essas máquinas resolvem o problema da parada das máquinas comuns, mas não conseguem resolver o seu próprio, pelo mesmo motivo das máquinas de tempo finito: se uma máquina pudesse prever a própria parada, daria para construir um programa que faz o contrário do que ela prevê, gerando contradição. A saída é dar à máquina uma "consulta mágica" (o oráculo) que responde instantaneamente às perguntas sobre a parada anterior. Isso cria uma máquina mais poderosa, mas que reencontra o mesmo bloqueio, agora num nível acima.
---
# Metalinguagem

**Núcleo.** Metalinguagem é a linguagem usada para falar sobre outra linguagem, seus símbolos, suas regras e suas verdades. Para descrever ou avaliar uma linguagem-objeto sem cair em contradição, é preciso situar-se num nível distinto, acima dela.

**Síntese.** A distinção opõe **linguagem-objeto** (aquela que se estuda) e **metalinguagem** (aquela em que se enuncia o estudo). Noções *semânticas* como "é verdadeiro", "denota" ou "satisfaz" não podem ser definidas dentro da própria linguagem-objeto sem gerar paradoxo; precisam de uma metalinguagem estritamente mais rica. É nesse nível superior que habitam a metamatemática de Hilbert (provar afirmações sobre um sistema formal) e o esquema de Tarski, que fixa as condições de verdade mencionando, de fora, as sentenças do nível inferior.

**Teoremas de Incompletude de Gödel.** As demonstrações ocorrem em metamatemática finitista informal: Gödel raciocina de fora sobre o sistema formal e, pela numeração, projeta para dentro da aritmética uma imagem aritmética desse raciocínio, que o sistema passa então a carregar sem compreender.
---
# Linguagem de Alto Nível

**Núcleo.** Linguagem de programação que descreve a computação em termos próximos do raciocínio humano e do domínio do problema, abstraindo os detalhes da máquina, como registradores e endereços de memória; um tradutor (compilador ou interpretador) converte esse código em instruções executáveis.

**Síntese.** O traço definidor é o nível de abstração: a linguagem oculta a arquitetura subjacente e oferece construções como variáveis, funções e estruturas de controle. Disso decorrem portabilidade (o mesmo código roda em máquinas diferentes) e produtividade, ao custo de menos controle fino sobre o hardware. O termo é relativo e gradual: define-se "alto" por contraste com o "baixo nível" (assembly, código de máquina). O compilador ou interpretador é a ponte entre a expressão humana e a execução física.

**Exemplo.** Haskell (alto) vs. C (baixo).
---
# Correspondência de Curry-Howard

**Núcleo.** A correspondência de Curry-Howard identifica provas e programas: uma proposição é um tipo, uma demonstração dessa proposição é um termo (programa) desse tipo, e normalizar a prova é executar o programa.

**Síntese.** A correspondência alinha três dimensões. Na dimensão lógica estão proposições e provas; na dimensão computacional, tipos e termos; e na dimensão operacional, simplificação de provas e avaliação de programas. Implicação corresponde ao tipo função, conjunção ao produto, disjunção à soma, e a normalização de provas (redução à forma normal) corresponde à beta-redução do cálculo lambda. Provar um teorema e habitar um tipo passam a ser a mesma coisa.

**Metalinguagem.** A linguagem-objeto na lógica é a dedução natural intuicionista (proposicional ou de primeira ordem). A linguagem-objeto computacional é o cálculo lambda (simplesmente tipado ou dependente). A metalinguagem é a matemática informal clássica.
| Lógica | Computação / Teoria dos Tipos | Representação em Scala (com exemplo) |
| --- | --- | --- |
| Proposição | Tipo | `Int`, `String`, `Boolean` ou definido pelo programador |
| Prova (demonstração) | Habitante do tipo | `1` é uma demonstração da proposição `Int` |
| Proposição é demonstrável | Tipo não vazio | `Int` é demonstrável; `Nothing` não é |
| Implicação A → B | Tipo função A → B | `(x: Int) => x.toString`, de tipo `Int => String` |
| Conjunção A ∧ B | Produto A × B | `(1, "a")`, de tipo `(Int, String)` |
| Disjunção A ∨ B | Soma A + B | `Left(1)` ou `Right("a")`, de tipo `Either[Int, String]` |
| Verdadeiro (⊤) | Tipo unitário | `Unit`, com o único valor `()` |
| Falso (⊥) | Tipo vazio | `Nothing`, sem nenhum valor habitante |
| Negação ¬A | Função A → ⊥ | `(x: Int) => ???`, de tipo `Int => Nothing` |
| Quantificador universal ∀x:T.A(x) | Tipo dependente Π(x:T).A(x) | Polimorfismo paramétrico: `def id[A](a: A): A = a` |
| Quantificador existencial ∃x:T.A(x) | Tipo soma dependente Σ(x:T).A(x) | Elemento do tipo abstrato: `trait Exists { type T; val v: T }` |
| Modus ponens | Aplicação de função | `id[Int](1)` |
| Introdução da implicação | Abstração lambda | `(x: Int) => x + 1` |
| Normalização (processo) | Beta-redução (execução) | `((x: Int) => x + 1)(2)` reduz a `3` |
| Prova em forma normal | Termo normalizado (valor) | `3`, sem expressão reduzível pendente |
| Hipótese / premissa | Variável livre no contexto | `val n: Int = 10; def multiplyByN(x: Int): Int = x * n`, onde `n` é a variável livre |
---
# Apêndice
## Definições

**Oráculo.** Um dispositivo idealizado, acoplado à máquina, que responde instantaneamente a uma pergunta fixa difícil (por exemplo, "tal programa para?"), sem que a máquina precise calcular a resposta. É um recurso teórico para medir o poder relativo: "o que eu conseguiria resolver se ganhasse de graça as respostas deste problema?".

**Salto de Turing.** É uma operação que transforma um conjunto A num conjunto estritamente mais difícil A'. A construção adiciona a A todas as respostas à pergunta "esse programa, usando A como oráculo, eventualmente para?", onde oráculo significa que a máquina pode consultar A instantaneamente, sem calcular suas respostas.
Classicamente, esse passo é único: qualquer entrada é um objeto finito que cabe escrito no início da fita, então a única distinção relevante é ter ou não acesso ao oráculo A.
Nas Máquinas de Turing de Tempo Infinito (MTTIs), o salto se desdobra em dois porque as entradas passam a ser sequências infinitas de bits. A maioria dessas sequências não possui descrição finita, logo não pode ser embutida no código do programa.
Por isso surgem dois saltos distintos:
1. **Salto fraco:** pergunta sobre programas que começam com a fita em branco, usando A como oráculo. Cobre apenas o comportamento independente de entrada.
2. **Salto forte:** pergunta sobre programas que começam com uma sequência infinita arbitrária na fita, inclusive as inescrevíveis, usando A como oráculo. Como sequências inescrevíveis não podem ser incorporadas ao código do programa, esse caso exige poder computacional genuinamente maior.
Os dois saltos capturam, portanto, poderes distintos, e a razão é estritamente a inescrevibilidade das entradas infinitas, que não admitem representação finita.

**Princípio do terceiro excluído.** Princípio da lógica clássica segundo o qual qualquer proposição é verdadeira ou sua negação é verdadeira; não há terceira possibilidade. Simbolicamente, $P \vee \lnot P$.

**Lógica intuicionista.**  Lógica clássica sem o princípio do terceiro excluído. Mantém a inferência usual mas recusa identificar "verdadeiro" com "não falso". Afirmar algo exige construí-lo, não apenas descartar sua negação.

**Metamatemática finitista.** Raciocínio sobre objetos sintáticos finitos (fórmulas, provas como sequências de símbolos) usando apenas operações concretamente verificáveis, sem apelar ao infinito.

**Metamatemática finitista informal.** Raciocínio sobre objetos sintáticos finitos (fórmulas, provas) conduzido fora de qualquer sistema formal, usando apenas operações decidíveis sobre os símbolos.