# Descrição

## Objetivo
Criar um sistema para gerar e processar 50 mil pedidos de venda, que podem conter
um ou mais itens por pedido. O sistema incluirá funcionalidades para vendedores,
produtos e empresas, com controle de acesso baseado em papéis de usuário
(vendedores e administradores). Também deverá ter um dashboard com KPIs e a
capacidade de deletar todos os pedidos.

## Escopo Funcional
    1. Cadastro
    1.1 Vendedores
      - Cada vendedor é vinculado a uma empresa.
      - Vendedores podem ver e gerenciar apenas os pedidos que criaram.
    1.2 Produtos
      - Cada produto terá um preço e nome
      - Produtos pertencem a uma empresa.
    1.3 Empresas
      ● A empresa deve ter nome e cnpj
      ● Só administradores podem gerenciar dados da empresa.
    1.4 Pedidos
      ● Cada pedido de venda será vinculado a uma empresa.
      ● Cada pedido pode ter um ou mais itens, sendo cada item um produto associado ao pedido.
      ● Gerar 50 mil pedidos com status inicial "Pendente". Cada pedido gerado deve ter os dados básicos de vendedor empresa e produto(s)
      ● Cada pedido estará associado a um vendedor e empresa, e deve conter 1 ou mais produtos
      ● Opção para deletar todos os pedidos de uma empresa ou de um vendedor.
    2. Processamento dos Pedidos
      ● Criar um job que processa pedidos a cada 1 minuto, alterando o status de "Pendente" para "Em processamento" e, em seguida, para "Concluído".
      ● As mudanças de status seguirão essa sequência:
      ● Pendente: Após a criação do pedido.
      ● Em processamento: Após o job rodar por 1 minuto.
      ● Concluído: Após o segundo ciclo de 1 minuto.
    3. Controle de Acesso
      ● Vendedores: Visualizam apenas seus próprios pedidos e itens.
      ● Administradores: Visualizam todos os pedidos e itens da empresa.
    4. Dashboard com KPIs
      O sistema deve incluir um dashboard que exiba indicadores-chave (KPIs) sobre os pedidos:
        ● Quantidade total de pedidos por status ("Pendente", "Em processamento",
        "Concluído").
        ● Quantidade de pedidos por vendedor, filtrados por status.
        ● Quantidade de pedidos por empresa.
        ● KPIs devem ser filtrados de acordo com o tipo de usuário (vendedor ou
        administrador).
    5. Recursos de Deleção de Pedidos
      ● Criar uma funcionalidade para deletar todos os pedidos de uma empresa ou
      de um vendedor específico.
      ● Garantir que a deleção afete apenas os pedidos e itens relacionados à
      empresa ou vendedor selecionado.

# Soluções
  ## Validações

  ![Validação_Empresa](https://github.com/user-attachments/assets/9a9aca80-1a94-4746-9c12-09172b023ba3)
  
  ![Validação_ItemPedido](https://github.com/user-attachments/assets/4a53f95a-463d-4afc-976f-4da1e34697ce)
  
  ![Validação_Produto](https://github.com/user-attachments/assets/c6809959-eb38-4b87-be3f-2437ffa487bd)
  
  ![Validação_Vendedor](https://github.com/user-attachments/assets/e076a20d-8a2d-4aa4-8b69-5fa63c823292)

  ## Permissões
  
  ![2_3_Empresas](https://github.com/user-attachments/assets/94e02ecf-0856-4421-9b64-6d3d11cdfb54)
  
  ![Vendedor](https://github.com/user-attachments/assets/4c221b4f-85fa-41f5-9a5b-30a3da746b0e)
  
  ## Domain Model Inicial
  
   ### Gerado com o Maia 
  
  ```markdown
  Criar um sistema para gerar e processar pedidos de venda, que podem conter um ou mais itens por pedido. 
  O sistema incluirá funcionalidades para vendedores, produtos e empresas, com controle de acesso baseado em papéis de usuário (vendedores e administradores). 
  Também deverá ter um dashboard com KPIs e a capacidade de deletar todos os pedidos. 
  
  Entidade Vendedores
  - Cada vendedor é vinculado a uma empresa.
  - Vendedores podem ver e gerenciar apenas os pedidos que criaram.
  
  Entidade Produtos
  - Cada produto terá um preço e nome
  - Produtos pertencem a uma empresa.
  
  Entidade Empresas
  - A empresa deve ter nome e cnpj
  - Só administradores podem gerenciar dados da empresa.
  
  Entidade Pedidos
  - ENUM Status
  - Cada pedido de venda será vinculado a uma empresa.
  - Cada pedido pode ter um ou mais itens, sendo cada item um produto
  associado ao pedido.
  - Cada pedido estará associado a um vendedor e empresa, e deve conter 1 ou
  mais produtos
  - Opção para deletar todos os pedidos de uma empresa ou de um vendedor.
  ```

  ![Captura de tela 2024-11-28 094519](https://github.com/user-attachments/assets/228c10ec-6ffa-4a94-8410-4b82637dd02d)
  
  ### Domain Model Final
  
  ![Domain_Model_Final](https://github.com/user-attachments/assets/bfd4d07c-3e7c-4e1c-9664-7b9a0ee5e86a)
