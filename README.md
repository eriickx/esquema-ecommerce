# esquema-ecommerce
Esquema conceitual para um e-commerce feito com o DBDesigner.

# Markup
Segue o markup do esquema

```bash

CLIENTE {
	ID integer pk increments unique
	NOME varchar(45)
	TIPO_PESSOA integer *> TIPO_PESSOA.ID
	DOCUMENTO varchar(14)
	ENDERECO varchar(45)
}

PEDIDO {
	ID integer pk increments unique
	STATUS integer *> STATUS.ID
	DESCRICAO varchar(45)
	ID_CLIENTE integer *> CLIENTE.ID
	VALOR_PEDIDO decimal
	VALOR_FRETE decimal
	CODIGO_RASTREIO varchar(45)
}

STATUS {
	ID integer pk increments unique
	DESCRICAO varchar(45)
}

PRODUTO {
	ID integer pk increments unique
	NOME varchar(45)
	DESCRICAO varchar(45)
	CATEGORIA integer *> CATEGORIA.ID
	PRECO decimal
}

CATEGORIA {
	ID integer pk increments unique
	DESCRICAO varchar(45)
}

FORMA_PAGAMENTO {
	ID integer pk increments unique
	DESCRICAO varchar(45)
}

FORNECEDOR {
	ID integer pk increments unique
	NOME varchar(45)
	DESCRICAO varchar(45)
	CNPJ varchar(14) unique
	TELEFONE varchar(11)
}

ESTOQUE_PRODUTO {
	ID_PRODUTO integer pk *> PRODUTO.ID
	ID_ESTOQUE integer pk *> ESTOQUE.ID
	QUANTIDADE integer
}

ESTOQUE {
	ID integer pk increments unique
	LOCALIZACAO varchar(45)
}

PRODUTOS_PEDIDO {
	ID_PEDIDO integer pk *> PEDIDO.ID
	ID_PRODUTO integer pk *> PRODUTO.ID
	QUANTIDADE_PRODUTO integer
}

FORNECEDOR_PRODUTO {
	ID_FORNECEDOR integer pk *> FORNECEDOR.ID
	ID_PRODUTO integer pk *> PRODUTO.ID
}

VENDEDOR {
	ID integer pk increments unique
	NOME varchar(45)
	CONTATO varchar(45)
}

VENDEDOR_PRODUTO {
	ID_VENDEDOR integer pk *> VENDEDOR.ID
	ID_PRODUTO integer pk *> PRODUTO.ID
}

TIPO_PESSOA {
	ID integer pk increments unique
	NOME_DOCUMENTO varchar(45)
}

PEDIDO_FORMA_PAGAMENTO {
	ID_PEDIDO integer pk *> PEDIDO.ID
	ID_FORMA_PAGAMENTO integer pk *> FORMA_PAGAMENTO.ID
	VALOR decimal
}

CARTAO {
	ID integer pk increments unique
	TIPO integer *> TIPO_CARTAO.ID
	ID_CLIENTE integer *> CLIENTE.ID
	NUMERO_CARTAO varchar(16)
	NOME_CARTAO varchar(45)
	VALIDADE_MES integer
	VALIDADE_ANO integer
}

TIPO_CARTAO {
	ID integer pk increments unique
	TIPO varchar(45)
}
```
