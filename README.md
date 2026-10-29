# Modelo Lógico de Banco de Dados (MBD) — Alberic Gastrobar

**Projeto Acadêmico — Banco de Dados**  
**Integrantes:** Daniel Baptista dos Santos (48821756), Eloise Abreu Rodrigues (49482602), Fernando Simoes de Menezes (49617133), Nathaly Pereira (47287560), Yasmin Jimenez Negrão (49595407).

---

## 1. Mapeamento Lógico (Esquema de Tabelas)

Legendas:
* **`[PK]`**: Chave Primária (*Primary Key*)
* **`[FK -> TABELA.coluna]`**: Chave Estrangeira (*Foreign Key*)
* **`[UQ]`**: Restrição de Unicidade (*Unique*)

---

### 1.1 Módulo: Atendimento e Salão

#### **`MESA`**
Armazena a identificação e status das mesas do restaurante.
* **`id_mesa`** `INT AUTO_INCREMENT` **[PK]**
* **`numero`** `INT NOT NULL` **[UQ]** — Número físico da mesa.
* **`capacidade`** `INT NOT NULL` — Lotação de assentos.
* **`status`** `VARCHAR(20) NOT NULL DEFAULT 'LIVRE'` — Ex: `LIVRE`, `OCUPADA`, `RESERVADA`.
* **`observacao`** `VARCHAR(255) NULL`

#### **`COMANDA`**
Registra cada sessão de atendimento associada a uma mesa.
* **`id_comanda`** `INT AUTO_INCREMENT` **[PK]**
* **`id_mesa`** `INT NOT NULL` **[FK -> MESA.id_mesa]**
* **`aberta_em`** `DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP`
* **`fechada_em`** `DATETIME NULL`
* **`status`** `VARCHAR(20) NOT NULL DEFAULT 'ABERTA'` — Ex: `ABERTA`, `AGUARDANDO_PAGAMENTO`, `FECHADA`, `CANCELADA`.

#### **`PEDIDO`**
Agrupa as solicitações efetuadas pelo garçom/cliente durante o atendimento.
* **`id_pedido`** `INT AUTO_INCREMENT` **[PK]**
* **`id_comanda`** `INT NOT NULL` **[FK -> COMANDA.id_comanda]**
* **`id_funcionario`** `INT NOT NULL` **[FK -> FUNCIONARIO.id_funcionario]** — Garçom/Atendente responsável.
* **`criado_em`** `DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP`
* **`status`** `VARCHAR(20) NOT NULL DEFAULT 'ENVIADO'` — Ex: `ENVIADO`, `EM_PREPARO`, `PRONTO`, `ENTREGUE`, `CANCELADO`.
* **`observacao`** `VARCHAR(255) NULL`

#### **`ITEM_PEDIDO`**
Relação reduzida $N:M$ entre Pedido e Produto, mantendo histórico de preços praticados.
* **`id_item_pedido`** `INT AUTO_INCREMENT` **[PK]**
* **`id_pedido`** `INT NOT NULL` **[FK -> PEDIDO.id_pedido]**
* **`id_produto`** `INT NOT NULL` **[FK -> PRODUTO.id_produto]**
* **`quantidade`** `DECIMAL(10,3) NOT NULL` — Suporta frações de unidades se necessário.
* **`preco_unitario`** `DECIMAL(10,2) NOT NULL` — Valor no momento da venda (preserva histórico).
* **`status`** `VARCHAR(20) NOT NULL DEFAULT 'PENDENTE'` — Ex: `PENDENTE`, `EM_PREPARO`, `PRONTO`, `ENTREGUE`, `CANCELADO`.
* **`observacao_item`** `VARCHAR(150) NULL` — Ex: "sem cebola", "bem passado".

---

### 1.2 Módulo: Cardápio e Estrutura Operacional

#### **`CATEGORIA`**
* **`id_categoria`** `INT AUTO_INCREMENT` **[PK]**
* **`nome`** `VARCHAR(50) NOT NULL` **[UQ]** — Ex: Porções, Bebidas, Sobremesas.
* **`descricao`** `VARCHAR(255) NULL`
* **`ativa`** `BOOLEAN NOT NULL DEFAULT TRUE`

#### **`SETOR`**
Representa os setores preparadores no estabelecimento.
* **`id_setor`** `INT AUTO_INCREMENT` **[PK]**
* **`nome`** `VARCHAR(50) NOT NULL` **[UQ]** — Ex: Cozinha, Bar, Salão, Caixa.
* **`descricao`** `VARCHAR(255) NULL`
* **`ativo`** `BOOLEAN NOT NULL DEFAULT TRUE`

#### **`PRODUTO`**
* **`id_produto`** `INT AUTO_INCREMENT` **[PK]**
* **`id_categoria`** `INT NOT NULL` **[FK -> CATEGORIA.id_categoria]**
* **`id_setor`** `INT NOT NULL` **[FK -> SETOR.id_setor]** — Setor produtivo responsável.
* **`nome`** `VARCHAR(100) NOT NULL`
* **`descricao`** `TEXT NULL`
* **`preco_venda`** `DECIMAL(10,2) NOT NULL`
* **`disponivel`** `BOOLEAN NOT NULL DEFAULT TRUE`

---

### 1.3 Módulo: Pessoal e Escalas

#### **`FUNCIONARIO`**
* **`id_funcionario`** `INT AUTO_INCREMENT` **[PK]**
* **`id_setor`** `INT NULL` **[FK -> SETOR.id_setor]**
* **`nome`** `VARCHAR(100) NOT NULL`
* **`funcao`** `VARCHAR(50) NOT NULL` — Ex: Garçom, Cozinheiro, Barman, Caixa, Gerente.
* **`usuario_login`** `VARCHAR(50) NULL` **[UQ]**
* **`senha_hash`** `VARCHAR(255) NULL`
* **`ativo`** `BOOLEAN NOT NULL DEFAULT TRUE`

#### **`ESCALA_FUNCIONARIO`**
* **`id_escala`** `INT AUTO_INCREMENT` **[PK]**
* **`id_funcionario`** `INT NOT NULL` **[FK -> FUNCIONARIO.id_funcionario]**
* **`inicio`** `DATETIME NOT NULL`
* **`fim`** `DATETIME NOT NULL`
* **`funcao_turno`** `VARCHAR(50) NOT NULL`
* **`status`** `VARCHAR(20) NOT NULL DEFAULT 'PREVISTO'` — Ex: `PREVISTO`, `CONFIRMADO`, `REALIZADO`, `FALTA`.

---

### 1.4 Módulo: Estoque e Compras

#### **`ESTOQUE`**
Controle do saldo atual de produtos.
* **`id_estoque`** `INT AUTO_INCREMENT` **[PK]**
* **`id_produto`** `INT NOT NULL` **[UQ]** **[FK -> PRODUTO.id_produto]** — Cardinalidade 1:1 com Produto.
* **`quantidade_atual`** `DECIMAL(10,3) NOT NULL DEFAULT 0.000`
* **`unidade_medida`** `VARCHAR(15) NOT NULL` — Ex: `UN`, `KG`, `L`, `GARRAFA`.
* **`estoque_minimo`** `DECIMAL(10,3) NULL`

#### **`MOVIMENTACAO_ESTOQUE`**
Trilha de auditoria das entradas, baixas e saídas do estoque.
* **`id_movimentacao`** `INT AUTO_INCREMENT` **[PK]**
* **`id_estoque`** `INT NOT NULL` **[FK -> ESTOQUE.id_estoque]**
* **`id_produto`** `INT NOT NULL` **[FK -> PRODUTO.id_produto]**
* **`id_funcionario`** `INT NOT NULL` **[FK -> FUNCIONARIO.id_funcionario]**
* **`tipo`** `VARCHAR(10) NOT NULL` — Ex: `ENTRADA`, `SAIDA`, `AJUSTE`.
* **`quantidade`** `DECIMAL(10,3) NOT NULL`
* **`ocorrido_em`** `DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP`
* **`motivo`** `VARCHAR(255) NOT NULL` — Ex: "Venda pedido #10", "Avaria", "Compra NF 452".

#### **`FORNECEDOR`**
* **`id_fornecedor`** `INT AUTO_INCREMENT` **[PK]**
* **`nome_razao_social`** `VARCHAR(120) NOT NULL`
* **`documento`** `VARCHAR(20) NULL` **[UQ]** — CNPJ ou CPF.
* **`telefone`** `VARCHAR(20) NOT NULL`
* **`email`** `VARCHAR(100) NULL`
* **`endereco`** `VARCHAR(255) NULL`
* **`ativo`** `BOOLEAN NOT NULL DEFAULT TRUE`

#### **`COMPRA`**
* **`id_compra`** `INT AUTO_INCREMENT` **[PK]**
* **`id_fornecedor`** `INT NOT NULL` **[FK -> FORNECEDOR.id_fornecedor]**
* **`id_funcionario`** `INT NOT NULL` **[FK -> FUNCIONARIO.id_funcionario]**
* **`solicitada_em`** `DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP`
* **`prevista_entrega`** `DATE NULL`
* **`status`** `VARCHAR(20) NOT NULL DEFAULT 'SOLICITADA'` — Ex: `SOLICITADA`, `APROVADA`, `RECEBIDA`, `CANCELADA`.
* **`valor_total`** `DECIMAL(10,2) NOT NULL DEFAULT 0.00`

#### **`ITEM_COMPRA`**
* **`id_item_compra`** `INT AUTO_INCREMENT` **[PK]**
* **`id_compra`** `INT NOT NULL` **[FK -> COMPRA.id_compra]**
* **`id_produto`** `INT NOT NULL` **[FK -> PRODUTO.id_produto]**
* **`quantidade_pedida`** `DECIMAL(10,3) NOT NULL`
* **`quantidade_recebida`** `DECIMAL(10,3) NOT NULL DEFAULT 0.000`
* **`custo_unitario`** `DECIMAL(10,2) NOT NULL`

---

### 1.5 Módulo: Financeiro, Caixa e Ocorrências

#### **`PAGAMENTO`**
* **`id_pagamento`** `INT AUTO_INCREMENT` **[PK]**
* **`id_comanda`** `INT NOT NULL` **[FK -> COMANDA.id_comanda]**
* **`forma_pagamento`** `VARCHAR(30) NOT NULL` — Ex: `DINHEIRO`, `CARTAO_CREDITO`, `CARTAO_DEBITO`, `PIX`.
* **`valor`** `DECIMAL(10,2) NOT NULL`
* **`pago_em`** `DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP`
* **`status`** `VARCHAR(20) NOT NULL DEFAULT 'CONCLUIDO'`
* **`referencia_transacao`** `VARCHAR(100) NULL`

#### **`CONTA_PAGAR`**
* **`id_conta_pagar`** `INT AUTO_INCREMENT` **[PK]**
* **`id_fornecedor`** `INT NOT NULL` **[FK -> FORNECEDOR.id_fornecedor]**
* **`id_compra`** `INT NULL` **[FK -> COMPRA.id_compra]**
* **`documento_referencia`** `VARCHAR(50) NULL`
* **`vencimento`** `DATE NOT NULL`
* **`valor`** `DECIMAL(10,2) NOT NULL`
* **`status`** `VARCHAR(20) NOT NULL DEFAULT 'PENDENTE'` — Ex: `PENDENTE`, `PAGO`, `ATRASADO`, `CANCELADO`.
* **`pago_em`** `DATE NULL`

#### **`FECHAMENTO_CAIXA`**
* **`id_fechamento`** `INT AUTO_INCREMENT` **[PK]**
* **`id_funcionario`** `INT NOT NULL` **[FK -> FUNCIONARIO.id_funcionario]**
* **`iniciado_em`** `DATETIME NOT NULL`
* **`encerrado_em`** `DATETIME NOT NULL`
* **`valor_sistema`** `DECIMAL(10,2) NOT NULL`
* **`valor_conferido`** `DECIMAL(10,2) NOT NULL`
* **`diferenca`** `DECIMAL(10,2) NOT NULL DEFAULT 0.00` — Calculado: `valor_conferido - valor_sistema`.
* **`observacao`** `TEXT NULL`

#### **`OCORRENCIA`**
* **`id_ocorrencia`** `INT AUTO_INCREMENT` **[PK]**
* **`id_comanda`** `INT NULL` **[FK -> COMANDA.id_comanda]**
* **`id_funcionario`** `INT NOT NULL` **[FK -> FUNCIONARIO.id_funcionario]**
* **`autorizado_por`** `INT NULL` **[FK -> FUNCIONARIO.id_funcionario]**
* **`registrada_em`** `DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP`
* **`descricao`** `TEXT NOT NULL`
* **`providencia`** `TEXT NOT NULL`
* **`cortesia_valor`** `DECIMAL(10,2) NULL DEFAULT 0.00`

---

## 2. Tabela de Mapeamento de Relacionamentos e Cardinalidades

| Tabela de Origem | Chave Estrangeira (FK) | Tabela de Destino | Chave Primária (PK) | Cardinalidade Lógica | Regra de Integridade |
|---|---|---|---|---|---|
| `COMANDA` | `id_mesa` | `MESA` | `id_mesa` | $N : 1$ | Toda comanda pertence a uma mesa. |
| `PEDIDO` | `id_comanda` | `COMANDA` | `id_comanda` | $N : 1$ | Uma comanda pode ter múltiplos pedidos. |
| `PEDIDO` | `id_funcionario` | `FUNCIONARIO` | `id_funcionario` | $N : 1$ | Identifica o atendente que gerou o pedido. |
| `ITEM_PEDIDO` | `id_pedido` | `PEDIDO` | `id_pedido` | $N : 1$ | Detalha os produtos do pedido. |
| `ITEM_PEDIDO` | `id_produto` | `PRODUTO` | `id_produto` | $N : 1$ | Associa o item vendido ao produto cadastrado. |
| `PRODUTO` | `id_categoria` | `CATEGORIA` | `id_categoria` | $N : 1$ | Associa produto a uma categoria. |
| `PRODUTO` | `id_setor` | `SETOR` | `id_setor` | $N : 1$ | Define o setor responsável pelo preparo. |
| `ESTOQUE` | `id_produto` | `PRODUTO` | `id_produto` | $1 : 1$ (UQ) | Cada produto possui um saldo de estoque único. |
| `MOVIMENTACAO_ESTOQUE` | `id_estoque` | `ESTOQUE` | `id_estoque` | $N : 1$ | Histórico de alterações do saldo. |
| `PAGAMENTO` | `id_comanda` | `COMANDA` | `id_comanda` | $N : 1$ | Permite pagamentos parciais por comanda. |
| `COMPRA` | `id_fornecedor` | `FORNECEDOR` | `id_fornecedor` | $N : 1$ | Associa pedido de compra ao fornecedor. |
| `ITEM_COMPRA` | `id_compra` | `COMPRA` | `id_compra` | $N : 1$ | Detalha os itens de uma compra. |
| `CONTA_PAGAR` | `id_fornecedor` | `FORNECEDOR` | `id_fornecedor` | $N : 1$ | Associa obrigações a pagar ao fornecedor. |
| `ESCALA_FUNCIONARIO` | `id_funcionario` | `FUNCIONARIO` | `id_funcionario` | $N : 1$ | Vincula os turnos ao colaborador. |

**Entrega final:** Relatório Técnico \+ Dicionário de Dados \+ Modelo Conceitual \+ Modelo Lógico \+ Script SQL \+ Massa de Dados \+ Repositório GitHub, seguidos da Apresentação Corporativa Final perante o professor e a turma.

&nbsp;
