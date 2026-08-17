# RFC-001 — Atualização do MySQL



## Solicitação de Mudança



**RFC:** RFC-001



**IC afetado:** Banco de dados — MySQL



**Versão atual:** MySQL 8.4



**Versão proposta:** MySQL 9.0



## Motivo da mudança



O MySQL 8.4 apresentou problemas de desempenho no ambiente de produção.

A atualização para o MySQL 9.0 é proposta com o objetivo de avaliar e

obter possíveis melhorias de desempenho.



## Riscos



- Incompatibilidade entre o MySQL 9.0 e a aplicação;

- Alterações no comportamento de consultas;

- Incompatibilidade com recursos utilizados atualmente;

- Indisponibilidade temporária do banco;

- Necessidade de rollback caso sejam identificados problemas.



## Impacto na aplicação



A aplicação utiliza o MySQL como banco de dados e pode apresentar erros

caso existam incompatibilidades entre a versão atual e a versão proposta.



## Ambientes afetados



- Desenvolvimento;

- Testes;

- Produção.



A alteração em produção deverá ocorrer somente após aprovação e validação

nos ambientes anteriores.



## Testes necessários



- Testar a conexão da aplicação com o MySQL 9.0;

- Executar consultas utilizadas pelo Sistema de Pedidos;

- Testar criação de pedidos;

- Testar consulta de pedidos;

- Testar atualização de pedidos;

- Testar exclusão de pedidos;

- Verificar logs da aplicação;

- Verificar estabilidade do banco;

- Avaliar possíveis erros de compatibilidade.



## Plano de implementação



1. Realizar backup do banco de dados;

2. Preparar ambiente de testes;

3. Atualizar o MySQL para a versão 9.0 no ambiente de testes;

4. Executar os testes de compatibilidade;

5. Validar o funcionamento da aplicação;

6. Aprovar a implementação em produção;

7. Atualizar o MySQL de 8.4 para 9.0 em produção;

8. Executar os testes de validação;

9. Registrar os resultados da mudança.



## Plano de rollback



Caso sejam identificados problemas:



1. Interromper a implementação;

2. Restaurar o backup realizado antes da mudança;

3. Retornar o banco para MySQL 8.4;

4. Validar o funcionamento da aplicação;

5. Registrar o rollback.



## Responsável



Grupo responsável pelo Sistema de Pedidos.



## Aprovação



**Status:** Aprovada.



A mudança deverá ser implementada somente após a avaliação de impacto e

a execução dos testes necessários
