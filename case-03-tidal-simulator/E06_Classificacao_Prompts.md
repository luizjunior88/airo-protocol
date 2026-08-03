# E06 - Classificação de Prompts

Este documento descreve e qualifica as entradas e direcionamentos efetuados pelo testador para influenciar diretamente a infraestrutura, a matemática ou o design final do aplicativo. 

## 1. Correção de Lógica e Fidelidade Matemática
Os prompts sob esta categoria visaram estreitar e tornar precisos os modelos algébricos ou de validação simulada da aplicação.

- **PRM-001** (`T-001`): "2pi/11 deve ser o x" 
  - **Natureza**: Correção de Lógica Algébrica/Matemática.
- **PRM-003** (`T-003`): "certifique-se de que o intervalo dos parâmetros atende aos pontos dados" 
  - **Natureza**: Correção de Lógica de Validação (tolerâncias).

## 2. Ajuste de Interface / Experiência do Usuário (Pedagógica)
Estes prompts serviram para moldar a interface (UI/UX) tendo o princípio pedagógico (facilitação do aluno) como condutor das ações visuais.

- **PRM-002** (`T-002`): "onde é exibido a função, deixe-a genérica f(x)=a+bsen(cx-d)" 
  - **Natureza**: Intervenção Textual e Pedagógica.
- **PRM-005** (`T-005`): "ajuste a responsividade. mesmo no modo desktop não se vê tudo no mesmo ecrã, no mobile também. para um aluno é melhor ter tudo à vista sempre" 
  - **Natureza**: Reorganização de Layout e Dimensões.
- **PRM-006** (`T-006`): "no mobile penso que está bom, mas no desktop, quero o gráfico e os parametros na mesma tela para que o aluno nao precise deslizar pela página." 
  - **Natureza**: Reorganização Estrutural Baseada em Breakpoints (Desktop).

## 3. Resolução de Erros e Estabilidade (Manutenção)
Estes focaram unicamente na correção de falhas e regressões técnicas durante a compilação ou execução do sistema base.

- **PRM-004** (`T-004`): "Fix the errors in the app [...] Failed to load image:" 
  - **Natureza**: Correção de Erros de Asset / Estabilidade Visual.
