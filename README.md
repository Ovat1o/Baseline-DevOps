# Baseline-DevOps

## Configuration Drift

| Situação | Mudança controlada? | Está na baseline? |
|---|---|---|
| Desenvolvedor alterou o código e realiza um novo commit | Sim, quando segue o processo de mudança | Não imediatamente |
| Administrador altera manualmente uma configuração em produção | Não | Não |
| Mudança aprovada e documentada gera a baseline v1.1 | Sim | Sim |


### O que acontece quando há uma alteração manual?

Se alguém alterar manualmente o servidor depois da criação da baseline
v1.1, o estado real do ambiente poderá ficar diferente do estado definido
na baseline. Essa diferença caracteriza um Configuration Drift.

A baseline continuará representando o estado oficialmente aprovado,
enquanto o servidor terá um estado diferente e não controlado.

# Atividade Prática — Baseline

## Gerência de Configuração e Controle de Mudanças

## 1. Objetivo

O objetivo desta atividade é demonstrar o conceito de Baseline dentro da
Gerência de Configuração, relacionando-o ao versionamento, aos Itens de
Configuração, ao controle de mudanças e à identificação de Configuration
Drift.

## 2. Sistema de Pedidos

A configuração inicial aprovada do sistema é:

| Categoria | Configuração |
|---|---|
| Sistema | Sistema de Pedidos — Versão 1.0 |
| Aplicação | Node.js 22; Express 5.1; Porta 3000 |
| Banco de dados | MySQL 8.4; Banco pedidos; Porta 3306 |
| Infraestrutura | Ubuntu Server 24.04; 4 GB RAM; 2 vCPUs |
| Código | Branch main; Commit abc123 |

## 3. Baseline v1.0

A baseline v1.0 representa o estado inicial, estável e aprovado do
Sistema de Pedidos.

Ela contém todos os Itens de Configuração definidos pela equipe técnica,
incluindo aplicação, banco de dados, infraestrutura e código.

O detalhamento da configuração está registrado no arquivo
`BASELINE-v1.0.md`.

## 4. Mudança não autorizada

Após a criação da baseline, o administrador atualizou diretamente o
MySQL de 8.4 para 9.0 em produção.

### 4.1 A baseline foi alterada?

Não. A baseline v1.0 continua representando o estado oficialmente
aprovado anteriormente, no qual o MySQL estava na versão 8.4.

A alteração ocorreu no ambiente real, que passou a apresentar uma
configuração diferente da baseline.

### 4.2 Qual IC foi modificado?

O Item de Configuração modificado foi o banco de dados MySQL.

A alteração foi:

MySQL 8.4 → MySQL 9.0.

### 4.3 A alteração deveria ter sido realizada diretamente em produção?

Não. A mudança deveria ter passado pelo processo formal de gerenciamento
de mudanças antes de ser implementada em produção.

### 4.4 Qual processo deveria ter sido executado?

O fluxo correto seria:

Solicitar → Avaliar impacto → Aprovar/Rejeitar →
Implementar/Testar → Verificar/Encerrar.

### 4.5 O que acontece com a baseline após uma mudança aprovada?

Após uma mudança ser aprovada, implementada e testada com sucesso, uma
nova baseline deve ser criada para registrar o novo estado oficial.

## 5. RFC-001

Foi criada a RFC-001 para formalizar a atualização do MySQL 8.4 para
MySQL 9.0.

A RFC registra o motivo da mudança, riscos, impacto, testes, plano de
implementação, plano de rollback e aprovação.

O documento está disponível em `RFC-001-mysql.md`.

## 6. Implementação e testes

Considerando o cenário proposto pela atividade, a mudança foi aprovada,
implementada e testada com sucesso.

O MySQL passou de:

MySQL 8.4 → MySQL 9.0.

## 7. Baseline v1.1

Após a aprovação, implementação e validação da mudança, foi criada a
baseline v1.1.

A nova baseline mantém todas as configurações anteriores, com exceção
da versão do MySQL, que passou a ser 9.0.

O detalhamento está disponível em `BASELINE-v1.1.md`.

## 8. Configuration Drift

| Situação | Mudança controlada? | Está na baseline? |
|---|---|---|
| Desenvolvedor altera o código e realiza um novo commit | Sim, quando segue o processo de mudança | Não imediatamente |
| Administrador altera manualmente uma configuração em produção | Não | Não |
| Mudança aprovada e documentada gera a baseline v1.1 | Sim | Sim |

Se alguém alterar manualmente o servidor depois da baseline v1.1, o estado
real do ambiente poderá ficar diferente do estado definido na baseline.
Essa diferença caracteriza Configuration Drift.

## 9. Histórico da configuração

v1.0 → Baseline inicial aprovada

RFC-001 → Solicitação formal de mudança

MySQL 8.4 → 9.0 → Implementação da mudança

Testes → Validação da alteração

Aprovação → Aceite da mudança

v1.1 → Nova baseline aprovada

## 10. Pergunta final

A baseline é importante porque define o estado oficial e aprovado de um
sistema, servindo como referência para a equipe DevOps. Ela facilita o
controle, a rastreabilidade e a identificação de alterações. Sem esse
controle, mudanças podem causar incompatibilidades, falhas e diferenças
entre o ambiente real e o estado esperado.
