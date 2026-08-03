---
title: "Estado 10: Registo de Problemas Encontrados e Resoluções"
author: "AI Studio Research Orchestrator"
date: "2026-07-27"
state: "10_problemas"
output_file: "10_problemas.md"
---

# 1. Resumo Executivo de Problemas
- Total de problemas registados durante o ciclo de desenvolvimento: 3 problemas principais documentados no histórico.
- Tipologia: Regressão de UX (1), Falha Lógica de Condição (1), Limitação de Renderização Geométrica (1).

# 2. Matriz de Problemas e Resoluções

| ID Problema | Origem / Categoria | Como foi descoberto | Como foi resolvido | Estado Atual |
|---|---|---|---|---|
| PRB-001 | Concorrência de Estado (UX / Lógica) | Deteção empírica pelo docente: Observou-se que a simulação continuava a reagir a alterações nos *sliders* de velocidade/posição com o temporizador a decorrer. | Adição do estado bloqueador `disabled={isSimulating}` em todos os controlos de *input*. | Resolvido (Fechado). |
| PRB-002 | Ocultação Gráfica em SVG (Visualização) | Análise de casos limite (Matemática): Em cenários de Sistema Possível e Indeterminado (SPI), as duas retas sobrepunham-se e anulavam a perceção da reta inferior. | Injeção condicional da propriedade SVG `strokeDasharray="8 8"` na reta sobreposta. | Resolvido (Fechado). |
| PRB-003 | Falso Positivo na Vantagem Zero (Lógica) | Fluxo condicional imperfeito: O aviso de "dar oportunidade" disparava mesmo em situações de velocidades idênticas (onde a simulação deveria avançar em paralelo). | Expansão da verificação rigorosa exigindo que a velocidade do gato seja diferente da do rato (`mouseSpeed !== catSpeed`). | Resolvido (Fechado). |

# 3. Análise de Impacto dos Problemas
- **Bugs Críticos (Crashes):** Não foram detetados problemas ou regressões que causassem falhas fatais ou ecrãs em branco na aplicação. Todo o desenvolvimento lidou com *edge cases* lógicos e de fluxo de utilizador.
- **Problemas de Manutenção (Débito Técnico):** Embora não haja problemas ativos, a aglomeração de regras (Validação Condicional, Estado e Renderização) no `handleRun` e nos `useEffect` denota fragilidades arquiteturais inerentes à abordagem de um único ficheiro monolítico, o que exigirá refatoração se o projeto escalar.
