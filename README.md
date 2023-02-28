# MeuJulius

Uma API para sistemas de controle de gastos pessoais.

## Endpoints

- Despesas
    - [cadsatrar](#cadastrar-despesas)
    - apagar
    - listar todas
    - alterar
    - [mostrar detalhes](#detalhes-das-despesas)
- Contas
    - cadsatrar
    - apagar
    - listar todas
    - alterar
    - mostrar detalhes
---

### Cadastrar despesas

`POST` /meujulius/api/despesa

**Campos da requisição**

|     campo    |   tipo  | obrigatório |               descrição
|--------------|---------|-------------|---------------------------------------
| valor        | decimal |     sim     | o valor da despesa deve ser maior que 0
| data         |   data  |     sim     | a data da despesa
| conta_id     |   int   |     sim     | o id da conta previamente cadastrada
| categoria_id |   int   |     sim     | o id de um acategoria  previamente cadastrada
| descricao    |  texto  |     não     | um texto sobre despesas

**Exemplo de corpo  de requisição**

```js
{
    valor: 100,00
    data:  '2023-02-27',
    conta_id: 1,
    categoria_id: 1,
    descricao: "cinema - homem aranha"
}
```

**Respostas**

| código | descrição
|--------|----------
|  201   | despesa cadastrada com sucesso
|  400   | campos inválidos

----------

### Detalhes das despesas

`GET` /meujulius/api/despesas/{id}

**Exemplo de respostas**

```js
{
    valor: 100,00
    data:  '2023-02-27',
    conta {
        conta_id: 1,
        nome: "itaú"
    }
    categoria {
        categoria_id: 1,
        nome: "lazer"
    }
    conta_id: 1,
    categoria_id: 1,
    descricao: "cinema - homem aranha"
}
```

**Código de Respostas**

| código | descrição
|--------|----------
|  200   | dados das despesas retornados
|  404   | não existe despesas com o id informado


