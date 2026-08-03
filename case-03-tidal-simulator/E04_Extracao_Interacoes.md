# E04 - Extração de Interações

Registro sequencial dos turnos de co-design e testagem extraídos das conversas, relatando expressamente as ações sem inferências de intenções.

- **T-001**:
  - **Ação do Usuário**: Declarou que "2pi/11 deve ser o x".
  - **Ação do Sistema**: Modificou a equação inicial (placeholder) nos estados de `App.tsx` substituindo as instâncias de `5 * x` pela notação `(2 * pi / 11) * x`.
- **T-002**:
  - **Ação do Usuário**: Solicitou "onde é exibido a função, deixe-a genérica f(x)=a+bsen(cx-d)".
  - **Ação do Sistema**: Editou o código fonte, alterando rótulos, equações exibidas para a versão algébrica padrão requisitada e ajustou o objeto `easyParams` para exibir letras A, B, C, D congruentes com o formato generalista, modificando também a representação matemática dentro do laço `for`.
- **T-003**:
  - **Ação do Usuário**: Pediu "certifique-se de que o intervalo dos parâmetros atende aos pontos dados".
  - **Ação do Sistema**: Modificou a lógica em `App.tsx` para introduzir a variável condicional `threshold`. Configurado como `1.0` no modo "easy" e `0.5` no modo "hard", alterando a margem de acerto avaliada frente ao pico máximo (`maxDiff`).
- **T-004**:
  - **Ação do Usuário**: Informou sobre "error 0: Failed to load image:".
  - **Ação do Sistema**: Removeu a constante `PIER_IMAGE_URL` (ligada à API Unsplash) que causava falha e gerou um gradiente desenhado programaticamente no `p5.setup` e `p5.draw` utilizando as funções de preenchimento vetorial.
- **T-005**:
  - **Ação do Usuário**: Apontou que "ajuste a responsividade. mesmo no modo desktop não se vê tudo no mesmo ecrã, no mobile também. para um aluno é melhor ter tudo à vista sempre".
  - **Ação do Sistema**: Atualizou as classes do Tailwind para redimensionar paddings (`p-2`, `sm:p-4`), diminuiu o tamanho do canvas de forma responsiva (`max-h-[35vh]`) e ajustou tamanhos de tipografia para condensar a informação em uma única janela de viewport sem rolagem.
- **T-006**:
  - **Ação do Usuário**: Reforçou que "no mobile penso que está bom, mas no desktop, quero o gráfico e os parametros na mesma tela para que o aluno nao precise deslizar pela página."
  - **Ação do Sistema**: Inseriu novas divisões baseadas em breakpoints Desktop (`lg:flex-row`, `lg:w-[400px]`), reposicionando o container da simulação (Canvas) lado a lado com os controles de parâmetros e blocos de feedback.
- **T-007**:
  - **Ação do Usuário**: Forneceu o protocolo de Inicialização, Requisitos e Arquitetura (Prompts E00, E01, E02).
  - **Ação do Sistema**: Gerou 3 arquivos `.md` na raiz, catalogando os metadados solicitados e mapeamentos de inventário e dependências.
- **T-008**:
  - **Ação do Usuário**: Forneceu o protocolo de Extração e Análise (Prompts E03, E04, E05, E06).
  - **Ação do Sistema**: Geração atual dos arquivos referentes ao mapeamento destas lógicas documentais.
