# 🧬 Diagrama de Classes

Renderizado automaticamente pelo GitHub (Mermaid).

```mermaid
classDiagram
direction TB

class Usuario {
  +ObjectId id
  +String email
  +String senhaHash
  +Perfil perfil
  +autenticar(senha) bool
}

class Proprietario {
  <<interface>>
}

class Cliente {
  +ObjectId id
  +String nome
  +String cpf
  +String rg
  +String endereco
  +String profissao
  +adicionarVinculo(v) void
  +removerVinculo(v) void
}

class VinculoEmpregaticio {
  +String entidadeEmpregadora
  +Decimal rendimento
}

class Agente {
  +ObjectId id
  +String nome
  +String cnpj
  +String endereco
  +TipoAgente tipo
  +avaliar(pedido, parecer, obs) AvaliacaoFinanceira
}

class Automovel {
  +ObjectId id
  +String marca
  +String modelo
  +int ano
  +String placa
  +String matricula
  +TipoProprietario tipoProprietario
  +ObjectId proprietarioId
}

class PedidoAluguel {
  +ObjectId id
  +Date dataCriacao
  +Date dataInicio
  +Date dataFim
  +StatusPedido status
  +cancelar() void
  +atualizarStatus(novo) void
}

class AvaliacaoFinanceira {
  +ObjectId id
  +Date dataAnalise
  +Parecer parecer
  +String observacao
}

class ContratoCredito {
  +ObjectId id
  +Decimal valorFinanciado
  +int prazoMeses
  +SituacaoCredito situacao
}

class Perfil {
  <<enumeration>>
  CLIENTE
  AGENTE
}
class TipoAgente {
  <<enumeration>>
  EMPRESA
  BANCO
}
class TipoProprietario {
  <<enumeration>>
  CLIENTE
  EMPRESA
  BANCO
}
class StatusPedido {
  <<enumeration>>
  EM_ANALISE
  APROVADO
  REPROVADO
  CANCELADO
  CONTRATO_EM_EXECUCAO
}
class Parecer {
  <<enumeration>>
  APROVADO
  REPROVADO
}
class SituacaoCredito {
  <<enumeration>>
  SOLICITADO
  ATIVO
  QUITADO
  CANCELADO
}

Usuario "1" --> "1" Perfil
Usuario "1" -- "0..1" Cliente : identifica
Usuario "1" -- "0..1" Agente : identifica
Cliente ..|> Proprietario
Agente ..|> Proprietario
Cliente "1" *-- "0..3" VinculoEmpregaticio : possui
Agente "1" --> "1" TipoAgente
Automovel "*" --> "1" Proprietario : pertence a
Automovel --> TipoProprietario
Cliente "1" -- "*" PedidoAluguel : solicita
Automovel "1" -- "*" PedidoAluguel : alugado em
Agente "0..1" -- "*" PedidoAluguel : responsável
PedidoAluguel --> StatusPedido
PedidoAluguel "1" -- "0..1" AvaliacaoFinanceira : recebe
Agente "1" -- "*" AvaliacaoFinanceira : realiza
AvaliacaoFinanceira --> Parecer
PedidoAluguel "1" -- "0..1" ContratoCredito : financiado por
Agente "1" -- "*" ContratoCredito : concede (tipo BANCO)
ContratoCredito --> SituacaoCredito
```

## Regras de negócio refletidas no modelo

| Regra | Onde é garantida |
|-------|------------------|
| Máx. 3 vínculos por cliente | Multiplicidade `0..3` + validação no model/service |
| Contrato de crédito só por agente tipo Banco | Restrição `{agente.tipo = BANCO}` validada no service |
| Automóvel sempre com proprietário | Multiplicidade `1` em `Automovel → Proprietario` |
| Só agente avalia; avaliação registra o agente | `AvaliacaoFinanceira` obrigatoriamente ligada a `Agente`; rota protegida por perfil |
| Cliente só mexe nos próprios pedidos | Verificação `pedido.cliente == usuarioLogado` no controller/service |
| Pedido cancelado não é aprovado nem executado | Máquina de estados abaixo |

## Máquina de estados do pedido

```mermaid
stateDiagram-v2
  [*] --> EM_ANALISE : cliente cria pedido
  EM_ANALISE --> APROVADO : agente aprova
  EM_ANALISE --> REPROVADO : agente reprova
  EM_ANALISE --> CANCELADO : cliente cancela
  APROVADO --> CONTRATO_EM_EXECUCAO : agente confirma
  APROVADO --> CANCELADO : cliente cancela
  REPROVADO --> [*]
  CANCELADO --> [*]
  CONTRATO_EM_EXECUCAO --> [*]
```