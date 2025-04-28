#conceitos_fundamentais/poo/conceitos_tecnicos/destrutor 

O destrutor é um [[Métodos e Atributos#Métodos|método]] especial  de uma classe que é automaticamente chamado quando o objeto está prestes a ser destruído ou quando seu tempo de vida acaba. Sua função é liberar recursos que o objeto possa ter adquirido durante a sua existência, como memória alocada dinamicamente, arquivos abertos ou conexões com dispositivos externos.

Esse coisa é utilizado explicitamente em linguagens como C++, onde o destrutor possui o mesmo nome da classe, precedido de um til (~), não recebendo parâmetros nem retornando valores. Só pode haver um destrutor por classe e ele não pode ser chamado explicitamente pelo programador, sua execução é automática quando o objeto sai de escopo ou é deletado.

Em linguagens com gerenciamento automático de memória, como C# e Java, o destrutor (também chamado de finalizador) é chamado pelo coletor de lixo quando o objeto não é mais acessível, mas o programador geralmente não precisa se preocupar em implementá-lo, a não ser em casos específicos de liberação de recursos não gerenciados