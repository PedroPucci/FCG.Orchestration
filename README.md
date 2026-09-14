# FIAP Cloud Games - Orchestration

Repositório central de orquestração, infraestrutura e documentação da **FIAP Cloud Games (FCG)**.

Este repositório concentra as configurações necessárias para execução integrada dos microsserviços e os componentes de infraestrutura introduzidos na Fase 3 do Tech Challenge.

## Arquitetura

A FCG utiliza uma arquitetura baseada em microsserviços, com responsabilidades separadas entre os serviços de usuários, catálogo, pagamentos e notificações.

### Microsserviços

| Serviço | Responsabilidade |
|---|---|
| UsersAPI | Gerenciamento de usuários e autenticação |
| CatalogAPI | Gerenciamento do catálogo de jogos |
| PaymentsAPI | Processamento do fluxo de pagamentos |
| Notifications | Processamento de notificações |
| FCG.Contracts | Contratos compartilhados entre os serviços |

## Repositórios

- UsersAPI: https://github.com/PedroPucci/FCG.UsersAPI
- CatalogAPI: https://github.com/PedroPucci/CatalogAPI
- PaymentsAPI: https://github.com/PedroPucci/PaymentsAPI
- NotificationsAPI: https://github.com/PedroPucci/NotificationsAPI
- FCG.Contracts: https://github.com/PedroPucci/FCG.Contracts

## Fase 3

A Fase 3 evolui a arquitetura da FCG com foco em segurança, escalabilidade, observabilidade, performance e otimização de recursos.

A arquitetura será composta pelos seguintes componentes:

- API Gateway
- Kubernetes
- Serverless
- Observabilidade
- Persistência Poliglota
- Cache Distribuído
- Mensageria

## Persistência Poliglota

### MongoDB - CatalogAPI

A CatalogAPI utiliza MongoDB para armazenar informações flexíveis e expandidas relacionadas ao catálogo de jogos.

A implementação utiliza:

- MongoDB
- MongoDB.Driver
- Docker
- ASP.NET Core
- Repository Pattern
- Dependency Injection

A camada de Application define a abstração de persistência através de `IGameCatalogRepository`, enquanto a implementação concreta utilizando MongoDB permanece na camada Infrastructure.

O MongoDB utiliza um índice único para `GameId`, evitando a criação de múltiplos documentos de catálogo para o mesmo jogo.

A API também possui tratamento centralizado de exceções para cenários como tentativa de cadastro duplicado.

## API Gateway

> Em desenvolvimento.

O API Gateway será utilizado como ponto único de entrada para os serviços da plataforma, sendo responsável pelo roteamento das requisições e validação de autenticação.

## Serverless Notifications

> Pendente.

A arquitetura de notificações será migrada para uma solução Serverless acionada através do sistema de mensageria.

## Observabilidade

> Pendente.

A solução de observabilidade será documentada nesta seção após a implementação da stack escolhida.

## Cache Distribuído

> Pendente.

Será implementada uma camada de cache distribuído para reduzir latência e diminuir consultas desnecessárias aos bancos de dados.

## Kubernetes

> Em desenvolvimento.

Os manifests Kubernetes necessários para execução dos componentes da plataforma serão mantidos neste repositório.

## Estrutura do Repositório

```text
FCG.Orchestration/
├── docker/
├── docs/
├── gateway/
├── k8s/
├── monitoring/
├── .gitignore
├── FCG.Orchestration.slnx
└── README.md
```

### Diretórios

- `docker/` - configurações relacionadas à execução dos containers.
- `docs/` - documentação da arquitetura.
- `gateway/` - configurações do API Gateway.
- `k8s/` - manifests Kubernetes.
- `monitoring/` - configurações da stack de observabilidade.

## Status

| Componente | Status |
|---|---|
| Microsserviços | Concluído |
| MongoDB - CatalogAPI | Concluído |
| Tratamento de erros MongoDB | Concluído |
| API Gateway | Em desenvolvimento |
| Serverless Notifications | Pendente |
| Observabilidade | Pendente |
| Cache Distribuído | Pendente |
| Kubernetes / Orquestração | Em desenvolvimento |

## Execução do Ambiente

As instruções completas para execução da plataforma serão adicionadas conforme os componentes de infraestrutura da Fase 3 forem implementados.

## Tech Challenge

Projeto desenvolvido como parte da Pós-Graduação em Arquitetura de Sistemas .NET da FIAP.
