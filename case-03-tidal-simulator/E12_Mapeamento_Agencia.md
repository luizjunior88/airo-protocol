# E12 - Mapeamento de Agência

Este documento consolida o mapeamento analítico da **Teacher Agency** (Agência Docente) manifestada durante a concepção e refinamento do Simulador de Marés. Através da triangulação entre os turnos de interação (E04) e a análise de intenções (E05), categorizamos o direcionamento pedagógico do professor perante a Inteligência Artificial.

## 1. Padrões de Agência Identificados (AGC)

### AGC-001: Agência Diagnóstica e Intervenção Algébrica
- **Definição**: Capacidade do docente de avaliar o modelo matemático base gerado pela IA e identificar falhas ou oportunidades de alinhamento com o currículo alvo.
- **Evidências (Turnos)**: `T-001` (Correção da variável angular para "2pi/11") e `T-003` (Ajuste de threshold e tolerância de parâmetros).
- **Análise Teórica**: O professor não atua como mero consumidor do artefato gerado. Ao intervir nos limites numéricos (`threshold = 1.0` vs `0.5`), ele instila a necessidade de "andaimes cognitivos" (scaffolding). A máquina é calibrada para suportar a frustração do erro humano, demonstrando domínio diagnóstico sobre o tempo de aprendizagem do aluno.
- **Códigos Relacionados**: `COD-CALIB` (Calibragem de Desafio), `COD-ALGE` (Rigor Algébrico).

### AGC-002: Agência Conceptual e Mediação Socrática
- **Definição**: Capacidade de transpor a representação computacional para uma estrutura conceitual abstrata e generalista que estimule a reflexão, em vez da simples execução.
- **Evidências (Turnos)**: `T-002` (Exibição da fórmula genérica `f(x)=a+bsen(cx-d)`).
- **Análise Teórica**: Em vez de mostrar a fórmula resolvida, o professor impõe uma representação algébrica abstrata, forçando a ponte cognitiva entre as ações motoras (sliders) e as variáveis teóricas (A, B, C, D). A IA é direcionada a atuar como mediadora socrática, escondendo a resposta e iluminando o processo de raciocínio.
- **Códigos Relacionados**: `COD-SOCR` (Mediação Socrática), `COD-ABS` (Abstração Simbólica).

### AGC-003: Agência Técnica e Subtração Tecnológica
- **Definição**: Domínio espacial e de interface focado na contenção. É o ato de restringir recursos técnicos expansivos (scroll, imagens complexas) em favor da atenção sustentada do aluno.
- **Evidências (Turnos)**: `T-004` (Remoção da imagem externa problemática) e `T-005` / `T-006` (Condensação do layout no mesmo viewport, forçando a IA a abolir o scroll).
- **Análise Teórica**: Este é o padrão mais forte de "subtração tecnológica". A IA possui viés generativo (tende a adicionar mais código, mais imagens, mais espaço). O professor age como curador restritivo: remove falhas de rede (imagem externa) trocando por gradientes locais, e obriga a UI a colapsar em uma única tela (`max-h-[35vh]`). Ele entende que a carga cognitiva extrínseca do "deslizar a tela" destrói a percepção temporal da simulação matemática.
- **Códigos Relacionados**: `COD-SUBT` (Subtração Tecnológica), `COD-CONT` (Continuidade Visual).

## 2. Padrões Transversais (PAT)

- **PAT-001 (Design por Contenção Educacional)**: A aplicação sistemática de limites técnicos pela vontade pedagógica (reduzir espaço, remover imagens, permitir margem de erro) evidencia que um bom design educacional não é colocar mais tecnologia na sala de aula, mas sim domar a tecnologia para caber no espaço da atenção humana.
