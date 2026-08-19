# Relatório de Atividades - Qualidade de Software

## 1. Identificação

- **Turma:** ADS NOITE
- **Data:** 18/08/2026
- **Elemento de Competência:** Compreender os fundamentos de qualidade de software e sua aplicação no desenvolvimento de sistemas.
- **Aplicação Analisada:** [https://local-eats-unisenac.vercel.app/](https://local-eats-unisenac.vercel.app/)

### Integrantes

| Nome | Usuário no GitHub |
| :--- | :--- |
| Izadora Calvetti Souza | [@Iza416](https://github.com/Iza416) |

---

## 2. Tarefa 1: Fundamentos da Qualidade

### 2.1 Necessidades Explícitas e Implícitas

| Tipo | Necessidade | Interessado | Consequência se não for atendida |
| :--- | :--- | :--- | :--- |
| **Explícita** | Realizar o pedido | Usuário | Não terão pedidos no sistema, os restaurantes terão prejuízos. |
| **Explícita** | Fazer cadastro | Usuário | Não será possível acessar o sistema para verificar os restaurantes e fazer pedidos. |
| **Implícita** | Mostrar que o pedido foi aceito e está sendo preparado | Usuário | Deixa o usuário perdido, sem saber se o seu pedido será feito, se foi atendido e se está sendo realizado. |
| **Implícita** | Fotos dos pratos | Usuário | Conecta o usuário visualmente com aquele restaurante, deixa ele com vontade de comer e deixa mais explícito o que é aquele prato. |

### 2.2 Questão sobre os Fundamentos da Qualidade

> **Um sistema que implementa todas as funcionalidades explicitamente solicitadas pode, ainda assim, apresentar baixa qualidade? Justifiquem utilizando pelo menos uma necessidade implícita identificada pela equipe.**

**Resposta:**  
Sim, o sistema pode funcionar perfeitamente, com as funcionalidades exigidas, mas não ter um cuidado com o usuário. Por exemplo, no caso que citei as fotos dos pratos, isso ajuda o cliente a ter certeza que quer aquela comida, além de ajudar o restaurante a vender já que comida também se come com os olhos.

---

## 3. Tarefa 2: Exploração da Aplicação

| Integrante | Funcionalidade | O que foi realizado | O que foi observado | Evidência |
| :--- | :--- | :--- | :--- | :--- |
| **Izadora** | Cadastro/login | Fiz meu cadastro na plataforma e já fui redirecionada para ela, sem precisar fazer o login. | O observado foi que não me deu a opção de fazer o login. Eu cadastrei e já fui redirecionada para a plataforma, o correto seria eu ter que realizar o meu login. | Vídeo no repositório |

---

## 4. Tarefa 3: Requisitos e Características de Qualidade

| Integrante | Requisito de Qualidade | Característica / Subcaracterística | Justificativa | Como avaliar |
| :--- | :--- | :--- | :--- | :--- |
| **Izadora** | O sistema deve garantir o controle seguro de autenticação no fluxo de cadastro, exigindo que o usuário valide suas credenciais criadas por meio da tela de login. | Segurança - Controle de acesso | Ao cadastrar um novo usuário e autenticá-lo imediatamente sem validação, o sistema pula a etapa formal de verificação de integridade das credenciais recém-registradas. Exigir o login inicial ou um fluxo formal de autenticação assegura que o usuário memorizou e testou suas credenciais de acesso, evita acessos indevidos em ambientes compartilhados e garante que a sessão do usuário seja iniciada de forma segura. | **Através de teste de aceite:**<br><br>• **Aceito:** O usuário faz seu cadastro, é direcionado para a página de login, insere seus dados válidos e corretos e então é direcionado para a plataforma.<br><br>• **Não aceito:** No momento em que se faz o cadastro, o usuário já é direcionado diretamente para a plataforma. |

---

## 5. Uso de Inteligência Artificial

- **Ferramenta utilizada:** Não utilizada
- **Como foi utilizada:** Não foi utilizada
- **Como as respostas foram verificadas:** —
