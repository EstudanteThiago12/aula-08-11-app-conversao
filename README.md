# Aula 08-11 - App Conversão de moeda

## Avaliação

* Implemente para que o usuário possa fazer conversão de outras moedas (mínimo + 3 moedas);
* Descreva abaixo o seu entendimento acerca desta atividade, explorando as funcionalidades das classes que contruímos e os principais pontos da aplicação;

## Entrega

* Clone este repositório e faça o que se pede;
* Realize um commit das suas alterações no seu repositório;
* Envie o link do repositório na avaliação gerada no classroom;

## Descritivo do Aluno:

# Conversor de Moedas

Este projeto é um aplicativo Android desenvolvido para facilitar a conversão de moedas. Ele oferece uma experiência simples e intuitiva, permitindo que os usuários escolham os pares de moedas diretamente na interface e insiram valores para conversão. A aplicação exibe os resultados de maneira imediata, utilizando taxas de câmbio atualizadas obtidas de uma API externa.

---

## 📋 Funcionalidades Principais

O aplicativo permite que o usuário:

- Escolha entre diferentes pares de moedas para conversão, incluindo:
  - Real para Dólar (BRL → USD)
  - Real para Euro (BRL → EUR)
  - Bitcoin para Real (BTC → BRL)
  - Dólar para Euro (USD → EUR)
  - Real para Sol do Peru (BRL → PEN)
- Insira um valor em uma caixa de texto para cálculo da conversão.
- Receba o resultado da conversão de forma rápida, exibido diretamente na tela.
- Veja mensagens de validação em caso de entrada incorreta, como não selecionar um par de moedas ou não preencher o campo de valor.

---

## 🛠️ Estrutura do Código

### 1. **Interface de Seleção**
A aplicação utiliza um **RadioGroup** com botões de opção (**RadioButtons**) para listar os pares de moedas disponíveis. Quando o usuário seleciona uma opção, o método `setOnCheckedChangeListener` captura essa escolha e atualiza a variável `opcaoSelecionada`, que armazena o par de moedas correspondente. Essa variável é essencial para a lógica de conversão.

### 2. **Validação do Input**
Antes de realizar qualquer operação:
- Verifica se o usuário escolheu um par de moedas no **RadioGroup**.
- Certifica-se de que o campo de texto possui um valor válido.
Caso contrário, uma mensagem de erro clara é exibida utilizando o componente **Toast**, evitando que a aplicação prossiga com informações incompletas.

### 3. **Integração com a API**
A comunicação com a API é feita pela classe **AwesomeClient**, que gerencia as requisições e respostas:
- Ela utiliza uma abordagem baseada em **callbacks** por meio da interface `ApiCallback`.
  - No caso de sucesso, o método `onSuccess` processa os dados recebidos.
  - No caso de erro, o método `onError` exibe uma mensagem para o usuário.
- Essa implementação modular permite reutilizar o código de comunicação com a API de forma eficiente e adaptável.

### 4. **Processamento de Dados**
Os dados retornados pela API vêm no formato JSON. A aplicação usa a biblioteca **Gson** para transformar esses dados em objetos da classe **CurrencyRate**. Essa classe contém os detalhes sobre a taxa de câmbio, incluindo o valor mais alto (`getHigh`), utilizado no cálculo da conversão.

### 5. **Cálculo da Conversão**
Com a taxa de câmbio em mãos:
- O valor digitado pelo usuário é multiplicado pela taxa obtida da API.
- O resultado é exibido diretamente no **TextView**, garantindo uma experiência fluida para o usuário.

### 6. **Gerenciamento de Erros**
A aplicação trata os erros de forma robusta:
- Falhas na comunicação com a API são capturadas pelo método `onError`, que exibe mensagens ao usuário explicando o problema.
- Qualquer exceção inesperada é registrada no log do sistema e exibida ao usuário de maneira genérica, mantendo a usabilidade.

---

## ⚙️ Tecnologias Utilizadas

- **Java**: Linguagem de desenvolvimento principal.
- **Android SDK**: Ferramentas e bibliotecas nativas para construção de interfaces e funcionalidades Android.
- **Gson**: Biblioteca para conversão e manipulação de dados JSON.
- **Toast**: Recurso para exibição de mensagens de validação e erros ao usuário.
- **AwesomeClient**: Classe customizada para lidar com as requisições à API.
- **ApiCallback**: Interface para organizar a lógica de sucesso e erro nas respostas.

---

## 🌟 Destaques do Projeto

- **Código Reutilizável**:
  - A implementação com `ApiCallback` simplifica a integração com APIs, tornando o código mais fácil de manter e expandir.
- **Validações e Feedback**:
  - O aplicativo fornece mensagens claras ao usuário, ajudando a corrigir entradas inválidas antes de prosseguir.
- **Estrutura Modular**:
  - Métodos separados garantem uma melhor organização do código, facilitando futuras modificações.
- **Interface Responsiva**:
  - Suporte a dispositivos modernos, com uso de configurações Edge-to-Edge para maior imersão e acessibilidade.

---
 ## 📝 Conclusão

O Conversor de Moedas é um exemplo prático de como integrar diferentes aspectos do desenvolvimento Android, desde a criação de interfaces até a comunicação com APIs externas. Ele oferece uma base sólida para quem busca aprender ou desenvolver projetos relacionados a finanças e conversão de moedas. Além disso, sua estrutura modular e reutilizável facilita a evolução do código para futuras funcionalidades.
