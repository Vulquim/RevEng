# Plano do RevEng

## Piloto em revisão

Comparar duas implementações próprias de uma lista de tarefas de demonstração. A referência usa dados sintéticos, de modo que os resultados possam ser reproduzidos a partir de um estado inicial definido. O piloto deve rodar localmente e registrar apenas o comportamento das operações descritas abaixo.

| Cenário | Entrada | Resultado esperado |
| --- | --- | --- |
| Estado inicial | Dados vazios | A lista informa que ainda não há tarefas |
| Criação | Título `Revisar orçamento` | Uma tarefa aparece com esse título e estado pendente |
| Validação | Título em branco | A interface informa o erro e a lista permanece igual |
| Mudança de estado | Concluir a tarefa criada | A tarefa recebe estado concluído e fica visível no filtro correspondente |
| Persistência | Reabrir a página após concluir a tarefa | O título e o estado concluído são restaurados |
| Exclusão | Remover a tarefa criada | A lista volta ao estado vazio e permanece assim depois de reabrir |

## Execução e evidência

1. Construir a referência e documentar como repor seu estado inicial.
2. Versionar entradas, ações de interface e resultados esperados. Revisar o contrato antes da implementação comparada.
3. Executar os cenários nas duas implementações a partir da mesma fixture. O Playwright é uma opção para repetir esses fluxos locais de interface.
4. Para cada cenário, registrar versão da referência, versão da implementação, versão do contrato, resultado esperado, resultado observado e ambiente. Capturar imagens apenas quando ajudam a entender uma divergência.
5. Marcar como conforme o cenário cujo comportamento observado atende ao contrato. Divergências registram o comportamento observado. Uma interrupção ou um dado ausente produz resultado inconclusivo com a causa registrada.

O piloto passa quando todos os cenários reproduzem o resultado esperado nas duas implementações e uma segunda execução limpa obtém os mesmos resultados. A revisão deve conferir também os estados de foco, erro e lista vazia.

## Componentes previstos

O piloto precisa de uma referência, uma implementação comparada, fixtures, contrato versionado e testes de interface. Os registros podem começar como arquivos locais com identificadores de execução. Interface de gestão, API, banco e orquestração serão avaliados quando o volume, os papéis e os requisitos de retenção estiverem definidos. As tecnologias listadas no [README](README.md) continuam em avaliação.

As decisões e entregáveis em aberto estão no [registro de alinhamento](docs/projeto/00-alinhamento.md).
