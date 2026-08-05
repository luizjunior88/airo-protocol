# Protocolo de Extração AIRO - Edição Workshop (v1.1)

Este documento contém os prompts de extração estruturados pelo modelo RTCRF (Role, Task, Context, Rules, Format) para a documentação do co-design da sua aplicação. Siga a sequência estrita da Máquina de Estados Finita Determinística (MEFD).

---
## CAMADA 1: IDENTIFICAÇÃO

### Prompt 1: Estado E00 - Inicialização
**[ROLE]**
Atue como um Especialista em Garantia de Qualidade (QA) e Co-designer de Tecnologia Educacional.

**[TASK]**
Inicialize o protocolo de testes para o novo aplicativo. Estruture os metadados do projeto e defina o escopo inicial (funcionalidades, fluxos). **Exporte obrigatoriamente a resposta em formato `.md` para a raiz do projeto.**

**[CONTEXT]**
Estamos iniciando o Estado E00 (Inicialização) do AI Studio Research Orchestrator. O aplicativo servirá a propósitos educacionais. Todo o desenvolvimento e validação devem ser conduzidos em português brasileiro.

**[RULES]**
1. Mantenha o rigor epistêmico: separe claramente o que é "Evidência" (dados concretos fornecidos sobre o app) do que é "Inferência" (pressuposições sobre o uso).
2. Não invente funcionalidades não declaradas. Solicite as informações complementares que faltarem.
3. Não avance para a análise de código ainda; foque apenas nos metadados de inicialização.

**[FORMAT]**
Estruture a saída com um cabeçalho YAML e seções numeradas. 
**Diretiva final:** Gere e salve o documento resultante como `E00_Metadados_Projeto.md`.

---
### Prompt 2: Estado E01 - Inventário de Artefatos
**[ROLE]**
Atue como Arquiteto de Software e Analista de Requisitos.

**[TASK]**
Analise o escopo do aplicativo discutido no estado anterior e construa o inventário completo de artefatos de teste (telas, componentes de UI, módulos lógicos). **Exporte obrigatoriamente a resposta em formato `.md`.**

**[CONTEXT]**
Estamos no Estado E01 (Histórico Completo). Os metadados já estão mapeados. Precisamos consolidar o que será testado antes de avançar para a Extração técnica.

**[RULES]**
1. Utilize a ontologia de identificadores: cada artefato mapeado deve receber um código único com o prefixo `ART` (ex: ART-001, ART-002).
2. O foco é puramente o mapeamento de ativos estruturais do aplicativo; evite justificativas didáticas neste momento.

**[FORMAT]**
Apresente os dados organizados em uma tabela (Catálogo de Artefatos) contendo: ID, Nome do Artefato, Descrição e Status de Teste. Salve como `E01_Inventario_Artefatos.md`.

---
## CAMADA 2: EXTRAÇÃO

### Prompt 3: Estado E02 - Metadados Técnicos e Stack
**[ROLE]**
Atue como Engenheiro de Software Full-Stack.

**[TASK]**
Documente a arquitetura e a stack tecnológica do aplicativo (bibliotecas, frameworks e requisitos de infraestrutura). **Exporte obrigatoriamente a resposta em formato `.md`.**

**[CONTEXT]**
Entramos no Estado E02 (Metadados Técnicos). Precisamos da base técnica clara para, posteriormente, cruzar decisões de design com as limitações da tecnologia.

**[RULES]**
1. Documente as versões das tecnologias sempre que fornecidas.
2. Sinalize como "Inferência" qualquer dependência técnica assumida que não tenha sido explicitamente declarada nos prompts anteriores.

**[FORMAT]**
Utilize formatação em blocos de código para dependências. Salve como `E02_Stack_Tecnologica.md`.

---
### Prompt 4: Estado E03 - Artefatos Produzidos
**[ROLE]**
Atue como Analista de QA e Especialista em Documentação Técnica.

**[TASK]**
Detalhe os artefatos produzidos mapeados no inventário inicial, especificando as características técnicas de cada componente da interface e lógica de estado. **Exporte obrigatoriamente em formato `.md`.**

**[CONTEXT]**
Estamos no Estado E03 (Artefatos Produzidos). Este estado foca no desdobramento técnico dos elementos construídos.

**[RULES]**
1. Continue usando o prefixo `ART` para cada artefato detalhado.
2. Mantenha o foco estritamente técnico e estrutural.
3. Separe "Evidência" (código e arquivos reais) de "Inferência".

**[FORMAT]**
Estruture com tabelas descritivas para cada componente. Salve como `E03_Artefatos_Produzidos.md`.

---
### Prompt 5: Estado E04 - Extração de Interações
**[ROLE]**
Atue como Pesquisador de Interação Humano-Computador.

**[TASK]**
Extraia e registre o log sequencial, turno a turno, das interações de co-design do aplicativo. **Exporte obrigatoriamente em formato `.md`.**

**[CONTEXT]**
Estado E04 (Extração de Interações). Esta fase documenta o processo dialógico base para rastrear as decisões de desenvolvimento.

**[RULES]**
1. Atribua a cada turno um identificador único com o prefixo `T` (ex: T-001, T-002).
2. **Restrição epistêmica estrita:** Registre apenas evidências. É expressamente proibida qualquer interpretação ou análise de intenções neste estado. Registe apenas o que foi gerado e escrito.

**[FORMAT]**
Lista sequencial clara. Salve como `E04_Extracao_Interacoes.md`.

---
### Prompt 6: Estado E05 - Análise de Intenções
**[ROLE]**
Atue como Analista de Design Instrucional.

**[TASK]**
Analise os turnos mapeados no estado anterior para identificar e documentar a intenção pedagógica que motivou o utilizador em cada decisão (adição, remoção ou alteração de código). **Exporte obrigatoriamente em formato `.md`.**

**[CONTEXT]**
Estamos no Estado E05 (Análise de Intenções). A análise deve refletir os objetivos didáticos que nortearam a direção tomada pelo professor em relação ao código gerado.

**[RULES]**
1. Trabalhe em cima do registro de turnos (prefixo `T`).
2. Diferencie claramente a "Evidência" (intenção explicitamente declarada pelo professor no turno) da "Inferência" (intenção deduzida pelo contexto).
3. Foque no mapeamento individual das intenções, sem sintetizar regras gerais ainda.

**[FORMAT]**
Tabela correlacionando o ID do Turno (T-XXX), a Ação de Código correspondente e a Intenção Pedagógica (Evidência ou Inferência). Salve como `E05_Analise_Intencoes.md`.

---
### Prompt 7: Estado E06 - Classificação de Prompts
**[ROLE]**
Atue como Engenheiro de Prompts.

**[TASK]**
Crie a taxonomia e a classificação dos prompts de desenvolvimento utilizados na construção da aplicação. **Exporte obrigatoriamente em formato `.md`.**

**[CONTEXT]**
Chegamos ao Estado E06, fechando a camada de Extração. O foco são os prompts de desenvolvimento emitidos pelo utilizador.

**[RULES]**
1. Utilize o prefixo `PRM` para identificar cada prompt catalogado (ex: PRM-001).
2. Classifique o prompt quanto à sua natureza técnica (ex: definição arquitetural, alteração visual, refinamento lógico, restrição de comportamento).

**[FORMAT]**
Catálogo estruturado. Salve como `E06_Classificacao_Prompts.md`.

---
## CAMADA 3: ANÁLISE

### Prompt 8: Estado E07 - Mapeamento de Decisões
**[ROLE]**
Atue como Arquiteto de Software.

**[TASK]**
Documente as principais decisões de design tomadas, adotando o formato de Architecture Decision Records (ADR). **Exporte obrigatoriamente em formato `.md`.**

**[CONTEXT]**
Estado E07 (Mapeamento de Decisões). O objetivo é entender o racional arquitetural por trás das escolhas estruturais do aplicativo.

**[RULES]**
1. Utilize o prefixo `DEC` para identificar cada decisão catalogada (ex: DEC-001).
2. Separe claramente a "Evidência" (a decisão implementada no código) do "Contexto" (por que foi tomada).

**[FORMAT]**
Estruture cada registro com: Título, Status, Contexto, Decisão e Consequências. Salve como `E07_Mapeamento_Decisoes.md`.

---
### Prompt 9: Estado E08 - Validação de Artefatos
**[ROLE]**
Atue como Analista de Testes QA.

**[TASK]**
Execute a verificação de consistência interna sobre os artefatos produzidos em relação aos requisitos solicitados. **Exporte obrigatoriamente em formato `.md`.**

**[CONTEXT]**
Estado E08 (Validação de Artefatos). O objetivo é garantir que o output gerado pela IA reflete com precisão os comandos arquiteturais fornecidos.

**[RULES]**
1. Não adicione novos recursos à aplicação; foque puramente na auditoria do que foi gerado vs. o que foi solicitado.
2. Identifique eventuais "alucinações" formais ou erros de lógica.

**[FORMAT]**
Relatório de checklist. Salve como `E08_Validacao_Artefatos.md`.

---
### Prompt 10: Estado E09 - Arquitetura do Artefato
**[ROLE]**
Atue como Engenheiro de Software Sênior.

**[TASK]**
Descreva a estrutura técnica consolidada do artefato, mapeando como os módulos e lógicas de estado se interligam na aplicação final. **Exporte obrigatoriamente em formato `.md`.**

**[CONTEXT]**
Estado E09 (Arquitetura do Artefato). O "raio-X" arquitetural definitivo.

**[RULES]**
1. Baseie-se estritamente nas evidências dos estados anteriores.
2. Destaque como a arquitetura do código acomoda as mecânicas de interação exigidas no projeto.

**[FORMAT]**
Tabelas de relacionamento e estrutura hierárquica. Salve como `E09_Arquitetura_Artefato.md`.

---
### Prompt 11: Estado E10 - Problemas e Limitações
**[ROLE]**
Atue como Engenheiro de Confiabilidade (SRE).

**[TASK]**
Levante todos os problemas técnicos, limites computacionais ou estruturais encontrados na solução gerada. **Exporte obrigatoriamente em formato `.md`.**

**[CONTEXT]**
Estado E10 (Problemas e Limitações). Transparência total sobre onde a solução gerada atinge os seus limites.

**[RULES]**
1. Utilize o prefixo `PRB` para identificar cada problema (ex: PRB-001).
2. Classifique a severidade do problema.

**[FORMAT]**
Matriz indicando ID, Descrição, Severidade e Status. Salve como `E10_Problemas_Limitacoes.md`.

---
### Prompt 12: Estado E11 - Tensões e Resoluções
**[ROLE]**
Atue como Pesquisador em Design Instrucional.

**[TASK]**
Catalogue as tensões técnico-pedagógicas que emergiram durante o co-design e descreva a ação corretiva aplicada pelo professor para alinhar o código à sua intenção. **Exporte obrigatoriamente em formato `.md`.**

**[CONTEXT]**
Estado E11 (Tensões e Resoluções). Este estado foca no atrito entre o output padrão (default) gerado pela máquina e a intenção instrucional que exigiu que o professor modificasse ou interviesse nesse resultado.

**[RULES]**
1. Utilize o prefixo `TEN` para identificar cada tensão catalogada (ex: TEN-001).
2. Demarque perfeitamente a distinção entre "Evidência" (o conflito gerado no código) e "Ação" (como foi resolvido).

**[FORMAT]**
Catálogo detalhado das tensões. Salve como `E11_Tensoes_Resolucoes.md`.