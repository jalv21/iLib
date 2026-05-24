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
- O leitor irá clicar no botão "Pegar emprestado" no card do livro que deseja, e o livro será adicionado na sua tela "Minha Estante" com um contador regressivo em cima da capa, indicando quanto falta para o fim do empréstimo. O tempo padrão do empréstimo é definido pelo Autor/Editora no cadastro do livro, mas pode aumentar se o leitor aplicar **cupons especiais** comprados com **moedas do sistema** na **loja** (funcionalidades que serão detalhadas mais à frente no documento.)
- Um leitor só pode pegar **um** livro emprestado por vez por padrão, mas ele pode aplicar **cupons da loja** para adicionar outro livro ao empréstimo.
- Após o fim do prazo, o livro será automaticamente removido da sua estante e uma **notificação** será criada na **página de notificações** informando a expiração do empréstimo. Caso o leitor queira voltar a lê-lo, deverá **comprá-lo de forma vitalícia** ou **esperar o mesmo tempo do seu empréstimo** (excetuando tempo extra de cupons) para solicitar um novo.

## 🔖 Épico - Leitura de Livros

## ⭐ Épico - Avaliação de Livros

## 📚 Épico - Organização de Livros

## 🏅 Épico - Sistema de XP

## 📋 Épico - Dashboard de Autores e Editoras



