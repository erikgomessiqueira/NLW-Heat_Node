<p align="center">
  <!--<img alt="Imagem Principal" src=""/> -->
</p>
<h1 align="center">🟩 NLW-Heat_Node 🟩</h1>
 <p align="center">
    <i>Repositório da aplicação disponibilizada no primeiro dia</i>
</p>
<br>

## ℹ Sobre a aplicação
<!--Aqui vai uma decrição breve-->
<p>
  Está aplicação foi desenvolvida durante o evento NLW Heat, ultimo NLW do ano de 2021 feito pela <a href="https://www.rocketseat.com.br/">Rocketseat</a>. Ela foi desenvolvida usando Node.js e a linguagem de programação TypeScript, além delas foram utilizados o Socket.IO para comunicação em tempo real, o Prisma para manipular Banco de dados e varias outras. Seu objetivo é:
</p>
<ul>
  <li>Fazer login com o GitHub</li>
  <li>Solicitar dadso do usuário pelo GitHub como nome, id, imagem e etc...</li>
  <li>Armazenar esses dados em um Banco de Dados</li>
  <li>Gerar um token para autenticar as requisições</li>
  <li>Gerar um token para autenticar as requisições</li>
  <li>Receber e armazenas menssagens eviadas pelo usuário no Banco de Dados</li>
  <li>Exibir essa menssagem na tela em tempo real</li>
  <li>Buscar e exibir as 3 mensagens mais recentes presentes no Banco de Dados</li>
</ul>
<br>

## 📄 Documentação
Primeiro temos que configurar a arquivo .env.example, vamos renomeá-lo para somente .env e abrindo ele encontramos:
```javascript
    GITHUB_CLIENT_SECRET = //Conseguimos no GitHub
    GITHUB_CLIENT_ID = //Conseguimos no GitHub
    JWT_SECRET = // Pode ser qualquer dado
```
 ### Obtendo o GITHUB_CLIENT_SECRET e GITHUB_CLIENT_ID
  Temos que estar logados no GitHub e acessar Settings => Developer Settings => OAuth Apps ou [Clicar Aqui](https://github.com/settings/developers). Nessa aba criaremos a aplicação(**New OAuth App**) e vamos conseguir esses dados.
  
  O GITHUB_CLIENT_ID é o código disponibilizado em **Client ID**.
  
  O GITHUB_CLIENT_SECRET é o código gerado(**Generate a new client secret**) em **Client secrets**. Você deve copiar esse código antes de recarregar a página se não tera que gerar outro código.
  
  ### Obtendo o JWT_SECRET
  Nesse podemos colocar qaulquer coisa, durante o evento foi mostrado que poderia se qualquer coisa, depois de ter decidido esse dado foi criptografado usando o MD5 que gera um código. Eu usei o o site [MD5 Hash Generator](https://www.md5hashgenerator.com/) e usei o MD5 Hash 
  ```
      Erik => MD5 => c4464d724b7dec8c7d5d58e3da24a960 (Uso esse código aqui nos exemplo)
  ```

<br>

## ⚠ Necessário
  - Git
  - Node.js
  - Yarn
  
<br/>

## 🔀 Rotas
<br/>

- **/github** => faz a autenticação e nos da permição atravéz de um código para requisitar os dados no usuário. Retorno => code

  ```javascript
      //Retorno Exemplo
      "c4464d724b7dec8c7d5d58e3da24a960"
  ```
  <br/>
  <br/>
  
- **/authenticate** => faz a requisição dos dados do usuário passando o código obtido com _/github_ no Body.


  ```javascript
      //Body
      {
        "code": "c4464d724b7dec8c7d5d58e3da24a960"
      }
  ```
  
  ```javascript
      //Response
      {
        "token": ,
        "user": {
          "id": ,
          "name": ,
          "github_id": ,
          "avatar_url": ,
          "login": 
        }
      }
  ```
  <br/>
  <br/>
  
- **/messages** => Passando o Token pelo Haeader e a mensagem pelo Body essa rota armazena a menssagem no Banco de Dados.


  ```javascript
      //Body
      {
          "message": "O DoWhile será sensacional"
      }
  ```
  
  ```javascript
      //Response
      {
        "id": ,
        "text": "O DoWhile será sensacional",
        "created_at": ,
        "user_id": ,
        "user": {
          "id": ,
          "name": ,
          "github_id": ,
          "avatar_url": ,
          "login": 
        }
      }
  ```
  <br/>
  <br/>
  
- **/profile** => Passando o Token pelo Haeader ela vai pegar os dados o usuário no Banco de Dados.

  
  ```javascript
      //Response
      {
        "id": ,
        "name": ,
        "github_id": ,
        "avatar_url": ,
        "login": 
      }
  ```
  <br/>
  <br/>
  
- **/messages/last3** => Retorna as 3 ultimas mensagens aramazenadas no Banco de Dados.

  
  ```javascript
      //Response
      [
        {
          "id": ,
          "text": ,
          "created_at": ,
          "user_id": ,
          "user": {
            "id": ,
            "name": ,
            "github_id": ,
            "avatar_url": ,
            "login": 
          }
        },
        {
          "id": ,
          "text": ,
          "created_at": ,
          "user_id": ,
          "user": {
            "id": ,
            "name": ,
            "github_id": ,
            "avatar_url": ,
            "login": 
          }
        },
        {
          "id": ,
          "text": ,
          "created_at": ,
          "user_id": ,
          "user": {
            "id": ,
            "name": ,
            "github_id": ,
            "avatar_url": ,
            "login": 
          }
        }
      ]
  ```
  

<br/>


## ▶❔ Como executar
  ### Clone o repositório
  ```bash
    $ git clone https://github.com/erikgomessiqueira/NLW-Heat_Node.git
  ```
  <br/>
  
  ### Instale as Dependências
  
  Instale com yarn ou npm:
  ```bash
    yarn install
  ```
  <br/>
  
  Crie as tabelas do Banco de Dados
  ```bash
    yarn prisma migrate dev 
  ```
<br>

## ▶ Executando a aplicação
  ```bash
    yarn dev
  ```
  <br/> 
  
  Deve retronar a Porta onde o servidor está sendo executado:
  ```bash
    yarn run v1.22.10
    $ ts-node-dev --exit-child src/server.ts
    [INFO] 22:02:34 ts-node-dev ver. 1.1.8 (using ts-node ver. 9.1.1, typescript ver. 4.4.4)
    🚀 Server is running on PORT 4000
  ```
  
<br>
  
## 😁 Contrubuindo ao projeto

   > [Guia de como contribuir no GitHub](https://github.com/firstcontributions/first-contributions)
