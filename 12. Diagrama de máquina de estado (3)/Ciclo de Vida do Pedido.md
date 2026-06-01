@startuml

skinparam monochrome true

skinparam shadowing false

title Ciclo de Vida do Pedido

\[\*\] \--\> Pendente : Criar Pedido

' Retrabalho do Doutor isolado à direita

Pendente \-right-\> RetrabalhoDoutor : Retrabalho

RetrabalhoDoutor \-left-\> Pendente : Atualizar Pedido

' Caminho Ideal

Pendente \--\> EmProducao : Iniciar Produção

EmProducao \--\> AguardandoAprovacao : Entregar Arquivo

state condicao\_aprovacao \<\<choice\>\>

AguardandoAprovacao \--\> condicao\_aprovacao : Avaliar Design

' Aprovação (Continua para baixo)

condicao\_aprovacao \--\> Finalizado : \[Design Aprovado\]

' Retrabalho do Cadista isolado à esquerda

condicao\_aprovacao \-left-\> RetrabalhoCadista : \[Solicitar Ajuste\]

RetrabalhoCadista \--\> EmProducao : Retomar Produção

Finalizado \--\> \[\*\]

@enduml

