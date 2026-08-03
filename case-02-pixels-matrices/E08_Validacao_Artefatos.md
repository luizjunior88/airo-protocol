# E08 - Validação de Artefatos

## Checklist de Validação Humana

1. **Intenção Original Preservada?** 
   - [x] O aplicativo atua como simulador 2D puro sem adições alucinadas da máquina.
2. **Consistência Visual (Anti-Slop)?** 
   - [x] O design é austero, minimalista e focado no Tailwind CSS de alto contraste sem ornamentos desnecessários (shadows exagerados ou degradês artificiais).
3. **Rigidez Matemática?** 
   - [x] Teste teórico comprova que a matriz `[1, 1.5, 0, 1]` produz efetivamente um *shear* horizontal. O determinante da matriz de rutura colapsa corretamente a dimensão (área 0).
4. **Alinhamento ao Design por Subtração?** 
   - [x] A interface obedece estritamente aos pedidos restritivos do professor (remoção do rodapé, renomeação enigmática das tabs).
5. **Navegabilidade Epistémica?**
   - [x] O usuário passa sequencialmente pelos nós didáticos corretos até à rutura conceptual.
6. **Robustez a Erros:**
   - [x] O erro anterior `points is not defined` foi mitigado na implementação validada e compilada.
