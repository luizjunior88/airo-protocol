---
title: "Estado 06: Extração e Mapeamento do Código Fonte"
author: "AI Studio Research Orchestrator"
date: "2026-07-27"
state: "06_extracao_codigo"
output_file: "06_extracao_codigo.md"
---

# 1. Arquitetura do Sistema de Ficheiros
Com base na listagem do diretório atual (`ls -la`), a árvore de ficheiros da aplicação apresenta a seguinte arquitetura standard de uma SPA (Single Page Application) baseada em Vite/React:

- **Configurações de Ambiente e Build:**
  - `package.json` / `package-lock.json` / `bun.lock` (Gestão de dependências e scripts)
  - `vite.config.ts` (Configuração do bundler Vite)
  - `tsconfig.json` (Configuração do compilador TypeScript)
  - `.env.example` (Variáveis de ambiente de referência)
  - `metadata.json` (Metadados do projeto no AI Studio)
  - `.gitignore` (Exclusões do sistema de controlo de versão)
- **Ficheiros Estáticos:**
  - `index.html` (Ponto de entrada do DOM)
  - `public/` (Diretório para assets estáticos e relatórios gerados nesta auditoria)
- **Código Fonte da Aplicação:**
  - `src/` (Diretório contendo o código fonte TypeScript/React)
    - `src/App.tsx` (Ficheiro principal monolítico que alberga a UI e Lógica)
- **Documentação de Auditoria (Gerada):**
  - `relatorio-auditoria-completa.tex`
  - `relatorio-tecnico-pedagogico.md`
  - Ficheiros numéricos `00_inicializacao.md` a `06_extracao_codigo.md`

# 2. Mapeamento Estrutural do Ficheiro Principal (`src/App.tsx`)
A análise dos *diffs* e excertos acedidos no histórico permite mapear a seguinte topologia interna do `src/App.tsx` (que possui ~1150 linhas):

- **Dependências e Importações:**
  - React Hooks (`useState`, `useEffect`).
  - Ícones do `lucide-react` (ex: `ChevronLeft`, `ChevronRight`).
  - Componentes gráficos da biblioteca `recharts` (inferidos pela tag `<Line>`).
- **Tipos e Interfaces TypeScript:**
  - `params`: Objeto controlando os parâmetros do sistema físico (`mouseStart`, `mouseSpeed`, `catStart`, `catSpeed`).
  - `viewMode`: Tipologia do estado de visualização (`'story'`, `'math'`, etc.).
- **Gestão de Estado Global/Local (Hooks):**
  - `isSimulating`: Booleano que tranca a interface e permite o avanço do tempo.
  - `currentTime`: Temporizador/Eixo X da simulação.
  - `showNoAdvantageWarning`: Controlo modal para avisos de domínio (vantagem nula).
  - `fichaPassword` / `fichaPasswordError` / `selectedFicha`: Gestão de autenticação client-side para funcionalidades bloqueadas.
  - `intersection`: Objeto de metadados da colisão matemática (contém o tipo, ex: `'SPI'`).
- **Lógica Matemática e Cinemática:**
  - Implementações de verificação para intersecção de duas retas em $s = s_0 + v \cdot t$.
  - Função `handleRun()` para iniciar a temporização validando as condições de contorno cinemático.
- **Componentes de UI / Layout:**
  - **Gráfico:** Representação cartesiana via SVG (Recharts).
  - **Painel de Controlo:** Sliders numéricos vinculados a `params` com botões iteradores passo-a-passo.
  - **Modais:** Telas de introdução de senhas com renderização condicional de assets fotográficos via URLs de Google Drive.

# 3. Transcrição / Trechos do Código Crítico

### A. Lógica de bloqueio de inputs durante a simulação (`isSimulating`)
Trecho que demonstra a proteção contra concorrência e manipulação durante o cálculo em *runtime*:
```tsx
<button 
  onClick={() => setParams(p => ({ ...p, mouseStart: Math.max(-50, Number((p.mouseStart - 0.1).toFixed(1))) }))}
  disabled={isSimulating}
  className="bg-blue-500/20 hover:bg-blue-500/30 p-1 rounded-md transition-colors disabled:opacity-50 disabled:cursor-not-allowed"
>
  <ChevronLeft className="w-4 h-4 text-blue-600" />
</button>
// ... [CÓDIGO DE OUTROS ELEMENTOS DO PAINEL] ...
<input 
  type="range"
  min="-50"
  max="50"
  step={viewMode === 'math' ? 0.1 : 1}
  value={params.mouseStart}
  onChange={(e) => setParams(p => ({ ...p, mouseStart: Number(e.target.value) }))}
  disabled={isSimulating}
  className="w-full h-1 md:h-3 bg-blue-600 rounded-lg appearance-none cursor-pointer disabled:opacity-50 disabled:cursor-not-allowed accent-black"
/>
```

### B. Tratamento de exceções lógicas (Vantagem Zero e SPI com `strokeDasharray`)
Trechos que asseguram a correção visual e conceitual das equações da cinemática:
```tsx
  useEffect(() => {
    if (viewMode === 'story' && params.mouseStart === 0 && params.mouseSpeed !== params.catSpeed) {
      setShowNoAdvantageWarning(true);
    }
  }, [params.mouseStart, params.mouseSpeed, params.catSpeed, viewMode]);

  const handleRun = () => {
    if (viewMode === 'story' && params.mouseStart === 0 && params.mouseSpeed !== params.catSpeed) {
      setShowNoAdvantageWarning(true);
      return;
    }
    setCurrentTime(0);
    setIsSimulating(true);
  };
```
Representação gráfica de retas coincidentes no Recharts:
```tsx
<Line 
  // ... [PROPRIEDADES DA LINHA (CÓDIGO NÃO DISPONÍVEL NO HISTÓRICO)] ...
  strokeWidth={4} 
  dot={false} 
  animationDuration={0}
  strokeDasharray={intersection.type === 'SPI' ? "8 8" : undefined}
/>
```

### C. Gestão e verificação de senhas do Modo História e Fichas
Lógica de validação estática client-side para aceder aos documentos pedagógicos:
```tsx
// Handlers de submissão de senha (onClick)
<button 
  onClick={() => {
    if (fichaPassword === 'profmat') {
      window.open(selectedFicha === 'story' ? 'https://drive.google.com/file/d/17NUIWZbw2e1PVc47Ldnaw_uD26a8WFDF/view?usp=sharing' : 'https://drive.google.com/file/d/1wZzUCtsoFkvrAlFHycE0H4YeMnQPe2x4/view?usp=drive_link', '_blank');
      setActiveModal(null);
      setSelectedFicha(null);
      setFichaPassword('');
      setFichaPasswordError(false);
    }
    // ... [CÓDIGO NÃO DISPONÍVEL NO HISTÓRICO - LÓGICA ELSE/ERRO]
  }}
>
```
Feedback visual lúdico para o erro de acesso ao "Modo Analítico":
```tsx
<img 
  src="https://lh3.googleusercontent.com/d/10jYE3-FZSvrRg6bXcBsqE_zQvFr6R3GQ" 
  alt="Erro de senha" 
  className="w-32 h-32 md:w-48 md:h-48 object-contain drop-shadow-md"
  referrerPolicy="no-referrer"
/>
<p className="text-sm text-red-500 font-bold">Senha incorreta.</p>
```
Feedback visual contido para o erro de acesso às fichas:
```tsx
{fichaPasswordError && (
  <p className="text-sm text-red-500 font-bold pl-1 pt-1">Senha incorreta.</p>
)}
```
