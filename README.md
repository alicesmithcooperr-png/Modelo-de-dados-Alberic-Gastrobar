*Entrega 1 — Modelo Conceitual (DER):*

Modelagem de um sistema de gestão de informações — Alberic Gastrobar
Projeto acadêmico — Banco de Dados

Metadados:
Informação:	               Registro:
Organização              	 Alberic Gastrobar
Natureza	                 Estabelecimento de alimentação e atendimento ao público
Pessoas envolvidas	       14, conforme informação obtida na pesquisa de campo
Endereço	                 Rua Dr. Raul da Rocha Medeiros, 306 — Tatuapé, São Paulo/SP, CEP 03071-100
Telefone	                 (11) 2362-7392
Instagram	                 @alberic_gastrobar
Data da pesquisa	         16/09/2026
Integrantes	               Daniel Baptista dos Santos; Eloise Abreu Rodrigues; Fernando Simoes de Menezes; Nathaly                                Pereira; Yasmin Jimenez Negrão
RGM — 48821756             Daniel Baptista dos Santos
RGM — 49482602             Eloise Abreu Rodrigues	
RGM — 49617133             Fernando Simoes de Menezes
RGM — 47287560             Nathaly Pereira	
RGM — 49595407             Yasmin Jimenez Negrão

Entrevistada/Função	       Não informado no material disponibilizado; preencher após confirmação com o grupo.
Volume de atendimentos	   Não informado na entrevista/material disponibilizado.


*1. Caracterização da organização*
*1.1 Nome, natureza e porte:*
O Alberic Gastrobar é um estabelecimento de alimentação e atendimento presencial, com comercialização de alimentos e bebidas. Segundo a pesquisa de campo, há 14 pessoas envolvidas na operação, distribuídas entre salão, cozinha, ajudantes, bar/barman, gerência e caixa.

*1.2 Rotina observada*
O cliente chega ao estabelecimento, é recebido por um garçom e encaminhado a uma mesa. O cardápio é apresentado e o pedido é registrado por dispositivo móvel no sistema Gom Web, conforme informado na entrevista. Os pedidos são direcionados aos setores responsáveis. A comanda numerada é associada à mesa e o pagamento ocorre no caixa.
O estoque é controlado atualmente por planilha, com baixa dos produtos utilizados ou retirados. Essa diferença entre o sistema de pedidos e o controle de estoque constitui uma oportunidade de integração.

*1.3 Necessidade e justificativa*
A necessidade identificada é facilitar e agilizar a rotina por meio de informações integradas sobre mesas, comandas, pedidos, produtos, setores, estoque e pagamentos. A equipe também relatou que ocorrências de atendimento são resolvidas de forma amigável e que, em alguns casos, pode ser oferecida uma cortesia.

*1.4 Evidências*
Endereço: Rua Dr. Raul da Rocha Medeiros, 306 — Tatuapé, São Paulo/SP. Telefone: (11) 2362-7392. Instagram: @alberic_gastrobar.
Foto da fachada: https://github.com/user-attachments/assets/6c420298-6589-4359-9bf4-7ba148c041c1
Foto da pesquisa de campo: https://github.com/user-attachments/assets/a7e627b9-ca7c-4fa5-beff-465971608744
A identificação da pessoa entrevistada, sua função e a confirmação de que aparece na foto devem ser preenchidas pelo grupo, pois essas informações não constam no material fornecido.

*2. Processos de negócio*
Os processos abaixo separam o que foi observado na pesquisa daquilo que é recomendado para completar o escopo do sistema. Os processos de compras, contas a pagar, fechamento de caixa, manutenção do cardápio e escala são propostas de modelagem e precisam ser confirmados com o estabelecimento antes de serem apresentados como práticas atuais.

2.1 Recepção e acomodação
O garçom recebe o cliente, verifica a disponibilidade de mesa e o encaminha para acomodação. A mesa deve ser identificada no sistema como disponível ou ocupada. (Observado em campo.)

*2.2 Abertura e associação da comanda*
A comanda é aberta e associada à mesa para reunir o consumo daquele atendimento. Uma mesa pode ter comandas diferentes ao longo do tempo, mas cada comanda aberta deve identificar o atendimento correspondente. (Baseado na rotina informada.)

*2.3 Registro do pedido*
O garçom registra os produtos e respectivas quantidades pelo dispositivo móvel/sistema Gom Web. O pedido deve ficar associado à comanda e conter ao menos um item antes de ser enviado. (Observado e regra proposta.)

*2.4 Encaminhamento e produção por setor*
Após o envio, os itens são direcionados ao setor responsável, como cozinha ou bar. O setor acompanha os pedidos recebidos e atualiza o andamento da preparação. O detalhamento dos estados do pedido deve ser validado com a equipe. (Encaminhamento observado; estados propostos.)

*2.5 Conferência e entrega à mesa*
Como processo recomendado, a equipe confere os itens preparados com o pedido e entrega na mesa correta, atualizando o status para entregue. O procedimento atual de conferência não foi detalhado na entrevista.

*2.6 Manutenção do cardápio e preços*
Processo proposto: usuário autorizado cadastra ou atualiza produtos, categorias, preços, disponibilidade e setor responsável. Alterações devem preservar o histórico de itens já vendidos.

*2.7 Tratamento de indisponibilidade e cancelamentos*
Se um produto estiver indisponível, a equipe comunica o cliente e, quando possível, oferece substituição. Cancelamentos de itens já enviados devem registrar motivo e responsável e, se necessário, avisar o setor de produção. A indisponibilidade foi mencionada; o fluxo de cancelamento é uma proposta.

*2.8 Fechamento da conta e pagamento*
Ao terminar o atendimento, o cliente solicita a conta e o caixa confere os itens e valores da comanda. O sistema registra um ou mais pagamentos, permite identificar eventual divisão da conta e só encerra a comanda quando o saldo estiver quitado. O pagamento no caixa foi observado; divisão de conta é proposta.

*2.9 Controle de estoque*
O estoque é controlado por planilha e recebe baixas quando produtos são utilizados ou saem. No sistema proposto, entradas e saídas serão registradas com produto, quantidade, data, motivo e responsável, permitindo consultar saldo e histórico. (Controle atual observado; integração proposta.)

*2.10 Cadastro de fornecedores*
Processo proposto a validar: cadastrar fornecedor com razão/nome, CNPJ/CPF quando aplicável, contatos, endereço e situação cadastral, evitando duplicidade.

*2.11 Cotação e pedido de compra*
Processo proposto a validar: registrar necessidade de reposição, consultar cotações, selecionar fornecedor conforme critérios aprovados e gerar pedido de compra com itens, quantidades, preços e previsão de entrega.

*2.12 Recebimento de mercadorias*
Processo proposto a validar: comparar mercadorias recebidas com o pedido e documento do fornecedor, registrar divergências, quantidades aceitas e validade/lote quando aplicável; somente após conferência lançar a entrada no estoque.

*2.13 Contas a pagar*
Processo proposto a validar: registrar títulos de fornecedores, vencimentos, valores e situação de pagamento, relacionando-os à compra e ao documento fiscal correspondente.

*2.14 Fechamento diário de caixa*
Processo proposto a validar: ao fim do expediente, comparar valores registrados no sistema com dinheiro, cartões e demais meios recebidos, registrar diferenças e submeter a conferência à gerência.

*2.15 Escala e gestão de funcionários*
Processo proposto a validar: manter cadastro de funcionários, função, setor e situação; permitir que pessoa autorizada organize escalas e consulte os responsáveis por cada turno.

*2.16 Registro de ocorrências e cortesias*
Quando há problema relacionado a uma mesa ou atendimento, a equipe procura resolver amigavelmente e pode oferecer cortesia. O sistema deve registrar descrição, comanda, responsável, decisão e eventual cortesia. A autorização e os limites precisam ser definidos pelo estabelecimento.


*3. Requisitos do sistema:*
*3.1 Requisitos funcionais*

Código	Requisito funcional
RF01	Cadastrar e consultar mesas e sua situação.
RF02	Abrir, consultar e encerrar comandas associadas a mesas.
RF03	Registrar pedidos vinculados a uma comanda.
RF04	Adicionar um ou mais itens e suas quantidades a um pedido.
RF05	Impedir o envio de pedido sem itens ou com quantidade inválida.
RF06	Encaminhar os itens aos setores responsáveis.
RF07	Acompanhar o status do pedido, incluindo recebido, em preparo, pronto e entregue; validar os estados com a equipe.
RF08	Cadastrar produtos, categorias, preços e disponibilidade.
RF09	Relacionar cada produto ao setor de preparação responsável.
RF10	Registrar cancelamentos e seus motivos, com identificação do responsável.
RF11	Registrar entradas e saídas de estoque com data, quantidade e motivo.
RF12	Consultar o saldo e o histórico de movimentações de estoque.
RF13	Cadastrar fornecedores e seus dados de contato.
RF14	Registrar cotações e pedidos de compra.
RF15	Registrar recebimento de mercadorias e divergências em relação ao pedido.
RF16	Registrar contas a pagar, vencimentos e situação de quitação.
RF17	Cadastrar funcionários, funções e setores.
RF18	Registrar pagamentos vinculados à comanda e permitir múltiplos pagamentos.
RF19	Exibir saldo pendente e impedir encerramento da comanda antes da quitação, salvo regra autorizada formalmente.
RF20	Registrar fechamento diário de caixa e diferenças encontradas.
RF21	Registrar ocorrências, providências e cortesias.
RF22	Consultar relatórios gerenciais de vendas, pedidos, estoque, compras e pagamentos.

*3.2 Requisitos não funcionais:*
*Código	Requisito não funcional*
RNF01	A interface deve ser simples e adequada ao uso durante o atendimento.
RNF02	O registro e envio de pedidos deve ocorrer com rapidez compatível com a operação.
RNF03	O sistema deve exigir autenticação e controlar o acesso conforme a função do usuário.
RNF04	O banco deve preservar a integridade dos relacionamentos e dos valores financeiros.
RNF05	O sistema deve estar disponível durante o horário de funcionamento, conforme infraestrutura contratada.
RNF06	Alterações relevantes em pedidos, estoque, preços e pagamentos devem manter trilha de auditoria.
RNF07	A estrutura deve permitir crescimento da quantidade de produtos, pedidos e movimentações.
RNF08	Identificadores de mesas, comandas, pedidos e registros devem ser únicos.

*4. Regras de negócio:*

*Código	Regra de negócio*
RN01	Toda comanda aberta deve estar associada a uma mesa.
RN02	Uma mesa pode estar associada a várias comandas ao longo do tempo; a regra de comandas simultâneas deve ser confirmada com o estabelecimento.
RN03	Uma comanda pode conter vários pedidos.
RN04	Todo pedido pertence a uma única comanda.
RN05	Todo pedido enviado deve possuir pelo menos um item.
RN06	A quantidade de cada item deve ser maior que zero.
RN07	Todo item de pedido deve referenciar um produto cadastrado.
RN08	O preço de venda do produto deve estar definido antes de sua disponibilização; o preço praticado no pedido deve ser preservado como histórico.
RN09	Cada item deve ser encaminhado ao setor responsável pela preparação.
RN10	Produto indisponível deve ser comunicado ao cliente e, quando possível, substituído mediante concordância.
RN11	O cancelamento de item já enviado deve registrar motivo, data e responsável e comunicar o setor envolvido.
RN12	A comanda só deve ser encerrada quando não houver saldo pendente, exceto se houver procedimento formal de autorização de exceção.
RN13	O sistema deve registrar a forma, o valor, a data e a comanda de cada pagamento.
RN14	O sistema deve permitir pagamentos parciais e divisão da conta sem perder o vínculo com a comanda original.
RN15	A taxa de serviço de 10%, se adotada pelo estabelecimento, deve ser informada ao cliente e calculada de forma transparente; confirmar política, exceções e forma de cobrança com a gerência antes da implantação.
RN16	As formas de pagamento aceitas devem ser cadastradas/configuradas pelo responsável e informadas ao cliente. As formas efetivamente aceitas pelo Alberic não foram informadas no material.
RN17	Cortesia deve ser registrada com motivo, valor estimado, funcionário solicitante e responsável que autorizou; níveis de autorização e limites dependem de definição da gerência.
RN18	Toda movimentação de estoque deve ser classificada como entrada ou saída.
RN19	A quantidade movimentada deve ser maior que zero.
RN20	O saldo de estoque não pode ficar negativo; ajustes devem ser registrados e justificados.
RN21	Toda saída de estoque deve ter registro correspondente e motivo identificável.
RN22	No recebimento, a mercadoria deve ser conferida contra o pedido e o documento do fornecedor antes da entrada definitiva no estoque.
RN23	Compra, recebimento e conta a pagar devem manter referências que permitam rastrear fornecedor, itens, valores e documentos.
RN24	O acesso a funções administrativas deve ser limitado por perfil: garçom, produção, caixa e gerente. As permissões específicas devem ser aprovadas pela gerência.
RN25	A venda de bebidas alcoólicas a menores de 18 anos é proibida, conforme legislação brasileira; o procedimento de verificação de idade deve ser definido pela organização.
RN26	As vendas devem ser documentadas fiscalmente conforme o enquadramento tributário e as obrigações aplicáveis ao estabelecimento; o tipo de documento fiscal deve ser confirmado com a contabilidade.
RN27	Produtos alimentícios devem ser armazenados e manipulados conforme normas sanitárias aplicáveis, incluindo controle de validade, conservação e prevenção de contaminação.
RN28	Dados de clientes e funcionários, quando coletados, devem ser acessados apenas por pessoas autorizadas e tratados para finalidades legítimas.
Observação: as regras RN15–RN28 são requisitos propostos para validação com a gerência e/ou contabilidade. Não se afirma que a taxa de 10%, as formas de pagamento ou os procedimentos internos já sejam adotados pelo Alberic Gastrobar.

*5. Dicionário de dados conceitual*

Entidade	Atributos sugeridos	Finalidade
MESA	id_mesa (PK): inteiro; numero: inteiro único; capacidade: inteiro; status: texto; observacao: texto opcional.	Identifica o local de atendimento.
COMANDA	id_comanda (PK): inteiro; id_mesa (FK): inteiro; aberta_em: data/hora; fechada_em: data/hora opcional; status: texto.	Agrupa o consumo de uma mesa em um atendimento.
PEDIDO	id_pedido (PK): inteiro; id_comanda (FK): inteiro; id_funcionario (FK): inteiro; criado_em: data/hora; status: texto; observacao: texto opcional.	Registra pedidos realizados em uma comanda.
ITEM_PEDIDO	id_item_pedido (PK): inteiro; id_pedido (FK): inteiro; id_produto (FK): inteiro; quantidade: decimal ou inteiro positivo; preco_unitario: decimal monetário; status: texto.	Detalha os produtos, as quantidades e os preços históricos de cada pedido.
PRODUTO	id_produto (PK): inteiro; id_categoria (FK): inteiro; id_setor (FK): inteiro; nome: texto; descricao: texto opcional; preco_venda: decimal monetário; disponivel: booleano.	Representa os produtos vendidos pelo estabelecimento.
CATEGORIA	id_categoria (PK): inteiro; nome: texto único; descricao: texto opcional; ativa: booleano.	Classifica os produtos.
SETOR	id_setor (PK): inteiro; nome: texto único; descricao: texto opcional; ativo: booleano.	Representa setores como cozinha e bar.
FUNCIONARIO	id_funcionario (PK): inteiro; nome: texto; funcao: texto; id_setor (FK): inteiro opcional; ativo: booleano; usuario_login: texto opcional.	Identifica os colaboradores e suas atribuições.
ESTOQUE	id_estoque (PK): inteiro; id_produto (FK, único): inteiro; quantidade_atual: decimal; unidade_medida: texto; estoque_minimo: decimal opcional.	Mantém o saldo atual de cada produto.
MOVIMENTACAO_ESTOQUE	id_movimentacao (PK): inteiro; id_estoque (FK): inteiro; id_produto (FK): inteiro; tipo: texto (entrada/saída/ajuste); quantidade: decimal positiva; ocorrido_em: data/hora; motivo: texto; id_funcionario (FK): inteiro.	Registra o histórico de entradas, saídas e ajustes de estoque.
PAGAMENTO	id_pagamento (PK): inteiro; id_comanda (FK): inteiro; forma_pagamento: texto; valor: decimal monetário; pago_em: data/hora; status: texto; referencia_transacao: texto opcional.	Registra os pagamentos vinculados às comandas.
OCORRENCIA	id_ocorrencia (PK): inteiro; id_comanda (FK): inteiro opcional; id_funcionario (FK): inteiro; registrada_em: data/hora; descricao: texto; providencia: texto; cortesia_valor: decimal opcional; autorizado_por (FK): inteiro opcional.	Registra problemas, providências e eventuais cortesias autorizadas.
FORNECEDOR	id_fornecedor (PK): inteiro; nome_razao_social: texto; documento: texto opcional; telefone: texto; email: texto; endereco: texto; ativo: booleano.	Armazena os dados dos fornecedores do estabelecimento.
COMPRA	id_compra (PK): inteiro; id_fornecedor (FK): inteiro; id_funcionario (FK): inteiro; solicitada_em: data/hora; prevista_entrega: data opcional; status: texto; valor_total: decimal monetário.	Registra pedidos de compra realizados junto aos fornecedores.
ITEM_COMPRA	id_item_compra (PK): inteiro; id_compra (FK): inteiro; id_produto (FK): inteiro; quantidade_pedida: decimal; quantidade_recebida: decimal; custo_unitario: decimal monetário.	Detalha os produtos solicitados e recebidos em cada compra.
CONTA_PAGAR	id_conta_pagar (PK): inteiro; id_compra (FK): inteiro opcional; id_fornecedor (FK): inteiro; documento_referencia: texto; vencimento: data; valor: decimal monetário; status: texto; pago_em: data opcional.	Controla os compromissos financeiros com fornecedores.
FECHAMENTO_CAIXA	id_fechamento (PK): inteiro; id_funcionario (FK): inteiro; iniciado_em: data/hora; encerrado_em: data/hora; valor_sistema: decimal monetário; valor_conferido: decimal monetário; diferenca: decimal monetário; observacao: texto opcional.	Permite conferir os valores do caixa e identificar diferenças.
ESCALA_FUNCIONARIO	id_escala (PK): inteiro; id_funcionario (FK): inteiro; inicio: data/hora; fim: data/hora; funcao_turno: texto; status: texto.	Organiza e controla os turnos de trabalho dos funcionários.

*6. Modelagem conceitual — entidades e relacionamentos*
Relacionamento	Cardinalidade mínima e máxima	Justificativa
MESA — COMANDA	MESA 1 : 0..N COMANDA; COMANDA 1 : 1 MESA	Uma mesa pode ainda não ter comandas ou acumular várias ao longo do tempo; cada comanda pertence a uma mesa.
COMANDA — PEDIDO	COMANDA 1 : 0..N PEDIDO; PEDIDO 1 : 1 COMANDA	Uma comanda pode receber vários pedidos; pedido não existe sem comanda.
PEDIDO — ITEM_PEDIDO	PEDIDO 1 : 1..N ITEM_PEDIDO; ITEM_PEDIDO 1 : 1 PEDIDO	Pedido enviado precisa de ao menos um item; cada item pertence a um pedido.
PRODUTO — ITEM_PEDIDO	PRODUTO 1 : 0..N ITEM_PEDIDO; ITEM_PEDIDO 1 : 1 PRODUTO	Um produto pode aparecer em muitos itens; cada item refere um produto.
CATEGORIA — PRODUTO	CATEGORIA 1 : 0..N PRODUTO; PRODUTO 1 : 1 CATEGORIA	Uma categoria agrupa produtos; cada produto pertence a uma categoria.
SETOR — PRODUTO	SETOR 1 : 0..N PRODUTO; PRODUTO 1 : 1 SETOR	Um setor prepara vários produtos; cada produto tem setor responsável principal.
FUNCIONARIO — PEDIDO	FUNCIONARIO 1 : 0..N PEDIDO; PEDIDO 1 : 1 FUNCIONARIO	Funcionário registra vários pedidos; cada pedido tem responsável pelo lançamento.
PRODUTO — ESTOQUE	PRODUTO 1 : 0..1 ESTOQUE; ESTOQUE 1 : 1 PRODUTO	O saldo pode ser criado após o cadastro; cada registro de estoque refere-se a um produto. Se todo produto precisar de saldo, alterar para 1:1 obrigatório.
ESTOQUE — MOVIMENTACAO_ESTOQUE	ESTOQUE 1 : 0..N MOVIMENTACAO_ESTOQUE; MOVIMENTACAO_ESTOQUE 1 : 1 ESTOQUE	Um saldo possui histórico de movimentações.
COMANDA — PAGAMENTO	COMANDA 1 : 0..N PAGAMENTO; PAGAMENTO 1 : 1 COMANDA	Uma comanda pode estar sem pagamento ou receber pagamentos parciais ou múltiplos.
COMANDA — OCORRENCIA	COMANDA 1 : 0..N OCORRENCIA; OCORRENCIA 0..1 : 1 COMANDA	Uma comanda pode ter várias ocorrências; uma ocorrência pode ser geral e não estar ligada a uma comanda, se permitido.
FORNECEDOR — COMPRA	FORNECEDOR 1 : 0..N COMPRA; COMPRA 1 : 1 FORNECEDOR	Um fornecedor pode atender diversas compras.
COMPRA — ITEM_COMPRA	COMPRA 1 : 1..N ITEM_COMPRA; ITEM_COMPRA 1 : 1 COMPRA	Cada compra contém um ou mais itens.
PRODUTO — ITEM_COMPRA	PRODUTO 1 : 0..N ITEM_COMPRA; ITEM_COMPRA 1 : 1 PRODUTO	Um produto pode aparecer em várias compras.
FORNECEDOR — CONTA_PAGAR	FORNECEDOR 1 : 0..N CONTA_PAGAR; CONTA_PAGAR 1 : 1 FORNECEDOR	Cada obrigação a pagar é associada ao fornecedor.
FUNCIONARIO — FECHAMENTO_CAIXA	FUNCIONARIO 1 : 0..N FECHAMENTO_CAIXA; FECHAMENTO_CAIXA 1 : 1 FUNCIONARIO	O funcionário responsável realiza os fechamentos.
FUNCIONARIO — ESCALA_FUNCIONARIO	FUNCIONARIO 1 : 0..N ESCALA_FUNCIONARIO; ESCALA_FUNCIONARIO 1 : 1 FUNCIONARIO	Cada registro de escala pertence a um funcionário.

*7. Justificativa técnica e alternativas*
COMANDA × PEDIDO:
Separar permite registrar vários pedidos durante um mesmo atendimento sem repetir dados da mesa e da comanda. Alternativa rejeitada: colocar todos os itens diretamente na comanda; isso dificulta distinguir pedidos enviados em momentos diferentes e acompanhar sua produção.

PEDIDO × ITEM_PEDIDO × PRODUTO
ITEM_PEDIDO resolve a relação de muitos-para-muitos entre pedido e produto e armazena quantidade e preço no momento da venda. Alternativa rejeitada: guardar uma lista de produtos em um único campo, pois prejudica consultas, integridade e cálculos.

PRODUTO × CATEGORIA e SETOR
Entidades separadas evitam repetir nomes de categorias e setores em cada produto e facilitam manutenção. O modelo assume uma categoria e um setor principal por produto; se um produto puder pertencer a várias categorias ou exigir vários setores, será necessária uma tabela associativa.

ESTOQUE × MOVIMENTACAO_ESTOQUE
ESTOQUE mantém o saldo atual e MOVIMENTACAO_ESTOQUE preserva o histórico. Alternativa rejeitada: guardar somente a quantidade atual, pois não permitiria auditar como o saldo mudou.

COMANDA × PAGAMENTO
Permite mais de um pagamento por comanda, inclusive pagamento parcial ou divisão da conta. Alternativa 1:1 foi descartada porque restringiria esses cenários.

FORNECEDOR, COMPRA e ITEM_COMPRA
São necessários para rastrear o ciclo de compra, os itens solicitados e o fornecedor. Sem ITEM_COMPRA, uma compra com vários produtos exigiria repetir dados ou armazenar listas não estruturadas.

COMPRA × CONTA_PAGAR
A obrigação financeira foi separada da compra para permitir vencimentos e pagamentos independentes; a ligação com compra é opcional quando houver conta não originada de uma compra registrada no sistema.

Mínimos e máximos
A cardinalidade máxima descreve o limite de ocorrências; a mínima indica se a participação é obrigatória. Por exemplo, uma comanda deve ter uma mesa (mínimo 1), enquanto uma mesa recém-cadastrada pode não ter nenhuma comanda (mínimo 0). As cardinalidades devem ser revistas se a operação real divergir.

*8. Uso de inteligência artificial*
*8.1 Ferramenta e etapa*
Ferramenta utilizada: ChatGPT. Foi usada como apoio à organização textual, levantamento de processos, elaboração de requisitos e regras, proposta de entidades e revisão da documentação.

*8.2 Prompt utilizado*
“Com base na entrevista realizada com o Alberic Gastrobar, organize as informações da pesquisa de campo e ajude a identificar processos, requisitos funcionais e não funcionais, regras de negócio, entidades, atributos, relacionamentos e cardinalidades para uma entrega de modelagem conceitual de banco de dados.”

*8.3 Síntese da resposta*
A ferramenta sugeriu organizar os processos de atendimento, pedidos, comandas, produção, estoque, pagamentos e ocorrências e propôs uma estrutura inicial de entidades e relacionamentos. Na revisão, o grupo ampliou o escopo conceitual para incluir compras, fornecedores, contas a pagar, fechamento de caixa e escala, identificando esses elementos como propostas a confirmar.

*8.4 Trechos rejeitados ou corrigidos*
•	A frase “Informações que não foram informadas na entrevista, como endereço, telefone, site e nomes/RGM dos alunos, não foram inventadas” foi removida, pois contradizia a presença desses dados no próprio documento.
•	A frase “O modelo final deverá ser validado pelo grupo antes da entrega” foi substituída por uma descrição do que precisa ser conferido, para não deixar a entrega com aparência de rascunho.
•	A lista repetida da Seção 5 foi eliminada e a numeração foi reorganizada.
•	A afirmação de que o dicionário e o DER estavam disponíveis em arquivos externos foi substituída por conteúdo incorporado ao documento e por um diagrama anexo.
•	Regras sobre taxa de serviço, formas de pagamento, compra, fornecedores e controles legais foram identificadas como propostas, pois não há evidência de que tenham sido confirmadas na entrevista.

*8.5 Critério de escolha final e reflexão crítica*
Foram mantidas as informações compatíveis com o material da pesquisa e propostas de modelagem que respondem às lacunas apontadas na avaliação. A IA não substitui a entrevista nem confirma procedimentos internos. Antes da entrega, o grupo deve validar com a organização as rotinas de compras, formas de pagamento, política de taxa de serviço, autorização de cortesias, controles de caixa, escala e dados da pessoa entrevistada. O grupo é responsável pela versão final.

*9. Pendências para validação do grupo*
•	Confirmar nome e função da pessoa entrevistada e informar se ela aparece na foto da visita.
•	Confirmar volume médio de atendimentos, caso o estabelecimento forneça esse dado.
•	Confirmar formas de pagamento, política de taxa de serviço e possibilidade de dividir a conta.
•	Confirmar se existem processos formais de compras, contas a pagar, fechamento de caixa e escala.
•	Validar permissões por função, política de cortesia e procedimento de cancelamento.
•	Confirmar com a gerência/contabilidade o enquadramento fiscal e procedimentos aplicáveis.
•	Revisar o DER e os atributos com o professor antes de implementar o banco.


