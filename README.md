# T&D_Json

Pipeline PySpark para ingestão, tratamento e análise de dados de nascimentos via API Health Data NY.

## Descrição

Este repositório contém um notebook PySpark que:
Faz download de um JSON público da API Health Data NY com registros de nascimentos.
Explode estruturas aninhadas usando posexplode para transformar listas em linhas.
Realiza pivot das posições de array em colunas tabulares.
Renomeia colunas conforme o metadado da API e converte tipos (inteiro, data, string).
Gera visualizações com matplotlib:
  - Distribuição de nascimentos por sexo.
  - Evolução de nascimentos ao longo dos anos.
    
Cria uma temporary view para consultas via Spark SQL.

## Estrutura do Pipeline

1. Aquisição de Dados: Requisição HTTP e parse do JSON.
2. Extração de Metadado: Mapeamento de índices para nomes de colunas.
3. Construção do DataFrame:
     - Criação de DataFrame inicial com o JSON bruto.
     - posexplode duplo para encontrar as colunas.
     - Pivot das colunas.
4. Limpeza e Conversão:
     - Cast de tipos (datas → DateType).
     - Drop de colunas auxiliares.

5. Seleção Final:
     - Escolha de colunas essenciais.

6. Visualizações: Gráficos de barras e linhas.
