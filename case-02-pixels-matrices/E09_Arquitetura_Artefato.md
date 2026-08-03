# E09 - Arquitetura do Artefato

## Raio-X Arquitetural

```text
/src
 ├── App.tsx (Main Stateful Component - Controller)
 │    ├── Gestão do Estado `part` (Nav/Router Lógico)
 │    ├── Gestão da Lógica Matricial (multiplyMatrices, deteção de matriz singular/shear)
 │    └── Componentes Filhos de UI:
 │         ├── <MatrixInput /> (Recebe e valida input numérico do user)
 │         └── <SvgCanvas /> (Renderização Pura 2D Geométrica)
 ├── components
 │    └── SvgCanvas.tsx (Presentation Component)
 │         └── Recebe matriz(es), aplica `transformPoint` ao SVG
 └── index.css (Estilos globais / Tailwind)
```

## Relacionamento de Módulos e Construtivismo
A arquitetura suporta o modelo construtivista pois separa a **Lógica Algébrica** (State no App.tsx) da **Representação Visual** (SvgCanvas.tsx). Quando o aluno altera o input no `<MatrixInput />`, a reatividade do React força o `SvgCanvas` a atualizar imediatamente os vértices da matriz poligonal em tela. Isso provê 'feedback extrínseco instantâneo', base do micro-mundo de Papert.
