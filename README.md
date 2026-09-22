**Entrega 1 — Modelo Conceitual (DER)**
Modelagem de um sistema de gestão de informações — Alberic Gastrobar

Projeto acadêmico — Banco de Dados

Organização estudada: Alberic Gastrobar

Este documento foi elaborado a partir da entrevista de campo fornecida pelo grupo. Informações que não foram informadas na entrevista, como endereço, telefone, site e nomes/RGM dos alunos, não foram inventadas.

---

**Metadados**

Informação                     Registro

Organização:                   Alberic Gastrobar

Natureza:                      Estabelecimento de alimentação e atendimento ao público

Pessoas envolvidas:             14

Área de atuação:                Gastronomia / alimentação / atendimento presencial

Integrantes:                      Eloise Abreu Rodrigues; Yasmin Jimenez Negrão; Fernando Simoes de Menezes; Daniel Baptista dos Santos;                                    Nathaly Pereira

RGM:                              Eloise Abreu Rodrigues — 49482602; Yasmin Jimenez Negrão — 49595407; Fernando Simoes de Menezes —                                         49617133; Daniel Baptista dos Santos — 48821756; Nathaly Pereira — 47287560

Data da pesquisa:                  16/09/2026

**1. Caracterização da Organização**

Nome e natureza da organização

A organização escolhida para o projeto é o Alberic Gastrobar, estabelecimento voltado ao atendimento presencial de clientes, comercialização de alimentos e bebidas e prestação de serviços de alimentação.

Contexto e porte

Segundo a entrevista realizada, o Alberic Gastrobar possui 14 pessoas envolvidas em sua operação. A estrutura de trabalho é dividida entre diferentes funções e setores, incluindo salão, cozinha, ajudantes, barman, gerente e operadora de caixa.

O atendimento ocorre presencialmente. O cliente chega ao estabelecimento, é abordado pelo garçom, encaminhado a uma mesa e recebe o cardápio. Após escolher os produtos, o pedido é registrado por meio de um sistema utilizado em dispositivo móvel, identificado na entrevista como Gom Web. O pedido é então encaminhado aos setores responsáveis.

A operação utiliza comandas numeradas, relacionadas ao número da mesa. No encerramento do atendimento, o pagamento é realizado no caixa local.

O controle de estoque é realizado por meio de planilha, com baixa dos produtos conforme eles são utilizados ou saem do estoque.

Setores identificados

Salão;

Cozinha;

Ajudantes;

Bar/Barman;

Gerência;

Caixa.

Produtos e serviços

A organização trabalha com alimentos e bebidas. Na entrevista, foram citados lanches como produtos de demanda relevante, além de outros itens de alimentação e bebidas comercializados pelo estabelecimento.

Problemas e necessidades identificados

A pessoa entrevistada informou que o estabelecimento não apresenta muitos problemas recorrentes. Quando ocorre alguma situação relacionada a uma mesa ou ao atendimento, a equipe busca solucionar o problema de maneira amigável, podendo oferecer uma cortesia para amenizar a situação.

Mesmo assim, foi identificada uma necessidade de melhoria relacionada à agilidade e facilidade da rotina de trabalho. O principal ponto técnico observado é a existência de diferentes formas de controle: os pedidos são registrados no sistema, enquanto o estoque é controlado por planilha.

O sistema proposto, portanto, deve buscar uma maior integração entre mesas, comandas, pedidos, produtos, setores, estoque e pagamentos.

Justificativa da escolha

O Alberic Gastrobar foi escolhido porque possui processos reais e suficientemente variados para a aplicação dos conceitos de modelagem de banco de dados.

A operação envolve atendimento de clientes, mesas, comandas, pedidos, produtos, produção em setores, controle de estoque e pagamentos. Esses processos geram informações que podem ser estruturadas em entidades e relacionamentos.

Além disso, a utilização de um sistema para pedidos e de planilha para estoque permite identificar uma oportunidade de integração das informações.

Evidências da organização

A existência e o acesso à organização devem ser comprovados pelo grupo com materiais reais da pesquisa, como:

foto da fachada ou do local, caso autorizada;

foto ou registro da visita de campo, caso autorizado;

Endereço: Rua Dr. Raul da Rocha Medeiros, 306 - Tatuapé, São Paulo - SP, CEP 03071-100;

Telefone: (11) 2362-7392;

Rede social: Instagram — @alberic_gastrobar;

Foto da fachada: registrada pelo grupo durante a pesquisa de campo;

identificação do responsável entrevistado, quando autorizado.

Dados verificados pelo grupo

As informações de endereço, telefone e rede social acima foram fornecidas pelo grupo como dados verificados da organização. A foto abaixo corresponde à fachada do estabelecimento registrada durante a pesquisa de campo.

<img width="1600" height="1200" alt="image" src="https://github.com/user-attachments/assets/6c420298-6589-4359-9bf4-7ba148c041c1" />

---

**2. Processos de Negócio**
**2.1 Atendimento**

Fluxo:

Cliente chega → Garçom aborda → Cliente é encaminhado à mesa → Cardápio é apresentado → Cliente escolhe produtos → Pedido é registrado.

2.2 Registro do pedido

O garçom registra o pedido utilizando dispositivo móvel e o sistema Gom Web informado na entrevista. O pedido é associado à comanda e à mesa e encaminhado aos setores correspondentes.

2.3 Produção

Após o registro, os pedidos chegam aos setores responsáveis. A produção é organizada por funções e os colaboradores executam as atividades conforme os pedidos recebidos.

2.4 Comanda

A comanda possui uma numeração utilizada para identificar o consumo. O número da comanda é associado ao número da mesa, permitindo que os garçons identifiquem a qual atendimento o pedido pertence.

2.5 Fechamento e pagamento

Quando o atendimento termina, o cliente realiza o pagamento no caixa local. As informações de pagamento ficam registradas no computador.

2.6 Controle de estoque

O estoque é controlado em planilha. Conforme os produtos são utilizados ou saem, é realizada a baixa correspondente.

2.7 Tratamento de ocorrências

Quando ocorre um problema no atendimento, a equipe procura resolver a situação de maneira amigável. Uma das medidas mencionadas na entrevista é oferecer uma cortesia ao cliente para amenizar a ocorrência.
---

**3. Requisitos do Sistema**

**3.1 Requisitos Funcionais**

Código

Requisito

RF01

O sistema deve permitir cadastrar mesas.

RF02

O sistema deve permitir consultar a situação das mesas.

RF03

O sistema deve permitir abrir uma comanda para uma mesa.

RF04

O sistema deve permitir registrar pedidos em uma comanda.

RF05

O sistema deve permitir incluir vários itens em um pedido.

RF06

O sistema deve permitir registrar a quantidade de cada item.

RF07

O sistema deve permitir encaminhar pedidos aos setores responsáveis.

RF08

O sistema deve permitir acompanhar a situação dos pedidos.

RF09

O sistema deve permitir cadastrar produtos.

RF10

O sistema deve permitir cadastrar categorias de produtos.

RF11

O sistema deve permitir relacionar produtos aos setores responsáveis.

RF12

O sistema deve permitir consultar produtos disponíveis.

RF13

O sistema deve permitir registrar entradas no estoque.

RF14

O sistema deve permitir registrar saídas do estoque.

RF15

O sistema deve permitir consultar o estoque atual.

RF16

O sistema deve permitir registrar funcionários e suas funções.

RF17

O sistema deve permitir fechar uma comanda.

RF18

O sistema deve permitir registrar pagamentos.

RF19

O sistema deve permitir consultar o histórico de pagamentos.

RF20

O sistema deve permitir registrar ocorrências de atendimento.

RF21

O sistema deve permitir registrar uma cortesia concedida em uma ocorrência.

RF22

O sistema deve permitir consultar informações gerenciais de vendas, pedidos e estoque.

**3.2 Requisitos Não Funcionais**

Código

Requisito

RNF01

O sistema deve possuir interface simples e adequada ao uso durante o atendimento.

RNF02

O registro de pedidos deve ocorrer rapidamente.

RNF03

O sistema deve proteger as informações por meio de autenticação e controle de acesso.

RNF04

O sistema deve manter a integridade dos relacionamentos entre comanda, pedido, item, produto e pagamento.

RNF05

O sistema deve estar disponível durante o horário de funcionamento do estabelecimento.

RNF06

O sistema deve permitir rastrear alterações relevantes em pedidos e estoque.

RNF07

O banco de dados deve suportar o crescimento da quantidade de produtos, pedidos e movimentações.

RNF08

O sistema deve evitar duplicidade de identificadores de mesas, comandas e registros.
---

**4. Regras de Negócio**

Regras operacionais

RN01. Toda comanda deve estar associada a uma mesa durante o atendimento.

RN02. Uma mesa pode possuir diferentes comandas ao longo do tempo.

RN03. Uma comanda pode possuir vários pedidos.

RN04. Todo pedido deve pertencer a uma comanda.

RN05. Todo pedido deve possuir pelo menos um item.

RN06. Todo item de pedido deve estar relacionado a um produto.

RN07. A quantidade de um item de pedido deve ser maior que zero.

RN08. Um produto deve possuir um preço de venda registrado.

RN09. Os pedidos devem ser encaminhados ao setor responsável pela preparação.

RN10. Uma comanda deve ser fechada antes de ser considerada encerrada.

RN11. O pagamento deve estar relacionado à comanda correspondente.

RN12. Toda movimentação de estoque deve indicar se representa entrada ou saída.

RN13. A quantidade movimentada deve ser maior que zero.

RN14. O estoque não deve apresentar quantidade negativa.

RN15. Quando um produto é utilizado ou sai do estoque, a movimentação correspondente deve ser registrada.

RN16. Uma ocorrência deve estar relacionada ao atendimento quando a situação envolver uma mesa ou comanda.

RN17. Quando houver uma cortesia, ela poderá ser registrada na ocorrência correspondente.

RN18. Produtos indisponíveis devem ser comunicados ao cliente e, quando possível, substituídos por outra opção.

Restrições organizacionais

A divisão entre salão, cozinha, bar e demais funções exige que o pedido seja encaminhado ao setor adequado.

A utilização de comandas numeradas e sua associação com mesas é necessária para que os garçons consigam identificar corretamente o atendimento.

O controle de estoque atualmente realizado por planilha demonstra a necessidade de manter registros de entradas e saídas e possibilitar futura integração com o sistema de pedidos.

---

**5. Dicionário de Dados Conceitual**

O dicionário completo está no arquivo:

Dicionario/dicionario_dados.html

As entidades utilizadas são:

MESA

COMANDA

PEDIDO

ITEM_PEDIDO

PRODUTO

CATEGORIA

SETOR

FUNCIONARIO

ESTOQUE

MOVIMENTACAO_ESTOQUE

PAGAMENTO

OCORRENCIA
---

**5. Dicionário de Dados Conceitual**

O dicionário completo está no arquivo:

Dicionario/dicionario_dados.html

As entidades utilizadas são:

MESA

COMANDA

PEDIDO

ITEM_PEDIDO

PRODUTO

CATEGORIA

SETOR

FUNCIONARIO

ESTOQUE

MOVIMENTACAO_ESTOQUE

PAGAMENTO

OCORRENCIA
---

**7. Diagrama Entidade-Relacionamento (DER)**

O DER está disponível em:

DER/der_alberic_gastrobar.png

Cardinalidades

Relacionamento            Cardinalidade

MESA — COMANDA -                 1

COMANDA — PEDIDO -               1

PEDIDO — ITEM_PEDIDO -           1

PRODUTO — ITEM_PEDIDO -          1

CATEGORIA — PRODUTO -            1

SETOR — PRODUTO -                1

FUNCIONARIO — PEDIDO -           1

SETOR — PEDIDO -                 1

PRODUTO — ESTOQUE -              1:1

ESTOQUE — MOVIMENTACAO_ESTOQUE - 1

PRODUTO — MOVIMENTACAO_ESTOQUE - 1

COMANDA — PAGAMENTO -            1

COMANDA — OCORRENCIA -           1

FUNCIONARIO — OCORRENCIA -       1
---

**8. Justificativa Técnica**

A entidade COMANDA foi separada de PEDIDO porque uma mesma comanda pode receber vários pedidos durante o atendimento. Essa separação representa melhor o funcionamento observado.

A entidade ITEM_PEDIDO foi criada porque um pedido pode conter vários produtos. Dessa forma, cada item registra individualmente o produto, a quantidade e o preço praticado no momento do pedido.

A entidade PRODUTO foi separada de CATEGORIA para evitar repetição de informações. Vários produtos podem pertencer a uma mesma categoria.

A entidade SETOR representa a divisão operacional observada no estabelecimento. A entrevista indicou a existência de cozinha, bar, salão e outras funções, tornando relevante identificar o setor responsável pelo atendimento ou produção.

A entidade FUNCIONARIO permite relacionar os registros aos responsáveis pelas atividades, principalmente no lançamento dos pedidos e no tratamento de ocorrências.

A entidade ESTOQUE representa a quantidade disponível dos produtos, enquanto MOVIMENTACAO_ESTOQUE registra o histórico de entradas e saídas. Essa decisão é especialmente importante porque o controle atual é realizado em planilha.

A entidade PAGAMENTO foi separada de COMANDA para manter as informações financeiras organizadas e permitir futura expansão para diferentes formas de pagamento.

A entidade OCORRENCIA representa os problemas de atendimento mencionados na entrevista. Mesmo que sejam pouco frequentes, o registro permite analisar situações e eventuais cortesias concedidas.

As cardinalidades foram escolhidas para representar a possibilidade de vários atendimentos, pedidos, itens e movimentações ao longo do funcionamento do estabelecimento.

---

**9. Uso de Inteligência Artificial**

Ferramenta e etapa

Ferramenta: ChatGPT.

Etapas: organização das informações da entrevista, identificação de processos, elaboração dos requisitos, regras de negócio, entidades, atributos, relacionamentos, cardinalidades, justificativa técnica e revisão textual.

Motivação

A IA foi utilizada como ferramenta de apoio para organizar as informações coletadas na pesquisa de campo e transformá-las em uma documentação estruturada de modelagem de banco de dados.

Prompt utilizado

"Com base na entrevista realizada com o Alberic Gastrobar, organize as informações da pesquisa de campo e ajude a identificar processos, requisitos funcionais e não funcionais, regras de negócio, entidades, atributos, relacionamentos e cardinalidades para uma Entrega 1 de modelagem conceitual de banco de dados."

Resposta recebida

A IA organizou os processos de atendimento, pedidos, comandas, produção, estoque, pagamentos e ocorrências e propôs uma estrutura inicial para o modelo conceitual.

Fontes consultadas e verificadas

A fonte principal das informações específicas da organização foi a entrevista de campo realizada pelo grupo. As sugestões produzidas pela IA foram comparadas com as informações fornecidas pelo entrevistado.

Trechos rejeitados ou corrigidos

Informações que não foram confirmadas pela entrevista não foram tratadas como fatos. Dados como endereço, telefone, site, quantidade de unidades e nomes de pessoas não foram inventados.

Justificativa da escolha final

Foram utilizadas as sugestões compatíveis com os processos descritos na entrevista. O modelo final deverá ser validado pelo grupo antes da entrega.

Reflexão crítica

A IA pode sugerir estruturas comuns a outros restaurantes que não necessariamente fazem parte da realidade do Alberic Gastrobar. Por esse motivo, a pesquisa de campo continua sendo a fonte principal para validar os processos e regras.
