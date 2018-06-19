Moviecine
O Moviecine será um novo canal de filmes na Globosat e para o lançamento gostaríamos de disponibilizar o catálogo de filmes do canal para usuário navegar. Após planejamento, definimos que deverá ser desenvolvida uma aplicação em Python ou Ruby atendendo a seguinte especificação:

Requisitos
A aplicação deve disponibilizar um site para os visitantes acessarem, ou seja, exibir o catálogo via browser.
A aplicação deve disponibilizar uma API REST que será usada para implementar os apps mobile.
A aplicação deve disponibilizar uma área administrativa acessível em /admin para que a equipe do canal possa atualizar os dados dos Filmes.
Cada Filme possui:
Título
Título Original
Slug (pode ser usado em alguns momentos na URL do acesso via browser)
Sinopse
Duração (em segundos)
Imagem (imagem do poster do filme)
Likes (número de likes realizados por visitantes)
Publicado (filme está disponível ou não)
Lista de atores
Funcionalidade esperadas (no site e no acesso via API)
Listar os filmes oferecendo as opções:
listar somente os filmes publicados
Permitir o usuário ordenar a listagem por nome do filme ou número de likes (ordem decrescente)
Permitir acesso aos dados de um filme por slug ou identificador;
Por exemplo, para acessar o Filme "Duro de Matar" você pode acessar a URL /filmes/duro-de-matar ou /filmes/1234 onde '1234' é o identificador do Filme e 'duro-de-matar' é o slug.
Permitir incrementar o contador de likes de um filme, usando como chave o slug ou identificador do filme.
Informações extras
Você pode utilizar qualquer biblioteca/dependência que achar conveniente.
Os dados de filmes não são atualizados com muita frequência.
Teremos muitos acessos na API e no Site.
A área administrativa deve ser acessada mediante atenticação.
Temos um catálogo enorme de filmes, portanto fique atento ao tamanho das listagens.
O código deve ser disponibilizado no github.
Instalação e execução
É necessário ter Python 3+ instalado. É conveniente criar um ambiente virtual para a execução do projeto. Informações detalhadas sobre a criação e ativação de ambientes virtuais podem ser encontradas em https://virtualenv.pypa.io/en/stable/.

Instale as dependências do projeto executanto pip install -r requirements.txt. Para iniciar o projeto, execute o comando python manage.py runserver no diretório raiz do mesmo e a aplicação será executada em http://127.0.0.1:8000/.

Informações sobre os endpoints da api podem ser encontrados em http://127.0.0.1:8000/api/.

Para acessar a área administrativa, vá para http://127.0.0.1:8000/admin e autentique-se com as credenciais abaixo.

username: admin
password: moviecine
