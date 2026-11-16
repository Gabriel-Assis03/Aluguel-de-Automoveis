<!-- README baseado no template do Prof. Dr. João Paulo Aramuni -->

---

# 🚗 Sistema Web de Aluguel de Automóveis 👨‍💻

> [!NOTE]
> Plataforma web que conecta **clientes** e **agentes financeiros** (empresas e bancos) para criar, analisar e acompanhar pedidos de aluguel de automóveis, com avaliação financeira e contrato de crédito opcional.

<table>
  <tr>
    <td width="800px">
      <div align="justify">
        Este projeto é um sistema web de gestão de <b>pedidos de aluguel de automóveis</b>. O <b>cliente</b> cadastra seus dados, seus automóveis e seus pedidos; o <b>agente</b> (empresa ou banco) analisa financeiramente cada pedido e altera seu status. Foi desenvolvido em <b>três sprints evolutivas</b>, combinando <i>modelagem UML</i> e um <i>protótipo funcional</i> com <b>Node.js, React e MongoDB</b> em arquitetura <b>MVC</b>.
      </div>
    </td>
    <td>
      <div>
        <!-- TODO: criar e adicionar a logo do projeto em docs/img/logo.png -->
        <img src="docs/img/logo.png" alt="Logo do Projeto" width="120px"/>
      </div>
    </td>
  </tr>
</table>

---

## 🚧 Status do Projeto

![Versão](https://img.shields.io/badge/Versão-v0.1.0-blue?style=for-the-badge)
![Node.js](https://img.shields.io/badge/Node.js-20-007ec6?style=for-the-badge&logo=nodedotjs&logoColor=white)
![React](https://img.shields.io/badge/React-18-007ec6?style=for-the-badge&logo=react&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-7-007ec6?style=for-the-badge&logo=mongodb&logoColor=white)
![Licença](https://img.shields.io/badge/Licença-MIT-007ec6?style=for-the-badge)

| Sprint | Escopo | Situação |
|--------|--------|----------|
| Sprint 1 | Modelagem UML (casos de uso, histórias de usuário, classes, pacotes) | 🟡 Em andamento |
| Sprint 2 | <!-- TODO: preencher conforme enunciado --> | ⚪ Não iniciada |
| Sprint 3 | <!-- TODO: preencher conforme enunciado --> | ⚪ Não iniciada |

---

## 📚 Índice
- [Links Úteis](#-links-úteis)
- [Sobre o Projeto](#-sobre-o-projeto)
- [Funcionalidades Principais](#-funcionalidades-principais)
- [Regras de Negócio](#-regras-de-negócio)
- [Modelagem UML](#-modelagem-uml)
- [Tecnologias Utilizadas](#-tecnologias-utilizadas)
- [Arquitetura](#-arquitetura)
- [Instalação e Execução](#-instalação-e-execução)
- [Estrutura de Pastas](#-estrutura-de-pastas)
- [Demonstração](#-demonstração)
- [Testes](#-testes)
- [Documentações utilizadas](#-documentações-utilizadas)
- [Autores](#-autores)
- [Contribuição](#-contribuição)
- [Agradecimentos](#-agradecimentos)
- [Licença](#-licença)

---

## 🔗 Links Úteis
* 🌐 **Demo Online:** <!-- TODO --> _a definir_
* 📖 **Documentação UML:** [`/docs`](./docs)
* 📋 **Histórias de Usuário:** [`docs/02-historias-de-usuario.md`](./docs/02-historias-de-usuario.md)

---

## 📝 Sobre o Projeto

**Por que existe:** apoiar a gestão de pedidos de aluguel de automóveis, que envolve não só o cliente e o veículo, mas também uma análise financeira feita por empresas ou bancos.

**Problema que resolve:** centraliza cadastro, solicitação, análise e acompanhamento do pedido em um único fluxo, com regras claras de quem pode fazer o quê.

**Contexto:** projeto acadêmico de Engenharia de Software (PUC Minas), desenvolvido em três sprints.

**Onde pode ser utilizado:** locadoras, concessionárias e instituições financeiras que concedem crédito para aluguel de veículos.

---

## ✨ Funcionalidades Principais

- 🔐 **Autenticação e perfis:** cadastro prévio obrigatório; perfis **Cliente** e **Agente** com permissões distintas.
- 👤 **Cadastro de clientes (CRUD):** nome, CPF, RG, endereço, profissão e até 3 vínculos empregatícios com rendimentos.
- 🚘 **Cadastro de automóveis (CRUD):** marca, modelo, ano, placa, matrícula e proprietário (cliente, empresa ou banco).
- 🏦 **Cadastro de agentes:** empresas e bancos (nome, CNPJ, endereço, tipo).
- 📄 **Pedidos de aluguel:** criar, consultar, editar e cancelar os próprios pedidos; acompanhar status.
- 💰 **Avaliação financeira:** agente consulta pedidos pendentes e registra parecer (aprovado/reprovado) com justificativa.
- 🧾 **Contrato de crédito (opcional):** vinculado ao pedido e concedido por agente do tipo banco.

### Status do pedido

| Status | Significado |
|--------|-------------|
| Em análise | Criado pelo cliente, aguardando avaliação |
| Aprovado | Aprovado financeiramente pelo agente |
| Reprovado | Recusado na análise financeira |
| Cancelado | Cancelado pelo cliente |
| Contrato em execução | Aprovado e confirmado para execução |

> Status adicionais, se criados, serão documentados aqui e nos diagramas.

---

## 📏 Regras de Negócio

1. Apenas usuários cadastrados podem utilizar o sistema.
2. O cliente cria, edita, consulta e cancela **apenas os seus** pedidos.
3. Pedido cancelado não pode ser aprovado nem colocado em execução.
4. Apenas agentes realizam avaliações financeiras, e a avaliação registra o agente responsável.
5. Um cliente possui no máximo **3** vínculos de empregador/rendimento.
6. Contrato de crédito, quando existir, é concedido por agente do tipo **banco**.
7. Todo automóvel possui proprietário identificado (cliente, empresa ou banco).
8. Mudanças relevantes nas regras ou no modelo devem ser refletidas nos diagramas e no código.

---

## 🧩 Modelagem UML

| Entrega (Sprint 1) | Arquivo |
|--------------------|---------|
| Diagrama de Casos de Uso | [`docs/01-casos-de-uso.md`](./docs/01-casos-de-uso.md) |
| Histórias de Usuário | [`docs/02-historias-de-usuario.md`](./docs/02-historias-de-usuario.md) |
| Diagrama de Classes (+ máquina de estados do pedido) | [`docs/03-diagrama-de-classes.md`](./docs/03-diagrama-de-classes.md) |
| Diagrama de Pacotes | [`docs/04-diagrama-de-pacotes.md`](./docs/04-diagrama-de-pacotes.md) |

> Os diagramas ficam versionados no repositório e são atualizados a cada sprint.

---

## 🛠 Tecnologias Utilizadas

### 💻 Front-end
* **Biblioteca:** React 18
* **Linguagem:** JavaScript (ES6+)
* **Build Tool:** Vite
* **Roteamento:** React Router
* **HTTP:** Axios
* **Estado de autenticação:** Context API

### 🖥️ Back-end
* **Runtime:** Node.js 20 (LTS)
* **Framework:** Express
* **Banco de Dados:** MongoDB 7
* **ODM:** Mongoose
* **Autenticação:** JWT + bcrypt
* **Validação:** Zod ou Joi

### ⚙️ Infraestrutura & DevOps
* **Containerização:** Docker / Docker Compose (MongoDB)
* **Versionamento:** Git + GitHub

---

## 🏗 Arquitetura

O sistema segue o padrão **MVC**, dividido em dois projetos:

| Camada MVC | Implementação |
|------------|---------------|
| **View** | React (`/frontend`) |
| **Controller** | Controllers Express (`/backend/src/controllers`) |
| **Model** | Schemas Mongoose (`/backend/src/models`) |

Complementos: camada de **services** (regras de negócio), **middlewares** (JWT e autorização por perfil) e **MongoDB** como persistência. Fluxo: `React → API REST (JSON) → routes → middlewares → controllers → services → models → MongoDB`.

Detalhes no [Diagrama de Pacotes](./docs/04-diagrama-de-pacotes.md).

---

## 🔧 Instalação e Execução

### Pré-requisitos
* **Node.js** 18+ (recomendado 20 LTS)
* **npm** ou **yarn**
* **Docker** (recomendado para o MongoDB) ou MongoDB local/Atlas

### 🔑 Variáveis de Ambiente

#### Back-end (`/backend/.env`)

| Variável | Descrição | Exemplo |
| :--- | :--- | :--- |
| `PORT` | Porta da API | `3000` |
| `MONGODB_URI` | String de conexão | `mongodb://localhost:27017/aluguel_automoveis` |
| `JWT_SECRET` | Chave de assinatura do token | `troque_esta_chave` |
| `JWT_EXPIRES_IN` | Validade do token | `1d` |

#### Front-end (`/frontend/.env`)

| Variável | Descrição | Exemplo |
| :--- | :--- | :--- |
| `VITE_API_URL` | URL base da API | `http://localhost:3000/api` |

### 📦 Instalação de Dependências

```bash
git clone <URL_DO_SEU_REPOSITÓRIO>
cd <pasta-do-projeto>

cd backend && npm install && cd ..
cd frontend && npm install && cd ..
```

### 💾 Banco de Dados (MongoDB)

```bash
docker run --name mongo_aluguel -p 27017:27017 -d mongo:7
```

Ou, com Docker Compose (na raiz):

```bash
docker-compose up -d
```

### ⚡ Como Executar

**Terminal 1 — Back-end**
```bash
cd backend
npm run dev
```
🚀 API em **http://localhost:3000**

**Terminal 2 — Front-end**
```bash
cd frontend
npm run dev
```
🎨 Aplicação em **http://localhost:5173**

---

## 📂 Estrutura de Pastas

```
.
├── README.md
├── .gitignore
├── docker-compose.yml           # 🐳 MongoDB (e demais serviços)
│
├── /docs                        # 📚 Modelos UML e documentação
│   ├── 01-casos-de-uso.md
│   ├── 02-historias-de-usuario.md
│   ├── 03-diagrama-de-classes.md
│   ├── 04-diagrama-de-pacotes.md
│   └── /img                     # 🖼️ Exportações dos diagramas e logo
│
├── /backend                     # 🖥️ API Node.js (Controller + Model)
│   ├── .env.example
│   ├── package.json
│   └── /src
│       ├── app.js / server.js
│       ├── /config              # 🔧 Conexão MongoDB, env
│       ├── /routes              # 🛣️ Rotas da API
│       ├── /middlewares         # 🛡️ Auth JWT, perfil, erros
│       ├── /controllers         # 🎮 Controllers
│       ├── /services            # ⚙️ Regras de negócio
│       ├── /models              # 🧬 Schemas Mongoose
│       └── /utils               # 🛠️ Utilitários
│
├── /frontend                    # 💻 React (View)
│   ├── .env.example
│   ├── package.json
│   └── /src
│       ├── /pages               # 📄 Telas
│       ├── /components          # 🧱 Componentes reutilizáveis
│       ├── /services            # 🔌 Chamadas HTTP
│       ├── /context             # 🔐 Autenticação
│       └── /routes              # 🧭 Rotas protegidas
│
└── /tests                       # 🧪 Testes
```

---

## 🎥 Demonstração

> _Será preenchida a partir da Sprint 2, com prints e GIFs do protótipo._

| Tela | Captura |
| :---: | :---: |
| **Login / Cadastro** | _em breve_ |
| **Painel do Cliente** | _em breve_ |
| **Painel do Agente** | _em breve_ |

---

## 🧪 Testes

```bash
cd backend && npm test      # testes unitários/integração (Jest + Supertest)
```

---

## 🔗 Documentações utilizadas

* 📖 [React](https://react.dev/reference/react)
* 📖 [Vite](https://vitejs.dev/config/)
* 📖 [Express](https://expressjs.com/)
* 📖 [Mongoose](https://mongoosejs.com/docs/)
* 📖 [MongoDB](https://www.mongodb.com/docs/)
* 📖 [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/)

---

## 👥 Autores

| 👤 Nome | :octocat: GitHub | 💼 LinkedIn | 📤 E-mail |
|---------|------------------|-------------|-----------|
| <!-- Nome --> | [@usuario](https://github.com/usuario) | [perfil](https://www.linkedin.com/in/usuario) | <!-- email --> |

---

## 🤝 Contribuição

1. Faça um `fork` do projeto.
2. Crie uma branch (`git checkout -b feature/minha-feature`).
3. Commit com [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) (`git commit -m 'feat: adiciona X'`).
4. `git push origin feature/minha-feature`.
5. Abra um **Pull Request**.

---

## 🙏 Agradecimentos

* [**Engenharia de Software PUC Minas**](https://www.instagram.com/engsoftwarepucminas/) — apoio institucional e estrutura acadêmica.
* [**Prof. Dr. João Paulo Aramuni**](https://github.com/joaopauloaramuni) — ensinamentos sobre Arquitetura de Software e Padrões de Projeto.

---

## 📄 Licença

Este projeto é distribuído sob a **Licença MIT**.

---
