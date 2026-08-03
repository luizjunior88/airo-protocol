# E09 - Arquitetura do Artefato

Abaixo se apresenta o mapeamento estrutural técnico e consolidado da Single Page Application (SPA), focando na correlação entre estados do React e os desdobramentos de UI para suportar o aprendizado ativo.

## 1. Estrutura Base de Árvore

```text
src/
 ├── main.tsx           # Entry point do React e montagem do DOM principal
 ├── index.css          # Injeção global das camadas do TailwindCSS
 ├── vite-env.d.ts      # Tipagens base de ambiente para o bundler Vite
 └── App.tsx            # Stateful Container único (Single-View component)
```

## 2. Mapa de Relacionamento de Módulos (App.tsx)

O arquivo `App.tsx` opera como maestro orquestrador de todos os fluxos. Toda a arquitetura foi mantida intencionalmente em um módulo autocontido para otimizar processamentos sequenciais de tokens no ambiente do AI Studio, sem fragmentação extrema, embora garantindo separação clara de responsabilidades por domínios de funções.

| Módulo/Hook | Descrição Arquitetural | Ligações / Dependências | Suporte Construtivista |
|---|---|---|---|
| **Estados Base** (`mode`, `isHardUnlocked`, `isWon`) | Gerenciamento de bloqueios e estágios do aplicativo. | Vinculados à renderização dos botões (ART-001) e inputs. | Garante progressão gamificada: o conhecimento estrutural avançado exige vitória empírica prévia. |
| **`easyParams`** (`A, B, C, D`) | Objeto de estado reativo contendo as variáveis matemáticas em uso. | Vinculado aos sliders (ART-002) e injetado na renderização do P5 via iteração matemática. | Fornece feedback instantâneo da ação motora e visual, cimentando correlações abstratas. |
| **`equation`** | Estado de texto literal (string). | Vinculado ao campo de texto do Modo Avançado (ART-003). | Transforma a observação intuitiva em formalização acadêmica (registro explícito). |
| **P5 Sketch** (`canvasRef`) | Função auto-invocada que gera a camada de visualização em loop. | Lê os estados correntes do componente pai a cada ciclo via objeto mutável não-reativo (`useRef` - `stateRef`). | O componente lúdico central, fornece materialização visual abstrata (gráfico + navio) ao problema lógico. |
| **`handleSimulate`** e **Feedback State** | Lógica síncrona engatilhada pelo botão Simular. Analisa deltas contra constantes geométricas (`TRUE_POINTS`). | Atualiza o estado `feedbackState` baseando-se no `threshold` corrente. Invoca `mathjs` no Modo Avançado. | O núcleo da mediação pedagógica socrática; direciona o foco do aluno e evita tentativa-e-erro cega. |

## 3. Dinâmica de Renderização Condicional
A aplicação evita transições de rotas complexas. A abordagem puramente SPA e de UI ancorada (sem scroll) é governada pela variável `mode`. Quando o `mode` altera, o DOM troca o painel de Sliders pelo Input Textual, preservando intacta a visualização lateral gráfica do P5, permitindo que a continuidade cognitiva da atividade seja ininterrupta.
