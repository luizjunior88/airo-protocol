---
title: "Estado 03: Catálogo de Versões do Código Fonte"
author: "AI Studio Research Orchestrator"
date: "2026-07-27"
state: "03_catalogo_versoes"
output_file: "03_catalogo_versoes.md"
---

# 1. Resumo do Catálogo de Versões
- **Total de iterações do código fonte principal (`src/App.tsx`) identificadas:** 6 versões com alterações confirmadas através de `edit_file`.
- **Mapeamento de modificações nas dependências:** Nenhuma alteração no `package.json` ou nas configurações estruturais (`vite.config.ts`, `tsconfig.json`) foi efetuada durante o histórico coberto. Todo o esforço de desenvolvimento incidiu estritamente sobre a lógica, UI e estado no `src/App.tsx`.

# 2. Tabela de Evolução do Código Fonte

| ID Versão | Turno Associado | Ficheiro(s) Alterado(s) | Modificações Principais / Funções Afetadas | Diferenças Estruturais / Refatorações |
|---|---|---|---|---|
| VER-001 | T-001 | `src/App.tsx` | UI de Feedback de Senha (Renderização Condicional) | Aumento da dimensão de imagem (Tailwind: `w-20 h-20 md:w-24 md:h-24`). Transformação do container em `flex-col`. |
| VER-002 | T-002 | `src/App.tsx` | UI de Feedback de Senha (Renderização Condicional) | Escala da imagem principal aumentada para `w-32 h-32 md:w-48 md:h-48`. Remoção completa do asset de imagem no erro de senha das fichas (reversão estrutural para um simples parágrafo textual). |
| VER-003 | T-003 | `src/App.tsx` | Controlos de Input (Sliders e Botões de Incremento) | Injeção da propriedade `disabled={isSimulating}` e adição das pseudoclasses Tailwind `disabled:opacity-50 disabled:cursor-not-allowed` em todos os manipuladores físicos (`mouseStart`, `mouseSpeed`, `catSpeed`, `catStart`). |
| VER-004 | T-004 | `src/App.tsx` | `handleRun` e Componente `<Line>` do Recharts | Adição de bloqueio e aviso (`setShowNoAdvantageWarning(true)`) no `handleRun` caso a vantagem inicial de Jerry seja zero. Introdução de propriedade SVG `strokeDasharray` dinâmica. |
| VER-005 | T-005 | `src/App.tsx` | Lógica de Estado `useEffect` e Função `handleRun` | Refatoração condicional do alerta de vantagem: Inclusão do comparador `params.mouseSpeed !== params.catSpeed`. Adição das dependências necessárias no array do `useEffect`. |
| VER-006 | T-006 | `src/App.tsx` | Handlers de Eventos de Teclado e Botões de Confirmação | Substituição estática do ID do ficheiro do Google Drive acedido por `window.open` quando `selectedFicha === 'story'` e a senha coincide com `profmat`. |

# 3. Análise Detalhada por Versão

### VER-001 (Turno T-001)
- **Descrição Técnica:** O código JSX encarregado de mostrar mensagens de "Senha incorreta" foi alterado. A imagem (`<img>`) passou da classe `w-5 h-5` para `w-20 h-20 md:w-24 md:h-24 drop-shadow-md`. O contentor alterou-se de `flex items-center gap-2 pl-1 pt-1` para `flex flex-col items-center justify-center gap-2 pt-4 pb-2`.
- **Motivação:** A imagem original era demasiado pequena para ter impacto visual.
- **Impacto no Runtime:** Ao inserir uma senha errada, a notificação visual torna-se no elemento central da ação.

### VER-002 (Turno T-002)
- **Descrição Técnica:** A imagem do modal principal foi novamente incrementada para `w-32 h-32 md:w-48 md:h-48`. Em contraste, na secção que lida com a senha da funcionalidade "fichas" (`fichaPasswordError`), o bloco DOM contendo a imagem foi totalmente removido, regressando a um elemento `<p>` com margens.
- **Motivação:** Exigência explícita do utilizador para "quero a imagem ainda maior" mas "Não quero a imagem para as fichas". 
- **Impacto no Runtime:** Assimetria propositada no feedback: erro de acesso analítico aciona um grande popup lúdico, erro de acesso às fichas apresenta uma mensagem de texto nativa.

### VER-003 (Turno T-003)
- **Descrição Técnica:** Múltiplas injeções no JSX dos painéis de controlo do simulador. O parâmetro `disabled={isSimulating}` foi adicionado a `<button>` e `<input type="range">`. Adicionadas classes de estilo (`disabled:opacity-50 disabled:cursor-not-allowed`).
- **Motivação:** "Queria que enquanto a simulação estiver a acontecer, os sliders fiquem travados" para impedir que alunos alterem os valores de posições ou velocidades e enviesem a simulação em curso.
- **Impacto no Runtime:** Proteção contra manipulação acidental/intencional durante a animação do tempo, travando a concorrência na alteração do estado global de física.

### VER-004 (Turno T-004)
- **Descrição Técnica:** Alteração da função encarregue de arrancar o temporizador (`handleRun`). Se `viewMode === 'story'` e a posição inicial de Jerry for 0, o estado do alerta de boleia é invocado (sem prosseguir a simulação). No componente gráfico do Recharts, foi adicionada a lógica `strokeDasharray={intersection.type === 'SPI' ? "8 8" : undefined}`.
- **Motivação:** Forçar o aluno a dar margem ao personagem. Ao mesmo tempo, garantir a distinção visual (linha tracejada) para equações coincidentes no gráfico (SPI - Sistema Possível e Indeterminado).
- **Impacto no Runtime:** Bloqueio da simulação em condições fisicamente inviáveis para o jogo e correção visual onde retas coincidentes pareciam apenas uma linha singular no plano cartesiano.

### VER-005 (Turno T-005)
- **Descrição Técnica:** Refatoração lógica no `useEffect` de monitorização de vantagem e na função `handleRun`. A condição de disparo da mensagem de erro (`setShowNoAdvantageWarning`) passou de `mouseStart === 0` para `mouseStart === 0 && params.mouseSpeed !== params.catSpeed`.
- **Motivação:** Se as velocidades forem iguais e a vantagem zero, a simulação decorre com ambos paralelos/coincidentes (regras da cinemática em sobreposição), não justificando o alerta que impedia a simulação.
- **Impacto no Runtime:** Eliminação de falsos positivos da validação UX. O aluno pode agora executar uma simulação "perfeitamente simétrica".

### VER-006 (Turno T-006)
- **Descrição Técnica:** Num manipulador de eventos `onKeyDown` (Enter) e `onClick` para desencadear um `window.open`. O ID antigo do Google Drive (`1GEjcujzOgw4_IgF_gil4EuvHkdW2jBCM`) associado ao modo "story" foi trocado por um novo (`17NUIWZbw2e1PVc47Ldnaw_uD26a8WFDF`).
- **Motivação:** Pedido direto para substituição do ficheiro de enunciado do modo história.
- **Impacto no Runtime:** A hiperligação da interface redigida aos alunos aponta agora para um novo documento PDF no ecossistema Drive.
