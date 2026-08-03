# E10 - Problemas e Limitações

Levantamento técnico, registro formal e status dos gargalos da solução, mapeando também limitações operacionais da arquitetura escolhida.

| ID | Descrição da Evidência | Severidade | Status |
|---|---|---|---|
| **PRB-001** | Quebra de carregamento da imagem via URL `p5.loadImage` causando travamento ou poluição no console. | Alta | Resolvido (Substituição por gradiente visual autogerado em `p5.lerpColor`). |
| **PRB-002** | Overflow vertical massivo forçando rolagem indesejada de tela, desvinculando fisicamente o gráfico dos controles no viewport do usuário. | Média | Resolvido (Aplicação drástica de classes CSS Flexbox, compactação de espaçamentos e altura limitante ao canvas `max-h-[35vh]`). |
| **PRB-003** | Limitações do Parser de Equação (`mathjs`): Embora seja seguro, formas erráticas de escrita (por exemplo: ignorar totalmente símbolos de multiplicação explícita em cenários não previstos) podem ser compreendidas equivocadamente ou lançar exceções silenciosas. | Baixa | Em aberto / Limitação Técnica Aceitável. |
| **PRB-004** | Vulnerabilidade do "Chute": O valor estático do Threshold (`1.0` no Easy, `0.5` no Hard) pode, eventualmente, permitir falsos positivos se a curva do usuário cruzar os `TRUE_POINTS` por pura sorte com uma função altamente destoante e descompensada. | Baixa | Em aberto / Limitação Pedagógica (mitigado pela verificação de amplitude e média). |
| **PRB-005** | Perda de Estado no Reload: Dado que o armazenamento da aplicação repousa exclusivamente na memória local (Client-Side), recarregar a página tranca novamente o modo Avançado (perda de progresso). | Média | Em aberto (Decisão arquitetural: sem backend por design, exige conclusão em sessão única). |

## Observações Gerais sobre a Performance
A integração entre React (baseado em Virtual DOM) e o `p5.js` (baseado em Canvas Frame Rendering direto) tem performance excepcionalmente alta no estado atual, porém a ponte de estado feita utilizando a mutação de uma `ref` no React dita que alterações muito bruscas podem, em hardwares antigos e dispositivos mobile de entrada, não ser precisamente renderizadas no exato milissegundo de troca do slider. A fluidez da experiência, entretanto, está totalmente assegurada em contextos escolares padrão.
