@startuml

skinparam monochrome true

skinparam shadowing false

autonumber

title Diagrama de Sequência 1: Criação de Novo Pedido

actor "Dentista" as dentista

participant "Frontend\\n(React)" as front

participant "API Backend\\n(Django REST)" as api

database "Base de Dados" as db

dentista \-\> front : Preencher dados e anexar arquivos

activate front

dentista \-\> front : Clicar em "Criar Pedido"

front \-\> front : Validar tamanho (\<200MB)

front \-\> api : POST /api/pedidos (Token JWT, Arquivos)

activate api

api \-\> api : Validar Token e Permissões

api \-\> db : INSERT INTO Pedidos (Estado: PENDENTE)

activate db

db \--\> api : Retorna o ID gerado

deactivate db

api \-\> api : Salvar arquivos no Banco de Dados

api \--\> front : 201 Created (Sucesso)

deactivate api

front \--\> dentista : Exibir mensagem de sucesso

deactivate front

@enduml

