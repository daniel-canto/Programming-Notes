#sap/sap_novo/abap_rap/tecnicas_abap_rap/json_no_abap_rap 

```table-of-contents
```

### Convertendo de ABAP para JSON
Normalmente, neste caso, transformamos ABAO para JSON para utilizam em requests. Para convertermos uma estrutura ABAP para JSON, precisamos seguir o tutorial abaixo.

1- **Definir o types da estrutura**
O primeiro passo é definir a estrutura da nossa requisição, dessa forma por exemplo:
``` abap
 TYPES: BEGIN OF ty_produtos,
             id_produto TYPE string,
             nome_produto TYPE string,
             data_criacao TYPE string,
           END OF ty_produtos.
tt_produtos TYPE STANDARD TABLE OF ty_produtos WITH EMPTY KEY.
 
 TYPES: BEGIN OF ty_request,
             lote TYPE string,
             produtos TYPE tt_produtos
           END OF ty_request.
```
Como podemos ver, o campo produtos será uma lista de produtos.

2- **Popular a estrutura de request**
Agora, vamos passar os dados para a nossa estrutura de request. Como no nosso caso nós precisamos enviar uma lista para o JSON, fazemos dessa forma para os produtos:
``` abap
DATA: lt_produtos TYPE tt_produtos.

" Essa it_keys seriam os registros selecionados no Fiori Elements.
LOOP AT it_produtos ASSIGNING FIELD-SYMBOL(<k>).
  APPEND VALUE ty_produtos(
	id_produto   = <k>-id_produto
	nome_produto = <k>-nome_produto
	data_criacao = <k>-data_criacao
  ) TO lt_produtos.
ENDLOOP.
```
Agora, com a `lt_produtos` populada, podemos popular a nossa estrutura root de request, dessa forma:
``` abap
DATA(ls_req) = VALUE ty_request( lote = 'lote_exemplo'
								produtos = lt_produtos ).
```

3- **Gerar o JSON**
Agora, vamos utilizar a classe `xco_cp_json` para gerar nosso JSON de request, dessa forma:
``` abap
RETURN xco_cp_json=>data->from_abap( ls_req )->apply(
	VALUE #( ( xco_cp_json=>transformation->boolean_to_abap_bool )
			 ( xco_cp_json=>transformation->underscore_to_pascal_case ) )
)->to_string( ).
```

Aqui, estamos passando algumas formatações, como o `boolean_to_abap_bool`, que transforma os flags ABAP em JSON Boolean. Além de formatarmos os nomes dos campos para pascal case, deixando nosso JSON assim:
``` json
{
  "Lote": "lote_exemplo",
  "Produtos": [
    {
      "IdProduto": "PROD-001",
      "NomeProduto": "Laptop",
      "DataCriacao": "20251028"
    },
    {
      "IdProduto": "PROD-002",
      "NomeProduto": "Mouse",
      "DataCriacao": "20251027"
    }
  ]
}
```

---
### Convertendo de JSON para ABAP
Normalmente fazemos essa conversão quando temos que tratar um retorno de uma API. Portanto, para isso, siga esse tutorial:

1- **Definir o types da estrutura**
``` abap
TYPES: BEGIN OF ty_produtos_vendidos,
			id_produto TYPE string,
			nome_produto TYPE string,
			data_criacao TYPE string,
	    END OF ty_produtos_vendidos.
tt_produtos_vendidos TYPE STANDARD TABLE OF ty_produtos_vendidos WITH EMPTY KEY.
	    
TYPES: BEGIN OF ty_response,
			id_venda TYPE string,
			data_venda TYPE string,
		END OF ty_response.
```

2-  **Gerar a estrutura ABAP**
``` abap
DATA lw_resp TYPE ty_response.

xco_cp_json=>data->from_string( iv_response )->apply(
	VALUE #( ( xco_cp_json=>transformation->boolean_to_abap_bool ) )
)->write_to( REF #( lw_resp ) ).

IF lw_resp IS INITIAL.
  RETURN.
ENDIF.
```
Agora, estamos transformando os dados do JSON em uma estrutura ABAP. Assim, podemos trabalhar com os dados do JSON normalmente.