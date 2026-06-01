@startuml

skinparam monochrome true

skinparam shadowing false

hide circle

title Diagrama de Classes UML: Protese Flow

' \==========================================

' SUPERCLASSE

' \==========================================

abstract class Usuario {

  \- id : Int

  \- nome : String

  \- email : String

  \- senhaHash : String

  \- isAtivo : Boolean

  \+ login() : Boolean

  \+ alterarSenha(novaSenha : String) : void

  \+ atualizarPerfil() : void

}

' \==========================================

' SUBCLASSES (HERANÇA)

' \==========================================

class Dentista {

  \- cro : String

  \- nomeClinica : String

  \+ criarPedido(dados : Pedido) : Pedido

  \+ aprovarDesign(idPedido : Int) : void

  \+ solicitarAjuste(idPedido : Int, motivo : String) : void

}

class Cadista {

  \- especialidade : String

  \+ iniciarProducao(idPedido : Int) : void

  \+ entregarServico(idPedido : Int, arquivo : Anexo) : void

  \+ devolverFaltaInfo(idPedido : Int, motivo : String) : void

}

class Gestor {

  \- nivelAcesso : Int

  \+ atribuirPedido(idPedido : Int, idCadista : Int) : void

  \+ gerirUsuarios() : void

}

' \==========================================

' CLASSES DE DOMÍNIO (NEGÓCIO)

' \==========================================

class Pedido {

  \- id : Int

  \- nomePaciente : String

  \- descricao : String

  \- estado : String

  \- dataCriacao : Date

  \+ atualizarEstado(novoEstado : String) : void

  \+ obterDetalhes() : String

}

class Anexo {

  \- id : Int

  \- nomeArquivo : String

  \- tamanhoMB : Float

  \- tipoExtensao : String

  \- caminhoStorage : String

  \+ validarTamanho() : Boolean

  \+ fazerUpload() : void

}

' \==========================================

' RELACIONAMENTOS UML (Bóson Treinamentos)

' \==========================================

' Herança (Generalização: Seta com triângulo vazio)

Usuario \<|-- Dentista

Usuario \<|-- Cadista

Usuario \<|-- Gestor

' Associação (Linha contínua com navegabilidade)

Dentista "1" \-- "0..\*" Pedido : solicita \>

Cadista "1" \-- "0..\*" Pedido : produz \>

Gestor "1" \-- "0..\*" Pedido : gerencia \>

' Composição (Losango preenchido: O Anexo pertence exclusivamente ao Pedido)

Pedido "1" \*-- "1..\*" Anexo : contém \>

@enduml

