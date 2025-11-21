#sap/sap_novo/abap_rap/virtual_elements 

```table-of-contents
```
### O que é?
Os Virtual Elements são utilizados para definir elementos (como campos) CDS adicionais que não são persistidos no banco de dados, mas realizam cálculos durante o tempo de execução usando classes ABAP que implementam a interface do Virtual Element. Ou seja, ele é um campo definido em runtime que pode mostrar cálculos ou processos para o usuário, tendo sua lógica implementada em classes ABAP. 

----
### Como utilizar?
Para se utilizar um Virtual Elements, caso haja uma Projection View, podemos definir nosso Virtual Elements nele, dessa forma:
``` cds
@ObjectModel.virtualElementCalculatedBy: 'ABAP:ZRAP110_CALC_TRAV_ELEM_001'
@EndUserText.label: 'Overall Status Indicator'
virtual OverallStatusIndicator : abap.int2,
```

Estamos definindo um campo virtual chamado `OverallStatusIndicator`, que é implementado pela classe ABAP `ZRAP110_CALC_TRAV_ELEM_001`. Além disso, estamos também definindo o texto que o usuário irá ver na tela com a anotação da linha 2.

Portanto, na classe `ZRAP110_CALC_TRAV_ELEM_001`, eu fiz a seguinte implementação:
```abap
CLASS zrap110_calc_trav_elem_001 DEFINITION
  PUBLIC
  FINAL
  CREATE PUBLIC .

  PUBLIC SECTION.
    INTERFACES if_sadl_exit_calc_element_read .
    CLASS-METHODS:
      calculate_trav_status_ind
        IMPORTING is_original_data TYPE ZRAP110_C_TravelTP_001
        RETURNING VALUE(result)    TYPE ZRAP110_C_TravelTP_001.

  PROTECTED SECTION.
  PRIVATE SECTION.
ENDCLASS.

CLASS ZRAP110_CALC_TRAV_ELEM_001 IMPLEMENTATION.

  METHOD IF_SADL_EXIT_CALC_ELEMENT_READ~CALCULATE.
    IF it_requested_calc_elements IS INITIAL.
      EXIT.
    ENDIF.

    LOOP AT it_requested_calc_elements ASSIGNING FIELD-SYMBOL(<fs_req_calc_elements>).
      CASE <fs_req_calc_elements>.
          "virtual elements from TRAVEL entity
        WHEN 'OVERALLSTATUSINDICATOR'.

          DATA lt_trav_original_data TYPE STANDARD TABLE OF ZRAP110_C_TravelTP_001 WITH DEFAULT KEY.
          lt_trav_original_data = CORRESPONDING #( it_original_data ).
          LOOP AT lt_trav_original_data ASSIGNING FIELD-SYMBOL(<fs_trav_original_data>).

            <fs_trav_original_data> = zrap110_calc_trav_elem_001=>calculate_trav_status_ind( <fs_trav_original_data> ).

          ENDLOOP.

          ct_calculated_data = CORRESPONDING #( lt_trav_original_data ).

      ENDCASE.
    ENDLOOP.
  ENDMETHOD.

  METHOD IF_SADL_EXIT_CALC_ELEMENT_READ~GET_CALCULATION_INFO.
    IF iv_entity EQ 'ZRAP110_C_TRAVELTP_001'. "Travel BO node
      LOOP AT it_requested_calc_elements ASSIGNING FIELD-SYMBOL(<fs_travel_calc_element>).
        CASE <fs_travel_calc_element>.
          WHEN 'OVERALLSTATUSINDICATOR'.
            APPEND 'OVERALLSTATUS' TO et_requested_orig_elements.

        ENDCASE.
      ENDLOOP.
    ENDIF.
  ENDMETHOD.

  METHOD CALCULATE_TRAV_STATUS_IND.
    result = CORRESPONDING #( is_original_data ).

    "travel status indicator
    "(criticality: 1  = red | 2 = orange  | 3 = green)
    CASE result-OverallStatus.
      WHEN 'X'.
        result-OverallStatusIndicator = 1.
      WHEN 'O'.
        result-OverallStatusIndicator = 2.
      WHEN 'A'.
        result-OverallStatusIndicator = 3.
      WHEN OTHERS.
    ENDCASE.
  ENDMETHOD.

ENDCLASS.
```
A classe implementa a interface de elemento virtual **IF_SADL_EXIT_CALC_ELEMENT_READ**, que deve ser implementada por classes de cálculo para elementos virtuais.

O método **IF_SADL_EXIT_CALC_ELEMENT_READ~GET_CALCULATION_INFO** fornece uma lista de todos os elementos que são necessários para calcular os valores dos elementos virtuais na entidade solicitada. Este método é chamado em tempo de execução antes da recuperação dos dados do banco de dados para garantir que todos os elementos necessários para o cálculo sejam preenchidos com dados.

O método **IF_SADL_EXIT_CALC_ELEMENT_READ~CALCULATE** executa o cálculo do valor para o elemento virtual. Este método é chamado em tempo de execução após os dados serem recuperados do banco de dados. Os elementos necessários para o cálculo dos elementos virtuais já estão dentro da tabela de dados passada para este método. O método retorna uma tabela que contém os valores dos elementos virtuais solicitados.

Esse Virtual Elements foi aplicado junto a outros no projeto [[Exercício AD260|AD260]].