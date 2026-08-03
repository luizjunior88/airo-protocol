# E10 - Problemas e Limitações

| ID | Descrição | Severidade | Status |
| :--- | :--- | :--- | :--- |
| PRB-001 | **Sobreposição Visual Confusa (Parte 4):** Se as matrizes inseridas apresentarem alta escala, as formas renderizadas simultaneamente podem vazar os limites do SVG ou ficar sobrecarregadas de ler. | Média | Em aberto |
| PRB-002 | **Ausência de Responsividade Tátil Fina:** A inserção de valores na matriz depende estritamente do teclado; não há manipulação direta (drag) dos vértices no plano para os alunos descobrirem os vetores inversamente. | Baixa | Limitação Arquitetural |
| PRB-003 | **Injeção de Ponto Flutuante:** Erros de precisão no javascript para valores complexos decimais do determinante (ex: 0.1 + 0.2), mas a lógica atual aproxima com margem (ex: `Math.abs(parsedGuess - det) < 0.05`). | Baixa | Mitigado por código |
