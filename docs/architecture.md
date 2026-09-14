# Arquitetura - FIAP Cloud Games

## Visão Geral

A FIAP Cloud Games utiliza uma arquitetura baseada em microsserviços, com serviços independentes responsáveis por usuários, catálogo, pagamentos e notificações.

A Fase 3 evolui essa arquitetura com novos componentes voltados a segurança, escalabilidade, observabilidade, performance e redução de custos operacionais.

## Componentes Principais

### UsersAPI

Responsável pelo gerenciamento de usuários, autenticação e emissão/validação de tokens JWT.

Repositório:

https://github.com/PedroPucci/FCG.UsersAPI

### CatalogAPI

Responsável pelo catálogo de jogos.

Utiliza persistência relacional para os dados principais e MongoDB para dados flexíveis e expandidos do catálogo.

Repositório:

https://github.com/PedroPucci/CatalogAPI

### PaymentsAPI

Responsável pelo fluxo relacionado aos pagamentos e compras de jogos.

Repositório:

https://github.com/PedroPucci/PaymentsAPI

### Notifications

O serviço de notificações será evoluído na Fase 3 para uma arquitetura Serverless acionada através do sistema de mensageria.

Repositório atual:

https://github.com/PedroPucci/NotificationsAPI

### FCG.Contracts

Biblioteca responsável pelos contratos compartilhados utilizados na comunicação entre os serviços.

Repositório:

https://github.com/PedroPucci/FCG.Contracts

## Persistência

A plataforma utiliza persistência poliglota.

### SQL Server

Utilizado nos serviços que possuem dados relacionais e regras transacionais.

### MongoDB

Utilizado na CatalogAPI para armazenamento de informações flexíveis relacionadas ao catálogo.

A implementação utiliza:

- MongoDB.Driver
- Repository Pattern
- Dependency Injection
- Índice único por GameId
- Tratamento centralizado de exceções

## Mensageria

A comunicação assíncrona entre componentes utiliza RabbitMQ.

O RabbitMQ é utilizado para publicação e consumo de eventos entre os microsserviços.

## API Gateway

O API Gateway será responsável por fornecer um ponto único de entrada para a plataforma.

Responsabilidades previstas:

- Roteamento de requisições
- Validação de JWT
- Encaminhamento para UsersAPI
- Encaminhamento para CatalogAPI

## Serverless

A NotificationsAPI será migrada para uma função Serverless.

A função será acionada através de mensagens provenientes do sistema de mensageria.

## Observabilidade

A arquitetura contará com uma stack centralizada de observabilidade para acompanhamento de:

- Latência
- Throughput
- Erros
- Logs
- Métricas
- Traces distribuídos

A solução específica será documentada após sua implementação.

## Cache Distribuído

Será adicionada uma camada de cache distribuído para reduzir a latência e a quantidade de acessos aos bancos de dados.

A implementação será documentada após a conclusão desta etapa.

## Kubernetes

O Kubernetes será utilizado para orquestração dos componentes da plataforma.

Os manifests serão mantidos no diretório:

```text
/k8s