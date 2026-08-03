# E01 - Inventário de Artefatos de Teste

Abaixo encontra-se o catálogo estruturado com os elementos mapeados para a execução da validação e testes de software do projeto "Simulador de Marés".

| ID | Nome do Artefato | Descrição | Status de Teste |
|---|---|---|---|
| ART-001 | Interface de Modos de Jogo | Botões de alternância e navegação entre "Modo Principiante" e "Modo Avançado" com controle de trava (disabled). | Pendente |
| ART-002 | Painel de Parâmetros (Sliders) | Controles numéricos deslizantes (input range) para definir dinamicamente os fatores de A, B, C e D no Modo Principiante. | Pendente |
| ART-003 | Input de Equação Manual | Campo de entrada de texto no Modo Avançado para digitação explícita da expressão trigonométrica. | Pendente |
| ART-004 | Canvas P5 (Gráfico Interativo) | Container adaptativo e sketch nativo do `p5.js` responsável por renderizar cenários visuais, grade, maré, navio e pontos-chave. | Pendente |
| ART-005 | Validador Lógico (Thresholds) | Estruturas condicionais do algoritmo que comparam os deltas geométricos do usuário frente aos `TRUE_POINTS`, gerenciando a folga de tolerância a erro. | Pendente |
| ART-006 | Interpretador Matemático | Módulo injetado via dependência (`mathjs`) encarregado do parsing, filtragem, compilação e avaliação em tempo-real do string literal no Modo Avançado. | Pendente |
| ART-007 | Container de Feedback Guiado | Caixa de notificação com respostas randômicas (Dicas Socráticas) e ícones semânticos da biblioteca Lucide. | Pendente |
| ART-008 | Grid Responsivo Unificado | Malha arquitetural responsiva de interface criada usando classes CSS do Tailwind (organização e distribuição espacial que previne o over-scrolling). | Pendente |
