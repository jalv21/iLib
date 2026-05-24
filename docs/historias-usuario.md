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
- O Autor/Editora clica em um botão "Novo livro" na sua página de "Livros cadastrados", O botão leva o usuário à um formulário de cadastro de livros, onde ele irá inserir o **ISBN** e os dados adicionais **Gênero(s)** (da lista de gêneros do sistema) e a **autodeclaração de dificuldade do livro**, escolhendo uma opção entre *Fácil*, *Médio* e *Dificíl*. Finalmente, ele irá fazer **upload do arquivo EPUB do livro**, definirá um **preço para compra vitalícia** e a **duração do empréstimo gratuito** em dias.
- Antes da castrar o livro, o Autor/Editora terá que confirmar sua identidade usando sua **Senha**.
- Uma vez cadastrado, a **API de livros** (*Google Books API*, *OpenLibrary API*, etc.) consumida pela aplicação vai retornar os dados completos do livro na sua interface front-end com base no ISBN inserido no cadastro.

**US05** - "Como Autor/Editora, quero poder editar dados dos meus livros para corrigir informações incorretas ou atualizar detalhes"

**Critérios de Aceitação**:
- O Autor/Editora poderá editar diretamente dados como **Gênero(s) do livro**, a **autodeclarção de dificuldade**, o **preço para compra vitalícia** e a **duração do empréstimo gratuito**, porém para a edição de um livro a nível de conteúdo pode ser feita apenas **substituindo o arquivo EPUB**. O **ISBN** do livro deve ser um dado imutável.

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

**US09** - "Como leitor, quero poder aplicar os meus cupons de desconto para os livros que eu quero comprar."

**Critérios de Aceitação**:
- O leitor irá incluir um cupom na sua compra na tela de checkout. Um leitor só pode aplicar um cupom por livro.

**US10** - "Como leitor, quero poder adicionar livros que desejo comprar em um 'carrinho', para que não precise comprá-los separadamente em compras de múltiplos livros."

**Critérios de Aceitação**:
- O leitor irá clicar em um botão próximo de "Comprar" no card do livro que deseja, e isso o adicionará ao seu *Carrinho*, para que compre múltiplos livros de uma só vez.

**US11** - "Como leitor, quero poder filtrar os livros que aparecem no feed por dados como faixa de preço, gênero, autor, editora e gênero, tal como selecionar filtros pré-estabelecidos, como 'Livros em Alta' ou 'Novidades'."

**Critérios de Aceitação**:
- O leitor irá selecionar filtros na barra de pesquisa selecionando os critérios de filtro desejados, ou selecionar no menu de filtros pré-estabelecidos no topo do feed o filtro que deseja.

**US12** - "Como leitor, quero poder pesquisar livros de forma eficaz. Minha pesquisa deve retornar os livros mais populares que contém o texto pesquisado no título ou autor." 

**Critérios de Aceitação**:
- O leitor irá digitar o que procura na barra de pesquisa, e os livros correspondentes serão retornados em ordem de popularidade.

## 🔃 Épico - Empréstimo de Livros

**US13** - "Como leitor, quero pegar livros emprestados por um determinado período de tempo antes de comprá-los de forma vitalícia. Caso eu não encerre a amostra manualmente até o fim do prazo, o sistema deve fazer isso por mim para impedir que eu contraia dívidas."

**Critérios de Aceitação**:
- O leitor irá clicar no botão "Pegar emprestado" no card do livro que deseja, e o livro será adicionado na sua tela "*Minha Biblioteca*" com um contador regressivo em cima da capa, indicando quanto falta para o fim do empréstimo. O tempo padrão do empréstimo é definido pelo Autor/Editora no cadastro do livro, mas pode aumentar se o leitor aplicar **cupons especiais** comprados com **moedas do sistema** na **loja** (funcionalidades que serão detalhadas mais à frente no documento.)
- Um leitor só pode pegar **um** livro emprestado por vez por padrão, mas ele pode aplicar **cupons da loja** para adicionar outro livro ao empréstimo.
- Após o fim do prazo, o livro será automaticamente removido da sua biblioteca e uma **notificação** será criada na **página de notificações** informando a expiração do empréstimo. Caso o leitor queira voltar a lê-lo, deverá **comprá-lo de forma vitalícia** ou **esperar o mesmo tempo do seu empréstimo** (excetuando tempo extra de cupons) para solicitar um novo.

**US14** - "Como Autor/Editora, quero que o sistema tenha regras para os empréstimos de livros para não prejudicar a minha receita na aplicação."

**Critérios de Aceitação**:
- A duração padrão do empréstimo de livros é definida diretamente pelos Autores/Editoras durante o cadastro dos livros.
- Mesmo com cupons de tempo extra aplicados, esses cupons terão um limite de tempo que podem conceder ao leitor, e somente um cupom desse tipo pode ser aplicado por livro no empréstimo.
- Cupons com maiores benefícios só estarão disponíveis para compra na loja para leitores acima de determinado nível de XP (funcionalidade será detalhada mais à frente).

## 🔖 Épico - Leitura de Livros

**US15** - "Como leitor, quero poder ler os ebooks em formato EPUB diretamente na aplicação, com uma interface intuitiva em relação à experiência de leitura de livros físicos."

**Critérios de Aceitação**:
- O sistema deve fornecer uma interface de usuário para leitura dos arquivos EPUB dos livros. Na aplicação mobile, isso seria feito com movimentos como deslize (*scroll*) da tela para a esquerda e direita virem páginas para frente e para trás, respectivamente. Na aplicação web, as teclas de seta para esquerda e direita (e alternativamente as teclas A e D) fariam esse papel.

**US16** - "Como leitor, quero poder marcar a página onde eu parei para que eu não tenha que procurá-la manualmente quando abrir novamente o livro depois de fechá-lo."

**Critérios de Aceitação**:
- Na aplicação mobile, o leitor poderá deslizar a tela para baixo e para cima no canto superior direito da interface para colocar e retirar o marcador de página, respectivamente. Na aplicação web, ele poderá clicar no canto superior direito para fazer isso.

## ⭐ Épico - Avaliação de Livros
> [!NOTE] Nota temporária (Apagar após o diagrama de componentes)
> Devido à alta carga de I/O da funcionalidade, essa feature poderia ser implementada dentro de um microsserviço em uma linguagem performática como Go.

**US17** - "Como leitor, quero poder avaliar os livros lidos em um sistema de 5 estrelas e dar meu feedback para o autor/editora."

**Critérios de Aceitação**:
- O leitor poderá avaliar o livro em uma seção "Avaliar", dando uma nota de 1 à 5 estrelas e deixando um comentário.
- Leitores podem comentar nas avaliações de outros leitores, porém as respostas do autor/editora, caso existam, estarão sempre em destaque no topo da seção de comentários da avaliação.

**US18** - "Como autor/editora, quero que as avaliações do meu livro sejam combinadas em uma média que será exibida junto com as informações gerais do livro."

**Critérios de Aceitação**:
- Será calculada uma média à partir das avaliações dos leitores, que será registrada como a média de avaliações do livro. Este dado então será usado para definir a prioridade do livro em pesquisas dos leitores, e vai passar a integrar o dashboard de autor/editora.

## 📚 Épico - Organização de Livros

**US19** - "Como leitor, quero que os livros que eu interagi sejam categorizados de forma diferente dentro da minha biblioteca para poder gerenciá-los de forma mais fácil e melhorar a experiência de navegação no sistema."

**Critérios de Aceitação**:
- Ao interagir com um livro, seja comprando, pegando emprestado, avaliando ou comentando, esse livro será exibido de forma diferente na biblioteca do leitor.
    - Livros que forem comprados pelo leitor irão para uma seção "Meus livros" dentro de "Minha Biblioteca"
    - Livros que estiverem dentro de um empréstimo ativo serão colocados nessa seção até o empréstimo acabar.
    - Livros que receberam uma avaliação do leitor serão colocados na seção "Minhas Avaliações"
    - Livros que não foram adquiridos, não foram avaliados nem estão em um empréstimo ativo não estarão na biblioteca. Caso o livro seja parte de um empréstimo que expirou, ele será registrado no histórico de empréstimos.

**US20** - "Como leitor, quero poder organizar os meus livros em pastas da forma que eu desejar."

**Critérios de Aceitação**:
- O leitor pode criar *Estantes* (pastas) para livros. Qualquer livro pode ser adicionado à qualquer estante, sem restrições.
- Essas pastas podem ser divididas em subpastas para uma camada extra de organização. Ao fazer isso, a estante se torna um *Acervo*, com as subpastas recebendo o nome de *Estantes* agora.

**US21** - "Como leitor, quero poder visualizar e interagir com estantes de outros leitores, tal como deixar as minhas disponíveis para outros leitores fazerem o mesmo."

**Critérios de Aceitação**:
- O leitor pode definir sua estante como pública ou privada. Estantes públicas podem ser acessadas e salvas por outros leitores através da seção "Estantes" no feed de livros da aplicação. Estantes privadas só podem ser acessadas por quem as criou.

**US22** - "Como Autor/Editora, quero poder criar minhas próprias estantes com meus livros, para que os leitores acessem através da seção 'Estantes' do feed de livros ou pela minha biblioteca de autor/editora."

**Critérios de Aceitação**:
- O autor/editora pode adicionar seus livros à estantes assim como o leitor, porém todas as estantes criadas por autores/editores são necessariamente públicas, não sendo possível a criação de estantes privadas.

## 🔹 Épico - Sistema de XP

## 🪙 Épico - Sistema de Moedas

## 🛍️ Épico - Loja e Cupons

## 📋 Épico - Dashboard de Autores e Editoras



