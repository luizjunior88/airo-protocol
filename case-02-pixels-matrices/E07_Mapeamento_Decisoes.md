# E07 - Mapeamento de Decisões (ADR)

## DEC-001: Renderização Simultânea Multicor (Parte 4)
* **Status:** Implementado
* **Contexto/Inferência:** Explicar a não-comutatividade requer que o aluno veja a diferença temporal ou espacial das operações matriciais.
* **Decisão (Evidência):** Adicionar suporte para sobreposição visual no SVG com cores Púrpura (M1xM2) e Laranja (M2xM1).
* **Consequências:** Aumenta a carga visual no canvas, mas diminui a carga da memória de trabalho, reduzindo o custo cognitivo da comparação temporal.

## DEC-002: Ocultação da Meta-Linguagem Didática (Navegação)
* **Status:** Implementado
* **Contexto/Inferência:** O professor notou que títulos de navegação como "Parte II: Rutura" e "Parte III: Shear" revelavam antecipadamente a solução do desafio.
* **Decisão (Evidência):** Renomear todos os botões no topo para texto cego "Part X".
* **Consequências:** Fomenta o modelo construtivista e 'inquiry-based', forçando o aluno a descobrir empiricamente o efeito gerado sem pistas textuais explícitas.

## DEC-003: Subtração do Rodapé
* **Status:** Implementado
* **Contexto/Inferência:** O rodapé exibia a taxa de frames (60 FPS) e autoria, elementos que atraem a atenção ocular, mas não colaboram para o raciocínio matemático pretendido (Princípio da Coerência de Mayer).
* **Decisão (Evidência):** Remoção total do elemento genérico (footer).
* **Consequências:** Interface mais minimalista, amplificando a 'canvas real-estate' e focando no plano cartesiano.
