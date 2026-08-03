---
title: "Estado 13: Matriz de Codificação Qualitativa e Livro de Códigos (Codebook)"
author: "AI Studio Research Orchestrator"
date: "2026-07-27"
state: "13_codificacao"
output_file: "13_codificacao.md"
---

# 1. Resumo Executivo da Codificação
A presente fase estabelece uma matriz de codificação qualitativa aplicada ao *corpus* documental extraído nos estados `00` a `12`. A metodologia de análise temática permitiu categorizar os padrões de comportamento do utilizador (docente) e as correspondentes soluções algorítmicas da IA.
As categorias temáticas emergentes estruturam-se em quatro eixos principais:
- **Design Didático e Modelação Cognitiva:** Esforços focados na transposição do rigor científico (Física/Matemática) para o modelo mental do aluno.
- **Gestão de Exceções e Lógica de Negócio:** Refinamentos nas regras condicionais do sistema.
- **Engenharia de Prompt e Orquestração:** Metodologias de interação do docente com a IA para estruturação do projeto e auditoria.
- **Arquitetura de Software e UX/UI:** Padrões de interface, feedback visual e gestão de dependências.

# 2. Livro de Códigos Qualitativos (Codebook)

| Categoria Temática | Código Qualitativo | Definição Operacional | Exemplo Factual no Histórico | Frequência / Relevância |
|---|---|---|---|---|
| Design Didático | `[DID-PROT]` Proteção de Modelo Cognitivo | Mecanismos de UI criados para evitar a manipulação indevida de conceitos físicos/matemáticos em runtime. | Trancar sliders com `disabled={isSimulating}` (T-003). | Alta (Crítico) |
| Design Didático | `[DID-VIS]` Representação Visual Geométrico-Matemática | Adaptação de componentes gráficos de renderização para ilustrar fenómenos matemáticos sobrepostos ou ocultos. | Injeção de `strokeDasharray` para revelar retas coincidentes em SPI (T-004). | Alta (Crítico) |
| UX/UI | `[UX-FEED]` Feedback Visual Assimétrico | Diferenciação explícita de elementos visuais de erro com base no peso lúdico ou rigoroso do contexto de acesso. | Ampliação da imagem de erro de senha analítica e remoção da mesma nas fichas pedagógicas (T-002). | Média (Relevante) |
| Gestão de Exceções | `[LOG-EXC]` Mitigação de Falsos Positivos | Refinamento estrito de condições lógicas (`if/else`) para evitar bloqueios em cenários cinemáticos perfeitamente válidos. | Adição da condição `params.mouseSpeed !== params.catSpeed` para permitir simulações paralelas (T-005). | Média (Crítico) |
| Eng. de Prompt | `[PRM-ORQ]` Orquestração Arquitetural | Formulação de comandos em linguagem natural impondo formatações rigorosas e estruturadas (YAML, Markdown, LaTeX) para forçar a IA a gerar auditorias documentais. | Geração sucessiva de ficheiros Pandoc-compatíveis (T-013 a T-019) e relatório LaTeX (T-013). | Alta (Dominante na Fase 4) |
| Infraestrutura | `[INF-EXT]` Dependência de Assets Externos | Vinculação estática a recursos não alojados localmente (cloud) para complementar a interface ou materiais didáticos. | Substituição de URL do Google Drive com documento PDF de enunciado (T-006). | Baixa (Vulnerabilidade) |

# 3. Análise da Densidade Temática e Cruzamento de Códigos

### Cruzamento `[DID-PROT]` e `[UX-FEED]` (Didática e Interface)
Observa-se uma interdependência forte entre a intenção de proteger o raciocínio do aluno e a restrição dos elementos de UI. O código `[DID-PROT]` não existe sem a sua correspondente manipulação de estado do React (`disabled`, opacidades). A intenção didática não se expressa através de grandes blocos de texto explicativo na aplicação, mas sim através de fricção algorítmica: o aluno é impedido fisicamente de cometer erros concetuais. O *feedback* visual assimétrico (`[UX-FEED]`) comprova que o professor dimensiona a tolerância ao erro dependendo de onde o aluno se encontra na sua jornada.

### Cruzamento `[DID-VIS]` e `[LOG-EXC]` (Visualização e Lógica Matemática)
A densidade temática em torno da correção matemática demonstra que o motor gráfico (Recharts) não estava originalmente apto para lidar com abstrações matemáticas como o Sistema Possível e Indeterminado (SPI). A união dos códigos `[DID-VIS]` e `[LOG-EXC]` revela um fluxo de transposição didática notável:
1. **Intencionalidade Pedagógica:** O aluno deve compreender que duas funções afins podem ser a mesma reta.
2. **Desafio Lógico (`[LOG-EXC]`):** Garantir que o sistema permite que as velocidades e vantagens sejam idênticas sem disparar alertas de domínio inválido.
3. **Solução Computacional (`[DID-VIS]`):** Modificar o SVG em runtime (tracejado) para que as limitações do motor de renderização bidimensional não destruam a premissa matemática.

### Transição de Esforço: De `[DID]` para `[PRM-ORQ]`
A evolução temporal do projeto evidencia uma clara transição de densidade temática. Nas fases iniciais (07 de Julho), os códigos predominantes relacionam-se com Design Didático (`[DID-PROT]`, `[DID-VIS]`) e Lógica (`[LOG-EXC]`). Na fase final (26-27 de Julho), o foco transita quase inteiramente para Orquestração (`[PRM-ORQ]`), onde a mediação cessa de focar o produto final (Simulador) para focar a documentação, auditoria e perenidade do conhecimento da co-criação.
