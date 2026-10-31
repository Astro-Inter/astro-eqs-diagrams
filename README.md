# astro-eqs-diagrams

Diagramas do projeto Astro em PlantUML, na tarefa
[SCRUM-558](https://luizacursino.atlassian.net/browse/SCRUM-558).

## Diagramas

| Arquivo PlantUML | Imagem de referência no ZIP |
| --- | --- |
| [Casos de uso](diagrams/casos-de-uso.plantuml) | `Entrega Astro/Diagramas/Diagrama de caso de usos.png` |
| [Fluxo do funcionário](diagrams/fluxo-funcionario.plantuml) | `Entrega Astro/Diagramas/Fluxo Funcionario - Diagrama de  atividades.jpg` |
| [Fluxo do gestor](diagrams/fluxo-gestor.plantuml) | `Entrega Astro/Diagramas/Fluxo Gestor - Diagrama de atividades.jpg` |

As referências atuais são as três imagens do arquivo
`c37f0fb9-e455-476d-bba6-24ab7ba6cc9c_entrega-astro.zip`.
Elas substituem as fontes anteriores de casos de uso (Lucidchart) e do
fluxo do funcionário (draw.io), que permanecem no histórico Git.

## Renderização

Com Java, PlantUML e Graphviz:

```sh
java -jar plantuml.jar -charset UTF-8 -tsvg diagrams/*.plantuml
```

Nas versões do PlantUML com Smetana, é possível renderizar sem instalar
Graphviz:

```sh
java -jar plantuml.jar -charset UTF-8 -Playout=smetana -tsvg diagrams/*.plantuml
```

## Critérios da conversão

Os rótulos, as decisões, as associações e os sentidos das setas foram
transcritos das imagens. O layout é calculado pelo PlantUML; as partições
organizam os fluxos sem reproduzir as coordenadas originais. Os nós finais
de cada diagrama de atividades são apresentados como um encerramento comum.

### Casos de uso

- Inclui os atores Funcionário e Gestor, 15 casos de uso, 20 associações
  dos atores e três relações `include`.
- No ZIP, ambos os atores se associam a `Visualizar certificados`, que
  inclui `Manipular certificados`. Esse sentido difere da fonte anterior
  do Lucidchart e foi preservado conforme a imagem recebida.
- As inclusões de eventos e NRs partem de `Manipular` para `Visualizar`.
  A legenda `NR: Normas Regulamentadoras` foi mantida.
- Cruzamentos com pontes representam linhas independentes, sem associação
  adicional entre os casos de uso.

### Fluxo do funcionário

- Inclui autenticação, calendário e detalhes de eventos, histórico de
  treinamentos, NRs, chatbot e chat com o gestor.
- As barras de sincronização foram preservadas, inclusive no histórico,
  que contém somente uma chamada de API na imagem do ZIP.
- As etapas `Voltar para Home`, `Voltar para Calendário` e `Volta para Login`
  foram mantidas como atividades sem seta de saída, conforme a imagem.
  Não foram acrescentados ciclos de navegação.
- Os dois chats incluem a decisão `Continuou conversa?`, a continuidade
  na tela e o salvamento da conversa no banco antes de `Outras ações`.
- O fluxo das NRs mantém o rótulo da API do Histórico e a ligação recebida
  da tela do chatbot, como aparecem no original.
- Na imagem, a atividade `Chat com o Gestor` não tem uma seta de entrada
  visível; foi mantida como início separado desse trecho.

### Fluxo do gestor

- Inclui acesso à Landing Page, verificação de cadastro, geração de chave
  de acesso, criação do workspace e suas configurações.
- O workspace permite configurar NRs da empresa, criar e configurar
  unidades e cadastrar funcionários por duas rotas: manual ou planilha.
- No cadastro manual, a ausência de unidade direciona à criação e
  configuração da unidade, encerrando essa rota como na imagem.
- As rotas de cadastro com unidade existente e por planilha convergem na
  geração de chaves para as contas dos funcionários.
- O rótulo `Exporta planilha de funcionários` foi preservado, assim como
  as etapas de criação de cargos e perfis por Excel e configuração de NRs.
