# Diagramas do Astro

Diagramas PlantUML revisados com os repositórios da [Astro-Inter](https://github.com/orgs/Astro-Inter/repositories), na tarefa [SCRUM-558](https://luizacursino.atlassian.net/browse/SCRUM-558).

A revisão de **31/10/2026** substitui a transcrição literal das imagens do ZIP por uma visão baseada no código e nos contratos consultados. O escopo visual mantém somente os três diagramas do ZIP: casos de uso, fluxo do funcionário e fluxo do gestor. Acesso, criação do workspace, eventos e comunicação aparecem dentro desses fluxos, sem diagramas adicionais. Foram inventariados **21 repositórios**, com aprofundamento nos fluxos pertinentes. O [relatório de revisão](docs/revisao-contexto.md) reúne correções, evidências fixadas por commit e divergências entre memorial e implementação.

Os diagramas representam o comportamento descrito no código. Eles não confirmam deploy, ativação de workers ou testes ponta a ponta. A versão que transcreve o ZIP permanece no histórico Git, no commit `d0a4543`.

## Navegação

| Diagrama | O que mostra | Fonte editável |
| --- | --- | --- |
| [Casos de uso e papéis](diagrams/rendered/casos_de_uso.svg) | Responsabilidades de Colaborador, Gestor, Gestor do Workspace e ADMIN. | [casos-de-uso.plantuml](diagrams/casos-de-uso.plantuml) |
| [Jornada do colaborador](diagrams/rendered/fluxo_funcionario.svg) | Eventos, perfil e NRs, alertas, conta e comunicação no mobile. | [fluxo-funcionario.plantuml](diagrams/fluxo-funcionario.plantuml) |
| [Jornada do gestor](diagrams/rendered/fluxo_gestor.svg) | Criação da empresa, operação cotidiana e ações exclusivas do responsável. | [fluxo-gestor.plantuml](diagrams/fluxo-gestor.plantuml) |

## Visualização

No VS Code, abra este README e pressione **Ctrl + Shift + V**. Expanda o diagrama desejado. Cada imagem possui um link para abrir em tamanho completo; os arquivos SVG podem ser abertos no navegador e ampliados sem perder nitidez.

<details open>
<summary>Casos de uso e papéis</summary>

Responsabilidades de Colaborador, Gestor, Gestor do Workspace e ADMIN.

[Abrir imagem em tamanho completo](diagrams/rendered/casos_de_uso.svg) · [Editar PlantUML](diagrams/casos-de-uso.plantuml)

![Casos de uso e papéis](diagrams/rendered/casos_de_uso.svg)

</details>

<details>
<summary>Jornada do colaborador</summary>

Eventos, perfil e NRs, alertas, conta e comunicação no mobile.

[Abrir imagem em tamanho completo](diagrams/rendered/fluxo_funcionario.svg) · [Editar PlantUML](diagrams/fluxo-funcionario.plantuml)

![Jornada do colaborador](diagrams/rendered/fluxo_funcionario.svg)

</details>

<details>
<summary>Jornada do gestor</summary>

Criação da empresa, operação cotidiana e ações exclusivas do responsável.

[Abrir imagem em tamanho completo](diagrams/rendered/fluxo_gestor.svg) · [Editar PlantUML](diagrams/fluxo-gestor.plantuml)

![Jornada do gestor](diagrams/rendered/fluxo_gestor.svg)

</details>

## Atualizar as imagens

Os `.plantuml` são as fontes; os SVGs em `diagrams/rendered/` são as imagens versionadas no README. Depois de editar uma fonte ou o estilo compartilhado `diagrams/estilo.iuml`, gere novamente as imagens a partir da raiz do repositório:

```sh
java -jar plantuml.jar -charset UTF-8 -checkonly "diagrams/*.plantuml"
java -jar plantuml.jar -charset UTF-8 -Playout=smetana -tsvg -o rendered "diagrams/*.plantuml"
```

O comando usa Java e PlantUML com Smetana, sem instalação separada de Graphviz. O estilo é local, sem includes remotos. Para manter fontes e imagens coerentes, inclua ambos no mesmo commit.

Os desenhos usam linguagem de negócio: ações das pessoas e decisões do processo. Endpoints, protocolos, bancos e detalhes de implementação ficam nas fontes técnicas do relatório de revisão.

Os losangos são usados somente para perguntas com respostas **sim** e **não**. As opções de menu aparecem em setas saindo da tela inicial, sem losangos de seleção ou de junção.

As etapas secundárias estão agrupadas para facilitar a leitura. Os três desenhos mostram os fluxos principais; as regras detalhadas e as evidências permanecem no relatório de revisão.

## Principais correções

- Separação de Colaborador, Gestor, Gestor do Workspace e ADMIN, com limites por canal.
- Primeiro acesso por chave separado de login Firebase e criação de workspace.
- Ações de navegação como escolhas, com retorno à Home; sem paralelismo artificial.
- Eventos com turmas, evidências e validação pelo gestor criador.
- Certificados tratados como possíveis evidências, sem uma relação obrigatória de consulta para alteração.
- Chat humano e IA com persistência durante a interação; sair da tela não dispara o salvamento.
- Integrações pertinentes descritas nos próprios fluxos, com seus limites documentados.

Consulte as [divergências que exigem decisão do projeto](docs/revisao-contexto.md#divergências-que-exigem-decisão-do-projeto) antes de usar estes diagramas como especificação de novas regras de negócio.
