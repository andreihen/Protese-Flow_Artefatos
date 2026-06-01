@startuml

skinparam monochrome true

skinparam shadowing false

autonumber

title Diagrama de Sequência 3: Avaliação de Anatomia

actor "Dentista" as dentista

participant "Frontend\\n(React)" as front

participant "API Backend\\n(Django REST)" as api

database "Base de Dados" as db

dentista \-\> front : Solicitar download do arquivo

activate front

front \-\> api : GET /api/pedidos/{id}/download

activate api

api \--\> front : Retorna Arquivo

deactivate api

front \--\> dentista : Arquivo transferido para o computador

deactivate front

dentista \-\> dentista : Avaliar arquivos enviados

alt Design Aprovado

    dentista \-\> front : Clicar em "Aprovar Design"

    activate front

    front \-\> api : POST /api/pedidos/{id}/aprovar

    activate api

    api \-\> db : UPDATE estado='FINALIZADO'

    activate db

    db \--\> api : OK

    deactivate db

    api \--\> front : 200 OK

    deactivate api

    front \--\> dentista : Exibe "Pedido Concluído"

    deactivate front

else Solicitar Ajuste (Reprovado)

    dentista \-\> front : Inserir Justificativa e clicar "Solicitar Ajuste"

    activate front

    front \-\> api : POST /api/pedidos/{id}/rejeitar (justificativa)

    activate api

    api \-\> db : UPDATE estado='RETRABALHO CADISTA'

    activate db

    db \--\> api : OK

    deactivate db

    api \--\> front : 200 OK

    deactivate api

    front \--\> dentista : Exibe "Ajuste Solicitado ao Operador"

    deactivate front

end

@enduml

