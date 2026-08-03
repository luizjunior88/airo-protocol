# E02 - Metadados Técnicos e Stack

## Stack Tecnológica

* **Framework Principal:** React (via Vite)
* **Linguagem:** TypeScript
* **Estilização:** Tailwind CSS v3/v4 (Inferência: baseamo-nos nas classes utilitárias no código)
* **Ícones:** `lucide-react` (Evidência: importação explícita de `RotateCcw`, `AlertTriangle`, `CheckCircle` em `App.tsx`)
* **Gráficos/Renderização:** SVG Nativo manipulado via React (DOM) em `SvgCanvas.tsx`.

## Dependências e Bibliotecas
```json
{
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "lucide-react": "^0.263.1"
  },
  "devDependencies": {
    "typescript": "^5.0.2",
    "vite": "^4.4.5",
    "tailwindcss": "latest"
  }
}
```

## Requisitos de Infraestrutura
* Hospedagem: Google AI Studio / Web (Evidência).
* Ambiente de execução: Navegador Web (Client-side puro).
* Persistência de Dados: Em memória (Stateful React). Não há evidência de banco de dados externo ou backend, portanto, as sessões perdem os dados ao atualizar a página.
