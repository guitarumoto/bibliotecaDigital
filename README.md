# Passo-a-passo para testar o projeto
* Clonar o repositório;
* Configurar banco de dados SQL na porta 3306 com uma database de nome "almoxarifado";
* Rodar o comando ````php artisan migrate```` para criar as tabelas do banco de dados;
* Rodar o comando ````php artisan serve```` para iniciar o servidor;
* Após a finalização do build o projeto estará rodando em ````http://localhost:8000````
#
OBS: Não foi possível realizar o Eager Loading de clientes na listagem de vendas.

#
## Endpoints


 ````POST api/clientes````

 Payload para cadastrar um cliente:

 ````
{
   "nome": "Guilherme",
   "email": "gui@gmail.com",
   "documento": "12345678912"
}
 ````

 Exemplo de resposta:

  ````
{
  "nome": "Guilherme",
  "email": "gui@gmail.com",
  "documento": "12345678912",
  "updated_at": "2021-01-25T21:58:45.000000Z",
  "created_at": "2021-01-25T21:58:45.000000Z",
  "id": 1
}
 ````

 ````POST api/produtos````

 Payload para criar um produto:<br>
 tipo 1 -> Produto Digital<br>
 tipo 2 -> Produto Físico

 ````
{
   "tipo": 1,
   "nome": "Livro digital",
   "descricao": "How SOLID works",
   "valor": 70.0, 
   "link": "livros.com/designpatterns"
}
 ````

 Exemplo de resposta:

  ````
{
  "tipo": 1,
  "nome": "Livro digital",
  "descricao": "How SOLID works",
  "valor": 70,
  "link": "livros.com\/designpatterns",
  "updated_at": "2021-01-25T23:28:24.000000Z",
  "created_at": "2021-01-25T23:28:24.000000Z",
  "id": 1
}
 ````
 
 ````GET api/produtos````

 Retorna a lista de produtos cadastrados:

 Exemplo de resposta:

  ````
 [
  {
    "id": 1,
    "nome": "Livro digital",
    "descricao": "How SOLID works",
    "tipo": 1,
    "valor": 70,
    "link": "livros.com\/designpatterns",
    "created_at": "2021-01-25T23:30:42.000000Z",
    "updated_at": "2021-01-25T23:30:42.000000Z"
  },
  {
    "id": 2,
    "nome": "Café",
    "descricao": "Mellita",
    "tipo": 0,
    "valor": 15,
    "link": null,
    "created_at": "2021-01-25T23:31:53.000000Z",
    "updated_at": "2021-01-25T23:31:53.000000Z"
  }
]
 ````

 ````PUT api/produtos/{id}````

 Inserir o id do produto a ser alterado no final lugar de {id}

 Payload para editar um produto:

 ````
{
   "tipo": 0,
   "nome": "Coca-cola",
   "descricao": "Zero",
   "valor": 5.0
}
 ````

 Exemplo de resposta:

  ````
{
  "success": "Produto atualizado com sucesso"
}
 ````

  ````GET api/estoques````

 Retorna a lista de produtos no estoque:

 Exemplo de resposta:

  ````
[
  {
    "id": 1,
    "id_produto": 1,
    "nome_produto": "Livro digital",
    "quantidade": 0,
    "created_at": "2021-01-25T23:30:42.000000Z",
    "updated_at": "2021-01-25T23:30:42.000000Z"
  },
  {
    "id": 2,
    "id_produto": 2,
    "nome_produto": "Coca-cola",
    "quantidade": 0,
    "created_at": "2021-01-25T23:31:53.000000Z",
    "updated_at": "2021-01-25T23:31:53.000000Z"
  }
]
 ````

 ````POST api/compras````

 Payload para cadastrar uma compra
 

 ````
{
   "produtos": [
   	{
   		"id_produto": 1,
   		"quantidade": 12
   	},
   	{
   		"id_produto": 2,
   		"quantidade": 126
   	}
   ]
}
 ````
Exemplo de resposta:

 ````
{
  "data_compra": "2021-01-25T00:00:00.000000Z",
  "updated_at": "2021-01-25T23:40:04.000000Z",
  "created_at": "2021-01-25T23:40:04.000000Z",
  "id": 1
}
 ````


 
 ````GET api/compras````

 Retorna a lista de compras realizadas

 Exemplo de resposta:

  ````
[
  {
    "id": 1,
    "id_produto": 1,
    "id_compra": 1,
    "data_compra": "2021-01-25",
    "quantidade": 12,
    "created_at": null,
    "updated_at": null
  },
  {
    "id": 2,
    "id_produto": 2,
    "id_compra": 1,
    "data_compra": "2021-01-25",
    "quantidade": 126,
    "created_at": null,
    "updated_at": null
  }
]
 ````

  ````POST api/vendas````

Payload para cadastro de venda:
 

 ````
{
	"customer_id": 1,
	"products": [
		{
			"product_id": 2,
			"quantity": 3
		},
		{
			"product_id": 3,
			"quantity": 10
		}
	]
}
 ````

 Exemplo de resposta:

  ````
{
  "Sucesso": "Venda cadastrada com sucesso!"
}
 ````

  ````GET api/vendas````
 
  Retorna a lista de vendas realizadas

 Exemplo de resposta:

````
[
  {
    "id": 1,
    "id_produto": 2,
    "id_venda": 2,
    "quantidade": 3,
    "created_at": null,
    "updated_at": null
  },
  {
    "id": 2,
    "id_produto": 2,
    "id_venda": 3,
    "quantidade": 3,
    "created_at": null,
    "updated_at": null
  },
]
 ````# bibliotecaDigital
# bibliotecaDigital
# bibliotecaDigital
