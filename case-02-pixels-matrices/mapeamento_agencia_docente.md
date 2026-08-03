# Mapeamento de Agência Docente no Co-Design com IA

Com base no histórico de interações (Estado E04) e nas decisões de design instrucional (Estado E07), apresenta-se a categorização dos padrões de agência exercidos pelo professor durante a sessão de desenvolvimento em co-design com a Inteligência Artificial.

## 1. Agência Diagnóstica
A agência diagnóstica manifestou-se nos momentos em que o professor assumiu o papel de avaliador crítico do rigor científico e da correção algorítmica do artefacto gerado pela IA. O docente não aceitou passivamente a resposta da máquina, utilizando o seu conhecimento especializado para auditar a lógica matemática.

* Evidência em T-001: "qual é a lógica matemática do SHEAR?" - O professor sonda a base de raciocínio da IA para garantir que a transformação geométrica do cisalhamento foi implementada com rigor.
* Evidência em T-003: "confirma se a lógica da parte 4 está certa" - Escrutínio direto sobre a funcionalidade central de composição de matrizes, garantindo a ausência de misconceções numéricas ou operacionais.

## 2. Agência Conceptual
A agência conceptual reflete as diretrizes do professor focadas na transposição didática, no design de interface para a aprendizagem e na intencionalidade pedagógica do simulador.

* Evidência em T-005: "e isto está a ser refletido na imagem gerada? Queria acionar ao mesmo tempo e criar uma figura resultante de cor diferente pra cada para ilustrar melhor a situação" - Traduz-se na DEC-001, em que o professor manipula o modelo visual para evidenciar a não-comutatividade em simultâneo, aliviando a carga na memória de trabalho (Teoria da Dupla Codificação).
* Evidência em T-009: "Deixe apenas Parte 1, Parte 2, Parte 3 e Parte 4" - Resulta na DEC-003, moldando a experiência de navegação para omitir a solução didática prévia e fomentar o ensino por investigação.
* Evidência em T-011: "traduza todo e qualquer texto para o inglÊs" - Relacionado com a DEC-004, expandindo o âmbito universal e a utilidade global da ferramenta.

## 3. Agência Técnica
A agência técnica evidenciou-se na capacidade de conduzir a sessão operacionalmente, sinalizando erros técnicos (bugs) e orquestrando o comportamento da própria Inteligência Artificial através de prompt engineering avançado.

* Evidência em T-007: "Fix the errors in the app error 0: Uncaught ReferenceError: points is not defined" - Atuação focada em repor o estado funcional da aplicação perante falhas de execução.
* Evidências em T-013, T-014 e T-015: Definição de personas ("Atua como investigador especialista"), atribuição de regras rígidas ("Não incluas tags", "Regista apenas decisões") e controlo de formato ("cria a resposta num .md na raiz"). O professor atua como arquiteto do próprio processo analítico da IA.

## 4. Episódios de Subtração Tecnológica
A Subtração Tecnológica é um indicador refinado de agência, ocorrendo quando o professor recusa ou remove proativamente affordances tecnológicas, detalhes estéticos ou excesso de informação (frequentemente sugeridos pela IA) para garantir o foco cognitivo do aluno e a pureza didática da ferramenta.

* Episódio 1 - Remoção de Metalinguagem Orientadora (T-009 / DEC-003): Ao solicitar a alteração dos botões de "Parte II: Rutura" e "Parte III: Shear" para apenas numeração simples ("Parte 2", "Parte 3"), o professor subtraiu conscientemente a "dica" presente na interface. Esta subtração forçou a problematização, não permitindo que o aluno antecipasse a resposta do exercício apenas por ler a navegação.
* Episódio 2 - Limpeza da Interface de Aprendizagem (T-011 / DEC-004): O pedido "- retire o rodapé" representa uma subtração arquitetural. O professor removeu métricas técnicas (FPS, Motor Reativo) e créditos de autoria para cumprir o Princípio da Coerência Multimédia, garantindo que nenhum pixel no ecrã subtraía atenção à tarefa matemática principal.
