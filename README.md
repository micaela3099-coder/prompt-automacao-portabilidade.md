# Prompt para criação de automação no n8n — Portabilidade Oracle

Atue como um especialista em automação de processos com n8n, Oracle Database, SQL e operações de sistemas em produção.

## Objetivo

Planeje uma automação no n8n para identificar tickets relacionados à portabilidade no Oracle, validar quais registros atendem às regras de negócio e atualizar automaticamente o campo `flag_temp` de `false` para `true` nos registros elegíveis.

## Público-alvo

Equipe de operações e sustentação de sistemas, responsável pelo acompanhamento e pela manutenção dos processos de portabilidade.

## Ferramentas envolvidas

- n8n para orquestração do workflow.
- Oracle Database para consulta e atualização dos registros.
- SQL para aplicação dos filtros e regras de negócio.
- Arquivo de log para auditoria e acompanhamento das execuções.

## Fluxo desejado

1. Iniciar o workflow manualmente ou por agendamento.
2. Consultar o Oracle para identificar os registros de portabilidade que atendam aos critérios definidos.
3. Verificar se existem registros elegíveis para processamento.
4. Caso não existam registros, registrar a execução sem realizar atualizações.
5. Caso existam registros, validar as condições de negócio e preparar a atualização.
6. Atualizar o campo `flag_temp` de `false` para `true` somente nos registros elegíveis.
7. Confirmar a quantidade de registros efetivamente atualizados.
8. Registrar data, hora, resultado da execução, quantidade de registros processados e eventuais erros.
9. Encerrar o workflow com um resultado que permita identificar sucesso, ausência de registros ou falha.

## Regras e restrições

- Respeitar integralmente os filtros definidos na consulta SQL.
- Atualizar somente registros que ainda atendam à condição `flag_temp = 'false'`, considerando o tipo real da coluna no Oracle.
- Não realizar atualizações quando não houver registros elegíveis.
- Evitar atualizações duplicadas e considerar possíveis execuções simultâneas.
- Utilizar credenciais seguras e permissões mínimas necessárias.
- Tratar erros de conexão, consulta e atualização.
- Considerar transações e rollback quando aplicável.
- Registrar os resultados para facilitar auditoria e troubleshooting.
- Não expor credenciais nem informações sensíveis nos logs.
- Não presumir nomes de tabelas, colunas ou relacionamentos que não tenham sido confirmados.

## O que a IA deve entregar

1. Uma proposta de arquitetura do workflow.
2. A sequência dos nós do n8n, explicando a função de cada um.
3. A lógica de decisão para os cenários com registros, sem registros e com erros.
4. Exemplos de consultas SQL de seleção e atualização, identificando claramente os campos que precisam ser adaptados ao esquema real.
5. Estratégias para evitar atualizações indevidas e permitir reexecuções seguras.
6. Uma proposta de tratamento de erros e registro de logs.
7. Um plano de testes com dados fictícios, incluindo cenários de sucesso, ausência de registros, falha de conexão e erro de atualização.
8. Recomendações para implantação segura em ambiente de produção.

## Formato da resposta

Apresente a solução em etapas, com um diagrama textual do fluxo, uma tabela dos nós do n8n, exemplos de SQL e explicações claras sobre as decisões tomadas.

Diferencie os exemplos ilustrativos das configurações que precisam ser confirmadas no ambiente real.

Não execute nem recomende atualizações em produção sem validação prévia das regras, dos filtros e dos registros que serão afetados.
