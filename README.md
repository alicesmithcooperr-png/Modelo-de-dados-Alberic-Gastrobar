# Entrega 1 — Modelo Conceitual (DER) 
### Modelagem de um sistema de gestão de informações para o Alberici Gastrobar

## Metadados

- **Integrantes do Grupo (Nomes e RGM):**
  -Eloise Abreu Rodrigues — 49482602
  -Yasmin Jimenez Negrão — 49595407
  -Fernando Simoes de Menezes — 49617133
  -Daniel Baptista dos Santos — 48821756
  -Nathaly Pereira — 47287560

---

## 1. Caracterização da Organização

- **Nome e natureza da organização:** 
  Alberici Gastrobar — Empresa comercial do ramo de alimentação e bebidas (gastronomia e entretenimento noturno/bar).

- **Contexto e porte:** 
  Organização de pequeno porte com fins lucrativos. Opera com salão para atendimento presencial (capacidade média de 15 a 20 mesas), atendimento no balcão e serviço de bar. A equipe é composta por cerca de 8 a 12 colaboradores (gerente, atendentes/garçons, barman, cozinheiros e operador de caixa).

- **Problemas e necessidades identificados:** 
  A organização sofre com atrasos e erros operacionais decorrentes da anotação manual de pedidos em blocos de papel e fichas de comanda física. Os principais gargalos incluem: perda ou extravio de comandas de clientes, atrasos na comunicação entre o salão e a cozinha/bar, inconsistências na soma da conta ao fechar a Mesa/Comanda, e falta de controle exato sobre o estoque de bebidas e insumos alimentícios, resultando em perdas de insumos por falta de baixa automatizada.

- **Justificativa da escolha:** 
  O Alberici Gastrobar apresenta o equilíbrio ideal para a modelagem: possui diversidade suficiente de processos operacionais integrados (atendimento, produção, estoque, caixa) sem complexidade excessiva de uma grande corporação. Além disso, a facilidade de acesso presencial garantida pela equipe permitiu o levantamento detalhado das rotinas operacionais *in loco*.

- **Evidências da organização:** 
  - **Endereço Completo:** Rua Exemplo do Gastrobar, 123 — Bairro Central, Cidade - SP.

  - **Contato / Responsável:** Tratar com a Gerência Geral.

  - **Registro visual e presença:** Fotos da visita de campo e das fichas de comanda física atualmente utilizadas anexadas no diretório `/docs/evidencias/` deste repositório.

---

## 2. Processos de Negócio

- **Principais processos mapeados:**

  1. **Abertura e Atendimento de Mesa/Comanda:** Recepção do cliente, vinculação do cliente ou mesa a um número identificador de comanda.

  2. **Registro de Pedido:** Garçom registra os itens solicitados (bebidas/pratos) vinculados à comanda e ao atendente.

  3. **Encaminhamento e Produção:** Divisão automática do pedido por setor de preparo (Cozinha para pratos; Bar para bebidas).

  4. **Controle e Baixa de Estoque:** Atualização e dedução de insumos/produtos do estoque conforme a confirmação dos itens vendidos.

  5. **Fechamento e Liquidação de Conta:** Consolidação de todos os pedidos da comanda, aplicação de taxa de serviço (opcional) e processamento do pagamento em múltiplos meios (Dinheiro, Cartão, PIX).

  6. **Tratamento de Exceções e Cancelamentos:** Registro de devoluções ou cancelamento de itens por falha de preparo ou indisponibilidade, exigindo justificativa.

---

## 3. Requisitos do Sistema

### 3.1 Requisitos Funcionais

- **RF01:** O sistema deve permitir o cadastro de funcionários, categorias de produtos, itens do cardápio e insumos do estoque.
- **RF02:** O sistema deve permitir a abertura, consulta, alteração e fechamento de comanda/mesa.
- **RF03:** O sistema deve permitir o registro de pedidos contendo um ou mais itens, associando-os à comanda, à mesa e ao funcionário responsável.
- **RF04:** O sistema deve permitir o cancelamento justificado de itens do pedido mediante permissão de perfil de gerência.
- **RF05:** O sistema deve realizar a baixa automática dos itens no estoque no momento da confirmação do pedido.
- **RF06:** O sistema deve calcular o valor total acumulado da comanda e permitir pagamentos parciais ou totais por diferentes meios de pagamento (Dinheiro, Débito, Crédito, PIX).

### 3.2 Requisitos Não Funcionais

- **RNF01 (Desempenho):** As consultas de saldo e inclusão de itens na comanda devem ser processadas em tempo inferior a 2 segundos na rede local do estabelecimento.
- **RNF02 (Usabilidade):** A interface de registro de pedidos deve ser otimizada para navegação rápida em dispositivos touch (tablets/smartphones).
- **RNF03 (Segurança e Restrição de Acesso):** O sistema deve implementar controle de acesso baseado em papéis (RBAC), restringindo funções críticas (como cancelamentos e relatórios financeiros) a gerentes.
- **RNF04 (Disponibilidade):** O sistema deve operar de forma ininterrupta durante todo o horário de funcionamento do bar, com mecanismo de backup diário dos dados operacionais.

---

## 4. Regras de Negócio

- **Regras Operacionais:**

  - **RO01 (Obrigatoriedade de Comanda):** Nenhum pedido pode ser lançado no sistema sem estar vinculado a uma comanda/mesa aberta.

  - **RO02 (Disponibilidade de Estoque):** O sistema não deve permitir o lançamento de produtos cujo estoque atual seja zero, emitindo um alerta de insumo esgotado.

  - **RO03 (Fechamento com Saldo Zerado):** Uma comanda só pode ser encerrada/liberada após a quitação total do valor acumulado dos seus pedidos.

  - **RO04 (Autorização de Cancelamento):** A remoção de itens já enviados à produção exige autenticação prévia do perfil de Gerente e preenchimento de justificativa.

- **Restrições Organizacionais:**
  - **RC01 (Conformidade Fiscal e Alcoólica):** Venda de bebidas alcoólicas é restrita a clientes maiores de 18 anos e deve seguir as alíquotas fiscais vigentes.

  - **RC02 (Limite de Ocupação por Mesa):** A associação de comandas por mesa deve respeitar a capacidade máxima física cadastrada para o arranjo de mesas do salão.

---

## 5. Dicionário de Dados Conceitual (Preliminar)

### Entidade: MESA
| Atributo | Descrição | Regra de negócio associada |
|----------|-----------|------------------------------|
| `id_mesa` | Identificador único da mesa no salão | Chave Primária. Numérico inteiro positivo. |
| `numero_mesa` | Número de identificação visível da mesa | Obrigatório, Único. |
| `capacidade` | Quantidade máxima de lugares | Obrigatório. Valor inteiro maior que 0. |
| `status_mesa` | Situação da mesa (Livre, Ocupada, Reservada) | Obrigatório. Padrão: 'Livre'. |

### Entidade: COMANDA
| Atributo | Descrição | Regra de negócio associada |
|----------|-----------|------------------------------|
| `id_comanda` | Identificador único da comanda | Chave Primária. Numérico inteiro. |
| `codigo_identificador` | Código impresso ou tag da comanda física | Obrigatório, Único. |
| `data_hora_abertura` | Registra a data e hora em que a comanda foi aberta | Obrigatório. Preenchimento automático. |
| `data_hora_fechamento` | Registra a data e hora do encerramento da comanda | Opcional (nulo enquanto aberta). |
| `status_comanda` | Estado atual da comanda (Aberta, Fechada, Cancelada) | Obrigatório. Padrão: 'Aberta'. |

### Entidade: FUNCIONARIO
| Atributo | Descrição | Regra de negócio associada |
|----------|-----------|------------------------------|
| `id_funcionario` | Identificador único do funcionário | Chave Primária. Numérico inteiro. |
| `nome` | Nome completo do funcionário | Obrigatório. Texto. |
| `cargo` | Função exercida (Garçom, Barman, Cozinheiro, Gerente) | Obrigatório. |
| `cpf` | Documento de identificação (exemplo fictício no sistema) | Único, Formato válido (exemplo fictício: 546.837.883.09). |

### Entidade: PRODUTO
| Atributo | Descrição | Regra de negócio associada |
|----------|-----------|------------------------------|
| `id_produto` | Identificador único do produto do cardápio | Chave Primária. Numérico inteiro. |
| `nome_produto` | Nome do item alimentício ou bebida | Obrigatório, Único. |
| `preco_venda` | Valor de venda praticado | Obrigatório. Valor decimal positivo (> 0.00). |
| `quantidade_estoque` | Saldo atual disponível do item | Obrigatório. Numérico inteiro (RO02). |
| `setor_preparo` | Local de produção do item (Cozinha, Bar, Dispensário) | Obrigatório. |

### Entidade: PEDIDO
| Atributo | Descrição | Regra de negócio associada |
|----------|-----------|------------------------------|
| `id_pedido` | Identificador único do lote do pedido | Chave Primária. Numérico inteiro. |
| `data_hora_pedido` | Data e hora exata da solicitação | Obrigatório. Preenchimento automático. |
| `status_pedido` | Fase do pedido (Pendente, Em Preparo, Entregue, Cancelado) | Obrigatório. Padrão: 'Pendente'. |

### Entidade: ITEM_PEDIDO
| Atributo | Descrição | Regra de negócio associada |
|----------|-----------|------------------------------|
| `id_item_pedido` | Identificador único da linha do item do pedido | Chave Primária. Numérico inteiro. |
| `quantidade` | Número de unidades solicitadas do produto | Obrigatório. Inteiro maior que 0. |
| `preco_unitario` | Preço praticado no momento da venda | Obrigatório. Histórico de valor. |
| `observacao` | Especificações do cliente (ex.: "sem gelo", "bem passado") | Texto opcional. |

### Entidade: PAGAMENTO
| Atributo | Descrição | Regra de negócio associada |
|----------|-----------|------------------------------|
| `id_pagamento` | Identificador único do registro de pagamento | Chave Primária. Numérico inteiro. |
| `valor_pago` | Quantia quitada na transação | Obrigatório. Decimal positivo. |
| `forma_pagamento` | Meio utilizado (Dinheiro, Débito, Crédito, PIX) | Obrigatório. |
| `data_hora_pagamento` | Instante da liquidação da transação | Obrigatório. |

---

## 6. Modelagem Conceitual

- **Entidades reconhecidas:**

  - **MESA:** Representa a estrutura física do salão utilizada pelos clientes.

  - **COMANDA:** Controla a conta e o saldo acumulado de consumo de um cliente ou grupo.

  - **FUNCIONARIO:** Registra quem abriu a comanda, anotou os pedidos ou efetuou o pagamento.

  - **PRODUTO:** Representa o catálogo de itens comercializados pelo gastrobar e seu nível de estoque.

  - **PEDIDO:** Agrupa uma solicitação feita em um determinado momento para a comanda.

  - **ITEM_PEDIDO:** Entidade associativa que detalha os produtos específicos e suas quantidades em cada pedido.

  - **PAGAMENTO:** Registra as transações financeiras de quitação da comanda.

- **Atributos e classificações:**

  - *MESA:* `id_mesa` (Identificador), `numero_mesa` (Simples/Monovalorado), `capacidade` (Simples), `status_mesa` (Simples).

  - *COMANDA:* `id_comanda` (Identificador), `codigo_identificador` (Simples), `data_hora_abertura` (Simples), `data_hora_fechamento` (Simples/Opcional), `status_comanda` (Simples).

  - *FUNCIONARIO:* `id_funcionario` (Identificador), `nome` (Simples), `cargo` (Simples), `cpf` (Simples).

  - *PRODUTO:* `id_produto` (Identificador), `nome_produto` (Simples), `preco_venda` (Simples), `quantidade_estoque` (Simples), `setor_preparo` (Simples).

  - *PEDIDO:* `id_pedido` (Identificador), `data_hora_pedido` (Simples), `status_pedido` (Simples).

  - *ITEM_PEDIDO:* `id_item_pedido` (Identificador), `quantidade` (Simples), `preco_unitario` (Simples), `observacao` (Simples/Opcional).

  - *PAGAMENTO:* `id_pagamento` (Identificador), `valor_pago` (Simples), `forma_pagamento` (Simples), `data_hora_pagamento` (Simples).

- **Relacionamentos pertinentes:**

  - **MESA e COMANDA (1:N):** Uma mesa pode ter várias comandas ao longo do tempo, mas uma comanda aberta está associada a no máximo uma mesa por vez.

  - **FUNCIONARIO e PEDIDO (1:N):** Um funcionário (garçom) pode anotar vários pedidos; cada pedido é anotado por exatamente um funcionário.

  - **COMANDA e PEDIDO (1:N):** Uma comanda pode conter múltiplos pedidos ao longo da noite; cada pedido pertence a apenas uma comanda.

  - **PEDIDO e ITEM_PEDIDO (1:N):** Um pedido é composto por um ou mais itens de pedido; cada item pertence a apenas um pedido.

  - **PRODUTO e ITEM_PEDIDO (1:N):** Um produto do cardápio pode constar em múltiplos itens de pedidos; cada item de pedido refere-se a apenas um produto.

  - **COMANDA e PAGAMENTO (1:N):** Uma comanda pode ser quitada através de um ou mais pagamentos (ex.: conta dividida entre amigos); cada pagamento refere-se a apenas uma comanda.

- **Restrições e políticas organizacionais aplicadas ao modelo:**

  - O isolamento entre a entidade `PEDIDO` e a entidade `ITEM_PEDIDO` garante que o histórico de preços não seja alterado caso o preço de venda do `PRODUTO` no cardápio mude no futuro.

---

## 7. Diagrama Entidade-Relacionamento (DER)

- **Imagem do Diagrama Conceitual:**
  *(O arquivo contendo a imagem do DER conceitual está localizado em `./der
