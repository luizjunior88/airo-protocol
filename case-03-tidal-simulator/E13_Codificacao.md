# E13 - Codificação

Este documento apresenta o Codebook qualitativo definitivo, contendo o dicionário temático que resume as interações, tensões e padrões de agência identificados no co-design da aplicação.

## Dicionário de Códigos (COD)

| ID | Nome do Código | Definição | Critério de Inclusão/Exclusão | Exemplo Extraído (Corpus) |
|---|---|---|---|---|
| **COD-CALIB** | Calibragem de Desafio | Ajuste dos níveis de tolerância e dificuldade do software para adequação ao estágio cognitivo do aluno. | *Inclusão*: Mudanças em variáveis de tolerância, pontuação ou regras de acerto.<br>*Exclusão*: Ajustes visuais não relacionados à dificuldade. | O ajuste de `threshold` diferenciado para o Modo Principiante (1.0) e Modo Avançado (0.5) (Ref: DEC-002, T-003). |
| **COD-ALGE** | Rigor Algébrico | Intervenção direcionada à precisão do domínio matemático, corrigindo falhas na lógica subjacente gerada pela IA. | *Inclusão*: Alterações em expressões matemáticas, fórmulas e variáveis.<br>*Exclusão*: Alterações textuais apenas estéticas. | Alteração da variável para refletir precisamente o ciclo do problema: `(2pi/11) * x` (Ref: T-001). |
| **COD-SOCR** | Mediação Socrática | Implementação de feedbacks investigativos e representações que estimulam o questionamento interno, em vez de dar a resposta final. | *Inclusão*: Mensagens que devolvem perguntas; representações parciais (scaffolding).<br>*Exclusão*: Feedbacks punitivos ou diretos (ex: "Resposta Errada"). | Uso da fórmula generalista `a+bsen(cx-d)` sem expor os números (Ref: T-002) e dicas focadas nas médias (ART-005). |
| **COD-SUBT** | Subtração Tecnológica | Ação deliberada de remover complexidade técnica, recursos excessivos ou dependências externas em favor da clareza e estabilidade pedagógica. | *Inclusão*: Remoção de APIs, imagens pesadas, animações distrativas ou features não-core.<br>*Exclusão*: Adição de features limitadoras temporárias (isso é Calibragem). | Troca da imagem externa fotográfica propensa a falhas por um gradiente algorítmico seguro (Ref: TEN-001, T-004). |
| **COD-CONT** | Continuidade Visual | Modificação de interface visando agrupar a "causa" e "efeito" no mesmo campo visual, minimizando a carga cognitiva de navegação. | *Inclusão*: Eliminação de scroll, condensação de grids, fixação de canvas.<br>*Exclusão*: Mudanças de cores ou fontes sem impacto estrutural de espaço. | Forçar a visualização do canvas e dos parâmetros em uma única janela sem rolagem em Desktop (`lg:flex-row`) (Ref: TEN-002, T-005, T-006). |

## Matriz de Padrões Transversais (PAT)

- **PAT-001**: O princípio da **Contenção Educacional**. A IA tende organicamente ao excesso generativo; o papel primário do professor como arquiteto no ciclo de co-design (identificado pelos códigos `COD-SUBT` e `COD-CONT`) é agir como um delimitador espacial e técnico. A educação acontece não pela abundância de recursos de software, mas pela curadoria rigorosa da interação visual e da frustração do aluno (`COD-CALIB` + `COD-SOCR`).
