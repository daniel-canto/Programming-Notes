No link ~={blue}(insira o linnk do repo)=~ existe um repositório onde contém um template pronto para o desenvolvimento de uma API Flask.
Abaixo, irei explicar essa estrutura com mais detalhes.

```table-of-contents
```

#### `Config.py`
Esse código é responsável por gerenciar as configurações da aplicação de forma flexível, permitindo que os valores sejam definidos tanto por variáveis de ambiente quanto por um arquivo `config.ini` (caso ele exista). Nessa lógica, o `config.ini` (se existir) tem prioridade. Se não houver ou faltar alguma chave, busca-se na variável de ambiente.
Vamos falar mais sobre ele abaixo:
###### Importações
`os`: permite acessar variáveis de ambiente do SO.
`configparser`: usado para ler arquivos de configuração no formato `.ini`.

###### Função `get_env_or_default` 
Ela busca uma variável de ambiente pelo nome (`key`). Se não existir, retorna o valor `default`.
Por exemplo, se o TEMPLATE_API_SECRET_KEY não estiver definida no ambiente, retorna o valor padrão passado.

###### Função `load_general_config`
Recebe dois parâmetros: `app` (uma instância da aplicação) e `config` (objeto do tipo ConfigParser.)
Ele verifica se existe uma seção `[GENERAL]` no arquivo de configuração.
* Se existir, tenta pegar cada configuração dessa seção.
* Se não existir, ou algum valor não estiver definido, busca o valor correspondente na variável de ambiente.
* Se nem no arquivo, nem no ambiente houver um valor, usa um valor padrão.
* Converte valores para a tipagem correta.

###### Função read_config
- Cria um objeto `ConfigParser`.
- Tenta ler um arquivo chamado `config.ini` se ele existir.
- Chama `load_general_config` para popular as configurações da aplicação.

#### `__init.py__`
Esse arquivo é um componente fundamental na estrutura de projetos Python, especialmente com Flask. Ele serve para marcar um diretório como um pacote Python e normalmente é o local onde a aplicação e suas extensões são inicializadas e configuras.

##### Funções do `__init.py__`em Flask
- **Marca o diretório atual como pacote Python:** permite importar módulos e subpacotes de forma estruturada.
- **Centraliza a inicialização da aplicação:** geralmente contém a criação da instância Flask, a configuração da aplicação e inicialização das extensões (como ORMs, JWT, CORS etc.).
- **Facilita o uso do Application Factory Pattern:** esse padrão recomenda criar uma função dentro do `__init.py__` para construir e configurar a aplicação dinamicamente, permitindo diversas configurações para testes, produção etc.

**Por isso, nesse template,  o `__init.py__` contém:**
- Importação das extensões (SQLAlchemy, JWTManager, Limiter, etc.).
- Criação da instância da aplicação Flask.
- Leitura das configurações (via função como `read_config`).
- Inicialização das extensões com a aplicação.
- Registro de blueprints e rotas (resources).
- Configuração de handlers de erro personalizados.