@startuml

skinparam monochrome true

skinparam shadowing false

title Autenticação JWT

\[\*\] \--\> Deslogado

Deslogado \--\> ValidandoCredenciais : Inserir E-mail e Palavra-passe

state condicao\_auth \<\<choice\>\>

ValidandoCredenciais \--\> condicao\_auth : Verificar Base de Dados

' Caminho Feliz (Centro)

condicao\_auth \--\> Autenticado : \[Credenciais Corretas\]

' Falha de login (Foge para a esquerda e sobe)

condicao\_auth \-left-\> Deslogado : \[Falha na Autenticação\]

' Logout (Sobe direto pela direita)

Autenticado \-right-\> Deslogado : Fazer Logout / Token Expirado

@enduml

