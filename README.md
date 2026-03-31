# CASE: Sistema Automob

O projeto consiste em desenvolver um sistema que possui entrada e saída de dados (I/O) e persistência em banco de dados, também conhecido por CRUD (**C**reate, **R**ead, **U**pdate, **D**elete).

Vamos nos concentrar em um sistema para cadastro de carros, começando pelas **marcas** e **modelos de veículos**.

## Estruturação do projeto:

#### Back-end (API):

- Utilizar Javascript (nodejs);
- Para banco de dados, utilizar MariaDB/MySQL ou SQLServer (versão developer ou express);

> **Requisitos:**
> 
> Rota para criação de uma marca: ```POST /api/v1/marca```
> ```SQL
> {
>    nome: varchar(100) NOT NULL,
>    pais: varchar(70) NOT NULL,
>    foto: varchar(255) NULL DEFAULT(NULL),
>    ano_criacao_marca: tinyint NOT NULL,
>    ativo: boolean NOT NULL DEFAULT(1)
> }
> ```
> 
> Rota para atualizar uma marca pelo ID: ```PUT /api/v1/marca/{id}```
> ```SQL
> {
>    nome: varchar(100),
>    pais: varchar(70),
>    foto: varchar(255),
>    ano_criacao_marca: tinyint,
>    ativo: boolean
> }
> ```
> 
> Rota para deletar uma marca pelo ID: ```DELETE /api/v1/marca/{id}```
>
> 
> Rota para listar todas as marcas ativas no sistema: ```GET /api/v1/marca```
>
>
> Rota para filtrar as marcas pelo seu nome: ```GET /api/v1/marca?nome={nome}```
>
> 
> > ----------------------------------------------------------------------
>
> 
> Rota para criação de um modelo: ```POST /api/v1/modelo```
> ```SQL
> {
>    id_marca: int NOT NULL,
>    nome: varchar(100) NOT NULL,
>    ativo: boolean NOT NULL DEFAULT(1)
> }
> ```
> 
> Rota para atualizar um modelo pelo ID: ```PUT /api/v1/modelo/{id-modelo}```
> ```SQL
> {
>    id_marca: int,
>    nome: varchar(100),
>    ativo: boolean
> }
> ```
> 
> Rota para deletar um modelo pelo ID: ```DELETE /api/v1/modelo/{id-modelo}```
> 
>
> Rota para listar todos os modelos: ```GET /api/v1/modelo```
> 
>
> Rota para filtrar os modelos pelo nome e/ou pela marca: ```GET /api/v1/modelo?nome={nome-modelo}&marca={nome-marca}```
>

-------------------------------

#### Banco de dados:

Utilize os corpos de requisição descritos no corpo/payload descritos nas rotas de criação (POST), logo acima.


--------------------------------
#### Front-end:

- **Na tela principal:** O usuário poderá visualizar os veículos de acordo com a marca e modelo filtrado, como se fosse um marketplace. Caso o usuário não aplique filtro, exibir mensagem "Aplique o filtro para visualizar os resultados";
- **Na tela principal:** Em uma parte superior do site, deve existir um botão para "Criação de marca" e outro para "Criação de modelo". Ao clicar nos botões de "Criação", a página web deve mostrar ambos os formulários para preenchimento, além do botão de "Salvar";
- **Na tela principal:** Ao clicar no veículo, deve ser possível visualizar o perfil do veículo, com todos os detalhes. Na tela de perfil, deverá ter um botão de excluir ou editar (para editar, é possível utilizar o mesmo formulário criado para a funcionalidade de "Criação".

## Fluxo do sistema:

- O usuário irá acessar o site e executar alguma ação, seja visualizar (READ), criar (CREATE), atualizar ou deletar uma marca/modelo (UPDATE ou DELETE);
- De acordo com a ação do usuário, o sistema deve mostrar o formulário com seus devidos campos e botão de "Salvar";
- Ao salvar o formulário, dentro do front-end, devemos fazer uma chamada para a API via **AJAX** ou **FETCH API**, onde devemos informar a rota e o corpo/payload da requisição;

## Dicas:

- Primeiramente, instale e configure o banco de dados;
- Crie as duas tabelas, de **marca** e de **modelo**.
- Comece a criar o back-end e inicie pela rota de CREATE (POST);
- Utilize softwares como Postman ou Insomnia para testar a API (rota POST);
- Entendendo o funcionamento da API, inicie o desenvolvimento do front-end.

## [BÔNUS] Pontos de melhoria para o sistema:

O cadastro de veículos ainda está bem cru, podemos ainda criar colunas de cor, ano, carroceria do veículo, se é 4 ou 2 portas ou se é gasolina, álcool ou flex. Porém, se colocarmos esses campos no banco de dados na tabela de **modelo**, vamos ter um problema de repetição, onde para cada cor ou ano do modelo, teremos que repetir inúmeras vezes o campo **nome** e por ai vai. Esse é um problema conhecido nos bancos de dados relacionais (MySQL, SQL Server...), e temos um estudo para resolver esse problema, que é a **normalização de dados em bancos relacionais**.

***Proposta:*** Para este problema, teremos que criar uma terceira tabela chamada de **modelo_versao**, onde vamos informar o id da tabela **modelo** e os demais atributos que queira colocar no sistema. E claro, será preciso criar rotas no back-end e formulário no front-end para que consigamos salvar esses detalhes no banco de dados.

## URLs importantes:

- Encontrar detalhes e código FIPE dos veículos: https://veiculos.fipe.org.br/
- Outra API pública: https://deividfortuna.github.io/fipe/
- Utilidade para criar o front-end: https://getbootstrap.com/docs/5.0/getting-started/introduction/ ou https://react.dev/
- Site para utilizar ícones no front-end: https://fontawesome.com/
