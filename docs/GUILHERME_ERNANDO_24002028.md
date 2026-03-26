Avaliação — Engenharia de Software
Sistema Integrado de Gestão de Farmácia — MVP Definido pelo Estudante

Aluno: Guilherme Ernando Ribeiro Alves
RA: 24002028
Data: 25/03/2026

# Definição do MVP
No meu MVP, eu escolhi focar nas funções principais da farmácia, principalmente as que fazem parte da venda de produtos e do controle básico do sistema.

Dentro do MVP, eu incluí o cadastro e identificação de clientes, a consulta de produtos, a verificação de estoque, o registro de vendas, a emissão de comprovante,
o registro de compras e o controle básico de contas a pagar e a receber.

Fora do MVP, eu deixei funções mais avançadas, como devoluções, controle de perdas, transferências entre unidades e relatórios mais completos.
Eu fiz essas escolhas porque quis definir uma primeira versão mais simples, mas que já fosse útil no dia a dia da farmácia.
Assim, o sistema já consegue atender as operações mais importantes sem ficar muito grande logo no começo.

# Regras de Negócio 


### RN01 — Controle de Estoque na Venda
O sistema não deve permitir a venda de produtos quando a quantidade solicitada for maior do que a disponível no estoque da unidade.

### RN02 — Cadastro de Cliente no Atendimento
Quando o cliente não estiver cadastrado, o atendente poderá fazer um cadastro rápido durante o atendimento para continuar a venda normalmente.

### RN03 — Validação de Receita Médica
Produtos que exigem receita médica só podem ser vendidos após a validação da receita por um farmacêutico autorizado.

### RN04 — Geração de Conta a Receber
Toda venda a prazo deve gerar automaticamente um lançamento em contas a receber, com valor, vencimento e status da cobrança.

### RN05 — Emissão de Comprovante de Venda
Ao finalizar uma venda, o sistema deve emitir um comprovante com os dados da operação realizada.

### RN06 — Atualização de Estoque nas Compras
Toda compra registrada deve atualizar o estoque da unidade que recebeu os produtos.

### RN07 — Geração de Conta a Pagar
Toda compra de fornecedor deve gerar automaticamente um lançamento em contas a pagar no setor financeiro.

### RN08 — Controle de Acesso por Perfil
Cada usuário só pode acessar as funções permitidas para o seu perfil, como atendente, farmacêutico, gerente, financeiro ou administrador.


# Requisitos Funcionais

### RF01 — Consultar Produtos
O sistema deve permitir a consulta de produtos pelo nome, código de barras ou fabricante.

### RF02 — Identificar Cliente
O sistema deve permitir identificar clientes cadastrados durante o atendimento para vincular a compra ao seu histórico.

### RF03 — Cadastrar Cliente
O sistema deve permitir o cadastro rápido de clientes no momento da venda, caso eles ainda não estejam registrados.

### RF04 — Registrar Venda
O sistema deve permitir o registro de vendas de medicamentos e produtos de conveniência realizados no balcão.

### RF05 — Verificar Estoque da Unidade
O sistema deve verificar se a quantidade solicitada do produto está disponível no estoque da unidade antes de concluir a venda.

### RF06 — Emitir Comprovante de Venda
O sistema deve emitir um comprovante ao final da venda com os dados da operação realizada.

### RF07 — Registrar Venda a Prazo
O sistema deve permitir registrar vendas a prazo para clientes recorrentes ou empresas conveniadas.

### RF08 — Gerar Conta a Receber
O sistema deve gerar automaticamente um lançamento em contas a receber quando uma venda a prazo for concluída.

### RF09 — Registrar Compra de Fornecedor
O sistema deve permitir registrar compras informando produto, quantidade, data, valor total, fornecedor e unidade que receberá os itens.

### RF10 — Atualizar Estoque e Financeiro nas Compras
O sistema deve atualizar o estoque da unidade e gerar o lançamento em contas a pagar após o registro de uma compra.

# 4. Requisitos Não Funcionais 

### RNF01 — Segurança de Acesso
O sistema deve exigir login e senha para acesso, permitindo que cada usuário entre apenas nas funções liberadas para o seu perfil.

### RNF02 — Desempenho no Atendimento
O sistema deve responder de forma rápida nas consultas de produtos, verificação de estoque e registro de vendas, para não atrasar o atendimento ao cliente.

### RNF03 — Confiabilidade das Informações
O sistema deve manter os dados de vendas, estoque, compras e financeiro sempre consistentes, evitando erros e divergências entre setores.

### RNF04 — Facilidade de Uso
O sistema deve ter uma interface simples e organizada, para que os usuários consigam realizar as operações do dia a dia com facilidade.

### RNF05 — Disponibilidade do Sistema
O sistema deve permanecer disponível durante o horário de funcionamento da farmácia, já que ele será usado em processos essenciais da operação.

### RNF06 — Integridade dos Processos Integrados
O sistema deve garantir que processos ligados entre si, como venda, estoque e financeiro, funcionem de forma integrada e sem perda de informações.



# 5 Casos de Uso 
## UC01 — Registrar Venda

**Ator(es):** Atendente

**Descrição:** Esse caso de uso descreve o processo de registrar uma venda no balcão da farmácia. Durante esse processo, o atendente identifica o cliente,
consulta o produto, informa a quantidade desejada, verifica se há estoque disponível e finaliza a operação.
Em alguns casos, a venda pode envolver receita médica ou pagamento a prazo.

**Pré-condições:** O atendente deve estar autenticado no sistema. O sistema deve estar disponível para consulta de produtos e estoque. Deve existir pelo menos um produto cadastrado no sistema.

**Pós-condições:** A venda fica registrada no sistema.
O estoque do produto é atualizado.
O comprovante da venda é emitido.
Caso a venda seja a prazo, o lançamento em contas a receber é gerado.

## Fluxo Principal:
1. O atendente inicia a venda.
2. O cliente é identificado no sistema.
3. O produto é consultado.
4. O sistema verifica se há estoque disponível.
5. A venda é confirmada.
6 O sistema registra a venda, atualiza o estoque e emite o comprovante.
7. O processo é finalizado.

## Fluxos Alternativos / Exceções

FA01 — Cliente não cadastrado
Se o cliente não for encontrado, o sistema informa essa situação e permite que o atendente execute o caso de uso Cadastrar Cliente. Após o cadastro, o processo de venda continua normalmente.

FA02 — Produto não encontrado
Se o produto pesquisado não existir no sistema, o sistema informa que o item não foi localizado e a venda não pode continuar com aquele produto.

FA03 — Estoque insuficiente
Se a quantidade informada for maior do que a disponível no estoque, o sistema informa a indisponibilidade e impede a finalização da venda.

FA04 — Produto exige receita médica
Se o produto exigir receita, o sistema solicita a validação por um farmacêutico antes de permitir a continuidade da venda.

FA05 — Venda a prazo
Se a venda for realizada a prazo, o sistema executa o caso de uso Registrar Venda a Prazo, gerando automaticamente o lançamento em contas a receber.

## Relacionamentos

**Include:**

Identificar Cliente
Consultar Produto
Verificar Estoque
Emitir Comprovante

**Extend:**

Cadastrar Cliente
Validar Receita Médica
Registrar Venda a Prazo

## Diagrama
<img width="1133" height="3471" alt="image" src="https://github.com/user-attachments/assets/4ce3cab1-0ff8-49e7-924a-a01bea69c5e5" />



## UC02 — Cadastrar Cliente

**Ator(es):** Atendente

**Descrição:** Esse caso de uso descreve o processo de cadastrar um novo cliente no sistema da farmácia. Esse cadastro acontece quando o cliente ainda não está registrado e o atendente precisa incluí-lo para continuar o atendimento e vincular a compra ao seu histórico.

**Pré-condições:** O atendente deve estar autenticado no sistema. O cliente não deve possuir cadastro prévio.

**Pós-condições:** O cliente fica registrado no sistema.
Os dados do cliente ficam disponíveis para futuras vendas e consultas.

## Fluxo Principal:
1. O atendente inicia o cadastro do cliente.
2. O sistema solicita os dados do cliente.
3. O atendente informa os dados necessários.
4. O sistema valida as informações preenchidas.
5. O sistema registra o novo cliente.
6. O sistema confirma o cadastro realizado.
7. O processo é finalizado.

## Fluxos Alternativos / Exceções

FA01 — Dados obrigatórios não informados
Se algum dado obrigatório não for preenchido, o sistema informa o erro e solicita a correção antes de continuar.

FA02 — Cliente já cadastrado
Se o sistema identificar que o cliente já possui cadastro, ele informa essa situação ao atendente e interrompe a criação de um novo registro.

## Relacionamentos

**Include:**

Nenhum.

**Extend:**

Registrar Venda

## Diagrama
<img width="1634" height="1289" alt="image" src="https://github.com/user-attachments/assets/b3d62fc3-e867-405a-b0d3-303a7dc9980e" />


## UC03 — Identificar Cliente

**Ator(es):** Atendente

**Descrição:** Esse caso de uso descreve o processo de localizar um cliente já cadastrado no sistema durante o atendimento. A identificação do cliente permite vincular a compra ao seu histórico e dar continuidade ao processo de venda.

**Pré-condições:** O atendente deve estar autenticado no sistema. O sistema deve estar disponível para consulta de clientes. O cliente deve informar um dado para identificação.

**Pós-condições:** O cliente é localizado no sistema e vinculado ao atendimento.
Caso o cliente não seja encontrado, o sistema informa essa situação.

## Fluxo Principal:
1. O atendente inicia a identificação do cliente.
2. O sistema solicita os dados de identificação.
3. O atendente informa os dados do cliente.
4. O sistema realiza a busca no cadastro.
5. O sistema apresenta o cliente localizado.
6. O cliente é vinculado ao atendimento.
7. O processo é finalizado.

## Fluxos Alternativos / Exceções

FA01 — Cliente não encontrado
Se o cliente não for localizado no sistema, o sistema informa essa situação e o atendimento pode seguir para o cadastro de um novo cliente.

FA02 — Dados informados incorretamente
Se os dados informados estiverem incompletos ou incorretos, o sistema solicita a correção para realizar uma nova busca.

## Relacionamentos

**Include:**

Nenhum.

**Extend:**

Nenhum.

## Diagrama
<img width="1689" height="1289" alt="image" src="https://github.com/user-attachments/assets/46b0cbeb-4586-4812-9d42-077195b3824f" />

## UC04 — Consultar Produto

**Ator(es):** Atendente

**Descrição:** Esse caso de uso descreve o processo de consultar um produto no sistema da farmácia durante o atendimento. A consulta permite localizar o item desejado e visualizar informações importantes, como nome, preço e disponibilidade.

**Pré-condições:** O atendente deve estar autenticado no sistema. O sistema deve estar disponível para consulta de produtos. Deve existir pelo menos um produto cadastrado.

**Pós-condições:** O produto é localizado no sistema e suas informações são exibidas.
Caso o produto não seja encontrado, o sistema informa essa situação.

## Fluxo Principal:
1. O atendente inicia a consulta do produto.
2. O sistema solicita os dados para pesquisa.
3. O atendente informa o nome, código ou outra informação do produto.
4. O sistema realiza a busca no cadastro.
5. O sistema apresenta o produto localizado.
6. O atendente visualiza as informações do produto.
7. O processo é finalizado.

## Fluxos Alternativos / Exceções

FA01 — Produto não encontrado
Se o produto não for localizado no sistema, o sistema informa essa situação e a consulta é encerrada.

FA02 — Dados de pesquisa inválidos
Se os dados informados estiverem incompletos ou incorretos, o sistema solicita a correção para realizar uma nova busca.

## Relacionamentos

**Include:**

Nenhum.

**Extend:**

Nenhum.

## Diagrama
<img width="1755" height="1289" alt="image" src="https://github.com/user-attachments/assets/f1432f8c-c677-4945-9372-7bf59a22686d" />


## UC05 — Verificar Estoque

**Ator(es):** Atendente

**Descrição:** Esse caso de uso descreve o processo de verificar a disponibilidade de um produto no estoque da unidade. Essa verificação é importante para garantir que a venda só seja concluída quando houver quantidade suficiente disponível.

**Pré-condições:** O atendente deve estar autenticado no sistema. O produto deve estar previamente consultado ou identificado no sistema. O sistema deve estar disponível para consulta de estoque.

**Pós-condições:** A quantidade disponível do produto é apresentada ao atendente.
Caso não haja estoque suficiente, o sistema informa a indisponibilidade do item.

## Fluxo Principal:
1. O atendente inicia a verificação de estoque.
2. O sistema solicita o produto a ser verificado.
3. O atendente informa o produto desejado.
4. O sistema consulta a quantidade disponível na unidade.
5. O sistema apresenta a quantidade em estoque.
6. O atendente visualiza a disponibilidade do produto.
7. O processo é finalizado.

## Fluxos Alternativos / Exceções

FA01 — Produto sem estoque disponível
Se o produto estiver sem estoque ou com quantidade insuficiente, o sistema informa a indisponibilidade ao atendente.

FA02 — Produto não localizado
Se o produto informado não for encontrado no sistema, o sistema informa essa situação e a verificação é encerrada.

## Relacionamentos

**Include:**

Nenhum.

**Extend:**

Nenhum.

## Diagrama
<img width="1615" height="1253" alt="image" src="https://github.com/user-attachments/assets/572faa8b-2f86-4f41-bba2-b71cd818b487" />


## UC06 — Emitir Comprovante

**Ator(es):** Atendente

**Descrição:** Esse caso de uso descreve o processo de emissão do comprovante ao final de uma venda realizada no sistema da farmácia. O comprovante registra os dados principais da operação e serve como confirmação para o cliente.

**Pré-condições:** O atendente deve estar autenticado no sistema. A venda deve ter sido registrada com sucesso. O sistema deve estar disponível para emissão do comprovante.

**Pós-condições:** O comprovante da venda é gerado pelo sistema.
As informações da operação ficam registradas para consulta.
O cliente recebe a confirmação da compra realizada.

## Fluxo Principal:
1. O atendente finaliza a venda no sistema.
2. O sistema identifica que a operação foi concluída com sucesso.
3. O sistema reúne os dados da venda realizada.
4. O sistema gera o comprovante da operação.
5. O comprovante é apresentado para emissão.
6. O atendente entrega o comprovante ao cliente.
7. O processo é finalizado.

## Fluxos Alternativos / Exceções

FA01 — Falha na geração do comprovante
Se ocorrer algum erro na geração do comprovante, o sistema informa a falha e registra a ocorrência.

FA02 — Dados da venda incompletos
Se os dados da venda não estiverem completos, o sistema impede a emissão do comprovante até que a operação seja validada corretamente.

## Relacionamentos

**Include:**

Nenhum.

**Extend:**

Nenhum.

## Diagrama
<img width="2521" height="1239" alt="image" src="https://github.com/user-attachments/assets/f802fce4-2467-4858-a7a9-8b6000670949" />


## UC07 — Validar Receita Médica

**Ator(es):** Farmacêutico

**Descrição:** Esse caso de uso descreve o processo de validação de receita médica para a venda de medicamentos que exigem esse controle. A validação é necessária para garantir que a venda ocorra de acordo com as regras da farmácia e com a necessidade de autorização profissional.

**Pré-condições:** O farmacêutico deve estar autenticado no sistema. O produto deve exigir receita médica. A receita deve ser apresentada pelo cliente no momento do atendimento.

**Pós-condições:** A receita médica é validada no sistema.
A venda do medicamento pode continuar, caso a receita esteja correta.
Caso a receita seja recusada, a venda do produto não pode ser concluída.

## Fluxo Principal:
1. O farmacêutico inicia a validação da receita médica.
2. O sistema solicita os dados da receita e do medicamento.
3. O farmacêutico informa os dados necessários.
4. O sistema apresenta as informações para conferência.
5. O farmacêutico realiza a validação da receita.
6. O sistema registra a validação realizada.
7. O processo é finalizado.

## Fluxos Alternativos / Exceções

FA01 — Receita inválida
Se a receita estiver incorreta, vencida ou incompatível com o medicamento, o sistema informa a invalidade e impede a continuidade da venda.

FA02 — Receita não apresentada
Se o cliente não apresentar a receita exigida, o sistema informa a impossibilidade de validação e a venda não pode seguir.

## Relacionamentos

**Include:**

Nenhum.

**Extend:**

Registrar Venda

## Diagrama
<img width="1687" height="2097" alt="image" src="https://github.com/user-attachments/assets/133cd527-c64b-4d09-8d5f-d7c6d62a24d2" />

## UC08 — Registrar Venda a Prazo

**Ator(es):** Atendente

**Descrição:** Esse caso de uso descreve o processo de registrar uma venda a prazo no sistema da farmácia. Esse tipo de venda permite que o pagamento seja feito posteriormente, desde que o cliente esteja apto para esse tipo de operação.

**Pré-condições:** O atendente deve estar autenticado no sistema. A venda deve estar em andamento. O cliente deve estar identificado no sistema. O cliente deve estar apto para compra a prazo.

**Pós-condições:** A venda a prazo é registrada no sistema.
O lançamento em contas a receber é gerado.
A operação fica vinculada ao cliente.

## Fluxo Principal:
1. O atendente inicia o registro da venda a prazo.
2. O sistema verifica os dados da venda.
3. O sistema verifica os dados do cliente.
4. O sistema valida se o cliente está apto para compra a prazo.
5. O sistema define o valor e o vencimento da cobrança.
6. O sistema gera o lançamento em contas a receber.
7. O processo é finalizado.

## Fluxos Alternativos / Exceções

FA01 — Cliente não apto para compra a prazo
Se o cliente não estiver apto para realizar compra a prazo, o sistema informa essa situação e impede a continuidade da operação.

FA02 — Falha na geração da conta a receber
Se ocorrer algum erro ao gerar o lançamento em contas a receber, o sistema informa a falha e a venda a prazo não é concluída.

## Relacionamentos

**Include:**

Nenhum.

**Extend:**

Registrar Venda

## Diagrama
<img width="1998" height="1386" alt="image" src="https://github.com/user-attachments/assets/48ad06d2-e29d-4a5d-8386-aede58ee3426" />

## UC09 — Registrar Compra de Fornecedor

**Ator(es):** Gerente

**Descrição:** Esse caso de uso descreve o processo de registrar uma compra de produtos junto ao fornecedor no sistema da farmácia. Esse registro é importante para controlar a entrada de mercadorias, atualizar o estoque e manter o acompanhamento financeiro da operação.

**Pré-condições:** O gerente deve estar autenticado no sistema. O fornecedor deve estar cadastrado. Deve existir pelo menos um produto válido para registro da compra.

**Pós-condições:** A compra fica registrada no sistema.
Os dados da operação ficam disponíveis para consulta.
A entrada dos produtos pode ser usada para atualização do estoque e controle financeiro.

## Fluxo Principal:
1. O gerente inicia o registro da compra.
2. O sistema solicita os dados da compra.
3. O gerente informa fornecedor, produtos, quantidades e valores.
4. O sistema valida as informações preenchidas.
5. O sistema registra a compra no sistema.
6. O sistema confirma o registro realizado.
7. O processo é finalizado.

## Fluxos Alternativos / Exceções

FA01 — Fornecedor não cadastrado
Se o fornecedor informado não estiver cadastrado, o sistema informa essa situação e a compra não pode ser registrada.

FA02 — Dados inválidos ou incompletos
Se os dados da compra estiverem incorretos ou incompletos, o sistema solicita a correção antes de concluir o registro.

## Relacionamentos

**Include:**

Nenhum.

**Extend:**

Nenhum.

## Diagrama
<img width="1709" height="1289" alt="image" src="https://github.com/user-attachments/assets/5053da59-0962-4b31-a5d0-dccfc5f771db" />

## UC10 — Atualizar Estoque

**Ator(es):**Sistema

**Descrição:** Esse caso de uso descreve o processo de atualização do estoque no sistema da farmácia após uma movimentação de entrada ou saída de produtos. Essa atualização é importante para manter a quantidade disponível sempre correta no sistema.

**Pré-condições:** Deve existir uma movimentação registrada no sistema, como venda ou compra. O produto deve estar cadastrado. O sistema deve estar disponível para processamento da atualização.

**Pós-condições:** A quantidade do produto é atualizada no estoque.
A movimentação fica refletida no sistema.
As informações atualizadas ficam disponíveis para futuras consultas.

## Fluxo Principal:
1. O sistema identifica uma movimentação de estoque.
2. O sistema localiza o produto relacionado.
3. O sistema verifica o tipo de movimentação realizada.
4. O sistema calcula a nova quantidade do produto.
5. O sistema atualiza o estoque da unidade.
6. O sistema registra a atualização realizada.
7. O processo é finalizado.

## Fluxos Alternativos / Exceções

FA01 — Produto não localizado
Se o produto relacionado à movimentação não for encontrado, o sistema informa a falha e a atualização não é realizada.

FA02 — Erro no processamento da atualização
Se ocorrer algum erro durante a atualização do estoque, o sistema registra a falha e mantém a quantidade anterior do produto.

## Relacionamentos

**Include:**

Nenhum.

**Extend:**

Nenhum.

## Diagrama
<img width="1769" height="1253" alt="image" src="https://github.com/user-attachments/assets/a40b27dd-0194-455f-8bd4-753626971db7" />


# Diagrama geral 
<img width="678" height="1122" alt="image" src="https://github.com/user-attachments/assets/592ddbd4-99ce-4b1c-b18a-0763a37ade6d" />



