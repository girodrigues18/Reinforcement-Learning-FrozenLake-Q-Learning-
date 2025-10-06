# 🧊 FrozenLake Q-Learning - Reinforcement Learning

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/)
[![Gymnasium](https://img.shields.io/badge/Gymnasium-0.29%2B-orange)](https://gymnasium.farama.org/)
[![Reinforcement Learning](https://img.shields.io/badge/Reinforcement-Learning-green)](https://www.ibm.com/think/topics/reinforcement-learning)

Uma implementação do algoritmo Q-Learning para resolver o ambiente FrozenLake-v1 do Gymnasium, onde um agente deve aprender a atravessar um lago congelado evitando buracos.

## 📋 Sobre o Projeto

Este projeto demonstra os fundamentos do **Aprendizado por Reforço** através da implementação prática do algoritmo **Q-Learning**. O agente começa sem conhecimento prévio e aprende através de tentativa e erro a navegar pelo ambiente FrozenLake.

**Problema**: Em um grid 4x4, o agente deve sair do ponto inicial (S) e chegar ao objetivo (G), evitando buracos (H) no gelo.

**Desafio**: O ambiente é "escorregadio" - as ações têm apenas 33% de chance de sucesso, tornando o aprendizado mais desafiador e realista.

### 🗺️ Visualização do Ambiente
SFFF

FHFH

FFFH

HFFG

🟦 S = Starting point (Safe) - Ponto de partida

⬜ F = Frozen surface (Safe) - Superfície congelada segura

🕳️ H = Hole (Game Over) - Buraco (Fim de jogo)

🎯 G = Goal (Success) - Objetivo (Sucesso)

## 🧠 O Algoritmo: Q-Learning

### Conceitos Fundamentais

- **Q-Table**: Tabela que armazena o valor esperado de cada par estado-ação
- **Política ε-greedy**: Balanceia exploração (ações aleatórias) e exploração (melhores ações conhecidas)
- **Equação de Atualização**:
Q(s,a) = Q(s,a) + α[r + γ * max(Q(s',a')) - Q(s,a)]

### Hiperparâmetros Utilizados

| Parâmetro | Valor | Descrição |
|-----------|-------|-----------|
| α (alpha) | 0.8 | Taxa de aprendizado |
| γ (gamma) | 0.95 | Fator de desconto |
| ε (epsilon) | 1.0 → 0.01 | Taxa de exploração (com decaimento) |
| Episódios | 20,000 | Número de sessões de treinamento |

## 📊 Resultados Esperados

Após a execução completa do treinamento (cerca de 2-5 minutos), o script exibirá:
### Desempenho Típico
- **Taxa de sucesso**: 70-85% em ambiente escorregadio
- **Estabilidade**: Política converge após ~15,000 episódios
- **Robustez**: Agente aprende caminhos alternativos devido à natureza estocástica

## 🏗️ Estrutura do Código

### Componentes Principais

1. **Inicialização do Ambiente**
   - Criação do ambiente FrozenLake-v1
   - Configuração do modo "escorregadio"

2. **Q-Table**
   - Matriz estados × ações inicializada com zeros
   - Atualizada iterativamente durante o treinamento

3. **Loop de Treinamento**
   - Política ε-greedy para seleção de ações
   - Atualização da Q-table usando a equação do Q-Learning
   - Decaimento gradual da exploração

4. **Avaliação**
   - Teste da política aprendida (sem exploração)
   - Medição da taxa de sucesso em 1000 episódios

## 🎯 Aprendizados e Insights

### Conceitos Demonstrados
- **Exploração vs Exploração**: Como balancear descoberta e aproveitamento do conhecimento
- **Aprendizado Temporal-Difference**: Atualizações baseadas em estimativas futuras
- **Políticas de Decisão**: Desenvolvimento de estratégias ótimas através de reforço

### Desafios Superados
- **Ambiente Estocástico**: Ações nem sempre produzem o resultado esperado
- **Recompensas Escassas**: Apenas recompensa no objetivo final
- **Convergência Lenta**: Necessidade de muitas iterações para estabilização
