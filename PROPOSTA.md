# :checkered_flag: Vitrine

A **Vitrine** é uma loja de roupas online que permite aos usuários visualizar produtos, pesquisar peças, filtrar por categorias, adicionar itens ao carrinho e realizar pedidos. O sistema também contará com áreas específicas para gerenciamento de produtos, categorias, estoque e pedidos.

## :technologist: Membros da equipe

* **Matrícula:** [553166] — **Nome:** João Eudes Silva Filho — **Curso:** Ciência da Computação

## :bulb: Objetivo Geral

Desenvolver uma aplicação web Fullstack para uma loja de roupas online, permitindo a visualização e compra de produtos, além do gerenciamento de roupas, categorias, estoque e pedidos por usuários autorizados.

## :eyes: Público-Alvo

Pessoas interessadas em comprar roupas pela internet de forma prática e organizada, além dos vendedores responsáveis pelo gerenciamento dos produtos e pedidos da loja.

## :star2: Impacto Esperado

A Vitrine busca facilitar o processo de compra de roupas pela internet, permitindo que os clientes encontrem produtos de acordo com suas preferências e realizem pedidos de maneira simples. Para a administração da loja, o sistema facilitará o controle de produtos, categorias, estoque e pedidos.

## :people_holding_hands: Papéis ou tipos de usuário da aplicação

* **Visitante:** usuário não autenticado que poderá visualizar, pesquisar e filtrar os produtos disponíveis na loja.
* **Cliente:** usuário autenticado que poderá gerenciar seu perfil, adicionar produtos ao carrinho e realizar e acompanhar seus próprios pedidos.
* **Vendedor:** poderá visualizar os pedidos realizados e atualizar seus status, além de consultar e atualizar informações relacionadas ao estoque dos produtos.
* **Administrador:** terá acesso completo ao sistema, podendo gerenciar usuários, produtos, categorias, estoque e pedidos.

Cada papel possuirá permissões diferentes dentro da aplicação.

## :triangular_flag_on_post: Principais funcionalidades da aplicação

### Funcionalidades públicas

* Visualização dos produtos disponíveis.
* Visualização dos detalhes de um produto.
* Pesquisa de produtos pelo nome.
* Filtragem de produtos por categoria.
* Paginação da listagem de produtos.
* Cadastro de novos clientes.
* Login de usuários.

### Funcionalidades do cliente autenticado

* Logout.
* Visualização e edição do próprio perfil.
* Adição e remoção de produtos do carrinho.
* Alteração da quantidade de produtos no carrinho.
* Finalização de pedidos.
* Visualização dos próprios pedidos.
* Visualização dos detalhes e status de um pedido.

### Funcionalidades do vendedor

* Visualização dos pedidos realizados.
* Atualização do status dos pedidos.
* Consulta dos produtos cadastrados.
* Atualização da quantidade disponível em estoque.

### Funcionalidades do administrador

* Cadastro, edição, visualização e remoção de produtos.
* Cadastro, edição, visualização e remoção de categorias.
* Gerenciamento do estoque.
* Visualização e gerenciamento dos pedidos.
* Gerenciamento dos usuários cadastrados.

O sistema utilizará autenticação por **JWT**, garantindo que as rotas restritas sejam acessíveis apenas por usuários autenticados e que cada tipo de usuário tenha acesso somente às funcionalidades permitidas para seu papel.

## :spiral_calendar: Entidades ou tabelas do sistema

### Usuário

Representa os usuários cadastrados no sistema.

Principais atributos:

* id
* nome
* email
* senha
* papel

### Categoria

Representa as categorias utilizadas para organizar os produtos.

Exemplos: camisetas, calças, shorts e acessórios.

Principais atributos:

* id
* nome
* descrição

### Produto

Representa as roupas disponíveis na loja.

Principais atributos:

* id
* nome
* descrição
* preço
* quantidadeEstoque
* imagem
* categoriaId

Cada produto estará associado a uma **Categoria**.

### Pedido

Representa uma compra realizada por um cliente.

Principais atributos:

* id
* data
* status
* valorTotal
* usuarioId

Cada pedido estará associado ao **Usuário** que realizou a compra.

### ItemPedido

Representa os produtos presentes em um pedido.

Principais atributos:

* id
* quantidade
* preçoUnitario
* pedidoId
* produtoId

O **ItemPedido** depende de um **Pedido** e de um **Produto**.

### Carrinho

Representa o carrinho de compras de um cliente.

Principais atributos:

* id
* usuarioId

Cada carrinho pertence a um **Usuário**.

### ItemCarrinho

Representa cada produto adicionado ao carrinho.

Principais atributos:

* id
* quantidade
* carrinhoId
* produtoId

O **ItemCarrinho** depende de um **Carrinho** e de um **Produto**.
