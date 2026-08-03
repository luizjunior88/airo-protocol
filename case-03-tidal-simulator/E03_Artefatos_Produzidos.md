---
estado: E03
fase: Artefatos Produzidos
tipo: Documentação Técnica
---

# E03 - Artefatos Produzidos

Abaixo está o detalhamento técnico dos artefatos estruturais mapeados na aplicação, separados em Evidência (código explícito) e Inferência (funcionamento subjacente ou padrão do ecossistema).

### ART-001: Interface de Modos de Jogo
- **Evidência**: Botões estilizados com classes Tailwind que alternam o estado `mode` (via `useState<'easy' | 'hard'>`) e possuem propriedades `disabled` lidas a partir do estado `isHardUnlocked`. Utiliza ícones `Lock` e `Unlock` do pacote `lucide-react`.
- **Inferência**: A separação de modos serve para guiar o aprendizado de forma gradativa, impedindo pular etapas cruciais sem completar o fluxo de onboarding matemático (Modo Principiante).

### ART-002: Painel de Parâmetros (Sliders)
- **Evidência**: Inputs do tipo `range` vinculados a um estado em formato de objeto `easyParams` (`{ A, B, C, D }`). Ao deslizar, disparam funções `onChange` que atualizam valores específicos utilizando desestruturação `...easyParams`.
- **Inferência**: Representa uma UI declarativa reativa que promove o pareamento bidirecional e instantâneo com a curva desenhada, consolidando o ciclo de experimentação.

### ART-003: Input de Equação Manual
- **Evidência**: Campo `<input type="text">` habilitado apenas no Modo Avançado, controlado por um estado do React (`equation`).
- **Inferência**: É o teste de conhecimento sintático final do aluno. O input string necessita ser higienizado e "parseado" por uma biblioteca dedicada à avaliação algébrica.

### ART-004: Canvas P5 (Gráfico Interativo)
- **Evidência**: Implementado através do uso de hooks de referência (`useRef`) onde a instância do `p5.js` é amarrada. O background de imagem com erro foi alterado para um gradiente algorítmico (desenhado com `p5.lerpColor`).
- **Inferência**: A utilização do p5.js injeta um ciclo de renderização (`draw`) dissociado da árvore DOM principal (React), o que demanda sincronização via objeto iterável (uso de `stateRef`).

### ART-005: Validador Lógico (Thresholds)
- **Evidência**: Lógica condicional dentro do método `handleSimulate` que compara os valores gerados pela curva em relação à matriz constante `TRUE_POINTS`. Estabelece a variável `threshold` (1.0 para 'easy' e 0.5 para 'hard'). 
- **Inferência**: A variação do `threshold` demonstra o compromisso entre acessibilidade (facilitar o primeiro uso) e o rigor exigido no estágio final de validação matemática.

### ART-006: Interpretador Matemático
- **Evidência**: Uso da biblioteca `mathjs` importada como `math`. No Modo Avançado, o código aplica limpezas de regex (`equation.replace(/Math\./g, '')`) seguidas pela compilação com `math.compile()` e avaliação num loop `expr.evaluate({ x, pi: Math.PI })`.
- **Inferência**: Impede falhas nativas do Javascript como injeção de código (eval), enquanto aumenta a flexibilidade e aceita sintaxes variadas inseridas pelos alunos.

### ART-007: Container de Feedback Guiado
- **Evidência**: Módulo de renderização condicional que depende do objeto `feedbackState` (`{ type, title, message }`). Utiliza interpolação condicional Tailwind e exibe mensagens extraídas de matrizes baseadas nos cálculos de diferença (deslocamento vertical e amplitude).
- **Inferência**: Encapsula as respostas simuladas da "mediação socrática", sem recarregar a tela, agindo de forma imperativa dependendo da avaliação lógica do ART-005.

### ART-008: Grid Responsivo Unificado
- **Evidência**: Camada container em Tailwind utilizando classes flexbox e grid (`flex-col`, `lg:flex-row`, `min-h-screen`, `max-h-[35vh]`) visando englobar todos os painéis e o gráfico num design de visualização singular sem overflow excessivo.
- **Inferência**: Refinamento de usabilidade (UX) requisitado explicitamente para melhorar o conforto visual e reduzir a sobrecarga cognitiva do aluno em desktop e mobile.
