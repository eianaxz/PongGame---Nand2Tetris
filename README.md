# PongGame---Nand2Tetris

# Pong Game – Projeto Nand2Tetris (Jack Language)
Este projeto implementa uma versão funcional do clássico **Pong**, utilizando a linguagem **Jack**, conforme definido no Projeto 11 do curso Nand2Tetris. O jogo possui dois jogadores, sistema de pontuação, checagem de colisão, regras de derrota, movimento com inclinação e rebote.
## Objetivo
Criar um Pong completo em Jack com: dois jogadores, movimentação realista da bola, colisões, rebotes, pontuação e tela de Game Over.
## Arquitetura do Sistema
O projeto usa três classes principais:  
**PongGame.jack** → controla regras, placar, game loop e teclado.  
**Ball.jack** → física, movimento, destino, inclinação e rebotes.  
**Bat.jack** → barras dos jogadores e seus movimentos.
## Funcionamento da Bola
A bola possui `x`, `y` (posição), `destX`, `destY` (destino), `dx`, `dy` (vetor de direção) e `factor` (inclinação).  
O método `setDestination()` calcula:  
`dx = destX - x`  
`dy = destY - y`  
Depois ele descobre qual eixo é o maior (dL) e qual é o menor (dS). O valor `factor = dS / dL` emula decimais e cria uma diagonal suave ao mover a bola.  
No movimento (`move()`), a bola se aproxima do destino seguindo o fator de inclinação, ajustando X e Y proporcionalmente.
## Paredes
O método `ball.move()` retorna:
1 → parede esquerda  
2 → parede direita  
3 → parede superior  
4 → parede inferior  
Paredes 1 e 2 sempre fazem rebote horizontal.  
Paredes 3 e 4 dependem da colisão com as barras (senão → derrota).
## Funcionamento das Barras
Cada barra tem posição, largura e direção (1 = esquerda, 2 = direita). As barras se movem horizontalmente dentro dos limites. Jogador 1 controla a barra inferior; Jogador 2 controla a barra superior.
## Regras de Derrota
### Jogador 1 perde quando:
A bola passa da altura da barra inferior:
`ball.getBottom() > bottomBat.getTop()`
### Jogador 2 perde quando:
A bola passa da barra superior:
`ball.getTop() < topBat.getBottom()`
Quando isso acontece, o jogo verifica colisão horizontal:
Se **toca na barra** → rebate e ganha ponto.  
Se **não toca** → Game Over.
### O que acontece no Game Over:
- a bola desaparece  
- aparece mensagem no centro da tela  
- `exit = true` e o jogo termina
## Pontuação
Quando o jogador rebate com sucesso:
- ganha +1 ponto  
- a largura da barra diminui (-2 pixels) para aumentar dificuldade  
- o placar é atualizado na tela  
`score1` = jogador inferior  
`score2` = jogador superior
## Controles
Jogador 1 (inferior): ← →  
Jogador 2 (superior): A D  
Geral: ESC para sair.
## Estrutura de Arquivos
Pong/  
├── Ball.jack  
├── Bat.jack  
└── PongGame.jack
## Como Executar
1) Compile todos os `.jack` no Jack Compiler  
2) Abra o diretório compilado no VM Emulator  
3) Execute o programa  
4) Jogue!
## Melhorias Futuras
- Velocidade variável da bola  
- Modo 1 player (IA)  
- Sons  
- Sprites melhores  
- Efeitos visuais
## Autores
Seu nome e Laura – Projeto Nand2Tetris (Project 11)
