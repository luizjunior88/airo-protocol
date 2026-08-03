---
title: "Estado 05: Extração e Taxonomia dos Prompts do Utilizador"
author: "AI Studio Research Orchestrator"
date: "2026-07-27"
state: "05_extracao_prompts"
output_file: "05_extracao_prompts.md"
---

# 1. Resumo Executivo dos Prompts
- **Total de prompts de instrução catalogados:** 17 prompts principais (excluindo resubmissões automáticas de erros de rede e o prompt inicial truncado).
- **Distribuição quantitativa e percentual por categoria de intenção:**
  - **Interface / UX:** 1 prompt (~6%)
  - **Lógica e Modelação Matemática:** 3 prompts (~18%)
  - **Gestão de Conteúdo / Assets:** 1 prompt (~6%)
  - **Documentação e Orquestração Técnica:** 12 prompts (~70%)

# 2. Taxonomia e Tabela Geral de Prompts

| ID Prompt | Turno Associado | Categoria de Intenção | Transcrição Fiel / Literal do Prompt | Componentes Pragmáticos (Instrução Direta, Restrição Lógica, Contexto) |
|---|---|---|---|---|
| PRM-001 | T-002 | Interface / UX | "quero a imagem ainda maior. Não quero a imagem para as fichas." | **Instrução:** Aumentar escala. **Restrição:** Excluir asset do contexto de fichas. |
| PRM-002 | T-003 | Lógica / UX | "percebi agora que ao fazer uma simulação, enquanto a mesma continua a acontecer, caso algum dos sliders seja modificado pelos alunos, a simulação altera-se em tempo real. Queria que enquanto a simulação estiver a acontecer, os sliders fiquem travados." | **Contexto:** Observação de regressão de usabilidade. **Instrução:** Desativar (`disabled`) sliders. **Restrição Lógica:** Apenas quando a simulação está ativa (tempo > 0). |
| PRM-003 | T-004 | Modelação Matemática / Lógica | "No caso em que a vantagem do Jerry é zero aparece um pop-up para dar outra chance ao Jerry, entretanto se o aluno simular novamente sem mexer em nenhum slider, a mensagem não aparece e a simulação é permitida. corrija isto. No caso em que a vantagem é zero e as velocidades forem iguais, as retas ficam sobrepostas, queria que neste momento aparecesse, em vez apenas da reta vermelha, fosse uma reta tracejada vermelha com os espaços vazios preenchidos a de azul para que o aluno veja as duas retas sobrepostas." | **Contexto:** Falha no ciclo de estado e limitação visual geométrica. **Instrução:** Corrigir fluxo de reset de estado. Alterar SVG para `strokeDasharray`. **Restrição Lógica:** Acionar pontilhado apenas em cenários de Sistema Possível e Indeterminado (SPI). |
| PRM-004 | T-005 | Modelação Matemática / UX | "Perfeito! Agora uma coisa mais: Se e somente se a vantagem do Jerry for zero E as velocidades forem iguais,não exiba o pop-up para dar mais uma oportunidade, pois neste caso, já há o pop-up da boleia. Em todos os outros casos está tudo perfeito." | **Instrução:** Suprimir modal de erro. **Restrição Lógica Extrema:** `(vantagem == 0) && (velJerry == velTom)`. Exceção booleana estrita. |
| PRM-005 | T-006 | Gestão de Assets | "substitua o arquivo do enunciado do modo história para este https://drive.google.com/file/d/17NUIWZbw2e1PVc47Ldnaw_uD26a8WFDF/view?usp=sharing" | **Instrução:** Substituição estática de URL para asset externo do modo história. |
| PRM-006 | T-007 | Documentação | "Atue como um documentador técnico e pedagógico. Analise todo o histórico da nossa conversa nesta sessão..." | **Contexto:** Mudança de persona da IA. **Instrução:** Preenchimento de relatório Markdown com foco didático. |
| PRM-007 | T-008 | Documentação | "agora faça um relatório técnico e pedagógico desde o início da nossa interação" | **Instrução:** Expansão do escopo de documentação. |
| PRM-008 | T-009 | Documentação | "Há como pedir um relatório de logs?" | **Contexto:** Exploração das capacidades da plataforma AI Studio. |
| PRM-009 | T-010 | Documentação | "Quero um relatório completo em html do conteudo deste chat" | **Instrução:** Geração de artefacto HTML estático. |
| PRM-010 | T-011 | Orquestração | "# PAPEL \nAssuma o papel de uma equipa multidisciplinar..." | **Contexto:** Definição arquitetural de framework de auditoria massiva. **Instrução:** Produzir reconstrução completa. |
| PRM-011 | T-012 | Documentação | "consegue exportar de alguma forma este relatório?" | **Contexto:** Extração de dados da plataforma para disco. |
| PRM-012 | T-013 | Orquestração | "[Prompt da Equipa Multidisciplinar repetido] ... Entregue o documento num ficheiro latex e sempre que precisar escrever um codigo utilize o ambiente \minted" | **Instrução:** Formatação estrita (LaTeX/Minted) para a auditoria. |
| PRM-013 | T-014 | Orquestração | "Gera um ficheiro Markdown estritamente compatível com Pandoc intitulado 00_inicializacao.md..." | **Instrução:** Construção padronizada de relatório Fase 00. |
| PRM-014 | T-015 | Orquestração | "Gera um ficheiro Markdown estritamente compatível com Pandoc intitulado 01_inventario.md..." | **Instrução:** Construção padronizada de relatório Fase 01. |
| PRM-015 | T-016 | Orquestração | "Gera um ficheiro Markdown estritamente compatível com Pandoc intitulado 02_mapa_cronologico.md..." | **Instrução:** Construção padronizada de relatório Fase 02. |
| PRM-016 | T-018 | Orquestração | "Gera um ficheiro Markdown estritamente compatível com Pandoc intitulado 03_catalogo_versoes.md..." | **Instrução:** Construção padronizada de relatório Fase 03. |
| PRM-017 | T-019 | Orquestração | "Gera um ficheiro Markdown estritamente compatível com Pandoc intitulado 04_extracao_interacoes.md..." | **Instrução:** Construção padronizada de relatório Fase 04. |

# 3. Análise da Linguagem de Modelação e Mediação Pedagógica

### Padrão Sintático e Semântico (Uso de Operadores Lógicos)
O utilizador (docente) adota uma linguagem de modelação altamente pragmática e algorítmica, expressa em linguagem natural, demonstrando forte acuidade técnica:
- **Clareza Booleana:** O prompt PRM-004 exibe uma estrutura condicional clássica explícita — *"Se e somente se a vantagem do Jerry for zero E as velocidades forem iguais"*. Esta construção (`IF (A == 0 && B == C)`) elimina qualquer margem de alucinação ou ambiguidade da IA.
- **Isolamento de Domínios:** Em PRM-001, a diretriz estabelece uma regra e uma restrição isolada simultaneamente ("quero a imagem ainda maior. Não quero a imagem para as fichas"), orientando a IA a bifurcar o código da renderização da interface em vez de aplicar estilos globais.

### Tradução de Intenções Pedagógicas em Regras Computacionais
O histórico revela que o utilizador monitoriza ativamente a jornada cognitiva do aluno final ("student-centered design"), mitigando atritos epistemológicos:
1. **Proteção Cognitiva contra Estado Concorrente:** O pedido PRM-002 reflete uma perceção de campo. O facto de um aluno poder alterar um *slider* durante o tempo de execução destrói a coesão do Movimento Retilíneo Uniforme. O professor não pediu "desative os botões", mas enquadrou o problema didático: *"a simulação altera-se em tempo real (...) sliders fiquem travados"*, levando a IA a usar o booleano de runtime (`isSimulating`).
2. **Representação Visual de Sistemas (SPI):** No PRM-003, o problema de retas coincidentes em sistemas de equações — que visualmente se sobrepõem e parecem apenas uma linha (ocultando a reta inferior) — é corrigido através da introdução brilhante de uma linha tracejada (`strokeDasharray`). O professor exige que os *espaços vazios sejam preenchidos a azul* para que o cérebro do aluno consiga ler a duplicidade do sistema sobreposto, um paradigma clássico da didática da matemática traduzido de forma fluida em código SVG condicional.
3. **Engenharia de Prompt Orquestrada:** Na fase final, o utilizador adota um paradigma de Orquestrador de Inteligência Artificial, recorrendo a prompts tabulares e restrições absolutas ("Regra estrita: Baseia-te estritamente nos excertos..."). A adoção de cabeçalhos YAML e a obrigatoriedade de Markdown compatível com Pandoc evidenciam a intencionalidade de inserir os artefactos diretamente em pipelines de compilação bibliográfica ou publicações.
