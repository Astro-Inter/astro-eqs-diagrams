# Diagramas do Astro

Diagramas PlantUML do Astro, na tarefa [SCRUM-558](https://luizacursino.atlassian.net/browse/SCRUM-558).

O repositório mantém somente os três diagramas do ZIP: casos de uso, fluxo do funcionário e fluxo do gestor. O caso de uso mantém a versão simplificada e os papéis ajustados. Os dois fluxos recuperam as etapas e conexões das imagens originais do ZIP, com apresentação padronizada em PlantUML.

O [relatório de revisão](docs/revisao-contexto.md) registra separadamente a análise dos 21 repositórios da Astro-Inter e as diferenças entre a documentação original e o código consultado.

No caso de uso, `<<include>>` representa a validação da chave como parte obrigatória da criação do workspace. `<<extend>>` representa a ativação da conta como complemento do acesso, apenas no primeiro acesso.

## Navegação

| Diagrama | O que mostra | Fonte editável |
| --- | --- | --- |
| [Casos de uso e papéis](diagrams/rendered/casos_de_uso.svg) | Responsabilidades de Colaborador, Gestor, Gestor do Workspace e ADMIN. | [casos-de-uso.plantuml](diagrams/casos-de-uso.plantuml) |
| [Jornada do colaborador](diagrams/rendered/fluxo_funcionario.svg) | Login, cadastro, calendário, histórico de treinamentos, NRs e conversas. | [fluxo-funcionario.plantuml](diagrams/fluxo-funcionario.plantuml) |
| [Jornada do gestor](diagrams/rendered/fluxo_gestor.svg) | Acesso ao workspace, configurações, unidades e cadastro de funcionários. | [fluxo-gestor.plantuml](diagrams/fluxo-gestor.plantuml) |

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

Login, cadastro, calendário, histórico de treinamentos, NRs e conversas.

[Abrir imagem em tamanho completo](diagrams/rendered/fluxo_funcionario.svg) · [Editar PlantUML](diagrams/fluxo-funcionario.plantuml)

![Jornada do colaborador](diagrams/rendered/fluxo_funcionario.svg)

</details>

<details>
<summary>Jornada do gestor</summary>

Acesso ao workspace, configurações, unidades e cadastro de funcionários.

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

## Referência dos fluxos

Os fluxos do funcionário e do gestor seguem as imagens de atividades do arquivo entrega-astro.zip. As etapas, ramificações e integrações descritas nessas imagens foram recuperadas; os ajustes visuais abrangem cores, organização por área, espaçamento e destaque dos rótulos. Os losangos são usados apenas para perguntas de **sim** ou **não**, sem anotações de rodapé.

O [relatório de revisão](docs/revisao-contexto.md) continua disponível para consultar as diferenças em relação ao código do projeto.
