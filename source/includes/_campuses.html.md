# Campi

## Listar campi

> Exemplo de requisição

```shell
curl "https://stock.querobolsa.com.br/api/universities/65605bf0-cad2-4dc2-ae11-65c77bc36508/campuses" \
  -H 'Authorization: Bearer ##########' \
  -H 'Content-Type: application/json'
```

> Exemplo de retorno JSON para esta requisição

```json
{
  "has_more": false,
  "items": [
    {
      "id": "00d9ef5a-d003-4212-99ff-c4308f18803d",
      "university": {
        "id": "65605bf0-cad2-4dc2-ae11-65c77bc36508",
        "name": "UniQuero",
      },
      "name": "Caxias",
      "address": "Rua Araão Reis, 1789, Bloco 1",
      "neighborhood": "Centro",
      "city": "Caxias",
      "state": "MA",
      "zip_code": "65604-060",
      "phone": "(00) 00000000",
      "latitude": -23.198976,
      "longitude": -45.901692
    },
    {
      "id": "9d49f7f8-5994-40ae-a8fa-b9c9d66adef8",
      "university": {
        "id": "65605bf0-cad2-4dc2-ae11-65c77bc36508",
        "name": "UniQuero",
      },
      "name": "Sorocaba",
      "address": "Av. Independência, 210",
      "neighborhood": "Éden",
      "city": "Sorocaba",
      "state": "SP",
      "zip_code": "18087-101",
      "phone": "(00) 00000000",
      "latitude": -23.198976,
      "longitude": -45.901692
    }
  ]
}
```

Lista os campus de uma dada faculdade. Apenas faculdades associadas ao usuário podem ser solicitadas. Em outros casos, a API retorna `404 - Not Found`.

Campi são retornados em páginas de até 1000 elementos, ordenadas pela última criação realizada. Se houver mais resultados, `has_more` retorna `true` indicando que é possível usar o parâmetro `ending_before` para consultar objetos antecessores à lista atual. Para mais informações, consulte a [seção de paginação](#paginacao).

### Requisição HTTP

`GET https://stock.querobolsa.com.br/api/universities/<UNIVERSITY_ID>/campuses`

### Parâmetros da requisição

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| UNIVERSITY_ID | path | ID da universidade onde deseja realizar a ação |

### Parâmetros da resposta

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| has_more | boolean | Indica se há mais elementos disponíveis antes ou após essa página |
| items | object array | Arranjo de objetos com dados de campus |
| id | string | Código identificador de campus |
| university | object | Objeto com dados de universidade |
| [university] id | string | Código identificador de universidade |
| [university] name | string | Nome da universidade |
| name | string | Nome do campus |
| address | string | Endereço do campus |
| neighborhood | string | Bairro do campus |
| city | string | Cidade do campus |
| state | string | Estado do campus |
| zip_code | string | Código CEP do campus |
| phone | string | Telefone do campus |
| latitude | float | Coordenada de latitude do campus |
| longitude | float | Coordenada de longitude do campus |

## Informações de um campus específico

> Exemplo de requisição

```shell
curl "https://stock.querobolsa.com.br/api/universities/65605bf0-cad2-4dc2-ae11-65c77bc36508/campuses/00d9ef5a-d003-4212-99ff-c4308f18803d" \
  -H 'Authorization: Bearer ##########' \
  -H 'Content-Type: application/json'
```

> Exemplo de retorno JSON para esta requisição

```json
{
  "id": "00d9ef5a-d003-4212-99ff-c4308f18803d",
  "university": {
    "id": "65605bf0-cad2-4dc2-ae11-65c77bc36508",
    "name": "UniQuero",
  },
  "name": "Caxias",
  "address": "Rua Araão Reis, 1789, Bloco 1",
  "neighborhood": "Centro",
  "city": "Caxias",
  "state": "MA",
  "zip_code": "65604-060",
  "phone": "(00) 00000000",
  "latitude": -23.198976,
  "longitude": -45.901692
}
```

Retorna informações de um campus específico.

### Requisição HTTP

`GET https://stock.querobolsa.com.br/api/universities/<UNIVERSITY_ID>/campuses/<CAMPUS_ID>`

### Parâmetros da requisição

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| UNIVERSITY_ID | path | ID da universidade onde deseja realizar a ação |
| CAMPUS_ID | path | ID do campus que deseja resgatar informações |

### Parâmetros da resposta

| Nome | Tipo | Descrição
| ---- | ---- | --------- |
| id | string | Código identificador de campus |
| name | string | Nome do campus |
| university | object | Objeto com dados de universidade |
| [university] id | string | Código identificador de universidade |
| [university] name | string | Nome da universidade |
| address | string | Endereço do campus |
| neighborhood | string | Bairro do campus |
| city | string | Cidade do campus |
| state | string | Estado do campus |
| zip_code | string | Código CEP do campus |
| phone | string | Telefone do campus |
| latitude | float | Coordenada de latitude do campus |
| longitude | float | Coordenada de longitude do campus |

## Inserir campi

> Exemplo de requisição

```shell
curl -X POST "https://stock.querobolsa.com.br/api/universities/65605bf0-cad2-4dc2-ae11-65c77bc36508/campuses" \
  -H 'Authorization: Bearer ##########' \
  -H 'Content-Type: application/json' \
  -d @campus_data.json
```

> Exemplo da estrutura JSON esperada:

```json
{
  "campuses": [
    {
      "name": "Caxias",
      "address": "Rua Araão Reis, 1789, Bloco 1",
      "neighborhood": "Centro",
      "city": "Caxias",
      "state": "MA",
      "zip_code": "65604-060",
      "phone": "(00) 00000000",
      "latitude": -23.198976,
      "longitude": -45.901692
    },
    {
      "name": "Sorocaba",
      "address": "Av. Independência, 210",
      "neighborhood": "Éden",
      "city": "Sorocaba",
      "state": "SP",
      "zip_code": "18087-101",
      "phone": "(00) 00000000",
      "latitude": -23.198976,
      "longitude": -45.901692
    }
  ]
}
```

> Resposta

```
Status Code: 200 OK
```

```json
{
  "error": false,
  "operation_id": "4e8c23c3-fab1-486d-9c0e-c49301305d94"
}
```

Esse endpoint cria campus em lote com informações enviadas em JSON.

Na inserção de campus, caso o ID seja enviado, o serviço irá fazer uma operação de **atualização** de informação, sobrescrevendo os dados enviando no modelo do banco.

Caso o ID do campus não seja enviado, uma **validação** com a base de dados será feita, a fim de evitar campi duplicados na nossa base.

### Requisição HTTP

`POST https://stock.querobolsa.com.br/api/universities/<UNIVERSITY_ID>/campuses/`

### Parâmetros da requisição

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| UNIVERSITY_ID | path | ID da universidade onde deseja realizar a ação |

<aside class="notice">
  A resposta da requisição retorna o <code>operation_id</code>, que pode ser utilizado para obter os detalhes da operação, como o progresso.

  Para mais informações, acesse a <a href="#operacoes-de-estoque">documentação de operações de estoque</a>.
</aside>

### Parâmetros da requisição

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| campuses | object array | Arranjo de objetos com dados de campus |
| [campuses] name | string | Nome do campus |
| [campuses] address | string | Endereço do campus |
| [campuses] neighborhood | string | Bairro do campus |
| [campuses] city | string | Cidade do campus |
| [campuses] state | string | Estado do campus |
| [campuses] zip_code | string | Código CEP do campus |
| [campuses] phone | string | Telefone do campus |
| [campuses] latitude | float | Coordenada de latitude do campus |
| [campuses] longitude | float | Coordenada de longitude do campus |

### Parâmetros da resposta

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| error | boolean | Indicador de ocorrência de erro na operação |
| operation_id | string | ID da operação de estoque criada |
