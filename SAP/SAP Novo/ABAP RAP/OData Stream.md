#sap/sap_novo/abap_rap/odata_stream

```table-of-contents
```
### O que é?
Seria a capacidade de lidar com LOBs(Large Objects), ou seja, arquivos grandes, como PDFs, planilhas, imagens, vídeos e outros tipos de dados binários, diretamente através do serviço OData.

---
### Como utilizar?
Para utilizar essa técnicas, você pode utilizar dois campos na sua entidade: um onde o arquivo será anexado, e outro que será o mimeType, dessa forma:
```cds
@Semantics.largeObject: { mimeType: 'MimeType',
fileName: 'Filename',
// acceptableMimeTypes: ['image/png', 'image/jpeg']
contentDispositionPreference: #ATTACHMENT }
attachment as Attachment,
@Semantics.mimeType: true
mime_type as MimeType,
```

* `mimeType` é um atributo obrigatório que indica o **nome do campo** que contém o mimeType do objeto. O valor é case-sensitive.
* `fileName` é um atributo opcional que indica o nome do campo que contém o nome do arquivo de um mime object. O valor é case-sensitive.
* `accepatableMimeTypes` é um atributo que fornece a lista de mime types permitidos para a stream em questão. Se qualquer subtype for aceito, você pode indicar com `*`.
* `contentDispositionPreference` é usado para definir se, dependendo das configurações do navegador, o anexo do arquivo será exibido no navegador (configuração `#INLINE`) ou baixado quando selecionado (opção `#ATTACHMENT`).

