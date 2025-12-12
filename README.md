# PongGame---Nand2Tetris

# 🏓 Pong Game – Projeto Nand2Tetris (Jack Language)

Este projeto implementa uma versão funcional do clássico **Pong**, utilizando a linguagem **Jack**, conforme o Projeto 11 do curso **Nand2Tetris**.  
O jogo possui: **dois jogadores**, **pontuação**, **movimento realista da bola**, **rebotes**, **colisões** e **tela de Game Over**. 🎮🔥

## 🎯 Objetivo
Criar uma versão completa do Pong em Jack com:
- Dois jogadores 👥  
- Movimento e inclinação da bola ⚪  
- Colisão e rebote 🔄  
- Pontuação e Game Over 🏁

## 🧱 Arquitetura do Sistema
O projeto é dividido em três arquivos principais:

📌 **PongGame.jack** → controla regras, placar, teclado e o game loop  
📌 **Ball.jack** → física da bola, destino, movimento, inclinação e rebotes  
📌 **Bat.jack** → barras dos jogadores e seu deslocamento

## ⚪ Como a Bola Funciona
A bola possui:
- `x`, `y` → posição atual  
- `destX`, `destY` → destino  
- `dx`, `dy` → vetor direção  
- `factor` → fator de inclinação da diagonal  

O método `setDestination()` calcula:
- `dx = destX - x`
- `dy = destY - y`
- identifica o maior valor (dL) e o menor (dS)
- cria `factor = dS / dL` para gerar movimento diagonal suave ✨

Durante `move()`, a bola anda aos poucos até o destino, ajustando X e Y conforme o fator → forma um movimento suave e natural.

## 🧱 Paredes
O método `ball.move()` retorna:

| Código | Parede |
|-------|--------|
| 1 | Esquerda ⬅️ |
| 2 | Direita ➡️ |
| 3 | Superior ⬆️ |
| 4 | Inferior ⬇️ |

➡️ Paredes **1 e 2** sempre fazem rebote  
⬆️⬇️ Paredes **3 e 4** dependem da barra; se não houver colisão → Game Over 💀

## 🟩 Funcionamento das Barras
As barras possuem:
- posição  
- largura  
- direção (1 = esquerda, 2 = direita)

Jogador 1 → barra inferior  
Jogador 2 → barra superior  

Elas se movem apenas horizontalmente e nunca ultrapassam a tela.

## 💀 Regras de Derrota
### ❌ Jogador 1 perde quando:
A bola passa da barra inferior:  
`ball.getBottom() > bottomBat.getTop()`

### ❌ Jogador 2 perde quando:
A bola passa da barra superior:  
`ball.getTop() < topBat.getBottom()`

### ✔️ Antes de decretar derrota:
O jogo verifica se houve **colisão horizontal** com a barra.

Se houve colisão → rebote e ponto ✔️  
Se **não houve colisão** → tela de **Game Over** ❌

### 🪦 No Game Over:
- A bola desaparece  
- Mensagem aparece no centro  
- `exit = true` encerra o jogo  

## 🏆 Sistema de Pontuação
Quando a barra rebate a bola corretamente:
- +1 ponto 🎉  
- a barra perde 2 pixels de largura (mais difícil!)  
- o placar na tela é atualizado  

🏅 `score1` → Jogador inferior  
🏅 `score2` → Jogador superior

## 🎮 Controles
Jogador 1 (inferior): **← →**  
Jogador 2 (superior): **A D**  
Sair do jogo: **ESC**

## 📁 Estrutura de Arquivos
Pong/  
├── **Ball.jack**  
├── **Bat.jack**  
└── **PongGame.jack**

## ▶️ Como Executar
1. Compile todos os `.jack` no **Jack Compiler**  
2. Abra o diretório compilado no **VM Emulator**  
3. Execute o programa  
4. Divirta-se! 🕹️

## ✨ Possíveis Melhorias
- Velocidade variável da bola  
- IA para modo 1 jogador 🤖  
- Efeitos sonoros 🔊  
- Sprites melhores 🎨  
- Partículas e efeitos visuais 💥

## 👥 Autores
**Ana** e **Laura** – Projeto Nand2Tetris (Project 11) 🌟
