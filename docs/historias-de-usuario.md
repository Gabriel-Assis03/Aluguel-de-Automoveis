# 📖 Histórias de Usuário

Formato: **Como** `<perfil>`, **quero** `<ação>`, **para** `<benefício>`. Prioridade pelo método MoSCoW (M = Must, S = Should, C = Could).

## Épico 1 — Acesso e cadastro

| ID | História | Critérios de aceitação | Prior. |
|----|----------|------------------------|--------|
| US01 | Como **cliente**, quero me cadastrar informando meus dados pessoais, para poder usar o sistema. | Campos obrigatórios: nome, CPF, RG, endereço, profissão, e-mail e senha. CPF e e-mail únicos. Senha armazenada com hash. | M |
| US02 | Como **cliente** ou **agente**, quero fazer login, para acessar as funcionalidades do meu perfil. | Sem cadastro prévio não há acesso. Após login, o sistema libera apenas as rotas do perfil. | M |
| US03 | Como **usuário**, quero encerrar minha sessão, para proteger meus dados. | Token invalidado/descartado no cliente. | S |

## Épico 2 — Perfil Cliente

| ID | História | Critérios de aceitação | Prior. |
|----|----------|------------------------|--------|
| US04 | Como **cliente**, quero consultar e editar meus dados, para mantê-los atualizados. | Cliente só acessa os próprios dados. | M |
| US05 | Como **cliente**, quero excluir meu cadastro, para deixar de usar o sistema. | Confirmação antes de excluir; pedidos em execução bloqueiam a exclusão. | M |
| US06 | Como **cliente**, quero informar até três entidades empregadoras com seus rendimentos, para que o agente analise minha capacidade financeira. | Máximo 3 vínculos; o 4º é rejeitado com mensagem clara. Cada vínculo tem entidade e rendimento. | M |
| US07 | Como **cliente**, quero cadastrar, consultar, editar e excluir automóveis de minha propriedade, para utilizá-los em pedidos. | Dados: marca, modelo, ano, placa, matrícula e proprietário (cliente). Placa única. | M |
| US08 | Como **cliente**, quero criar um pedido de aluguel escolhendo automóvel e período, para solicitar a análise. | Data de criação automática; status inicial **Em análise**; período com início < fim. | M |
| US09 | Como **cliente**, quero consultar meus pedidos e o status atualizado, para acompanhar o andamento. | Lista apenas pedidos próprios; exibe status, período, automóvel e avaliação (se houver). | M |
| US10 | Como **cliente**, quero consultar o histórico de alterações de status de um pedido, para entender o que aconteceu. | Histórico com status, data e responsável. | C |
| US11 | Como **cliente**, quero editar um pedido **Em análise**, para corrigir período ou automóvel. | Pedidos já avaliados ou cancelados não podem ser editados. | M |
| US12 | Como **cliente**, quero cancelar meu pedido, para desistir do aluguel. | Status vira **Cancelado**; pedido cancelado nunca pode ser aprovado ou entrar em execução. | M |

## Épico 3 — Perfil Agente

| ID | História | Critérios de aceitação | Prior. |
|----|----------|------------------------|--------|
| US13 | Como **agente**, quero me cadastrar como Empresa ou Banco, para poder analisar pedidos. | Dados: nome, CNPJ, endereço, tipo (Empresa/Banco), e-mail e senha. CNPJ único. | M |
| US14 | Como **agente**, quero listar os pedidos pendentes, para priorizar minhas análises. | Lista pedidos com status **Em análise**, com dados do cliente (inclusive rendimentos) e do automóvel. | M |
| US15 | Como **agente**, quero registrar uma avaliação financeira (aprovado/reprovado com justificativa), para decidir sobre o pedido. | Registra agente, data da análise, parecer e observação. Só agentes podem avaliar. Status passa a **Aprovado** ou **Reprovado**. | M |
| US16 | Como **agente**, quero que pedidos cancelados não possam ser avaliados, para evitar inconsistências. | Tentativa de avaliar/aprovar pedido cancelado retorna erro. | M |
| US17 | Como **agente**, quero confirmar a execução de um pedido aprovado, para iniciar o contrato. | Status passa a **Contrato em execução** somente a partir de **Aprovado**. | M |
| US18 | Como **agente Banco**, quero associar um contrato de crédito a um pedido, para formalizar o financiamento. | Contrato com valor financiado, prazo e situação; só agentes do tipo Banco podem concedê-lo. Opcional por pedido. | S |
| US19 | Como **agente**, quero cadastrar e manter automóveis da minha empresa/banco, para disponibilizá-los para aluguel. | Proprietário = o próprio agente (Empresa ou Banco). | S |

## Premissas assumidas (validar com o professor)

1. A confirmação de **Contrato em execução** é feita pelo **agente** após a aprovação.
2. O cliente pode cancelar um pedido até antes de ele entrar em execução.
3. O automóvel pode ser de qualquer proprietário (cliente, empresa ou banco); o proprietário é modelado como referência polimórfica.
4. Não haverá painel administrativo nesta versão.