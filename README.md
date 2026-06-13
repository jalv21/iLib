<a href="https://classroom.github.com/online_ide?assignment_repo_id=99999999&assignment_repo_type=AssignmentRepo"><img src="https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg" width="200"/></a> <a href="https://classroom.github.com/open-in-codespaces?assignment_repo_id=99999999"><img src="https://classroom.github.com/assets/launch-codespace-2972f46106e565e64193e422d61a12cf1da4916b45550586e14ef0a7c637dd04.svg" width="250"/></a>

---

# 📗 iLib - Livraria de Ebooks

> [!NOTE]
> Plataforma de ebooks focada em conectar leitores, autores independentes e editoras. **Publique seus ebooks com métricas inteligentes, compre e avalie livros de editoras e autores independentes e discuta as avaliações de seus leitores.**

<table>
  <tr>
    <td width="800px">
      <div align="justify">
        O <b>iLib</b> é um ecossistema digital projetado para transformar a experiência de publicação e consumo de livros digitais (EPUBs). A plataforma fornece um ambiente onde editoras e autores independentes gerenciam suas obras por meio de dashboards analíticos detalhados (vendas, receitas e avaliações). Ao mesmo tempo, oferece aos leitores recursos avançados de organização de bibliotecas via estantes personalizadas e sub-estantes, ferramentas integradas de leitura continuada e uma forte camada de interação social baseada em avaliações e comentários.
      </div>
    </td>
  </tr>
</table>

---

## 📋 Sumário
* [Visão Geral do Projeto](#-visão-geral-do-projeto)
* [Modelos de Usuário e Atores](#-modelos-de-usuário-e-atores)
* [Funcionalidades e Casos de Uso](#-funcionalidades-e-casos-de-uso)
* [Arquitetura e Tecnologias](#-arquitetura-e-tecnologias)
* [Estrutura do Banco de Dados](#-estrutura-do-banco-de-dados)
* [Como Executar o Projeto](#-como-executar-o-projeto)
* [Histórico de Revisões](#-histórico-de-revisões)
* [Agradecimentos](#-agradecimentos)

---

## 👁️ Visão Geral do Projeto
A plataforma subdivide-se em três grandes pilares operacionais:
1. **Compra e Leitura de Livros:** Leitores compram livros digitais e utilizam o motor nativo `LeitorEPUB` com marcadores de página automatizados.
2. **Avaliação e Discussão de Avaliações:** Sistema dinâmico de notas, avaliações textuais estruturadas e respostas moderadas pelos publicadores da obra.
3. **Dashboard Editorial para Análise:** Painéis gerenciais em tempo real que mapeiam a receita, o perfil demográfico do público leitor e o desempenho geral das estantes públicas.

---

## 👥 Modelos de Usuário e Atores
O sistema adota uma estrutura hierárquica clara de permissões e perfis de acesso:
* **Usuário:** Ator geral da plataforma que serve como base de identificação comum (nome, e-mail, username e credenciais).
* **Usuário Editorial:** Especialização voltada para a publicação. Divide-se em **Autor Independente** (Pessoa Física com CPF) e **Editora** (Pessoa Jurídica com CNPJ e lista de autores licenciados).
* **Leitor:** Consumidor final com permissões exclusivas para compras, leituras, criação de estantes particulares e emissão de avaliações de livros.

---

## 🎯 Funcionalidades e Casos de Uso
O escopo funcional do iLib é composto por **35 casos de uso**, organizados em subsistemas complementares:

### 🔐 Autenticação e Cadastro
* **UC01 & UC02:** Cadastro inicial e login criptografado.
* **UC05:** Autenticação por reconfirmação de senha antes de operações críticas ou financeiras.

### 📚 Gerenciamento de Livros com CRUD
* **UC03 & UC04:** Cadastro unificado de livros com metadados (ISBN, gênero, preço) com upload do arquivo `.epub` para repositório Cloud Storage.
* **UC06, UC07 & UC08:** Edição, arquivamento (soft delete) e remoção permanente de livros do catálogo.

### 🛒 E-commerce de Livros
* **UC09 & UC10:** Fluxo completo de compra de livros com seleção Dinâmica de Métodos de Pagamento via integração externa.
* **UC11:** Visualização analítica dos repasses e valores a receber por obra vendida.

### 🔍 Pesquisa e Leitura de EPUB Integrada ao Sistema
* **UC12, UC13 & UC14:** Pesquisa avançada textual e aplicação de filtros combinados (gêneros, novidades, mais lidos).
* **UC16, UC17 & UC18:** Motor de leitura integrado `LeitorEPUB` com salvamento de estado da última página lida, marcadores de progresso e histórico automatizado.

### 💬 Avaliações de Livros e Discussão
* **UC19 & UC20:** Publicação e edição de avaliações de obras consumidas (Estrelas e Texto).
* **UC21 & UC22:** Threads públicas de debate sobre avaliações e suporte para respostas destacadas com badges do Autor/Editora.

### 🗂️ Organização de Bibliotecas Pessoais
* **UC23 a UC26:** Provisionamento automático da biblioteca do usuário com estantes nativas do sistema (`Adquiridos`, `Avaliados` e `Histórico`) acionadas via microsserviços.
* **UC27 a UC30:** Criação de novas estantes customizadas (públicas/privadas) e organização em sub-estantes hierárquicas de até dois níveis.

### 📊 Dashboard Editorial para Publicadores
* **UC31 a UC35:** Monitoramento em tempo real do faturamento periódico, comportamento e preferência de gênero literário do público leitor, ranking interno de avaliações e métricas de aderência de títulos em estantes alheias.

---

## 🏗️ Arquitetura e Tecnologias
O iLib foi construído sob uma **Arquitetura de Microsserviços descentralizada**, composta por **18 nós físicos/lógicos** orquestrados em contêineres e comunicando-se via APIs RESTful HTTP.

### Tecnologias Utilizadas:
* **Front-End:** React.js (Adotado pela alta capacidade de reaproveitamento de componentes reutilizáveis em páginas com estruturas similares).
* **API Entrypoint & Gateways:** Go / Gin Framework (Fornece excelente desempenho de baixo nível com foco em I/O rápido e consumo enxuto de recursos).
* **Microsserviços de Negócio:** Java / Spring Boot (Responsável pelos módulos de *Gerenciamento de Livros, Estantes, Leitura, Catálogo e Compras* devido à sua tipagem forte e POO ideal para regras complexas de negócio).
* **Microsserviço de Analytics:** Python / Pandas (Escolhido especificamente para o módulo de *Dashboard*, processando grandes volumes de dados analíticos nativamente).
* **Orquestração e DevOps:** Docker & Kubernetes (Garante estabilidade, alta disponibilidade e escalabilidade horizontal para os serviços).

---

## 🗄️ Estrutura do Banco de Dados
A persistência da aplicação é estruturada em um **Cluster de Banco de Dados NoSQL** integrado na nuvem:
* **SGBD Utilizado:** **Amazon DynamoDB** (Escolhido devido à escalabilidade linear e total compatibilidade operacional com os serviços AWS).
* **Bancos Isolados por Contexto (Database-per-Service):**
  * `BD Livros:` Armazena dados de registros, metadados editoriais e arquivos EPUB.
  * `BD Bibliotecas:` Mapeia as coleções, estantes ativas e sub-estantes dos usuários.
  * `BD Avaliações:` Gerencia as árvores e sequências de comentários e curtidas.
  * `BD Compras:` Histórico transacional financeiro e auditoria de vendas.

---

## 🚀 Como Executar o Projeto

### Pré-requisitos
Antes de começar, certifique-se de ter instalado em sua máquina:
* **Docker** e **Docker Compose**
* **Node.js** (versão 18+)
* **Go** (versão 1.20+)
* **JDK 17** (para compilar os microsserviços Spring)

### Passo a Passo

1. **Clonar o Repositório:**
```bash
   git clone [https://github.com/usuario/ilib-plataforma.git](https://github.com/usuario/ilib-plataforma.git)
   cd ilib-plataforma
```

2. **Subir o Cluster de Microsserviços e Bancos (Docker):**
```bash
docker-compose up -d --build
```


3. **Executar a Aplicação Front-End (React):**
```bash
cd frontend
npm install
npm run dev
```

4. **Acessar o Sistema:**
Abra o seu navegador e acesse a aplicação em `http://localhost:3000`.

## 📝 Histórico de Revisões

Acompanhamento de alterações na documentação e modelagem do projeto:

| Autor | Data | Razões para Mudança | Versão |
| --- | --- | --- | --- |
| **João Alvaro Rodrigues Araujo** | 21/05/2026 | Criação e modelagem inicial do sistema iLib. | 0.1 |
| **João Alvaro Rodrigues Araujo** | 13/06/2026 | Adicionando numeração nos casos de uso do modelo. | 1.0 |

---

## 🙏 Agradecimentos

O desenvolvimento do ecossistema iLib contou com referências acadêmicas essenciais:

* **Engenharia de Software PUC Minas** – Pelo suporte à infraestrutura de ensino e inovação de projetos de software.
* **Prof. Dr. João Paulo Aramuni** – Pelas diretrizes de projeto de software e padrões de projeto aplicados neste sistema.
