# LIGHTSOUT RGB*

## Apague todas as l�mpadas

Autores: Bruno Ribas, Bruno Ribeiro, Igor Penha, Lucas Bergholz e Wagner Cunha

### Descri��o do jogo

O jogo LightsOut � um quebra-cabe�a eletr�nico lan�ado pela Tiger Electronics em 1995. No jogo f�sico, h� uma matriz de luzes que podem estar ligadas ou desligadas. O objetivo � desligar todas as luzes, por�m, ao pressionar uma luz, seu estado e o estado das luzes adjacentes s�o invertidos.

A hist�ria por tr�s do jogo � que, em uma noite escura, todas as luzes da cidade de Lightsville apagaram repentinamente. Para restaurar a luz na cidade, o jogador assume o papel de um engenheiro el�trico encarregado de restaurar a energia nas ruas iluminadas. O desafio est� em encontrar a sequ�ncia correta de cliques para trazer a luz de volta a todas as ruas.

Com a populariza��o dos dispositivos eletr�nicos e a evolu��o dos jogos digitais, o LightsOut foi adaptado para v�rias plataformas, como computadores, smartphones e tablets. A ess�ncia do jogo permanece a mesma: resolver o quebra-cabe�a desligando todas as luzes da matriz.

Nesta vers�o modificada do jogo LightsOut, introduzimos a vers�o LightsOut RGB, aqui as luzes do jogo n�o est�o restritas � apenas dois estados (ON/OFF) mas sim, quatro estados poss�veis (RED, GREEN, BLUE e OFF). Outrossim, n�o s� as luzes adjacentes s�o invertidos, mas todas as luzes que estiverem na mesma linha e coluna da luz inicialmente clicada. Todavia, foi introduzido tamb�m a caracter�stica de bot�es quebrados. Essa modifica��o foi inspirada em jogos f�sicos que foram muito usados, desse modo, alguns bot�es podem apresentar diferentes comportamentos em resposta as a��es executadas. Exitem quatro tipos de bot�es quebrados:

1. Os que n�o mudam de estado quando clicados. No entanto, as luzes adjacentes, mesma linha e coluna, ainda s�o afetadas e trocariam de estado.
2. Os que n�o mudam de estado como consequ�ncia do clique de um bot�o em mesma coluna. No entanto, mudam de estado quando clicados ou como conseq�ncia do clique de um bot�o em mesma linha.
3. Os que n�o mudam de estado como consequ�ncia do clique de um bot�o em mesma linha. No entanto, mudam de estado quando clicados ou como conseq�ncia do clique de um bot�o em mesma coluna.
4. Os que n�o mudam de estado como consequ�ncia nem do clique de um bot�o em mesma linha nem em mesma coluna. No entando, mudam de estado quando clicados.

### Descri��o do problema

Voc� desenvolver um programa que leia a especifica��o do desafio, gere o modelo PDDL do jogo LightsOut RGB, crie os arquivos de dom�nio e problema PDDL correspondentes, chame o planejador selecionado com os par�metros corretos, obtenha o plano retornado pelo planejador e gere uma sa�da no formato especificado na descri��o do trabalho.

### Descri��o dos planejadores

Existem v�rios planejadores dispon�veis para resolver o problema do jogo LightsOut. A localiza��o e a forma de chamada dos planejadores s�o as seguintes:

- **Planejadores Madagascar (M, Mp, MpC):**
  - Localiza��o: `/tmp/dir/software/planners/madagascar/{M,Mp,MpC}`.
- **Fast Downward:**
  - Localiza��o: `/tmp/dir/software/planners/downward/fast-downward.py`.
  - Localiza��o: `/tmp/dir/software/planners/downward-fdss23/fast-downward.py`.
  - Localiza��o: `/tmp/dir/software/planners/scorpion-maidu/fast-downward.py`.
- **Planejador em Julia:**
  - Localiza��o: `/tmp/dir/software/planners/julia/planner.jl`.

### Como classificar nesta modalidade

Nesta modalidade de classifica��o, o problema � dividido em tr�s categorias: AGILE, SATISFICING e OPTIMAL. A pontua��o � computada da seguinte forma:

- **Categoria AGILE:**
  - A pontua��o � obtida pela f�rmula 
    ```
    log(TEMPPODEEXECUCAO) / log(150)
    ```
    Se o tempo de execu��o for menor ou igual a 1 segundo, a pontua��o � 1.
  - A track tem um time limit de 30s.

- **Categoria SATISFICING:**
  - A pontua��o � calculada pela f�rmula 
    ```
    C* / C
    ```
    onde `C*` � a quantidade de passos do plano de refer�ncia e `C` � a quantidade de passos do plano encontrado.
  - Quanto menor for a quantidade de passos do plano encontrado em rela��o ao plano de refer�ncia, melhor ser� a pontua��o.
  - A track tem um time limit de 180s.

- **Categoria OPTIMAL:**
  - O objetivo � responder o plano �timo.
  - O desempenho � avaliado pela corretude do plano e n�o pela pontua��o.
  - A track tem um time limit de 180s.

O vencedor ser� determinado com base na soma dos pontos obtidos em todas as categorias.

### Entrada

A entrada � composta com um conjunto de linhas, e dever�o ser lidas da entrada padr�o. As linhas, da entrada, representam a matriz do jogo, voc� descobrir� as dimens�es conforme faz a leitura. A entrada termina em EOF.

Cada l�mpada/bot�o � representado por dois caracteres, um representando a condi��o (tipo que quebra) do bot�o e outro o estado atual da luz, nessa ordem, conforme a descri��o abaixo:

- `W` representa uma luz desligada;
- `R` representa uma luz ligada na cor vermelha;
- `G` representa uma luz ligada na cor verde;
- `B` representa uma luz ligada na cor azul;
- `-` representa a condi��o de um bot�o n�o quebrado;
- `*` representa a condi��o de um bot�o com o tipo de quebra 1;
- `_` representa a condi��o de um bot�o com o tipo de quebra 2;
- `|` representa a condi��o de um bot�o com o tipo de quebra 3;
- `#` representa a condi��o de um bot�o com o tipo de quebra 4;

### Sa�da

A sa�da � composta por uma �nica linha contendo as coordenadas dos bot�es apertados, em ordem, a fim de obter todas as l�mpadas apagadas. Cada clique �
