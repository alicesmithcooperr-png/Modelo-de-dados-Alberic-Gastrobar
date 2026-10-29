# Entrega 1 — Modelo Lógico de Banco de Dados (MBD / Relacional)

## Sistema de Gestão de Informações — Alberic Gastrobar

### Projeto Acadêmico — Banco de Dados

---

## 1. Contextualização e Mapeamento
O Modelo Lógico de Banco de Dados (MBD) traduz o Modelo Entidade-Relacionamento (DER) para o paradigma Relacional. As entidades conceituais foram mapeadas em **tabelas relacionais**, com suas respectivas **Chaves Primárias (PK)**, **Chaves Estrangeiras (FK)**, tipos de dados, regras de preenchimento (`NOT NULL`, `UNIQUE`) e restrições de integridade.

---

## 2. Esquema das Tabelas (Estrutura Relacional)

### 2.1 Módulo: Salão e Atendimento

#### `MESA`
Armazena a identificação das mesas físicas do estabelecimento.
* **`id_mesa`** `INT` `AUTO_INCREMENT` **[PK]**: Identificador único da mesa.
* **`numero`** `INT` `NOT NULL` `UNIQUE`: Número físico visível da mesa.
* **`capacidade`** `INT` `NOT NULL`: Quantidade máxima de assentos.
* **`status`** `VARCHAR(20)` `NOT NULL` `DEFAULT 'LIVRE'`: Situação atual (`LIVRE`, `OCUPADA`, `RESERVADA`, `MANUTENÇÃO`).
* **`observacao`** `VARCHAR(255)` `NULL`: Observações adicionais (ex.: "próximo à janela").

#### `COMANDA`
Registra o ciclo de atendimento/consumo associado a uma mesa.
* **`id_comanda`** `INT` `AUTO_INCREMENT` **[PK]**: Identificador único da comanda.
* **`id_mesa`** `INT` `NOT NULL` **[FK -> MESA.id_mesa]**: Mesa vinculada.
* **`aberta_em`** `DATETIME` `NOT NULL` `DEFAULT CURRENT_TIMESTAMP`: Data/hora de abertura.
* **`fechada_em`** `DATETIME` `NULL`: Data/hora do encerramento.
* **`status`** `VARCHAR(20)` `NOT NULL` `DEFAULT 'ABERTA'`: Situação da comanda (`ABERTA`, `AGUARDANDO_PAGAMENTO`, `FECHADA`, `CANCELADA`).

#### `PEDIDO`
Agrupa os itens solicitados pelo cliente em um determinado momento da permanência.
* **`id_pedido`** `INT` `AUTO_INCREMENT` **[PK]**: Identificador único do pedido.
* **`id_comanda`** `INT` `NOT NULL` **[FK -> COMANDA.id_comanda]**: Comanda do pedido.
* **`id_funcionario`** `INT` `NOT NULL` **[FK -> FUNCIONARIO.id_funcionario]**: Garçom/atendente que registrou.
* **`criado_em`** `DATETIME` `NOT NULL` `DEFAULT CURRENT_TIMESTAMP`: Data/hora do envio.
* **`status`** `VARCHAR(20)` `NOT NULL` `DEFAULT 'ENVIADO'`: Estado global (`ENVIADO`, `EM_PREPARO`, `PRONTO`, `ENTREGUE`, `CANCELADO`).
* **`observacao`** `VARCHAR(255)` `NULL`: Observações gerais do pedido.

#### `ITEM_PEDIDO`
Tabela associativa que detalha cada produto inserido em um pedido.
* **`id_item_pedido`** `INT` `AUTO_INCREMENT` **[PK]**: Identificador único do item do pedido.
* **`id_pedido`** `INT` `NOT NULL` **[FK -> PEDIDO.id_pedido]**: Pedido de origem.
* **`id_produto`** `INT` `NOT NULL` **[FK -> PRODUTO.id_produto]**: Produto solicitado.
* **`quantidade`** `DECIMAL(10,3)` `NOT NULL`: Quantidade do item (suporta fracionado se necessário).
* **`preco_unitario`** `DECIMAL(10,2)` `NOT NULL`: Preço praticado no momento do pedido (preserva histórico).
* **`status`** `VARCHAR(20)` `NOT NULL` `DEFAULT 'PENDENTE'`: Estado no setor (`PENDENTE`, `EM_PREPARO`, `PRONTO`, `ENTREGUE`, `CANCELADO`).
* **`observacao_item`** `VARCHAR(150)` `NULL`: Especificações (ex.: "sem cebola", "ponto do cliente").

---

### 2.2 Módulo: Cardápio e Estrutura Operacional

#### `CATEGORIA`
Classifica os produtos do cardápio.
* **`id_categoria`** `INT` `AUTO_INCREMENT` **[PK]**: Identificador da categoria.
* **`nome`** `VARCHAR(50)` `NOT NULL` `UNIQUE`: Nome da categoria (ex.: Porções, Bebidas, Sobremesas).
* **`descricao`** `VARCHAR(255)` `NULL`: Descrição da categoria.
* **`ativa`** `BOOLEAN` `NOT NULL` `DEFAULT TRUE`: Indicador de atividade no cardápio.

#### `SETOR`
Representa os setores físicos preparadores/operacionais.
* **`id_setor`** `INT` `AUTO_INCREMENT` **[PK]**: Identificador do setor.
* **`nome`** `VARCHAR(50)` `NOT NULL` `UNIQUE`: Nome do setor (ex.: Cozinha, Bar, Salão, Caixa).
* **`descricao`** `VARCHAR(255)` `NULL`: Descrição sumária das responsabilidades.
* **`ativo`** `BOOLEAN` `NOT NULL` `DEFAULT TRUE`: Situação cadastral.

#### `PRODUTO`
Cadastro dos itens comercializados.
* **`id_produto`** `INT` `AUTO_INCREMENT` **[PK]**: Identificador único do produto.
* **`id_categoria`** `INT` `NOT NULL` **[FK -> CATEGORIA.id_categoria]**: Categoria vinculada.
* **`id_setor`** `INT` `NOT NULL` **[FK -> SETOR.id_setor]**: Setor responsável pela produção/preparo.
* **`nome`** `VARCHAR(100)` `NOT NULL`: Nome comercial do item.
* **`descricao`** `TEXT` `NULL`: Detalhamento dos ingredientes/características.
* **`preco_venda`** `DECIMAL(10,2)` `NOT NULL`: Valor monetário padrão de venda.
* **`disponivel`** `BOOLEAN` `NOT NULL` `DEFAULT TRUE`: Flag de oferta ativa no sistema.

---

### 2.3 Módulo: Pessoal e Escala

#### `FUNCIONARIO`
Registra colaboradores do estabelecimento e credenciais de acesso.
* **`id_funcionario`** `INT` `AUTO_INCREMENT` **[PK]**: Identificador único do funcionário.
* **`id_setor`** `INT` `NULL` **[FK -> SETOR.id_setor]**: Setor principal de atuação.
* **`nome`** `VARCHAR(100)` `NOT NULL`: Nome completo.
* **`funcao`** `VARCHAR(50)` `NOT NULL`: Cargo/Função (ex.: Garçom, Barman, Cozinheiro, Gerente, Caixa).
* **`usuario_login`** `VARCHAR(50)` `NULL` `UNIQUE`: Usuário para autenticação no sistema.
* **`senha_hash`** `VARCHAR(255)` `NULL`: Hash de segurança da senha.
* **`ativo`** `BOOLEAN` `NOT NULL` `DEFAULT TRUE`: Situação do contrato no sistema.

#### `ESCALA_FUNCIONARIO`
Organiza e aloca os turnos de trabalho da equipe.
* **`id_escala`** `INT` `AUTO_INCREMENT` **[PK]**: Identificador da escala.
* **`id_funcionario`** `INT` `NOT NULL` **[FK -> FUNCIONARIO.id_funcionario]**: Colaborador alocado.
* **`inicio`** `DATETIME` `NOT NULL`: Data e hora de início do turno.
* **`fim`** `DATETIME` `NOT NULL`: Data e hora de término do turno.
* **`funcao_turno`** `VARCHAR(50)` `NOT NULL`: Função exercida especificamente no turno.
* **`status`** `VARCHAR(20)` `NOT NULL` `DEFAULT 'PREVISTO'`: Situação (`PREVISTO`, `CONFIRMADO`, `REALIZADO`, `FALTA`).

---

### 2.4 Módulo: Estoque e Compras

#### `ESTOQUE`
Armazena a posição atualizada do saldo em estoque de cada produto.
* **`id_estoque`** `INT` `AUTO_INCREMENT` **[PK]**: Identificador do registro de estoque.
* **`id_produto`** `INT` `NOT NULL` `UNIQUE` **[FK -> PRODUTO.id_produto]**: Produto associado (relação 1:1 com Produto).
* **`quantidade_atual`** `DECIMAL(10,3)` `NOT NULL` `DEFAULT 0.000`: Saldo físico disponível.
* **`unidade_medida`** `VARCHAR(15)` `NOT NULL`: Unidade (ex.: `UN`, `KG`, `L`, `GARRAFA`).
* **`estoque_minimo`** `DECIMAL(10,3)` `NULL`: Ponto de pedido para reposição.

#### `MOVIMENTACAO_ESTOQUE`
Histórico de rastreabilidade de entradas, saídas e ajustes de inventário.
* **`id_movimentacao`** `INT` `AUTO_INCREMENT` **[PK]**: Identificador único do lançamento.
* **`id_estoque`** `INT` `NOT NULL` **[FK -> ESTOQUE.id_estoque]**: Item de estoque movimentado.
* **`id_produto`** `INT` `NOT NULL` **[FK -> PRODUTO.id_produto]**: Produto correspondente.
* **`id_funcionario`** `INT` `NOT NULL` **[FK -> FUNCIONARIO.id_funcionario]**: Responsável pelo registro.
* **`tipo`** `VARCHAR(10)` `NOT NULL`: Tipo de movimentação (`ENTRADA`, `SAIDA`, `AJUSTE`).
* **`quantidade`** `DECIMAL(10,3)` `NOT NULL`: Volume movimentado (sempre positivo).
* **`ocorrido_em`** `DATETIME` `NOT NULL` `DEFAULT CURRENT_TIMESTAMP`: Data/hora do evento.
* **`motivo`** `VARCHAR(255)` `NOT NULL`: Justificativa (ex.: "Venda pedido #12", "Perda/Avaria", "Compra NF 123").

#### `FORNECEDOR`
Cadastro de parceiros comerciais e fornecedores de mercadorias.
* **`id_fornecedor`** `INT` `AUTO_INCREMENT` **[PK]**: Identificador do fornecedor.
* **`nome_razao_social`** `VARCHAR(120)` `NOT NULL`: Razão social ou nome fantasia.
* **`documento`** `VARCHAR(20)` `NULL` `UNIQUE`: CNPJ ou CPF.
* **`telefone`** `VARCHAR(20)` `NOT NULL`: Contato telefônico principal.
* **`email`** `VARCHAR(100)` `NULL`: E-mail de contato comercial.
* **`endereco`** `VARCHAR(255)` `NULL`: Endereço completo.
* **`ativo`** `BOOLEAN` `NOT NULL` `DEFAULT TRUE`: Status cadastral.

#### `COMPRA`
Registro de cabeçalho dos pedidos de compra de insumos/produtos.
* **`id_compra`** `INT` `AUTO_INCREMENT` **[PK]**: Identificador da compra.
* **`id_fornecedor`** `INT` `NOT NULL` **[FK -> FORNECEDOR.id_fornecedor]**: Fornecedor contratado.
* **`id_funcionario`** `INT` `NOT NULL` **[FK -> FUNCIONARIO.id_funcionario]**: Comprador/solicitante.
* **`solicitada_em`** `DATETIME` `NOT NULL` `DEFAULT CURRENT_TIMESTAMP`: Data do pedido.
* **`prevista_entrega`** `DATE` `NULL`: Previsão de entrega do fornecedor.
* **`status`** `VARCHAR(20)` `NOT NULL` `DEFAULT 'SOLICITADA'`: Estado (`SOLICITADA`, `APROVADA`, `RECEBIDA`, `CANCELADA`).
* **`valor_total`** `DECIMAL(10,2)` `NOT NULL` `DEFAULT 0.00`: Soma total do pedido de compra.

#### `ITEM_COMPRA`
Detalhamento dos produtos solicitados em uma ordem de compra.
* **`id_item_compra`** `INT` `AUTO_INCREMENT` **[PK]**: Identificador do item da compra.
* **`id_compra`** `INT` `NOT NULL` **[FK -> COMPRA.id_compra]**: Ordem de compra pai.
* **`id_produto`** `INT` `NOT NULL` **[FK -> PRODUTO.id_produto]**: Produto a ser reposto.
* **`quantidade_pedida`** `DECIMAL(10,3)` `NOT NULL`: Quantidade encomendada.
* **`quantidade_recebida`** `DECIMAL(10,3)` `NOT NULL` `DEFAULT 0.000`: Quantidade entregue/conferida.
* **`custo_unitario`** `DECIMAL(10,2)` `NOT NULL`: Preço unitário pago ao fornecedor.

---

### 2.5 Módulo: Financeiro, Caixa e Ocorrências

#### `PAGAMENTO`
Registra liquidações financeiras associadas às comandas.
* **`id_pagamento`** `INT` `AUTO_INCREMENT` **[PK]**: Identificador do pagamento.
* **`id_comanda`** `INT` `NOT NULL` **[FK -> COMANDA.id_comanda]**: Comanda quitada (total ou parcialmente).
* **`forma_pagamento`** `VARCHAR(30)` `NOT NULL`: Meio utilizado (`DINHEIRO`, `CARTAO_CREDITO`, `CARTAO_DEBITO`, `PIX`).
* **`valor`** `DECIMAL(10,2)` `NOT NULL`: Valor pago nesta transação.
* **`pago_em`** `DATETIME` `NOT NULL` `DEFAULT CURRENT_TIMESTAMP`: Data/hora do recebimento.
* **`status`** `VARCHAR(20)` `NOT NULL` `DEFAULT 'CONCLUIDO'`: Situação (`CONCLUIDO`, `ESTORNADO`).
* **`referencia_transacao`** `VARCHAR(100)` `NULL`: Código autorização maquininha/NSU/Pix.

#### `CONTA_PAGAR`
Gestão de compromissos financeiros e obrigações com fornecedores.
* **`id_conta_pagar`** `INT` `AUTO_INCREMENT` **[PK]**: Identificador da obrigação financeira.
* **`id_fornecedor`** `INT` `NOT NULL` **[FK -> FORNECEDOR.id_fornecedor]**: Credor da obrigação.
* **`id_compra`** `INT` `NULL` **[FK -> COMPRA.id_compra]**: Compra de origem (opcional para contas diversas).
* **`documento_referencia`** `VARCHAR(50)` `NULL`: Número da NF ou boleto.
* **`vencimento`** `DATE` `NOT NULL`: Data limite para pagamento.
* **`valor`** `DECIMAL(10,2)` `NOT NULL`: Valor nominal da fatura.
* **`status`** `VARCHAR(20)` `NOT NULL` `DEFAULT 'PENDENTE'`: Estado (`PENDENTE`, `PAGO`, `ATRASADO`, `CANCELADO`).
* **`pago_em`** `DATE` `NULL`: Data em que foi efetuada a quitação.

#### `FECHAMENTO_CAIXA`
Conferência de turno e fechamento diário do caixa físico.
* **`id_fechamento`** `INT` `AUTO_INCREMENT` **[PK]**: Identificador do fechamento.
* **`id_funcionario`** `INT` `NOT NULL` **[FK -> FUNCIONARIO.id_funcionario]**: Operador de caixa responsável.
* **`iniciado_em`** `DATETIME` `NOT NULL`: Data/hora de abertura do turno no caixa.
* **`encerrado_em`** `DATETIME` `NOT NULL`: Data/hora de fechamento do turno.
* **`valor_sistema`** `DECIMAL(10,2)` `NOT NULL`: Valor computado pelas vendas registradas.
* **`valor_conferido`** `DECIMAL(10,2)` `NOT NULL`: Valor contado fisicamente/relatórios.
* **`diferenca`** `DECIMAL(10,2)` `NOT NULL` `DEFAULT 0.00`: Apuração de sobra ou falta (`valor_conferido - valor_sistema`).
* **`observacao`** `TEXT` `NULL`: Justificativa de divergências encontradas.

#### `OCORRENCIA`
Registra incidentes operacionais, reclamações e concessão de cortesia.
* **`id_ocorrencia`** `INT` `AUTO_INCREMENT` **[PK]**: Identificador da ocorrência.
* **`id_comanda`** `INT` `NULL` **[FK -> COMANDA.id_comanda]**: Comanda envolvida (se aplicável).
* **`id_funcionario`** `INT` `NOT NULL` **[FK -> FUNCIONARIO.id_funcionario]**: Funcionário lançador.
* **`autorizado_por`** `INT` `NULL` **[FK -> FUNCIONARIO.id_funcionario]**: Gerente autorizador (se houver cortesia).
* **`registrada_em`** `DATETIME` `NOT NULL` `DEFAULT CURRENT_TIMESTAMP`: Data/hora do evento.
* **`descricao`** `TEXT` `NOT NULL`: Relato do problema/ocorrência.
* **`providencia`** `TEXT` `NOT NULL`: Ação tomada pela equipe.
* **`cortesia_valor`** `DECIMAL(10,2)` `NULL` `DEFAULT 0.00`: Valor financeiro concedido em desconto/cortesia.

---

## 3. Resumo dos Relacionamentos e Integridade Referencial

| Tabela Origem (FK) | Tabela Destino (PK) | Relacionamento | Regra de Negócio / Integridade |
| :--- | :--- | :---: | :--- |
| `COMANDA.id_mesa` | `MESA.id_mesa` | N : 1 | Toda comanda é aberta para uma mesa. |
| `PEDIDO.id_comanda` | `COMANDA.id_comanda` | N : 1 | Vários pedidos pertencem a uma mesma comanda. |
| `PEDIDO.id_funcionario` | `FUNCIONARIO.id_funcionario` | N : 1 | Identifica o atendente criador do pedido. |
| `ITEM_PEDIDO.id_pedido` | `PEDIDO.id_pedido` | N : 1 | Detalha os produtos contidos em um pedido. |
| `ITEM_PEDIDO.id_produto` | `PRODUTO.id_produto` | N : 1 | Vincula o item vendido ao produto do cardápio. |
| `PRODUTO.id_categoria` | `CATEGORIA.id_categoria` | N : 1 | Classifica o produto em uma categoria. |
| `PRODUTO.id_setor` | `SETOR.id_setor` | N : 1 | Define o setor responsável por preparar o produto. |
| `ESTOQUE.id_produto` | `PRODUTO.id_produto` | 1 : 1 (UNIQUE) | Cada produto possui exatamente um saldo em estoque. |
| `MOVIMENTACAO_ESTOQUE.id_estoque`| `ESTOQUE.id_estoque` | N : 1 | Registra as alterações no saldo de um estoque. |
| `PAGAMENTO.id_comanda` | `COMANDA.id_comanda` | N : 1 | Permite múltiplos pagamentos para quitar uma comanda. |
| `COMPRA.id_fornecedor` | `FORNECEDOR.id_fornecedor` | N : 1 | Identifica o fornecedor da ordem de compra. |
| `ITEM_COMPRA.id_compra` | `COMPRA.id_compra` | N : 1 | Detalha os produtos de um pedido de compra. |
| `CONTA_PAGAR.id_fornecedor` | `FORNECEDOR.id_fornecedor` | N : 1 | Define a quem o título financeiro deve ser pago. |
