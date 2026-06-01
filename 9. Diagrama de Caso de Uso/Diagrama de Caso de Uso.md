@startuml

left to right direction

skinparam packageStyle rectangle

skinparam monochrome true

skinparam shadowing false

actor "Dentista" as dentista

actor "Gestor" as gestor

actor "Cadista" as cadista

rectangle "Sistema Protese Flow" {


  usecase "UC01 \- Realizar Login" as UC01

  usecase "UC02 \- Visualizar Dashboard" as UC02

  usecase "UC03 \- Gerenciar Perfil/Senha" as UC03

  usecase "UC09 \- Visualizar Detalhes do Pedido" as UC09


  usecase "UC07 \- Criar Novo Pedido" as UC07

  usecase "UC08 \- Editar Pedido" as UC08

  usecase "UC10 \- Aprovar Pedido" as UC10

  usecase "UC11 \- Solicitar Ajuste" as UC11

  usecase "UC04 \- Gerir Usuários" as UC04

  usecase "UC05 \- Acessar Lixeira de Usuários" as UC05

  usecase "UC06 \- Atribuir Pedido" as UC06

  usecase "UC12 \- Iniciar Produção" as UC12

  usecase "UC13 \- Retrabalho" as UC13

  usecase "UC14 \- Entregar Arquivos Finais" as UC14

}

dentista \--\> UC01

dentista \--\> UC02

dentista \--\> UC03

dentista \--\> UC07

dentista \--\> UC08

dentista \--\> UC09

dentista \--\> UC10

dentista \--\> UC11

gestor \--\> UC01

gestor \--\> UC02

gestor \--\> UC03

gestor \--\> UC04

gestor \--\> UC05

gestor \--\> UC06

gestor \--\> UC09

UC01 \<-- cadista

UC02 \<-- cadista

UC03 \<-- cadista

UC09 \<-- cadista

UC12 \<-- cadista

UC13 \<-- cadista

UC14 \<-- cadista

@enduml