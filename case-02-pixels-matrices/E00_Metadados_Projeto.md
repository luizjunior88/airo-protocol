---
projeto: Pixels and Matrices (Simulador de Álgebra Linear)
estado_atual: E00 - Inicialização
data_extracao: 2026-07-28
analista: Especialista em QA e Co-designer de Tecnologia Educacional
idioma_analise: pt-BR
---

# E00 - Inicialização e Metadados do Projeto

## 1. Metadados do Projeto
- **Nome da Aplicação:** Pixels and Matrices (Pixels e Matrizes)
- **Subtítulo/Foco:** Linear Algebra Simulator (Simulador de Álgebra Linear)
- **Objetivo Principal:** [Evidência] Servir como laboratório e simulador dinâmico para demonstrar transformações geométricas no plano cartesiano a partir de matrizes 2x2.
- **Público-Alvo:** [Inferência] Alunos do ensino secundário/médio ou ensino superior introdutório que estão a estudar Álgebra Linear e Geometria Analítica.
- **Idioma da Interface:** [Evidência] Inglês (recentemente traduzido do Português por decisão instrucional).
- **Ambiente de Hospedagem:** [Evidência] Google AI Studio (Web/Cloud Run).

## 2. Escopo Inicial dos Testes
O aplicativo é dividido em 4 partes principais (módulos didáticos), que formam o escopo central de validação funcional:
- **Part 1 (Reflexões e Cadeado Pedagógico):** [Evidência] Teste de inserção de coeficientes para atingir reflexão em Ox e Oy. Verificação do bloqueio/desbloqueio do segredo vetorial ("Pedagogical Lock").
- **Part 2 (Cálculo de Determinante):** [Evidência] Teste do input analítico de matrizes e validação do palpite (guess) do determinante pelo usuário antes de permitir a aplicação da "matriz de rutura" (matriz singular).
- **Part 3 (Transformação de Cisalhamento/Shear):** [Evidência] Teste de deteção automática da inclinação horizontal mantendo a base invariante.
- **Part 4 (Composição de Matrizes):** [Evidência] Validação da entrada de duas matrizes simultâneas (M1 e M2) e da renderização sobreposta/diferenciada (cores purple/orange) evidenciando a não-comutatividade.
- **Ações Rápidas (Quick Actions):** [Evidência] Teste dos botões de atalho para matrizes pré-definidas (Identity, Reflection, Rotation, Scale, Shear, Singular Matrix).

## 3. Checklist Ética e de Acessibilidade
- [ ] **Contraste Visual:** [Inferência] O aplicativo utiliza cores semânticas (vermelho, esmeralda, púrpura, laranja). É necessário testar se o contraste entre o fundo e os vetores atende aos padrões WCAG AA/AAA para alunos com daltonismo.
- [ ] **Sobrecarga Cognitiva (Cognitive Load):** [Evidência] A interface já sofreu processos de "subtração tecnológica" (remoção do rodapé, renomeação de botões). A validação deve garantir que não há excesso de estímulos visuais concorrentes na área do plano cartesiano (SVG Canvas).
- [ ] **Navegação por Teclado:** [Inferência] Sendo um aplicativo voltado à educação, os inputs de matriz e botões de validação devem ser plenamente acessíveis via navegação por tecla `Tab`.
- [ ] **Feedback de Erro e Mediação Socrática:** [Evidência] O sistema emite dicas socráticas em caso de erro no cálculo do determinante. O teste deve validar se essas mensagens não são frustrantes, mas sim encorajadoras.

## 4. Informações Ausentes/Requeridas (RFI)
Para avançar o protocolo com maior precisão metodológica, as seguintes informações seriam úteis, embora possamos inferi-las a partir do código:
1. Há integração prevista com bases de dados ou o estado deve ser estritamente local (client-side/in-memory)? 
2. Existem métricas de acessibilidade específicas (ex: suporte a leitores de tela) exigidas pelo currículo ou pela escola?
