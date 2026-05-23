# 📗 iLib - Histórias de Usuário

### 👨‍💻 Épico: Cadastro de Usuários
**US01** - "Como leitor, quero poder me cadastrar na aplicação para que eu possa ler livros."

**Critérios de Aceitação**
 - O leitor utilizará o formulário de cadastro padrão para se registrar em uma conta padrão de leitor, preenchendo os dados de **Nome**, **Username** único no formato **`@username`**, **Email** e **Senha**.

**US02** - "Como autor ou editora de um livro, quero me cadastrar na aplicação para que eu possa cadastrar meus livros para serem lidos por leitores."

**Critérios de Aceitação**
- O autor ou editora utilizará o formulário especial indicado em uma seção "Publique seu livro no iLib" na página inicial da aplicação, preenchendo os mesmos dados, porém com a adição de um **CPF** ou **CNPJ** para confirmar a sua legitimidade.

**US03** - "Como usuário, quero poder fazer login na aplicação após realizar o meu cadastro."

**Critérios de Aceitação**
- Após o cadastro do usuário, ele deve ser automaticamente redirecionado para sua página inicial dentro da aplicação uma vez autenticado (para usuários, o **catálogo de livros do sistema**, para autores/editoras, o ***Dashboard* de autor/editora**.)
<br/>

- Caso o login seja feito após o término da primeira sessão do usuário no sistema feita logo após o cadastro, ele deverá preencher o formulário de login com  seu **Email** ou **Username**, e sua **Senha**. O formulário de login é igual para todos os usuários.