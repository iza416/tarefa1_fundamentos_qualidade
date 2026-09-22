# Atividade 3: Estratégia e Projeto de Testes do LocalEats

## 1. Identificação
- **Turma:** ADS NOITE  
- **Equipe:** Izadora Calvetti Souza  
- **Data:** 21/09/2026  
- **Modalidade:** Individual  
- **Elemento de Competência:** Planejar e projetar testes selecionando técnicas adequadas  
- **Aplicação:** https://local-eats-unisenac.vercel.app/static/index.html  

### Integrantes
| Nome | Usuário no GitHub |
| :--- | :--- |
| Izadora Calvetti Souza | @iza416 |

---

## 2. Tarefa 1: Planejamento dos testes

### 2.1 Objetivo dos testes
Verificar se o fluxo de fazer pedido valida adequadamente a autenticação do cliente, a seleção de itens do cardápio, o endereço de entrega e a forma de pagamento, assegurando que o pedido seja enviado ao restaurante somente quando todos os dados obrigatórios estiverem preenchidos e válidos.

### 2.2 Escopo

#### Funcionalidades incluídas
| Integrante | Funcionalidade incluída | O que será verificado |
| :--- | :--- | :--- |
| Izadora Calvetti Souza | Fazer pedido | Escolha do restaurante, seleção do prato, endereço de entrega, forma de pagamento e validações de finalização do carrinho. |

#### Funcionalidade não incluída
| Funcionalidade não incluída | Justificativa |
| :--- | :--- |
| Criar conta | A validação será restrita ao fluxo de pedidos, utilizando credenciais de usuário previamente cadastradas. |

### 2.3 Abordagem
| Item | Decisão da equipe | Justificativa |
| :--- | :--- | :--- |
| **Níveis de teste** | Teste de Sistema | Avaliar a jornada ponta a ponta pela interface (adicionar ao carrinho, preencher dados e confirmar pedido). |
| **Tipos de teste** | Funcional | Assegurar o correto cumprimento das regras de negócio do processo de checkout. |
| **Perspectiva** | Caixa-preta | Foco nas entradas fornecidas pelo usuário e nos resultados observáveis na tela. |
| **Técnicas de teste** | Tabela de Decisão | O fechamento do pedido depende de múltiplas condições lógicas combinadas (autenticação, carrinho, endereço e pagamento). |

### 2.4 Ambiente e responsabilidades
| Item | Definição |
| :--- | :--- |
| **Ambiente necessário** | Aplicação web (https://local-eats-unisenac.vercel.app/static/index.html), navegador Google Chrome atualizado, conexão de internet Wi-Fi e conta de usuário pré-cadastrada. |
| **Responsável pelo planejamento** | Izadora Calvetti Souza |
| **Responsável pela especificação dos casos** | Izadora Calvetti Souza |
| **Responsável pela futura execução** | Izadora Calvetti Souza |

### 2.5 Critérios
| Critério | Definição da equipe |
| :--- | :--- |
| **Entrada** | Aplicação web publicada e acessível, cardápios de restaurantes carregando com itens e preços válidos e conta de usuário disponível para autenticação. |
| **Saída** | Todos os três casos de teste planejados, executados e documentados e eventuais evidências de bugs. |
| **Suspensão** | Aplicação fora do ar ou indisponibilidade de  itens ao carrinho. |

---

## 3. Tarefa 2: Riscos e técnicas de teste

### 3.1 Análise dos riscos
| ID | Integrante | Funcionalidade | Risco | Consequência | Probabilidade | Impacto | Prioridade | Justificativa |
| :--- | :--- | :--- | :--- | :--- | :---: | :---: | :---: | :--- |
| **R01** | Izadora | Fazer pedido | O cliente pedir o prato sem ter ou informar um endereço válido. | O cliente pode ter a entrega atrasada até o restaurante conseguir contato para confirmar a localização, gerando insatisfação e atrasos na cozinha. | Média | Alto | **Alta** | Este problema quebra o fluxo operacional da loja, prejudica a logística de entrega e gera problemas/dúvidas no banco de dados. |
| **R02** | Izadora | Fazer pedido | O sistema permitir o envio de pedido com o carrinho vazio. | O restaurante recebe chamados zerados, ocupando filas de processamento e gerando cancelamentos desnecessários. | Baixa | Médio | **Média** | O impacto é moderado, mas a regra deve ser travada no sistema para evitar desperdício de alimentos e futuras falhas.. |

### 3.2 Aplicação da técnica

- **Integrante responsável:** Izadora Calvetti Souza  
- **Funcionalidade:** Fazer pedido  
- **Riscos relacionados:** R01 e R02  
- **Técnica escolhida:** Tabela de Decisão  

#### Por que a técnica foi escolhida
O fluxo de finalização de um pedido depende de uma combinação de pré-requisitos: o carrinho deve ter produtos válidos, o usuário precisa fornecer um endereço de entrega, deve escolher uma forma de pagamento e estar autenticado. A Tabela de Decisão é a técnica mais eficaz para mapear todas as combinações de entradas e garantir que as ações sejam acionadas sem problemas.

**Regra de negócio:** O pedido deve ir para o restaurante quando o cliente estiver autenticado, selecionar o prato que quer e informar endereço e forma de pagamento.

#### Aplicação da técnica

| Regra | Usuário autenticado | Carrinho possui itens válidos | Endereço informado | Forma de pagamento selecionado | Resultado esperado |
| :---: | :---: | :---: | :---: | :---: | :--- |
| **1** | Sim | Sim | Sim | Sim | Pedido enviado ao restaurante[cite: 1] |
| **2** | Sim | Sim | Não | Sim | O sistema deve informar que o cliente precisa informar o endereço |
| **3** | Sim | Sim | Sim | Não | O sistema deve informar que o pagamento deve ser informado |
| **4** | Sim | Não | Sim | Não | O sistema deve informar que o cliente precisa selecionar o prato que deseja |
| **5** | Não | Não | Não | Não | Solicitar autenticação e não realizar o pedido |

#### Casos derivados
- **CT01:** Pedido enviado ao restaurante com todos os dados preenchidos.
- **CT02:** Bloqueio de finalização de pedido sem endereço informado.
- **CT03:** Bloqueio de finalização com carrinho vazio / sem prato selecionado.

---

## 4. Tarefa 3: Casos de teste e rastreabilidade

### 4.1 Casos de teste

#### CT01: Pedido enviado ao restaurante com todos os dados preenchidos
- **Integrante responsável:** Izadora Calvetti Souza  
- **Funcionalidade:** Fazer pedido  
- **Risco ou requisito relacionado:** Requisito de finalização de pedido com sucesso  
- **Técnica utilizada:** Tabela de Decisão  
- **Pré-condição:** Usuário previamente autenticado no LocalEats e com restaurante acessível na plataforma.  
- **Dados de entrada:**  
  - Restaurante: primeiro restaurante da listagem  
  - Prato: 1x Prato principal selecionado  
  - Endereço: "Rua Dr. Francisco Ribeiro Da Silva, 251 - Pelotas/RS"  
  - Forma de pagamento: "Cartão de Crédito"  
- **Passos:**  
  1. Acessar a aplicação e realizar login com a conta de teste.  
  2. Escolher um restaurante na tela inicial.  
  3. Adicionar um prato do cardápio ao carrinho de compras.  
  4. Acessar a tela de checkout/carrinho.  
  5. Preencher o campo de endereço com "Rua Dr. Francisco Ribeiro Da Silva, 251 - Pelotas/RS".  
  6. Selecionar a opção de pagamento "Cartão de Crédito".  
  7. Clicar em "Confirmar Pedido".  
- **Resultado esperado:** O pedido é finalizado e enviado ao restaurante com sucesso, exibindo tela de confirmação com status de acompanhamento do pedido e esvaziando o carrinho.

---

#### CT02: Bloqueio de finalização de pedido sem endereço informado
- **Integrante responsável:** Izadora Calvetti Souza  
- **Funcionalidade:** Fazer pedido  
- **Risco ou requisito relacionado:** R01 Cliente pedir o prato sem ter ou informar um endereço válido 
- **Técnica utilizada:** Tabela de Decisão  
- **Pré-condição:** Usuário autenticado com prato previamente adicionado ao carrinho de compras.  
- **Dados de entrada:**  
  - Prato: 1x Prato principal no carrinho  
  - Endereço: *vazio / não informado*  
  - Forma de pagamento: "Cartão de Crédito"  
- **Passos:**  
  1. Certificar-se de que o usuário está logado e há prato no carrinho.  
  2. Deixar o campo de endereço de entrega em branco.  
  3. Selecionar a forma de pagamento Cartão de Crédito.  
  4. Clicar no botão Confirmar Pedido.  
- **Resultado esperado:** O sistema impede o envio do pedido e exibe mensagem de alerta informando que o cliente precisa preencher o endereço de entrega para prosseguir.

---

#### CT03: Bloqueio de finalização com carrinho vazio / sem prato selecionado
- **Integrante responsável:** Izadora Calvetti Souza  
- **Funcionalidade:** Fazer pedido  
- **Risco ou requisito relacionado:** R02 Sistema permitir o envio de pedido com o carrinho vazio   
- **Técnica utilizada:** Tabela de Decisão  
- **Pré-condição:** Usuário previamente autenticado com o carrinho de compras zerado.  
- **Dados de entrada:**  
  - Prato: 0 pratos selecionados (carrinho vazio)  
  - Endereço: "Rua Dr. Francisco Ribeiro da Silva, 251 - Pelotas/RS"  
  - Forma de pagamento: *não selecionada*  
- **Passos:**  
  1. Efetuar login na aplicação LocalEats.  
  2. Clicar em um restaurante.  
  3. Tentar ir para o carrinho vazio ou completar a compra
- **Resultado esperado:** O sistema impede, sinalizando que o carrinho está vazio com aviso de que o cliente precisa selecionar ao menos um prato antes de concluir.

---

### 4.2 Matriz de rastreabilidade

| Integrante | Funcionalidade | Risco ou requisito | Técnica utilizada | Casos de teste |
| :--- | :--- | :--- | :--- | :--- |
| Izadora Calvetti Souza | Fazer pedido | Requisito: Envio de pedido completo (Regra 1) | Tabela de Decisão | CT01 |
| Izadora Calvetti Souza | Fazer pedido | R01: Pedido sem endereço de entrega (Regra 2) | Tabela de Decisão | CT02 |
| Izadora Calvetti Souza | Fazer pedido | R02: Pedido com carrinho vazio (Regra 4) | Tabela de Decisão | CT03 |

---

## 5. Uso de inteligência artificial

**Ferramenta utilizada:**  
Gemini

**Como foi utilizada:** 
Formatação do documento no padrão Markdown.

**Uma sugestão que precisou ser alterada ou rejeitada:**  
nenhuma

