# Won Games - API

## Instalação

Acesse a pasta `app` e execute:

```
npm install
```

## Problemas comuns

### Em caso de problemas no MAC

Acesse a pasta `app` e execute:

```bash
npm install
```

OBS: com o `yarn` causou alguns problemas após a instalação. É possível que funcione mas sem garantias de sucesso.

Caso esteja usando um Mac, após finalizar o processo de instalação de pacotes, será necessário reinstalar o `sharp` utilizando outra platform da seguinte maneira:

```bash
npm remove sharp && npm install --arch=x64 --platform=linux sharp
```

Obs:

> `ERROR: An HTTP request took too long to complete. Retry with --verbose to obtain debug information. If you encounter this issue regularly because of slow network conditions, consider setting COMPOSE_HTTP_TIMEOUT to a higher value (current value: 60).`

Caso aconteça o erro de slow network muitas vezes, utilize:

```
COMPOSE_HTTP_TIMEOUT=200 docker-compose up
```

### Permissão de arquivos

Na primeira vez que for executado, os arquivos poderão estar no usuário root. Será necessário atualizar as permissões:

```bash
sudo chown -R seuusuario.seuusuario ./
```

<br />

## Iniciando a aplicação:

Na pasta raiz

```
docker-compose up
```

## Admin

- acesse `http://localhost:1337/admin` e crie o seu usuário.

- acesse no menu `Settings > Roles(users & permissions) > public` e dê permissões para as seguintes rotas:

```
	Aba Application
		Banner
			- find

		Category
			- count
			- find
			- findone

		Developer
			- count
			- find
			- findone

		Game
			- count
			- create (desative após popular)
			- find
			- findone
			- populate (desative após uso)

		Home
			- find

		Platform
			- count
			- find
			- findone

		Publisher
			- count
			- find
			- findone

	Aba Upload
		- upload

```

- acesse no menu `Settings > Roles(users & permissions) > Authenticated` e dê permissões para as seguintes rotas:

```
	Aba Application
		ORDER
			- count
			- create
			- createpayment
			- find
			- findone

		WISHLIST
			- count
			- find
			- findone

	Aba Upload
		- upload

```

<br />

## Populando dados

Execute a aplicação e rode o comando no terminal.

```
curl -X POST http://localhost:1337/games/populate
```
