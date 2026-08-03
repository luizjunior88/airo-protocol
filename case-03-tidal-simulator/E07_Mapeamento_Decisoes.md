# E07 - Mapeamento de Decisões

Este documento estrutura as principais escolhas arquiteturais e de design efetuadas durante o co-design do aplicativo, adotando o formato ADR (Architecture Decision Records).

## DEC-001: Adoção do `p5.js` para renderização visual
- **Status**: Aceito e Implementado.
- **Contexto/Inferência**: O aplicativo educacional não exibe gráficos estáticos, mas simula um ambiente dinâmico (com a representação de um navio e o nível da água) que precisa ser atualizado a cerca de 60fps conforme os parâmetros numéricos mudam. Bibliotecas de gráficos cartesianos tradicionais não suportariam o apelo lúdico e a dinamicidade esperados.
- **Decisão (Evidência)**: Incorporação de um canvas instanciado e gerenciado através da biblioteca `p5.js`, acoplado ao ciclo de vida do componente React utilizando o hook `useRef`.
- **Consequências**:
  - *Positivas*: Liberdade absoluta para desenhar gradientes, malhas, navios estilizados e a curva da maré de maneira customizada.
  - *Negativas*: Introduz complexidade de estado, pois exige que as variáveis do React sejam sincronizadas de forma imperativa (através de referências mútuas) para o escopo isolado do loop `draw()` do p5.

## DEC-002: Margem de Tolerância (Threshold) Dinâmica
- **Status**: Aceito e Implementado.
- **Contexto/Inferência**: Exigir a função trigonométrica numericamente perfeita em todos os momentos pode ser frustrante para alunos novatos, ocasionando o abandono. Uma mediação socrática dita que os desafios devem aumentar progressivamente.
- **Decisão (Evidência)**: O algoritmo calculador de deltas foi alterado para validar os dados baseados no modo de jogo: `threshold = 1.0` no Modo Principiante (Easy) e `threshold = 0.5` no Modo Avançado (Hard).
- **Consequências**: Atua como um andaime (scaffolding) educacional eficaz. Evita frustração precoce, mas garante o rigor necessário antes que o usuário seja considerado aprovado na simulação avançada.

## DEC-003: Validação Algébrica Segura (Modo Avançado)
- **Status**: Aceito e Implementado.
- **Contexto/Inferência**: No Modo Avançado, a intenção pedagógica exige que o aluno estruture ativamente e de forma literal a equação completa. Executar entradas do usuário (strings) nativamente em JavaScript (via `eval`) criaria um risco de segurança e de estabilidade diante de possíveis erros de sintaxe (digitações errôneas).
- **Decisão (Evidência)**: Utilização da biblioteca `mathjs` para realizar a compilação segura da string em uma árvore de expressão e sua posterior avaliação em tempo-real contra a variável `x` e a constante `pi`.
- **Consequências**: O sistema perdoa melhor a sintaxe e está blindado contra injeções. Porém, adiciona peso ao bundle final (dependência externa robusta).

## DEC-004: Layout de Tela Única Restritivo (No-Scroll)
- **Status**: Aceito e Implementado.
- **Contexto/Inferência**: Conforme documentado (T-005 e T-006), o aluno precisa ver, ao mesmo tempo, a ação (alteração no slider) e a reação (atualização da curva trigonométrica). O scroll vertical afasta fisicamente causa e efeito.
- **Decisão (Evidência)**: Ajuste maciço nas regras CSS usando Tailwind. Foram introduzidas restrições de altura máxima (`max-h-[35vh]`), paddings condensados, redimensionamento semântico (`text-sm`, `text-base`), e layout `lg:flex-row` para abrigar gráfico e controles no mesmo viewport em telas desktop e mobile.
- **Consequências**: Reduz drasticamente a sobrecarga cognitiva do aluno e garante a eficiência do ciclo de experimentação construtivista.
