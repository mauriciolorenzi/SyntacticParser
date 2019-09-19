# SyntacticParser
Análise Sintática O que é Sintaxe? Sintaxe é a parte da gramática que estuda a disposição das palavras na frase e a das frases no discurso, bem como a relação lógica das frases entre si (Só Português (Links para um site externo.)).  Sintaxe é o estudo das regras que regem a construção de frases nas línguas naturais (Wikipédia (Links para um site externo.)).  [Linguística] Parte da linguística que se dedica ao estudo das regras e dos princípios que regem a organização dos constituintes das frases. [Informática] Conjunto de regras que regem a escrita de uma linguagem de programação (Priberam (Links para um site externo.)).  O analisador sintático O objetivo do analisador é reconhecer as estruturas do código (frases) passado ao compilador. A lista de tokens, produzida como saída da etapa anterior, é transformada em uma árvore que representa a gramática reconhecida pelo analisador.  frase.svg  A lista de lexemas dessa árove são suas folhas, no caso: [ Santo, de, casa, não, faz, milagre ]. Os tipos dos lexemas são os nós precedentes a cada um: [ Núcleo, ..., Verbo Transitivo Direto, Objeto Direto ]. Os tokens são formado a partir dessas listas de lexemas e tipos, como exemplo temos o token [ texto: Santo, tipo: Núcleo, localização [ linha:1, indice:0 ] ].  O analisador sintático é implementado a partir de uma gramática, um conjunto de regras que define como os tokens devem ser agrupados para compor a árvore sintática. Repare que a ordem dos tokens não é alterada, eles são aninhados até que um grupo raiz seja formado. Os tokens, Santo, de, e casa são aninhado no grupo Sujeito Simples; que é aninhado no grupo Oração.  Esse tipo de estrutura e de regras são formalmente representados por gramáticas livre de contexto. As gramáticas mais completas (sensíveis ao contexto e irrestritas) são complexas de implementar; e a gramática mais simples (expressões regulares) não permite representar regras (padrões) recursivos (aninhamento de blocos condicionais, if's aninhados).  Anicca, um pouco de sua gramática Vamos representar a gramática para um trecho da linguagem Anicca, e mostrar como a partir de um código fonte gerar a árvore sintática. Existem modos formais de representar a gramática, aqui não teremos tanto cuidado, [] são regras, ? regras opcionais, e -> derivação da regra.  Trecho da Gramática de Anicca:  [programa] -> [funcao] [programa] | EOF [funcao] -> [identificador] : Funcao [?parametros?] [?retorno?] :: { [?corpo?] } [identificador] -> palavra com letras minusculas [parametros] -> ( [list] ) [list] -> [identificador] : [tipo] , [list] | [identificador] : [tipo] [tipo] -> Logica | Texto | Numero [retorno] -> : [tipo]  Código de entrada da compilação: inicio:Funcao(valor:Logica,item:Texto):Numero::{ }  tiposDeVariaveis:Funcao::{ } Árvore sintática: exemplo.svg  Erros Sintáticos São erros associados com a construção da árvore sintática. Como tokens que não são associados a regra alguma. Um exemplo é uma lista de parâmetros com somente parênteses abertos para a esquerda: ( valor:Logica (.
