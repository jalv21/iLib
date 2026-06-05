# 📗 iLib - Histórias de Usuário

## 👨‍💻 Épico: CRUD de Usuários
**US01** - "Como leitor, quero poder me cadastrar na aplicação para que eu possa ler livros."

**Critérios de Aceitação**
 - O leitor utilizará o formulário de cadastro padrão para se registrar em uma conta padrão de leitor, preenchendo os dados de **Nome**, **Username** único no formato **`@username`**, **Email** e **Senha**.

**US02** - "Como autor ou editora de um livro, quero me cadastrar na aplicação para que eu possa cadastrar meus livros para serem lidos por leitores."

**Critérios de Aceitação**
- O autor ou editora utilizará o formulário especial indicado em uma seção "Publique seu livro no iLib" na página inicial da aplicação, preenchendo os mesmos dados, porém com a adição de um **CPF** ou **CNPJ** para confirmar a sua legitimidade.

**US03** - "Como usuário, quero poder fazer login na aplicação após realizar o meu cadastro."

**Critérios de Aceitação**
- Após o cadastro do usuário, ele deve ser automaticamente redirecionado para sua página inicial dentro da aplicação uma vez autenticado (para usuários, o **catálogo de livros do sistema**, para autores/editoras, o ***Dashboard* de autor/editora**.)
- Caso o login seja feito após o término da primeira sessão do usuário no sistema feita logo após o cadastro, ele deverá preencher o formulário de login com  seu **Email** ou **Username**, e sua **Senha**. O formulário de login é igual para todos os usuários.

## 📖 Épico - CRUD de Livros

**US04** - "Como Autor/Editora, quero poder cadastrar meus livros no catálogo da aplicação para que leitores possam lê-los."

**Critérios de Aceitação**:
- O Autor/Editora clica em um botão "Novo livro" na sua página de "Livros cadastrados", O botão leva o usuário à um formulário de cadastro de livros, onde ele irá inserir o **ISBN** e os dados adicionais **Gênero(s)** (da lista de gêneros do sistema) e irá fazer **upload do arquivo EPUB do livro** e definirá um **preço para compra**.
- Antes da castrar o livro, o Autor/Editora terá que confirmar sua identidade usando sua **Senha**.
- Uma vez cadastrado, a **API de livros** (*Google Books API*, *OpenLibrary API*, etc.) consumida pela aplicação vai retornar os dados completos do livro na sua interface front-end com base no ISBN inserido no cadastro.

**US05** - "Como Autor/Editora, quero poder editar dados dos meus livros para corrigir informações incorretas ou atualizar detalhes"

**Critérios de Aceitação**:
- O Autor/Editora poderá editar diretamente dados como **Gênero(s) do livro** e o **preço**, porém para a edição de um livro a nível de conteúdo pode ser feita apenas **substituindo o arquivo EPUB**. O **ISBN** do livro deve ser um dado imutável.

**US06** - "Como Autor/Editora, quero poder remover meus livros do catálogo da aplicação caso deseje."

**Critérios de Aceitação**: 
- O Autor/Editora irá clicar na opção "arquivar livro",  confirmar sua identidade pela sua **Senha** e arquivar o livro, que será removido do catálogo do sistema e será movido para a seção *Livros Arquivados* até que ele restaure ou exclua o livro.

## 🛒 Épico - Catálogo de Livros

**US07** - "Como leitor, quero poder selecionar o livro que quero ler e comprá-lo."

**Critérios de Aceitação**:
- O usuário deve selecionar um livro e clicar no seu botão "Comprar". Ele então vai selecionar a forma de pagamento em uma tela de checkout e confirmar a compra.

**US08** - "Como Autor/Editora, quero receber pelos livros meus que forem comprados por leitores."

**Critérios de Aceitação**:
- A **API de Transações** consumida pelo sistema vai realizar uma transação entre o leitor e o autor/editora, fazendo com que ele receba o valor do livro na sua conta bancária.
- O valor do livro será registrado no seu histórico de vendas e aparecerá no seu dashboard integrando a quantia total vendida.

**US09** - "Como leitor, quero poder adicionar livros que desejo comprar em um 'carrinho', para que não precise comprá-los separadamente em compras de múltiplos livros."

**Critérios de Aceitação**:
- O leitor irá clicar em um botão próximo de "Comprar" no card do livro que deseja, e isso o adicionará ao seu *Carrinho*, para que compre múltiplos livros de uma só vez.

**US10** - "Como leitor, quero poder filtrar os livros que aparecem no feed por dados como faixa de preço, gênero, autor, editora e gênero, tal como selecionar filtros pré-estabelecidos, como 'Livros em Alta' ou 'Novidades'."

**Critérios de Aceitação**:
- O leitor irá selecionar filtros na barra de pesquisa selecionando os critérios de filtro desejados, ou selecionar no menu de filtros pré-estabelecidos no topo do feed o filtro que deseja.

**US11** - "Como leitor, quero poder pesquisar livros de forma eficaz. Minha pesquisa deve retornar os livros mais populares que contém o texto pesquisado no título ou autor." 

**Critérios de Aceitação**:
- O leitor irá digitar o que procura na barra de pesquisa, e os livros correspondentes serão retornados em ordem de popularidade.

## 🔖 Épico - Leitura de Livros

**US12** - "Como leitor, quero poder ler os ebooks em formato EPUB diretamente na aplicação, com uma interface intuitiva em relação à experiência de leitura de livros físicos."

**Critérios de Aceitação**:
- O sistema deve fornecer uma interface de usuário para leitura dos arquivos EPUB dos livros. Na aplicação mobile, isso seria feito com movimentos como deslize (*scroll*) da tela para a esquerda e direita virem páginas para frente e para trás, respectivamente. Na aplicação web, as teclas de seta para esquerda e direita (e alternativamente as teclas A e D) fariam esse papel.

**US13** - "Como leitor, quero poder marcar a página onde eu parei para que eu não tenha que procurá-la manualmente quando abrir novamente o livro depois de fechá-lo."

**Critérios de Aceitação**:
- Na aplicação mobile, o leitor poderá deslizar a tela para baixo e para cima no canto superior direito da interface para colocar e retirar o marcador de página, respectivamente. Na aplicação web, ele poderá clicar no canto superior direito para fazer isso.

## ⭐ Épico - Avaliação de Livros
> [!NOTE] Nota temporária (Apagar após o diagrama de componentes)
> Devido à alta carga de I/O da funcionalidade, essa feature poderia ser implementada dentro de um microsserviço em uma linguagem performática como Go.

**US14** - "Como leitor, quero poder avaliar os livros lidos em um sistema de 5 estrelas e dar meu feedback para o autor/editora."

**Critérios de Aceitação**:
- O leitor poderá avaliar o livro em uma seção "Avaliar", dando uma nota de 1 à 5 estrelas e deixando um comentário.
- Leitores podem comentar nas avaliações de outros leitores, porém as respostas do autor/editora, caso existam, estarão sempre em destaque no topo da seção de comentários da avaliação.

**US15** - "Como autor/editora, quero que as avaliações do meu livro sejam combinadas em uma média que será exibida junto com as informações gerais do livro."

**Critérios de Aceitação**:
- Será calculada uma média à partir das avaliações dos leitores, que será registrada como a média de avaliações do livro. Este dado então será usado para definir a prioridade do livro em pesquisas dos leitores, e vai passar a integrar o dashboard de autor/editora.

## 📚 Épico - Organização de Livros

**US16** - "Como leitor, quero que os livros que eu interagi sejam categorizados de forma diferente dentro da minha biblioteca para poder gerenciá-los de forma mais fácil e melhorar a experiência de navegação no sistema."

**Critérios de Aceitação**:
- Ao interagir com um livro, seja comprando, pegando emprestado, avaliando ou comentando, esse livro será exibido de forma diferente na biblioteca do leitor.
    - Livros que forem comprados pelo leitor irão para uma seção "Meus livros" dentro de "Minha Biblioteca"
    - Livros que receberam uma avaliação do leitor serão colocados na seção "Minhas Avaliações"
    - Livros que não foram adquiridos e não foram avaliados não estarão na biblioteca. Caso o livro seja parte de um empréstimo que expirou, ele será registrado no histórico de empréstimos.

**US17** - "Como leitor, quero poder organizar os meus livros em pastas da forma que eu desejar."

**Critérios de Aceitação**:
- O leitor pode criar *Estantes* (pastas) para livros. Qualquer livro pode ser adicionado à qualquer estante, sem restrições.
- Essas pastas podem ser divididas em subpastas para uma camada extra de organização. Ao fazer isso, a estante se torna um *Acervo*, com as subpastas recebendo o nome de *Estantes* agora.

**US18** - "Como Autor/Editora, quero que os meus livros sejam organizados dentro da minha biblioteca para gerenciá-los de forma mais fácil e melhorar a minha experiência no sistema."

**Critérios de Aceitação**:
- Livros cadastrados no catálogo serão inseridos na seção "Meus livros" da biblioteca do autor/editora. 
- Livros arquivados serão movidos para a seção "Arquivo"

**US19** - "Como Autor/Editora, quero poder criar minhas próprias estantes com meus livros, para que os leitores acessem através da seção 'Estantes' do feed de livros ou pela minha biblioteca de autor/editora."

**Critérios de Aceitação**:
- O autor/editora pode adicionar seus livros à estantes assim como o leitor, porém todas as estantes criadas por autores/editores são necessariamente públicas, não sendo possível a criação de estantes privadas.

## 📋 Épico - Dashboard de Autores e Editoras
>[!NOTE] Apagar após diagrama de componentes
> Considerar microsserviço implementado com Python pela análise pesada de dados nessa feature.

**US20** - "Como autor/editora, quero ter acesso aos dados sobre as minhas vendas na aplicação, com análises avançadas relacionadas à receita obtida, as avaliações dos livros com dados sobre o nível de XP para aquele livro dos usuários que o avaliaram para que eu tenha noção sobre qual exatamente é o meu público de leitores, além de gráficos exibindo esses dados em relação ao tempo."

**Critérios de Aceitação**
- O sistema terá como página inicial para autores/editoras o seu Dashboard, com todas essas informações organizadas em um só lugar. Podem ser aplicados diversos filtros e análises por uma gama de critérios.

