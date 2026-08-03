---
projeto: Simulador de Marés
tipo: Aplicativo Educacional Interativo
estado: E00
fase: Inicialização
idioma: pt-BR
---

# E00 - Inicialização do Protocolo de Testes

## 1. Metadados do Projeto
- **Nome do Projeto**: Simulador de Marés
- **Objetivo Educacional**: Facilitar o aprendizado prático e visual das variáveis de uma equação trigonométrica (seno), especificamente funções da forma `f(x) = a + b * sen(cx - d)`.
- **Público-Alvo**: Estudantes (com dificuldades ou em níveis avançados) necessitando compreender translações, amplitudes, períodos e fases.
- **Metodologia de Ensino Associada**: Construtivismo interativo e mediação socrática, oferecendo feedback responsivo e imediato conforme a manipulação empírica através da experimentação ("Modo Principiante" com painéis visuais e "Modo Avançado" com input algébrico).

## 2. Escopo Inicial (Funcionalidades e Fluxos)
### Evidências Funcionais (Explícitas)
- **Modo Principiante (Easy)**: Interface utilizando controles deslizantes (sliders) para ajustar os parâmetros matemáticos `a`, `b`, `c` e `d` da função de forma intuitiva, exibindo as mudanças em tempo real no gráfico ao lado.
- **Modo Avançado (Hard)**: Modo de desafio desbloqueado apenas após a conclusão bem-sucedida do modo inicial. Exige a inserção da fórmula explícita manualmente pelo aluno.
- **Canvas de Visualização**: Gráfico dinâmico desenhado utilizando `p5.js`, apresentando a malha, a curva de maré, a posição visual do navio e os pontos de referência (maré real).
- **Sistema de Feedback e Dicas**: Exibição de alertas contextualizados (sucesso ou erro). Em cenários de erro, o aplicativo verifica a variação de amplitude e de deslocamento vertical (médias) para emitir mensagens com questionamentos focados (hints) que ajudam o aluno a corrigir a lógica sem dar a resposta direta.

### Inferências de Fluxo
- Espera-se que o aluno compreenda o impacto de cada componente da equação trigonométrica no "Modo Principiante" (observando o comportamento gráfico instantâneo) antes de avançar para a abstração e estruturação da fórmula no "Modo Avançado".
- A validação de precisão altera dinamicamente a margem de erro permitida dependendo da dificuldade (threshold de 1.0 no Easy e 0.5 no Hard).

## 3. Checklist de Ética e Acessibilidade
- [ ] Contraste visual adequado garantido entre o fundo do gráfico, as linhas da grade e a curva traçada.
- [ ] Mensagens de erro construtivas, focadas e investigativas, evitando linguagem punitiva (aplicação de método socrático real com randomização de dicas).
- [ ] Responsividade adaptada, garantindo layout que organiza gráficos e painéis paramétricos de forma concisa na mesma tela (Desktop e Mobile) reduzindo a fadiga de scroll cognitivo.
- [ ] Indicadores claros de estado habilitado/desabilitado nos elementos da interface, incluindo feedback visual (cadeado Lock/Unlock) para modos travados.
