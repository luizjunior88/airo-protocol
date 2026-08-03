# E03 - Artefatos Produzidos

## Detalhamento Técnico dos Artefatos

### ART-001: App.tsx
* **Natureza:** Componente Funcional React (Root)
* **Características:**
  - Gere múltiplos estados globais (`part`, `matrix`, `matrix1`, `matrix2`, `isSecretRevealed`, etc).
  - Inclui a lógica condicional de apresentação das Partes 1 a 4.
  - Implementa funções de verificação (ex: verificar determinante, cadeado pedagógico).

### ART-002: SvgCanvas.tsx
* **Natureza:** Componente Visual React
* **Características:**
  - Recebe as props `matrix`, `part`, `matrix1`, `matrix2` para definir a renderização.
  - Renderiza uma grelha cartesiana de base.
  - Utiliza `transformPoint` para calcular as novas coordenadas com base nos coeficientes `a, b, c, d`.
  - Na parte 4, processa e renderiza duas transformações sobrepostas para evidenciar não-comutatividade.

### ART-003: Lógica Algébrica
* **Natureza:** Funções Utilitárias TypeScript
* **Características:**
  - `multiplyMatrices(m1, m2)`: Calcula produto matricial 2x2.
  - Valida matematicamente efeitos específicos (ex: `a === 1 && d === -1` para reflexão horizontal).

### ART-004: Quick Actions (Presets)
* **Natureza:** Objeto TypeScript (`PRESETS`)
* **Características:**
  - Mapeia matrizes constantes nomeadas (Identity, Rotation, Scale, Shear, Singular).
  - Atualiza o estado da aplicação via a função `animateToMatrix`.
