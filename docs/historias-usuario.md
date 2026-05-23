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
- O Autor/Editora clica em um botão "Novo livro" na sua página de "Livros cadastrados", O botão leva o usuário à um formulário de cadastro de livros, onde ele irá inserir os dados básicos de identificação **Título**, **Autor** e **ISBN**, e os dados adicionais **Gênero(s)** (da lista de gêneros do sistema), e uma **autodeclaração de dificuldade do livro**, escolhendo uma opção entre *Fácil*, *Médio* e *Dificíl*. Finalmente, ele irá fazer **upload do arquivo EPUB do livro**.
- Antes da castrar o livro, o Autor/Editora terá que confirmar sua identidade usando sua **Senha**.
- Uma vez cadastrado, a **API de livros** (*Google Books API*, *OpenLibrary API*, etc.) consumida pela aplicação vai retornar os dados completos do livro na sua interface disponível para os leitores com base no ISBN inserido no cadastro.