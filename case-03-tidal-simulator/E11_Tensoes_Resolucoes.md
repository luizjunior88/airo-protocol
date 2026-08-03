# E11 - Tensões e Resoluções

Este catálogo explora os conflitos fundamentais que emergiram entre as limitações ou propensões tecnológicas (a forma como o software e a IA tentam resolver o problema) versus o rigor e a intenção metodológica e pedagógica propostas na testagem.

## TEN-001: Ludicidade Fotorrealista vs. Resiliência de Conexão
- **Evidência**: A primeira versão do software tentou injetar uma imagem externa de alta resolução carregada a partir de uma API da Unsplash como pano de fundo do simulador (`PIER_IMAGE_URL`), que ocasionalmente produzia falhas de carregamento e lograva erros (`Failed to load image`).
- **Interpretação (O Conflito)**: A IA tentou maximizar a beleza e a ludicidade da cena visual importando ativos de terceiros. Pedagogicamente, qualquer distração visual derivada de dependências externas não carregadas e indicadores de erro pode minar a concentração da sessão de estudo e frustrar o usuário final, destruindo o ambiente seguro de aprendizado.
- **Resolução (Subtração Tecnológica)**: A imagem foi deliberadamente removida. Optou-se por utilizar o core de processamento visual para desenhar iterativamente um gradiente seguro de cores (`p5.lerpColor`). Isso trocou "embelezamento frágil" por "design imersivo inquebrável".

## TEN-002: Detalhamento Paramétrico vs. Carga Cognitiva no Espaço
- **Evidência**: O layout inicialmente apresentava seus componentes em um fluxo linear de coluna (`flex-col`), obrigando o canvas e os painéis de parâmetro a ocuparem, sucessivamente, o espaço de tela inferior e forçando a barra de rolagem.
- **Interpretação (O Conflito)**: A arquitetura web padrão propõe que listas ou empilhamentos verticais são excelentes para consumo de conteúdo responsivo longo (artigos, feeds). Todavia, na teoria de construtivismo e cognição situada, afastar o local onde se insere a variável matemática da área exata em que ocorre a reação anula o ciclo de feedback da experimentação prática.
- **Resolução (Restrição Positiva)**: Foi aplicada uma compressão rigorosa no design através de comandos (`max-h-[35vh]`, paddings mínimos, readequação grid em `lg:flex-row`). O software foi forçado a sacrificar espaços mortos luxuosos para garantir que a atenção visual do aluno englobe a equação manipulada e o gráfico instantaneamente, simultaneamente.

## TEN-003: Avaliação de Texto Dinâmico vs. Segurança Rigorosa
- **Evidência**: O "Modo Avançado" requer que o estudante escreva a equação trigonometrica exata usando um teclado ou pad de string.
- **Interpretação (O Conflito)**: Existe uma dificuldade computacional gigantesca na extração de lógica determinística via campos de texto livres em javascript (risco de falhas sintáticas que a engine web não perdoa). Seria tecnicamente muito mais estável limitar os alunos a escolher botões ou selecionar opções pré-determinadas para os parâmetros. No entanto, ceder à estabilidade tecnológica nesse ponto destruiria o propósito pedagógico avaliativo final, onde o cérebro tem de passar da manipulação mecânica para a formalização abstrata literal.
- **Resolução**: Instalação e acoplamento do `mathjs` somado a higienizações de `regex`. Trata-se do ponto em que a tecnologia foi forçada a acomodar (mesmo encarecendo a compilação do pacote web) o requisito epistemológico central. O aluno está livre para digitar e a tecnologia é responsável por compreender sua gramática matemática segura e compilar o resultado da maré.
