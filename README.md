# teste-frontend
Repositório usado para o teste de front-end do Núcleo de Tecnologia Multimídia.

## O que?
Relatório que, utilizando dados de uma api, mostre a taxa (média) de ex-alunos do SENAI que continuam estudando por estado e também a taxa nacional.


Abaixo existe um link com um mockup que você pode usar de base, fique a vontade para mudá-lo, podendo usar grafico ao inves de tabelas ou como quiser, iremos levar isso consideração na hora de avaliar.

Para baixar o mockup, [clique aqui](https://github.com/SENAI-NTM/teste-frontend/blob/master/mockup.png).

## Como?
1. Consulta a API/JSON.
2. Pegar resultado e exibir para o usuário de forma usual.

## Público alvo do relatório
Gestores e coordenadores de Educação do SENAI.

## Dados de entrada
1. Consulta a api do teste anterior ou arquivo JSON a seguir, ambos na mesma estrutura abaixo:
```json
{
  "regionals": [
    {"description": "AC", "average": 23.30},
    {"description": "AL", "average": 61.00},
    {"description": "AP", "average": 30.10},
    {"description": "AM", "average": 56.30},
    ...
  ],
  "national": 47.50
}
```
Faça download clicando [aqui](https://github.com/SENAI-NTM/teste-backend/blob/master/data.json).

## Instruções?
1. Você está livre para escolher (ou não) qualquer framework/lib front-end.
2. Adicione a esse README, instruções de como executar a sua solução.
3. Você pode subir o seu código front-end através de um fork desse repositório github ou enviar por tudo email. Lembrando que temos preferência pelo o uso do github e iremos levar isso consideração na hora de avaliar.
4. Você tem uma semana (7 dias) para a finalização do teste, a partir da data de envio do e-mail.
5. Se não conseguir finalizar os testes, não se preocupe, envie a sua solução no estágio de desenvolvimento que estiver.

## Instruções antes da instalação
Antes de rodar o projeto, suba o servidor da API, voce pode fazê-lo das seguintes formas:
1. Colocando na pasta padrão (localhost);
2. Subindo com o servidor do CakePHP (na pasta "api" do projeto, execute o comando "bin/cake server" e a api estará disponível em localhost:8765).
Se subir o servidor com a última opção, lembre-se de dar permissão 777 para as pastas "tmp" e "log" ("sudo chmod -R 777 tmp logs").

## Instruções de instalação
1. Entre na pasta "app" do projeto.
2. Suba o servidor de desenvolvimento com o comando "SERVER_BASE=raiz_da_api quasar dev"
3. O projeto estará rodando em "localhost:8080"

OBS: em "raiz_da_api" colocar o caminho da raiz da api, seja ele "localhost:8765" ou "localhost/teste-backend/api".
