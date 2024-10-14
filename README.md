# Modelagem e Transformação de Dados com DAX no Power BI

Este projeto consiste na criação de um **Star Schema** para análise de dados financeiros utilizando a tabela `Financial Sample` como base. As transformações de dados foram realizadas no Power BI, com a utilização de funções DAX para a criação de tabelas de dimensão e colunas calculadas.

## Estrutura do Projeto

### Tabelas Criadas

1. **Tabela de Backup (Oculta)**: `Financials_origem`, usada como base de dados para referência.
2. **Dimensões**:
   - `D_Produtos`: Detalha os produtos, incluindo métricas como a média, mediana e extremos das vendas.
   - `D_Produtos_Detalhes`: Informações detalhadas sobre os produtos, como preço de venda e unidades vendidas.
   - `D_Descontos`: Agrupa dados de desconto e faixas de desconto.
   - `D_Calendário`: Gerada via DAX para fornecer granularidade temporal.
   
3. **Tabela Fato**: `F_Vendas`, que consolida os dados de vendas, lucro, produto, país e segmentação.

### Funções DAX Utilizadas

- **Média de Unidades Vendidas**: `AVERAGE([Units Sold])`
- **Mediana do Valor de Vendas**: `MEDIANX(...)`
- **Valor Máximo e Mínimo de Venda**: `MAXX(...)`, `MINX(...)`
- **Tabela de Calendário**: `CALENDAR()`
- **Coluna Calculada para Índice de Produtos**: Criada com `SWITCH()` para classificar produtos como "Alto", "Médio" ou "Baixo" com base no volume de vendas.

### Diagrama do Star Schema

![Star Schema](./diagrama_star_schema_dax.png)

## Etapas do Projeto

1. Criação de uma tabela de backup oculta (`Financials_origem`) para preservação dos dados originais.
2. Criação de tabelas de dimensão a partir da tabela original, agrupando dados de produtos, descontos e detalhes específicos.
3. Implementação de uma tabela de calendário com granularidade flexível, criada com a função `CALENDAR()`.
4. Construção da tabela fato (`F_Vendas`) consolidando as métricas principais para análise de vendas e desempenho financeiro.
5. Utilização de funções DAX para transformar e calcular novas métricas, como índices de produtos baseados em vendas.

## Conclusão

Este projeto demonstrou como transformar e modelar dados financeiros no Power BI utilizando DAX, criando uma estrutura de Star Schema otimizada para análise. O modelo permite uma análise detalhada do desempenho de vendas e das relações entre produtos, descontos e lucros.

## Licença

Este projeto está licenciado sob a Licença MIT.
