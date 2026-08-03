---
title: "Estado 14: Relatório Científico de Investigação - Reconstrução, Auditoria e Análise de Co-Criação no Simulador Cinemático"
author: "AI Studio Research Orchestrator"
date: "2026-07-27"
state: "14_relatorio_cientifico"
output_file: "14_relatorio_cientifico.md"
abstract: |
  Este artigo científico apresenta a reconstrução rigorosa e a análise de co-criação Homem-IA do projeto "Simulador Cinemático (Tom & Jerry)", desenvolvido para o ensino de Matemática e Física. Utilizando uma metodologia de orquestração por máquina de estados (Estados 00 a 13), o estudo examina a transposição didática digital, a agência do docente (Teacher Agency) e a resiliência da arquitetura de software cliente (React/TypeScript). Os resultados evidenciam como a fricção computacional deliberada e a representação visual de exceções (como Sistemas Possíveis e Indeterminados) previnem concepções erradas nos alunos, mantendo o docente no papel de gestor e orquestrador do design algorítmico.
---

# 1. Introdução e Contextualização

O ensino de conceitos abstratos, tais como o Movimento Retilíneo Uniforme (MRU) na Física e a resolução geométrica de Sistemas de Equações Lineares na Matemática, apresenta desafios cognitivos estruturais para alunos do ensino básico e secundário. A transição da intuição cinemática para a sua representação cartesiana rigorosa resulta frequentemente no desenvolvimento de conceções erróneas (*misconceptions*).

Neste contexto, foi desenvolvido o **Simulador Cinemático (Tom & Jerry)**, uma aplicação interativa (SPA) que introduz elementos de gamificação para apoiar o processo de ensino e aprendizagem. A aplicação bifurca a experiência em dois modelos de visualização (Modo História e Modo Analítico) suportados por *gatekeeping* pedagógico. Este artigo documenta a reconstrução integral do ciclo de vida deste projeto no ambiente Google AI Studio, focando-se na mecânica de co-criação entre o docente e a Inteligência Artificial Generativa.

# 2. Fundamentação Teórica e Metodologia

### Fundamentação Teórica
A investigação apoia-se em três eixos concetuais:
1. **Transposição Didática Digital:** O processo pelo qual o saber académico é transformado em saber ensinado através da mediação de artefactos tecnológicos, convertendo restrições físicas em regras computacionais de UX/UI.
2. **Teacher Agency (Agência do Docente):** A capacidade do professor em assumir o controlo ativo do *design* do software, atuando como Arquiteto Pedagógico e Gestor de Produto, modelando o ambiente educativo ao invés de atuar como mero consumidor passivo de ferramentas padronizadas.
3. **Co-Criação Homem-IA:** Um paradigma onde a IA atua como um executor técnico ou compilador semântico, eliminando a barreira da linguagem de programação, mas cedendo a soberania conceptual, lógica e didática ao orquestrador humano.

### Metodologia
A extração e auditoria empírica basearam-se no protocolo de orquestração por máquina de estados do **AI Studio Research Orchestrator**. Ao longo das Fases `00` a `13`, efetuou-se uma reconstrução cronológica profunda abrangendo:
- Extração de artefactos e código fonte (`01`, `06`).
- Mapeamento cronológico das interações e evolução temporal (`02`, `03`, `04`).
- Taxonomia e codificação qualitativa das intenções subjacentes aos *prompts* (`05`, `13`).
- Auditoria de arquitetura, funcionalidades e decisões técnicas (`07`, `08`, `09`, `11`).

# 3. Análise da Arquitetura e Engenharia do Software

### Pilha Tecnológica e Padrão Monolítico
O sistema baseia-se numa arquitetura puramente cliente desenvolvida em TypeScript, suportada pelo ecossistema React 18 e empacotada com o Vite. O interface tira partido do Tailwind CSS para a estilização utilitária e da biblioteca Recharts (baseada em D3.js) para a renderização gráfica SVG vetorial.

A arquitetura apresenta um forte acoplamento através da adoção de um padrão monolítico centrado num único ficheiro (`src/App.tsx`, com aproximadamente 1150 linhas). Todo o fluxo de dados, a gestão de estado (via hooks `useState` e `useEffect`), o ciclo de vida da simulação (`isSimulating`, `currentTime`), a lógica matemática e os componentes UI encontram-se interligados, gerando uma complexidade cognitiva elevada que configura débito técnico para futura escalabilidade.

### Regras de Negócio e Tratamento de Exceções
A engenharia foi rigorosa na mitigação de *edge cases* lógicos da cinemática:
- **Exceção de Vantagem Zero:** Tratamento da impossibilidade empírica de vantagem nula sem colisão imediata quando as velocidades divergem. O bloqueio exige a condição estrita `mouseStart === 0 && params.mouseSpeed !== params.catSpeed`.
- **Sistemas Possíveis e Indeterminados (SPI):** Resolvido através da modificação da propriedade de renderização `strokeDasharray="8 8"`. Quando posições e velocidades são equivalentes, a sobreposição das retas cartesianas é visualmente mitigada com uma linha tracejada, evidenciando a dualidade das equações sobre o mesmo espaço geométrico.

# 4. Resultados: Agência Docente e Transposição Didática

### O Professor como Orquestrador
Os resultados empíricos (Fase `12`) demonstram inequivocamente a prevalência da liderança diretiva e arquitetural do docente. O utilizador formulou *prompts* assentes numa lógica booleana clara (ex.: *"Se e somente se a vantagem do Jerry for zero E as velocidades forem iguais"*), ditando restrições de comportamento precisas (código qualitativo `[LOG-EXC]`).

### Fricção Computacional Deliberada
A transposição didática materializou-se no software através do que definimos como **fricção computacional deliberada**:
- **Congelamento Cognitivo (`[DID-PROT]`):** A injeção universal do estado `disabled={isSimulating}` nos *sliders* de manipulação (T-003) impede que a manipulação espacial do utilizador corrompa a execução temporal (MRU). 
- **Gatekeeping Lúdico e Feedback Assimétrico (`[UX-FEED]`):** O recurso a senhas estáticas (`velocidadefuriosa`) garante que os alunos validem empiricamente as suas observações no Modo História antes de acederem à matriz abstrata das equações. A diferenciação no feedback de erro (imagens gigantes para falhas analíticas, texto discreto para recursos) comprova a intenção de modelar a resiliência do aluno face ao erro.

# 5. Discussão, Limitações e Recomendações

### Discussão da Arquitetura de Apoio
Embora a transposição didática seja extremamente eficaz, a implementação técnica levanta vulnerabilidades no que concerne à resiliência:
- **Segurança Client-Side:** O uso de senhas (*plain-text*) verificadas no cliente é intrinsecamente inseguro do ponto de vista criptográfico corporativo. Contudo, na perspetiva do modelo educativo em foco, revela-se ser a opção arquitetural ideal (Baixo Custo / Atrito Didático Eficaz) para atrasar o progresso irrefletido do utilizador sem necessitar de complexos serviços de base de dados ou gestão de sessões.
- **Dependência Cloud (`[INF-EXT]`):** A inserção de URLs rígidos para carregar fotografias ou documentos (Google Drive) estabelece um *Single Point of Failure*, recomendando-se o alojamento nativo estático no diretório `/public` na próxima versão major do software, a fim de garantir integridade *offline*.

### Limitações da Auditoria
Uma limitação expressiva desta pesquisa diz respeito ao truncamento do histórico na plataforma. A análise empírica documentada assenta nos metadados obtidos a partir do Turno T-001 registado (iniciado com a correção estética de assets), impossibilitando a análise direta das sessões génese (Turno 0 absoluto) onde a base monolítica (`App.tsx`) foi originalmente concebida com o Recharts.

# 6. Conclusão

A reconstrução documentada neste relatório demonstra o sucesso do modelo de co-criação suportado por IA no desenvolvimento de soluções educativas sob medida (*tailor-made*). O "Simulador Cinemático (Tom & Jerry)" atingiu com rigor a fase de Produção (MVP Educativo), evidenciando que a barreira técnica associada à programação reativa de interfaces deixou de ser um impedimento para os pedagogos. 

Em suma, a inteligência da aplicação não provém de algoritmos complexos ou machine learning endógeno, mas sim da clareza das instruções didáticas e condicionais booleanas definidas pelo docente — a quem se credita o verdadeiro mérito arquitetural da ferramenta — as quais traduziram de modo fiel as limitações da Física e as idiossincrasias cognitivas da Matemática para a interface gráfica.
