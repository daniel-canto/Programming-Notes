#sap/sap_novo/sap_btp/extensibilidades 

```table-of-contents
```

### O que é?
O termo "extensibilidade" no SAP BTP se refere à capacidade de adicionar novas funcionalidades, personalizar processos e criar novas aplicações que se integram e ampliam as soluções padrão a SAP, como o SAP S/4 HANA, atendendo às individualidades de cada empresa, sem afetar o core do sistema.
Ou seja, isso seria o oposto do que ocorria no SAP ECC, onde as extensibilidades afetavam diretamente o core do sistema.

Portanto, ao falar de **extensibilidades** no SAP BTP, surge dois tipos principais, que serão individualmente abordados abaixo.

---
### Tipos de extensibilidade
##### Extensibilidade Side-by-Side
Este é o modelo principal e recomendado pela SAP para a maioria dos casos de extensão no BTP. Como o nome sugere, as extensões não são desenvolvidas e executadas **fora do sistema SAP principal**, como o SAP S/4 HAN, mas sim dentro da plataforma SAP.
Portanto, suas características são:

* **Acoplamento fraco**, onde as extensibilidades são frouxamente acopladas ao sistema central. Assim, a comunicação ocorre por meio de APIs e eventos. Isso garante que atualizações não afetarão as extensões e nem o contrário.

* **Flexibilidade Tecnológica**, pois agora os desenvolvedores não estão mais limitados a utilizar apenas as soluções da SAP, podendo utilizar diversas tecnologias como linguagens e frameworks para o desenvolvimento, ou simplesmente utilizar uma solução de terceiros já desenvolvida.

* **Escalabilidade independente**

###### Casos de uso ideais
- Desenvolvimento de aplicações completamente novas com interfaces modernas como o Fiori.
- Criação de soluções que integram outras soluções, não-SAP ou SAP.
- Processos de negócio que envolvam usuários externos, como clientes e fornecedores.
- Cenários que exigem uso intensivo de recursos ou lógicas complexas que não devem impactar no desempenho do sistema principal, como a análise de um grande volume de dados.

##### Extensibilidade In-App
Este modelo permite fazer extensões dentro da própria pilha de tecnologia do SAP S/4 HANA, mas de uma forma controlada e segura, sem modificar o código padrão.
Portanto, suas principais características são:

* **Acoplamento forte**, pois elas rodam no mesmo sistema que os dados e processo de negócio.

- **Tecnologia restrita**, pois estas extensões são desenvolvidas usando tecnologias e ferramentas da própria SAP, como o ABAP for Cloud Development (uma versão mais segura e restrita do ABAP) e CDS (Core Data Services).

###### Tipos de extensões
Mesmo dentro desse tipo de extensibilidade, ainda há subcategorias, explicadas abaixo:

**Key User Extensibility**: São ferramentas low-code/no-code que permitem que usuários de negócio (com o devido conhecimento) façam pequenas adaptações, como adicionar campos personalizados a telas e relatórios, criar lógicas de negócio simples ou ajustar formulários.

**Developer Extensibility**: Conhecida como "**Embedded Steampunk**", permite que desenvolvedores criem extensões mais complexas usando o ambiente SAP dentro do S/4 HANA, mas de uma forma que adere às regras de nuvem e não crie conflitos com futuras atualizações.

---
### Quando usar cada tipo de extensibilidade?
- Utilizamos o **In-App** para pequenas adaptações e extensões que estão nitidamente ligadas a um processo ou objeto de negócio específico dentro do S/4 HANA e precisam da mesma transação lógica.

- Utilizamos o **Side-by-Side** para criar novas aplicações, processos desacoplados, integrações complexas ou quando precisar de flexibilidade tecnológica e escalabilidade independente.
