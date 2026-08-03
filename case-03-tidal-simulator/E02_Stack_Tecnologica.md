# E02 - Metadados Técnicos e Stack Tecnológica

## 1. Arquitetura e Ambiente
- **Tipo de Aplicação**: Single Page Application (SPA), renderização puramente Client-Side.
- **Framework e Bundler**: React 18+ com Vite.
- **Linguagem**: TypeScript.

## 2. Bibliotecas e Dependências
Abaixo estão as dependências mapeadas a partir das instâncias documentadas:
- **`react`** / **`react-dom`**: Construção reativa de UI, gerenciamento de ciclos de vida e estados através de hooks (`useState`, `useEffect`, `useRef`).
- **`p5`**: Biblioteca para renderização gráfica e simulações iterativas via elemento `<canvas>`, responsável pelos plots de funções visuais matemáticas, preenchimentos gradientes e modelagem lúdica em 2D.
- **`mathjs`**: Interpretador matemático encarregado de parsear strings e instanciar árvores de expressão (`math.compile()`, `expr.evaluate()`) injetadas no Modo Avançado.
- **`lucide-react`**: Coleção vetorizada para uso na iconografia indicativa de estado (Ícones usados: `AlertCircle`, `Ship`, `CheckCircle2`, `Lock`, `Unlock`, `RefreshCw`).
- **Tailwind CSS**: Utilitário em-linha (utility-first framework) para composição estrutural, tipografia, paletas de cor exclusivas e sistema de containers responsivos (`flex`, `grid`).

## 3. Comandos de Infraestrutura

```bash
# Instalação limpa dos pacotes
npm install

# Inicialização do servidor de desenvolvimento HMR
npm run dev

# Compilação e tipagem da aplicação em bundle estático unificado
npm run build

# Validação do código estático (Lint e Verificação sintática de TypeScript)
npm run lint
```

## 4. Inferências Arquiteturais Extras
- **Inferência**: Dado o projeto operar estritamente em interações síncronas entre os hooks do React e o core de parseamento numérico nativo em navegador, conclui-se que o presente sistema descarta o uso de back-ends acoplados ou banco de dados em rede para gerenciar pontuações/progressos, sendo toda a mutabilidade operada internamente pelo cliente em memória volátil, resetando as condicionais (ex: locks) nos processos de unmount do ambiente de teste local.
