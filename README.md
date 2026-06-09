<div align="center">
  <h1>🎲 DiceBox 📦</h1>
</div>

> [!NOTE]
> Um sistema de e-commerce e gerenciamento focado em jogos de tabuleiro, cartas e mídias físicas. O projeto conecta clientes a vendedores de forma escalável e resiliente, utilizando uma arquitetura distribuída moderna com microsserviços.

---

## 🚧 Status do Projeto

[![Versão](https://img.shields.io/badge/Versão-v1.0-blue?style=for-the-badge)](#) ![Java](https://img.shields.io/badge/Java-17-007ec6?style=for-the-badge&logo=openjdk&logoColor=white) ![Spring Boot/Micronaut](https://img.shields.io/badge/Framework-Spring_Boot_/_Micronaut-007ec6?style=for-the-badge) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-16-007ec6?style=for-the-badge&logo=postgresql&logoColor=white) ![RabbitMQ](https://img.shields.io/badge/RabbitMQ-AMQP-007ec6?style=for-the-badge&logo=rabbitmq&logoColor=white) ![Docker](https://img.shields.io/badge/Docker-Container-007ec6?style=for-the-badge&logo=docker&logoColor=white) ![AWS](https://img.shields.io/badge/AWS-Cloud-007ec6?style=for-the-badge&logo=amazonwebservices&logoColor=white)

---

## 📚 Índice
- [Sobre o Projeto](#-sobre-o-projeto)
- [Funcionalidades Principais](#-funcionalidades-principais)
- [Tecnologias Utilizadas](#-tecnologias-utilizadas)
- [Arquitetura e Diagramas](#-arquitetura-e-diagramas)
  - [Modelos de Sistema e Domínio](#modelos-de-sistema-e-domínio)
  - [Diagramas de Sequência](#diagramas-de-sequência)
- [Instalação e Execução](#-instalação-e-execução)
- [Modelagem de Dados](#-modelagem-de-dados)
- [Autores](#-autores)

---

## 📝 Sobre o Projeto
O **DiceBox** é um sistema desenvolvido como parte da disciplina de Projeto de Software. O propósito central da aplicação é fornecer uma plataforma robusta onde clientes possam explorar um catálogo diversificado de jogos (tabuleiros, cartas e CDs) e vendedores possam gerenciar suas vendas e estoques de maneira eficiente.

O sistema foi arquitetado visando **escalabilidade e alta disponibilidade**. Para suportar picos de vendas e garantir que falhas em serviços externos (como APIs de pagamento) não derrubem a aplicação, adotou-se uma infraestrutura baseada em contêineres e comunicação assíncrona.

---

## ✨ Funcionalidades Principais

As operações do sistema foram mapeadas em casos de uso direcionados a dois atores principais:

### 🛒 Fluxo do Cliente
- **Gestão e Navegação:** O cliente pode gerenciar sua conta, navegar pelo catálogo de jogos e visualizar detalhes específicos dos produtos.
- **Compras:** O sistema permite gerenciar o carrinho de compras, fechar pedidos e realizar pagamentos processados via API externa.
- **Pós-venda:** É possível acompanhar o status do pedido de forma atualizada e, após o recebimento, avaliar a compra.

### 📦 Fluxo do Vendedor
- **Catálogo e Estoque:** O vendedor pode cadastrar novos produtos à venda e controlar rigidamente as quantidades em estoque.
- **Gestão de Pedidos:** Acompanhamento de pedidos pendentes, execução das rotinas de envio (informando o código de rastreio) e notificação automática de status para o cliente.

---

## 🛠 Tecnologias Utilizadas

A base tecnológica do DiceBox foi selecionada para sustentar uma operação distribuída de alto desempenho na nuvem.

### 🖥️ Back-end & Infraestrutura
* **Linguagem:** Java.
* **Frameworks:** Micronaut ou Spring Boot (visando inicialização rápida de microsserviços).
* **Banco de Dados Relacional:** PostgreSQL, com instâncias dedicadas para cada microsserviço.
* **Mapeamento Objeto-Relacional (ORM):** JPA/Hibernate.
* **Mensageria:** RabbitMQ (via Amazon MQ) para filas de comunicação assíncrona.
* **Infraestrutura e Deploy:** Contêineres Docker hospedados em um cluster na Nuvem AWS (ECS/EKS e Amazon RDS).
* **Notificações:** Integração com Amazon SNS para disparos de mensagens via PUSH e SMS.

---

## 🏗 Arquitetura e Diagramas

O sistema adota os seguintes padrões arquiteturais e de projeto:
- **Microsserviços Isolados:** A plataforma foi desmembrada em serviços independentes de *Catálogo e Inventário*, *Pedidos*, *Pagamento* e *Notificação*. 
- **Comunicação Assíncrona e Event-Driven:** O acoplamento entre os serviços é minimizado pelo uso do RabbitMQ. 
- **Arquitetura Hexagonal (Ports and Adapters):** O núcleo de regras de negócios está completamente isolado de tecnologias externas.
- **Design Pattern Facade:** Utilizado primariamente na finalização de compras, simplificando as chamadas para o cliente.

Abaixo estão as representações visuais da arquitetura e fluxos do sistema:

### Modelos de Sistema e Domínio

| Casos de Uso | Diagrama de Classes |
| :---: | :---: |
| <img src="./Diagramas/US.png" alt="Diagrama de Casos de Uso" width="100%"> | <img src="./Diagramas/Classes.png" alt="Diagrama de Classes" width="100%"> |

| Componentes | Implantação |
| :---: | :---: |
| <img src="./Diagramas/Componentes.png" alt="Diagrama de Componentes" width="100%"> | <img src="./Diagramas/Implantacao.png" alt="Diagrama de Implantação" width="100%"> |

| Entidade-Relacionamento (DER) | Máquina de Estados |
| :---: | :---: |
| <img src="./Diagramas/DER.png" alt="Diagrama DER" width="100%"> | <img src="./Diagramas/Estado.png" alt="Diagrama de Estados" width="100%"> |

| Comunicação |
| :---: |
| <img src="./Diagramas/Comunicacao.png" alt="Diagrama de Comunicação" width="100%"> |

### Diagramas de Sequência

Abaixo estão detalhados os fluxos de interação e sequência das operações principais:

| Sequência Geral | Gestão de Usuário |
| :---: | :---: |
| <img src="./Diagramas/sequenciaGeral.png" alt="Diagrama de Sequência Geral" width="100%"> | <img src="./Diagramas/usuario.png" alt="Sequência - Usuário" width="100%"> |

| Catálogo e Compra | Carrinho de Compras |
| :---: | :---: |
| <img src="./Diagramas/catalagoCompra.png" alt="Sequência - Catálogo" width="100%"> | <img src="./Diagramas/carrinho.png" alt="Sequência - Carrinho" width="100%"> |

| Realizar Pedido | Acompanhar Pedido |
| :---: | :---: |
| <img src="./Diagramas/realizarPedido.png" alt="Sequência - Realizar Pedido" width="100%"> | <img src="./Diagramas/acompanharPedido.png" alt="Sequência - Acompanhar Pedido" width="100%"> |

| Gerenciar Estoque | Gerenciar Pedido (Vendedor) |
| :---: | :---: |
| <img src="./Diagramas/gerenciarEstoque.png" alt="Sequência - Gerenciar Estoque" width="100%"> | <img src="./Diagramas/gerenciarPedido.png" alt="Sequência - Gerenciar Pedido" width="100%"> |

---

## 🔧 Instalação e Execução

### Pré-requisitos
* **Java JDK 17+**
* **Docker e Docker Compose** (Para rodar o PostgreSQL e o RabbitMQ localmente)
* **Maven ou Gradle** (Dependendo do framework escolhido)

### Execução via Docker Compose
Na raiz do projeto, suba a infraestrutura de bancos de dados e mensageria:

```bash
docker-compose up -d
