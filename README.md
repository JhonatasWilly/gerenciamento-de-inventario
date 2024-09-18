# Sistema de inventario com relatorio de vendas 

 Sistema de Gerenciamento de Inventário para uma Loja Virtual

 1. Apresentação do programa
 2. Principais funcionalidades
 3. Funcionalidades acessórias

## Apresentação do programa

Trata-se de um programa para uso interno de uma loja virtual realizar o controle de estoque/inventário de seus produtos.

De maneira resumida, o programa permite ao usuário o cadastro, atualização, exclusão/desativação e listagem de produtos, além de realizar vendas e gerar relatórios detalhados em formato CSV, sendo que em todas as operações o programa saberá lidar com erros sem interrupção de funcionamento.


## Principais funcionalidades

### i) Cadastro de produtos

Permite ao usuário cadastrar um novo produto, além daqueles pré existentes, sendo obrigatório o preenchimento de informações de nome, preço, quantidade, categoria, e opcionalmente uma descrição, além do preenchimento automático da informação de produto "valido" (vide explicação detalhada no item *iii) Exclusão de produtos*)

Para os campos obrigatórios que forem deixados em branco o sistema irá emitir uma mensagem de erro, informando ao usuário a obrigatoriedade de preenchimento do respectivo campo com a informação.

Ao final de todo o processo de preenchimento das informações, um número de identificação será criado automaticamente para cada novo produto, levando-se em conta o ID dos produtos existentes para evitar sobrescrição de produtos.

Todos os produtos ficam salvos em um dicionário de produtos para melhor organização e manipulação de dados pelo programa.

### ii) Listagem de produtos

Ao acionar esta função, o usuário receberá como retorno do programa uma lista enumerada com todos os produtos "ativos".

Importante notar que o dicionário de produtos pode conter vários produtos, "ativos" e "inativos", porém somente os "ativos" aparecerão quando está função é selecionada.

### iii) Exclusão de produtos

Ao usuário final é oferecida a opção de excluir um produto, de modo que após essa operação o produto não estará mais disponível para venda, porém, o produto não é de fato excluído da base de dados (dicionário de produtos).

O que o programa faz na realidade é apenas converter a chave "ativo" de "True" para "False" e com esta pequena alteração o produto passa a estar indisponível para futuras vendas e também deixa de ser listado na opção *Listar produtos*.

Dessa maneira, o dicionário de produtos continua alimentado com as informações de produtos "excluídos" de modo a garantir a persistência de dados e evitando-se erros de execução e emissão de relatórios.

### iv) Realização de venda

Permite ao usuário incluir múltiplos produtos em quantidades variáveis (desde que haja estoque o suficiente do produto selecionado). 

A cada produto vendido o estoque é atualizado automaticamente.

Se o estoque for insuficiente para a quantidade desejada, o sistema lança uma mensagem de erro, informando ao usuário a quantidade total que existe do produto que ele está tentando vender.

A cada nova venda completada, um novo ID de venda é gerado automaticamente e arquivado no dicionário "vendas", para posteriormente ser utilizado na emissão de relatório de vendas.

### v) Emissão de relatório de vendas

O sistema gerar relatórios de vendas em formato CSV, contendo informações detalhadas como o nome do produto, quantidade vendida, preço unitário, valor total da venda e data e hora da transação.

Na prática existe um único arquivo de vendas e pra cada nova venda o programa apenas adiciona a nova trasação ao final do arquivo.

A diferenciação de uma transação para outra pode ser feita com base na data da venda, garantindo organização na leitura e manipulação dos dados do relatório.

Também é possível incluir no relatório, numa futura atualização do sistema, a informação do ID de venda que fica arquivado no dicionário "relatórios".

### vi) Persistência de dados

Os dados do inventário e as informações das vendas são persistidos em arquivos CSV, garantindo que nenhuma informação seja perdida entre execuções do programa.

Por isso, a cada nova inicialização o programa importa automaticamente o relatório de vendas com todo o histórico de vendas realizadas, atualizando automaticamente o estoque de produtos.
