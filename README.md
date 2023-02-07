#### Rest API Votos

<h2>Descrição da implementação</h2>
<p> Foi utilizado as separações dos domínios de Associados, Pauta, Sessão e Votos. Assim, poderá trabalhar independentemente </p>
<p> No caso, foi utilizado constraints para não repetir votos na mesma pauta para cada associado </p>
<p> Para isso, precisa criar um associado, uma pauta, uma sessão e, posteriormente votar. Ao fim das votações, precisa utilizar o /processes
para apurar os votos </p>
<p> Foi utilizado um Json na variável results da Sessão para que, se tiver mais tipos de votos como abstenção, nulo, será automatizamente inserida 
pela lógica da aplicação, só adicionar os votos no ENUM</p>
<p> Para contabilização da solução não perder os votos, foi utilizada as persistências </p>

<h2>O que foi utilizado:</h2>

<ul>Java 17</ul>
<ul>Spring Boot 3</ul>
<ul>Lombok</ul>
<ul>Mockito</ul>
<ul>Junit</ul>
<ul>Maven</ul>
<ul>JPA + Hibernate</ul>
<ul>MySQL</ul>
<ul>RabbitMQ</ul>

<h2>Rodando o Projeto</h2>

<p>O projeto está configurando com o tomcat embarcado. Não precisa necessidade de ter tomcat instalado. Somente o Java.</p>
<p>Na raiz do projeto, execute o comando ./mnvw clean package install. Isso irá gerar um build do projeto na pasta target</p>
<p>Depois, para iniciar o projeto, dentro da pasta target, utilize o comando: "java -jar assembliescorp-0.0.1-SNAPSHOT.jar"

<h5> Criar database </h5>
<p>Neste caso, vai precisar do MySql e RabbitMq Instalado e, caso precise, aponte variáveis de acordo com o aplication.yml</p>
<p> No caso, precisa criar uma base de dados no mysql do nome 'assembly' para poder usar o projeto </p>
<p> Poderá usar o Adminer http://localhost:9998/ para isto </p>

<h4> Docker Compose </h4>
<p>Com o docker instalado na máquina, execute o comando dentro da pasta do projeto:<p>
<p>utilize o docker-compose.yaml após gerar o pacote java. O apontamento do JAR está no ./target</p>


<p>A Base da API está na porta 8080</p>

http://localhost:8090/

<h2>Swagger - Documentação</h2>

<p>Documentação do swagger http://localhost:8080/swagger-ui/index.html</p>


---

# Desafio Técnico
## Objetivo
No cooperativismo, cada associado possui um voto e as decisões são tomadas em assembleias, por votação. A partir disso, você precisa criar uma solução back-end para gerenciar essas sessões de votação. Essa solução deve ser executada na nuvem e promover as seguintes funcionalidades através de uma API REST:
- Cadastrar uma nova pauta;
- Abrir uma sessão de votação em uma pauta (a sessão de votação deve ficar aberta por um tempo determinado na chamada de abertura ou 1 minuto por default);
- Receber votos dos associados em pautas (os votos são apenas 'Sim'/'Não'. Cada associado é identificado por um id único e pode votar apenas uma vez por pauta);
- Contabilizar os votos e dar o resultado da votação na pauta.

Para fins de exercício, a segurança das interfaces pode ser abstraída e qualquer chamada para as interfaces pode ser considerada como autorizada. A escolha da linguagem, frameworks e bibliotecas é livre (desde que não infrinja direitos de uso).

É importante que as pautas e os votos sejam persistidos e que não sejam perdidos com o restart da aplicação.

O foco dessa avaliação é a comunicação entre o backend e o aplicativo mobile. Essa comunicação é feita através de mensagens no formato JSON, onde essas mensagens serão interpretadas pelo cliente para montar as telas onde o usuário vai interagir com o sistema. A aplicação cliente não faz parte da avaliação, apenas os componentes do servidor. 
