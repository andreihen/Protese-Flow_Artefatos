@startuml

skinparam monochrome true

skinparam shadowing false

title Validação de Anexo

\[\*\] \--\> AguardandoUpload

AguardandoUpload \--\> ValidandoArquivo : Selecionar e Enviar

state validador\_regras \<\<choice\>\>

ValidandoArquivo \--\> validador\_regras : Processar Metadados

' Caminho Feliz (Centro)

validador\_regras \--\> ArquivoAceito : \[Tamanho \< 200MB e Válido\]

' Fluxo de Erro isolado à direita

validador\_regras \-right-\> ArquivoRejeitado : \[Extensão Inválida / \> 200MB\]

ArquivoRejeitado \-up-\> AguardandoUpload : Tentar Novamente

ArquivoAceito \--\> \[\*\]

@enduml

