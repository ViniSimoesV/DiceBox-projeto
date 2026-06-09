@startuml

left to right direction



' --- CONFIGURAÇÕES VISUAIS ---

skinparam shadowing false

skinparam defaultFontName "Segoe UI"

skinparam defaultFontSize 14



' Estilo do Sistema

skinparam rectangle {

&#x20;   BackgroundColor White

&#x20;   BorderColor Black

&#x20;   BorderThickness 1.5

&#x20;   FontColor Black

&#x20;   FontStyle bold

}



' Estilo dos Atores

skinparam actor {

&#x20;   BackgroundColor White

&#x20;   BorderColor Black

&#x20;   FontColor Black

}



' Estilo dos Casos de Uso

skinparam usecase {

&#x20;   BackgroundColor WhiteSmoke

&#x20;   BorderColor Black

&#x20;   BorderThickness 1

&#x20;   ArrowColor DimGray

&#x20;   FontColor Black

}



' Estilo das Setas

skinparam arrow {

&#x20;   Color Black

&#x20;   Thickness 1

&#x20;   FontColor Black

&#x20;   FontSize 12

}

' ---------------------------------------------------



' Atores e Herança

actor "Usuário" as usuario

actor "Cliente" as cliente

actor "Vendedor" as vendedor

actor "API de Pagamento" as api <<Sistema Externo>>



usuario <|-- cliente

usuario <|-- vendedor



rectangle "DiceBox" {

&#x20;   

&#x20;   ' Casos de Uso - Cliente

&#x20;   usecase "Gerenciar Conta de Cliente" as UC01

&#x20;   usecase "Navegar pelo Catálogo de Jogos" as UC02

&#x20;   usecase "Gerenciar Carrinho de Compras" as UC03

&#x20;   usecase "Realizar Pedido" as UC04

&#x20;   usecase "Realizar Pagamento" as UC05

&#x20;   usecase "Acompanhar Pedido" as UC06

&#x20;   usecase "Avaliar Compra" as UC07



&#x20;   ' Casos de Uso - Vendedor

&#x20;   usecase "Gerenciar Conta de Vendedor" as UC08

&#x20;   usecase "Gerenciar Produtos à Venda" as UC09

&#x20;   usecase "Gerenciar Pedidos" as UC10

&#x20;   usecase "Controlar Estoque" as UC11

&#x20;   usecase "Realizar Envio" as UC12

&#x20;   usecase "Notificar Status" as UC13



&#x20;   ' Relacionamentos do Cliente (Lado Esquerdo)

&#x20;   cliente -- UC01

&#x20;   cliente -- UC02

&#x20;   cliente -- UC03

&#x20;   cliente -- UC04

&#x20;   cliente -- UC06

&#x20;   

&#x20;   ' Relacionamentos do Vendedor (Lado Esquerdo)

&#x20;   vendedor -- UC08

&#x20;   vendedor -- UC09

&#x20;   vendedor -- UC10



&#x20;   ' Includes e Extends 

&#x20;   UC04 ..> UC05 : <<include>>

&#x20;   UC06 <.. UC07 : <<extend>>

&#x20;   UC09 <.. UC11 : <<extend>>

&#x20;   UC10 <.. UC12 : <<extend>>

&#x20;   UC10 <.. UC13 : <<extend>>



&#x20;   ' API Externa

&#x20;   UC05 -- api

}

@enduml

