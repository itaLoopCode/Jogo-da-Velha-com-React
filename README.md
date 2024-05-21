
Este código demonstra a estrutura básica de um jogo da velha construído com componentes React. Ele lida com a gestão de turnos, atualizações de estado do jogo, detecção de vencedores e permite o acompanhamento do histórico do jogo.

### Componente Square:

* Este componente representa um único quadrado no jogo da velha.
* Ele recebe duas props:
    * `valor`: O valor atual do quadrado (seja 'X', 'O' ou null).
    * `onSquareClick`: Uma função a ser chamada quando o quadrado é clicado.
* Ele renderiza um elemento de botão que exibe o `valor` e chama a função `onSquareClick` quando clicado.

### Componente Board:

* Este componente representa todo o tabuleiro do jogo da velha.
* Ele recebe três props:
    * `xIsNext`: Um booleano que indica se é a vez de X ou O.
    * `quadrados`: Um array contendo o estado atual de todos os quadrados (9 elementos).
    * `onPlay`: Uma função a ser chamada quando um quadrado é clicado.
* Ele define uma função `handleClick` que lida com cliques em quadrados individuais.
    * Ele verifica se já há um vencedor ou se o quadrado está preenchido antes de continuar.
    * Cria uma cópia do array `quadrados` (`nextSquares`).
    * Atualiza o quadrado clicado com a marca do jogador atual (X ou O).
    * Chama a função `onPlay` para atualizar o estado com os novos `nextSquares`.
* Ele calcula o vencedor usando a função `calculateWinner`.
* Define a mensagem de status do jogo com base no vencedor ou no jogador atual.
* Renderiza o tabuleiro com 3 linhas, cada uma contendo 3 componentes `Square`.

### Componente Game (Principal):

* Este componente gerencia o estado geral do jogo e a lógica.
* Ele usa o hook `useState` do React para manter o estado do jogo:
    * `xIsNext`: Rastreia quem está jogando.
    * `história`: Um array contendo a história de todos os estados do tabuleiro após cada movimento.
* Ele define funções para lidar com ações do jogo:
    * `handlePlay`: Atualiza o histórico com o novo estado do tabuleiro e troca as jogadas.
    * `jumpTo`: Esta função lida com a mudança para um movimento anterior no histórico do jogo (atualmente não implementado).
* Ele calcula uma lista de movimentos (botões) para permitir que você pule para estados anteriores na história do jogo.
* Renderiza o jogo com o tabuleiro e a lista de histórico de movimentos.

### Função calculateWinner:

* Esta função verifica se há um vencedor no estado atual do tabuleiro.
* Ele define um array contendo todas as combinações vencedoras (linhas de 3 quadrados).
* Ele itera por cada combinação vencedora e verifica se todos os quadrados na linha têm o mesmo valor ('X' ou 'O').
* Se uma combinação vencedora for encontrada, ela retorna o jogador vencedor ('X' ou 'O').
* Caso contrário, retorna nulo.
