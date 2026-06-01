@startuml

skinparam monochrome true

skinparam shadowing false

autonumber

title Diagrama de Sequência 2: Atribuição de Pedido

actor "Gestor" as gestor

participant "Frontend\\n(React)" as front

participant "API Backend\\n(Django REST)" as api

database "Base de Dados" as db

gestor \-\> front : Selecionar Pedido "PENDENTE"

activate front

gestor \-\> front : Escolher Cadista e clicar em "Atribuir"

front \-\> api : PUT /api/pedidos/{id}/atribuir (id\_cadista)

activate api

api \-\> api : Validar permissão de Gestor (Admin)

api \-\> db : UPDATE Pedidos SET cadista\_id, estado='EM PRODUCAO'

activate db

db \--\> api : Confirmação de Update

deactivate db

api \--\> front : 200 OK (Atualizado com sucesso)

deactivate api

front \--\> gestor : Atualizar Kanban e exibir alerta

deactivate front

@enduml

