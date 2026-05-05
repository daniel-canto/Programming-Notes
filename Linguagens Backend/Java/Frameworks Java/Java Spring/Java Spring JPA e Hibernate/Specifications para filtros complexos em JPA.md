#backend/java/frameworks_java/java_spring/java_spring_jpa_e_hibernate/specifications_para_filtros_complexos_em_jpa
#specifications #java #jpa

```table-of-contents
```

### O que  é?

Esse é um recurso poderoso do Spring que permite com que nos utilizemos filtros dinâmicos de forma simplificada e reutilizável dentro da nossa aplicação, sem criar vários métodos repository atendendo cada combinação de filtros.

Ele na verdade é um conceito já criado por Evans em seu livro Domain-Driven-Design, onde ele introduz esse conceito de specification, que nada mais é do que um objeto que encapsula critérios de filtragem e assim os reutiliza em vários pontos da aplicação.

Tecnicamente falando no contexto de Java, ele é a Specification é basicamente um recurso fornecido pelo [[Java Spring]], que nada mais é do que um interface, onde nós implementamos a lógica de filtro utilizando o [[JPA Criteria API]]. Dessa forma, somos capazes de criar e combinar essas specifications em diferentes ocasiões. Mesmo que nós tenhamos um filtro opcional que esteja vazio (caso ele possa ser vazio), aquele filtro será dinamicamente ignorado, o que antes era um problema no contexto Java.

---
### Exemplos de uso

#### Rota GET com todos os parâmetros opcionais + filtro boolean `active`.
Nesse exemplo, foi um caso real de desenvolvimento onde eu tive esse problema, que foi ao realizar um filtro dinâmico, onde todos os parâmetros eram opcionais em minha rota `GET` da entidade `Invite`, além de possuir um filtro booleano `activate` que poderia retornar apenas invite válidos ou inválidos de acordo com a data.

Então, para desenvolver isso, eu tive que criar uma nova classe Specification para essa entidade e criar um método no Service para poder utilizar esse método no meu Controller.
Abaixo, segue os exemplos dos códigos:

```java title:"InviteSpecification"
package com.cofrinho.specifications.invite;  
  
import com.cofrinho.models.Invite;  
import org.springframework.data.jpa.domain.Specification;  
  
import java.time.Instant;  
import java.util.UUID;  
  
public class InviteSpecification {  
    public static Specification<Invite> filterWorkspace(UUID workspaceId) {  
        return (root, query, builder) ->  
            workspaceId == null ? null : builder.equal(root.get("workspace").get("id"), workspaceId);  
        }  
  
    public static Specification<Invite> filterReceiverId(UUID receiverId) {  
        return (root, query, builder) ->  
            receiverId == null ? null : builder.equal(root.get("receiver").get("id"), receiverId);  
    }  
  
    public static Specification<Invite> filterSenderId(UUID senderId) {  
        return (root, query, builder) ->  
            senderId == null ? null : builder.equal(root.get("sender").get("id"), senderId);  
    }  
  
    public static Specification<Invite> filterActive(Boolean active) {  
        return (root, query, builder) -> {  
            if (active == null) {  
                return null;  
            }  
            if (!active) {  
                return builder.greaterThan(root.get("expiresAt"), Instant.now());  
            } else {  
                return builder.lessThanOrEqualTo(root.get("expiresAt"), Instant.now());  
            }  
        };  
  
  
    }  
}
```

**Explicação do código**
Basicamente, criamos uma classe normal em Java com o nome Specification, logo em seguida, para cada filtro definimos um [[Métodos e Atributos#Método Estático|método estático]] para a montagem dos filtros. 

~={green}Os parâmetros `root`, `query` e `builer` são a base do [[JPA Criteria API]], onde elas serve para representar a tabela, a query e a condição, respectivamente.=~
É isso que faz a mágica de fazer nosso select funcionar corretamente. Como os filtros são opcionais, primeiro analisamos se eles estão vazios, e se sim, o Spring simplesmente ignora elas na query, por estarem retornando `null`.

O `.builder` possuí diversas condições, segue abaixo:
```Java title:"Condições do CriteriaBuilder"
builder.equal()           // =
builder.greaterThan()     // >
builder.like()            // LIKE
builder.and()             // AND
builder.or()              // OR
builder.isNull()          // IS NULL
```

Além disso, podemos também acessar os atributos de modelos relacionados, como no caso do `filterSender` e `filterReceiver`.


O próximo passo agora, é criarmos um método no Service que utilize qualquer conjunto desses filtros com qualquer condição, dessa forma:

```java tittle:"InviteService"
public List<Invite> getInviteList(InviteGetListRequest filters) {  
    Specification<Invite> spec = Specification  
            .where(InviteSpecification.filterWorkspace(filters.workspaceId()))  
            .and(InviteSpecification.filterSenderId(filters.senderId()))  
            .and(InviteSpecification.filterReceiverId(filters.receiverId()))  
            .and(InviteSpecification.filterActive(filters.active()));  
  
    return inviteRepository.findAll(spec);  
}
```

**Explicação do código**
Aqui montamos a nossa query utilizando as specifications que criamos na classe anterior. Dessa forma, nós apenas selecionamos exatamente os filtros que queremos utilizar e definimos as condições `.and` ou `.or`. Dessa forma, agora nós apenas passamos essa specification `spec` para o repository com o `findAll`, assim achamos todos os registros com esse filtro, retornando uma lista de invites para nós.  

----

### Fontes

- https://blog.formacao.dev/introducao-ao-uso-de-specification-no-spring-boot/
