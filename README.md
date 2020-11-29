## Sobre o desafio

Nesse desafio, você deve criar uma aplicação para treinar o que você aprendeu até agora no Node.js!

Essa será uma aplicação para armazenar repositórios do seu portfólio, que irá permitir a criação, listagem, atualização e remoção<br> dos repositórios, e além disso permitir que os repositórios possam receber "likes".

## Template da aplicação

Para te ajudar nesse desafio, criamos para você um modelo que você deve utilizar como um template do Github.

O template está disponível na seguinte url: <b>[Acessar Template](https://github.com/rocketseat-education/gostack-template-conceitos-nodejs)</b>

## Rotas da aplicação

`POST /repositories:` A rota deve receber title, url e techs dentro do corpo da requisição, sendo a URL o link para o github desse repositório.<br>Ao cadastrar um novo projeto, ele deve ser armazenado dentro de um objeto no seguinte formato:
{ id: "uuid", title: 'Desafio Node.js', url: 'http://github.com/...', techs: ["Node.js", "..."], likes: 0 };
<br>Certifique-se que o ID seja um UUID, e de sempre iniciar os likes como 0.

`GET /repositories:` Rota que lista todos os repositórios;

`PUT /repositories/:id:` A rota deve alterar apenas o title, a url e as techs do repositório que possua o id igual ao id presente nos parâmetros da rota;

`DELETE /repositories/:id:` A rota deve deletar o repositório com o id presente nos parâmetros da rota;

`POST /repositories/:id/like:` A rota deve aumentar o número de likes do repositório específico escolhido através do id presente nos parâmetros da rota,<br> a cada chamada dessa rota, o número de likes deve ser aumentado em 1;

`Dica:` Acima utilizamos POST em uma rota, mesmo ela alterando o número de likes do repositório sem criar nada diretamente.

Se dividirmos semânticamente as responsabilidades da nossa aplicação em entidades, o like seria uma entidade, e repository seria outra entidade.

Com essa separação, temos diferentes regras de negócio para cada entidade, assim, ao chamar a rota de like e adicionamos apenas um like, podemos interpretar <br>que estamos criando um novo like, e não atualizando os likes.

Então por que não usar PUT no lugar de POST? Justamente por estarmos "criando" UM novo like, e não atualizando o número de likes para qualquer outro valor.

## Específicação dos testes

Em cada teste, tem uma breve descrição no que sua aplicação deve cumprir para que o teste passe.

Para esse desafio temos os seguintes testes:

- <b>should be able to create a new repository:</b> Para que esse teste passe, sua aplicação deve permitir que um repositório seja criado, <br>e retorne um json com o projeto criado.

- <b>should be able to list the repositories:</b> Para que esse teste passe, sua aplicação deve permitir que seja retornado um array com todos os repositórios <br>que foram criados até o momento.

- <b>should be able to update repository:</b> Para que esse teste passe, sua aplicação deve permitir<br>que sejam alterados apenas os campos url, title e techs.

- <b>should not be able to update a repository that does not exist:</b> Para que esse teste passe, você deve validar na sua rota de update se o id do repositório enviado <br>pela url existe ou não. Caso não exista, retornar um erro com status 400.

- <b>should not be able to update repository likes manually:</b> Para que esse teste passe, você não deve permitir que sua rota de update altere diretamente os likes desse repositório,<br> mantendo o mesmo número de likes que o repositório já possuia antes da atualização. Isso porque o único lugar que deve atualizar essa informação <br>é a rota responsável por aumentar o número de likes.

- <b>should be able to delete the repository:</b> Para que esse teste passe, você deve permitir que a sua rota de delete exclua um projeto, e ao fazer a exclusão, <br>ele retorne uma resposta vazia, com status 204.

- <b>should not be able to delete a repository that does not exist:</b> Para que esse teste passe, você deve validar na sua rota de delete se o id do repositório enviado pela url existe ou não.<br> Caso não exista, retornar um erro com status 400.

- <b>should be able to give a like to the repository:</b> Para que esse teste passe, sua aplicação deve permitir que um repositório com o id informado possa receber likes.<br> O valor de likes deve ser incrementado em 1 a cada requisição, e como resultado, retornar um json contendo o repositório com o número de likes atualizado.

- <b>should not be able to like a repository that does not exist:</b> Para que esse teste passe, você deve validar na sua rota de like se o id do repositório enviado pela url existe ou não.<br> Caso não exista, retornar um erro com status 400.
