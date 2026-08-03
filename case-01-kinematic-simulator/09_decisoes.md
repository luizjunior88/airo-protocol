---
title: "Estado 09: Registo e Análise de Decisões Técnicas e Pedagógicas"
author: "AI Studio Research Orchestrator"
date: "2026-07-27"
state: "09_decisoes"
output_file: "09_decisoes.md"
---

# 1. Resumo Executivo das Decisões
O desenvolvimento do Simulador Cinemático foi fortemente impulsionado por um alinhamento rigoroso entre as restrições da física clássica (Movimento Retilíneo Uniforme) e os objetivos didáticos em sala de aula. As decisões mapeadas no histórico evidenciam uma priorização da **clareza cognitiva do aluno** em detrimento de abordagens de engenharia de software tradicionais (como segurança criptográfica ou modularização extrema).

- **Total de decisões arquiteturais/pedagógicas críticas mapeadas:** 5.
- **Distribuição:** 
  - Regras de Negócio e Modelação Matemática (40%)
  - UX/UI (40%)
  - Arquitetura e Segurança (20%)

# 2. Matriz Geral de Registos de Decisão (ADR / PDR)

| ID Decisão | Turno / Versão | Categoria | Decisão Tomada | Motivação / Justificação | Impacto e Trade-offs |
|---|---|---|---|---|---|
| DEC-001 | T-002 / VER-002 | UX/UI | Aplicação de assimetria no feedback visual de erro (Imagem gigante no Modo Analítico, apenas texto nas Fichas). | Separar o peso lúdico da falha de conhecimento (Modo Analítico) do erro operacional no acesso a materiais (Fichas). | Aumentou a complexidade da renderização condicional, mas clarificou o contexto visual para o aluno. |
| DEC-002 | T-003 / VER-003 | Pedagógica / UX | Injeção global de `disabled={isSimulating}` em todos os sliders e botões de input físico. | Manipulação de variáveis em tempo real destruía a consistência do modelo (MRU). | Proteção rigorosa do *runtime* à custa da interatividade fluida contínua. |
| DEC-003 | T-004 / VER-004 | Matemática / UI | Implementação condicional da propriedade SVG `strokeDasharray="8 8"` no Recharts para sistemas coincidentes. | Sistemas Possíveis e Indeterminados (SPI) originavam retas sobrepostas, parecendo haver apenas uma. | Solução de altíssimo impacto pedagógico e custo computacional nulo ($O(1)$). |
| DEC-004 | T-005 / VER-005 | Modelação Lógica | Refinamento da regra de "Vantagem Zero" para incluir o diferencial de velocidades (`mouseSpeed !== catSpeed`). | O popup impedia configurações simétricas (mesma velocidade e partida) de serem simuladas. | Complexidade condicional acrescida, mas eliminação total de falsos positivos na UX. |
| DEC-005 | Histórico Geral | Arquitetura | *Hardcoding* de palavras-passe locais (`velocidadefuriosa` e `profmat`) no cliente em vez de base de dados. | Criação de um *gatekeeping* puramente didático sem necessidade de backend, latência ou contas de utilizador. | Sem segurança criptográfica real (inseguro contra injeção ou devtools), mas perfeito para atrito cognitivo numa sala de aula. |

# 3. Análise Detalhada das Decisões Chave

### 3.1. Trancamento de Inputs durante Simulação (Prevenção de Concorrência)
- **O Problema:** A interface reativa do React (via `onChange` nos sliders) permitia aos alunos deslizar a posição de partida dos corpos enquanto o relógio (`currentTime`) estava a avançar. O modelo físico, baseado na função afim $s = s_0 + v \cdot t$, sofria saltos descontínuos irrealistas se $s_0$ variasse em tempo real, corrompendo a representação cinemática e criando falsos modelos mentais nos alunos.
- **A Decisão:** A IA e o utilizador concordaram em trancar a manipulação de variáveis espaciais/vetoriais na dimensão de planeamento. Através do booleano de estado `isSimulating`, a UI desativa componentes (`disabled`) e reduz a opacidade (`opacity-50`), forçando o aluno a separar o tempo de *setup* empírico do tempo de observação empírica.
- **Trade-off:** Retira-se a capacidade de brincar dinamicamente (como num videojogo de física) em prol do rigor científico de uma experiência controlada.

### 3.2. Representação Visual de Sistemas Possíveis Indeterminados (SPI)
- **O Problema:** Matematicamente, quando as posições e as velocidades de ambos os personagens são iguais (vantagem = 0, velocidades equivalentes), as retas geradas no gráfico Distância-Tempo coincidem espacialmente (são linearmente dependentes). Devido à natureza da renderização em camadas do Recharts (e do motor SVG), a última linha desenhada (azul) sobrepunha-se à primeira (vermelha), apagando-a visualmente. O aluno era induzido em erro, achando tratar-se do gráfico de apenas um personagem.
- **A Decisão:** Em vez de duplicar dados de eixo ou aplicar sombras pesadas (`shadow-dom`), a decisão recaiu sobre a aplicação de um tracejado (`strokeDasharray="8 8"`) condicionado pelo tipo de colisão (`intersection.type === 'SPI'`). Os "espaços vazios" deixam ver a linha sólida inferior.
- **Trade-off:** Brilhante em termos de performance e legibilidade, sendo a tradução gráfica perfeita de um conceito abstrato matemático sem recorrer a bibliotecas de visualização 3D.

### 3.3. Autenticação Client-Side para Gatekeeping Pedagógico
- **O Problema:** Era necessário bloquear os alunos para que não saltassem etapas (e.g., olhar para o gráfico matemático analítico antes de testarem intuitivamente na história, ou abrirem fichas e gabaritos indevidamente).
- **A Decisão:** Implementação de verificação em *plain-text* dentro da lógica do componente React (`if (fichaPassword === 'profmat')`).
- **Trade-off:** Num sistema corporativo, armazenar senhas em *client-side* é uma falha crítica de segurança. Contudo, em engenharia didática, esta arquitetura (SPA estática) elimina custos de *cloud storage*, latência e infraestrutura Backend. O objetivo não é proteger dados sensíveis de cibercrimes, mas sim criar uma **fricção educacional** suficiente para bloquear o impulso imediato de um aluno. A decisão demonstra excelente discernimento de contexto operacional por parte da equipa de desenvolvimento.
