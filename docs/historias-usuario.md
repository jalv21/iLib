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



