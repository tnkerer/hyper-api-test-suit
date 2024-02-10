# Suite de testes API Hyperverse

## 1️⃣ Importando Endpoints

Para importar os endpoints, basta baixar o arquivo `Hyperverse Auth.postman_collection.json` deste repositório e importar para o Postman:

![image](https://github.com/tnkerer/hyper-api-test-suit/assets/78161484/b69c09a9-7892-44f6-b400-82ff4c7302a1)

## 2️⃣ Criando uma conta

Para criar uma nova conta na API, basta usar o endpoint `https://hyperverse-api-sfhnrqb7ba-uc.a.run.app/users/register` usando o método `POST` preenchendo o corpo do método `BODY` da seguinte forma:

```json
{
    "name": "Seu Nome",
    "email": "seuemail@gmail.com",
    "password": "sua_senha"
}
```

E clicar em `SEND`. A resposta será um objeto **JSON** com o conteúdo da nova conta criada na base de dados. Exemplo:

```json
{
    "id": "3f8cd507-559c-4222-bd2f-4cf2524e4567",
    "name": "Seu Nome",
    "email": "seuemail@gmail.com",
    "roles": [
        "USER"
    ],
    "balance": 0,
    "recoveryToken": null,
    "referralCode": "70d35fca477987e3",
    "maxStakedTime": 0,
    "AirdropValue": 0
}
```
![image](https://github.com/tnkerer/hyper-api-test-suit/assets/78161484/26e844f6-f495-4cc6-b507-bf5c6559e164)

## 3️⃣ Buscando informações de unsuário da base de dados

As informações criadas no passo 2️⃣ podem ser acessadas a qualquer momento usando o endpoint `https://hyperverse-api-sfhnrqb7ba-uc.a.run.app/users/info` com o método `GET`. Mas para isso, é importante primeiro estar autenticado na API através do endpoint de LOGIN: `https://hyperverse-api-sfhnrqb7ba-uc.a.run.app/login`

Vamos fazer um teste simples de duas etapas, onde vamos primeiro LOGAR e em seguida BUSCAR AS INFORMAÇÕES DE USUÁRIO:

### - Logando:

No endpoint `https://hyperverse-api-sfhnrqb7ba-uc.a.run.app/login` vamos preencher o corpo da chamada de API com a informação de usuário criada:

```json
{
    "email": "seuemail@gmail.com",
    "password": "sua_senha"
}
```
Um acesso feito com sucesso vai retornar um token único do tipo JWT, que vai ser automaticamente salvo para as próximas chamadas da API neste ambiente de testes:

```json
{
    "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIzZjhjZDUwNy01NTljLTQyMjItYmQyZi00Y2YyNTI0ZTQ1NjciLCJlbWFpbCI6InNldWVtYWlsQGdtYWlsLmNvbSIsIm5hbWUiOiJTZXUgTm9tZSIsInJvbGVzIjpbIlVTRVIiXSwiaWF0IjoxNzA3NjA2MzY2LCJleHAiOjE3MDc2OTI3NjZ9.CBLX2l1LHSqRrYlaTB2bAHWl9u16B9LG4woWv67wpio"
}
```

![image](https://github.com/tnkerer/hyper-api-test-suit/assets/78161484/df304944-0126-4961-abbc-363e721a71e4)

### - Buscando informações de usuário:

Se na etapa anterior, a API retornou um token de acesso com sucesso. Agora podemos avançar para o endpoint `https://hyperverse-api-sfhnrqb7ba-uc.a.run.app/users/info`. Essa chamada não precisa de conteúdo, simplesmente clicamos em `SEND` e o resultado deve ser as informações do usuário:

```json
{
    "id": "3f8cd507-559c-4222-bd2f-4cf2524e4567",
    "name": "Seu Nome",
    "email": "seuemail@gmail.com",
    "roles": [
        "USER"
    ],
    "balance": 0,
    "ewallet": "GE7ZptHCnCp4gqZMeHd1Vi3kBqyT7ntg57tJ9iPNeuuy",
    "recoveryToken": null,
    "referralCode": "70d35fca477987e3",
    "maxStakedTime": 0,
    "AirdropValue": 0
}
```
![image](https://github.com/tnkerer/hyper-api-test-suit/assets/78161484/38dc5a49-07e3-4ae3-a953-702463567c9d)

