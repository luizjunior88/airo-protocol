---
title: "Estado 07: Catálogo e Mapeamento de Funcionalidades"
author: "AI Studio Research Orchestrator"
date: "2026-07-27"
state: "07_funcionalidades"
output_file: "07_funcionalidades.md"
---

# 1. Resumo Executivo das Funcionalidades
- **Visão geral dos modos operacionais do simulador:** O sistema foi desenhado em torno de dois modos de visualização primários (Modo História/Story e Modo Analítico/Math), apoiados por um módulo secundário de acesso a recursos (Fichas Pedagógicas).
- **Estrutura de controlo de acessos e regras de permissão:** A aplicação emprega *gatekeeping* pedagógico através de palavras-passe locais estáticas. O "Modo História" é de acesso público (livre). O "Modo Analítico" requer a validação de uma senha (`velocidadefuriosa`). O repositório de Fichas exige uma chave separada de acesso (`profmat`). Este modelo restringe a evolução do aluno até que a dedução lógica necessária para desbloquear o conhecimento superior seja alcançada.

# 2. Matriz de Funcionalidades da Aplicação

| ID Funcionalidade | Nome do Recurso / Módulo | Modo de Acesso / Condição | Mecânica de Funcionamento | Propósito Pedagógico / Didático |
|---|---|---|---|---|
| FNC-001 | Modo História (`viewMode === 'story'`) | Livre | Representação gamificada do problema cinemático (Tom e Jerry), com controlos inteiros e foco na intuição e geometria visual do Movimento Retilíneo Uniforme. | Introduzir o aluno ao conceito de posição, velocidade, tempo de intersecção e taxa de variação constante de forma intuitiva. |
| FNC-002 | Modo Analítico (`viewMode === 'math'`) | Palavra-passe (`velocidadefuriosa`) | Comutação da UI para exibição explícita do sistema cartesiano, equações lineares ($s = s_0 + v \cdot t$) subjacentes e precisão decimal no controlo numérico dos parâmetros de contorno. | Relacionar as grandezas físicas aos modelos algébricos puros, solidificando a noção de um sistema de equações lineares. |
| FNC-003 | Acesso a Fichas Pedagógicas | Palavra-passe (`profmat`) | Menu modal que valida a senha local e utiliza `window.open` para referenciar PDFs remotos no Google Drive consoante o modo ativo (Story ou Math). | Fornecer a documentação de suporte (guião formativo) para acompanhar as explorações na aplicação simulada. |
| FNC-004 | Controlo Dinâmico do Eixo Y (Posição e Velocidade) | Livre (Travado por `isSimulating`) | Utilização de `input type="range"` e botões de incremento (setas) para alterar os estados de posições originais e vetores de velocidade dos corpos envolvidos. | Experimentação prática para verificar como a alteração das variáveis independentes muda o tempo e o ponto de intersecção. |
| FNC-005 | Renderização Temporal (Gráficos) | Livre | Desenho em tempo real através de motor gráfico (Recharts) acompanhando as variáveis em colisão calculadas num intervalo de tempo iterativo (`currentTime`). | Permite a leitura de gráficos Distância-Tempo (d-t) e a interpretação geométrica do avanço temporal. |

# 3. Análise Detalhada das Regras de Domínio e Exceções

### Prevenção de Manipulação de Variáveis
A arquitetura de UI detém um mecanismo estrito de integridade de simulação: quando a simulação é iniciada (temporizador em *runtime*), todos os componentes que alteram as constantes de movimento (velocidades e pontos de partida) ficam bloqueados de imediato, implementado via injeção generalizada do atributo `disabled={isSimulating}`. Este fluxo evita a deturpação gráfica e impede o desenvolvimento de paradoxos cinemáticos, salvaguardando a estabilidade da simulação.

### Tratamento de Exceções Cinemáticas
O utilizador (docente) identificou duas zonas de risco conceptual que foram modeladas em restrições booleanas específicas no ficheiro `App.tsx`:
1. **Regra de "Vantagem Zero" (Impossibilidade Prática):** Quando o sistema opera no modo história e as velocidades são diferentes, a posição inicial do fugitivo (Jerry) não pode ser zero. A aplicação inspeciona isto (via função `handleRun` e ciclo `useEffect` com `params.mouseStart === 0 && params.mouseSpeed !== params.catSpeed`) alertando o utilizador com o estado de erro `showNoAdvantageWarning` para "dar uma chance" ao fugitivo, forçando a compreensão de sistemas não-concorrentes ou imediatos.
2. **Sistema Possível Indeterminado (SPI):** Quando a vantagem original é zero e ambas as velocidades se equivalem, as duas funções espaciais convergem numa única reta no gráfico cartesiano. Em renderizações SVG tradicionais, a camada superior oculta a base. Para corrigir este enviesamento e mostrar que ambas existem coincidentemente, um sistema condicional adiciona o atributo gráfico `strokeDasharray="8 8"` à linha sobreposta. Isso preenche visualmente os vazios e ilustra a infinitude das soluções de um SPI.

### Fluxo de Autenticação Distribuído e Feedbacks de Erro
A introdução de falhas de autenticação reflete um domínio assimétrico, intencional em design:
- Se falhar o acesso analítico (falta de conhecimento da dedução matemática), a UI preenche a tela com um elemento fotográfico massivo do Google Drive (`w-32 h-32 md:w-48 md:h-48`) gerando um aspeto lúdico/recreativo para o falhanço do aluno.
- Se a palavra-passe para recursos formativos (`profmat`) falhar (`fichaPasswordError`), o feedback contrai-se para um elemento meramente textual, mantendo o aspeto técnico reservado aos elementos estritamente de trabalho de aula. A obtenção bem-sucedida efetua sempre *routing* cego via `window.open` para um documento do Drive atualizado programaticamente (e.g. alterado no T-006).
