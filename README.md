# astro-eqs-diagrams

Diagramas do projeto Astro em PlantUML.

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
