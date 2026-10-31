# astro-eqs-diagrams

Diagramas do projeto Astro em PlantUML.

## Casos de uso

O arquivo [diagrams/casos-de-uso.plantuml](diagrams/casos-de-uso.plantuml)
converte a página `Diagrama de caso de uso` do
[documento no Lucidchart](https://lucid.app/lucidchart/2a5bf69e-c376-4aea-a181-a1d802ce6fba/edit?page=.Q4MUjXso07N),
também na tarefa [SCRUM-558](https://luizacursino.atlassian.net/browse/SCRUM-558).
Contém os atores Funcionário e Gestor, os 15 casos de uso, as 20 associações
dos atores e as três relações `include`, dentro do limite do sistema Astro.

A conversão foi conferida com as exportações JSON e SVG do Lucidchart.
Conexões do Gestor que terminavam em linhas de associação do Funcionário
foram representadas como associações diretas ao mesmo caso de uso.
A inclusão de `Visualizar certificados` em `Manipular certificados` foi
confirmada visualmente, pois sua ponta não está vinculada no JSON exportado.
A legenda de NRs foi mantida; os campos de pontos de extensão presentes
no JSON, mas não exibidos no original, não foram acrescentados ao desenho.

Para renderizar sem instalar Graphviz, usando PlantUML com Smetana:

```sh
java -jar plantuml.jar -charset UTF-8 -Playout=smetana -tsvg diagrams/casos-de-uso.plantuml
```

## Fluxo do funcionário

O arquivo [diagrams/fluxo-funcionario.plantuml](diagrams/fluxo-funcionario.plantuml)
converte o diagrama draw.io `Diagrama sem nome` (página `Página-1`) para
PlantUML, conforme a tarefa [SCRUM-558](https://luizacursino.atlassian.net/browse/SCRUM-558).
Inclui autenticação, calendário e detalhes de eventos, histórico de treinamentos,
NRs, chatbot e chat com o gestor.

Para gerar uma imagem com Java e o renderizador PlantUML:

```sh
java -jar plantuml.jar -charset UTF-8 -tsvg diagrams/fluxo-funcionario.plantuml
```

A renderização usa Graphviz. Nas versões do PlantUML com o motor Smetana,
é possível renderizar sem instalar Graphviz:

```sh
java -jar plantuml.jar -charset UTF-8 -Playout=smetana -tsvg diagrams/fluxo-funcionario.plantuml
```

### Particularidades da conversão

- As barras de sincronização e as atividades paralelas foram mantidas.
- Setas sobrepostas com a mesma origem e destino foram consolidadas.
- Conectores sem vínculo explícito foram associados às atividades ou barras
  nas quais suas extremidades terminam visualmente. Trechos soltos sem
  atividade identificável e o texto avulso `Text` foram omitidos.
- O histórico tem duas atividades com o mesmo rótulo de API no original;
  ambas foram mantidas como atividades distintas.
- O fluxo das NRs também usa o rótulo da API do Histórico no original.
- A conexão da tela do chatbot para a API do Histórico do fluxo das NRs
  foi preservada, pois existe explicitamente no arquivo de origem.
- O encerramento do histórico foi inferido a partir da saída de sua barra
  de sincronização; no original, essa seta termina sem atividade vinculada.
- Os nós finais foram reunidos em um encerramento comum. O layout é
  calculado pelo PlantUML e não reproduz as coordenadas do draw.io.
