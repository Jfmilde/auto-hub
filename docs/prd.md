# 📄 Product Requirements Document (PRD) - AutoHub

## 1. Visão Geral e Objetivo

O **AutoHub** é uma aplicação web responsiva que permite ao usuário gerenciar sua frota de veículos e controlar manutenções de forma intuitiva e eficiente. A aplicação possibilita o registro de carros, inserção de histórico de manutenções periódicas e a consulta do valor atualizado do veículo no mercado.

**O diferencial:** Fornecer uma visão clara e centralizada da saúde mecânica e do valor patrimonial do veículo, aposentando os cadernos de anotação e planilhas confusas através de um painel intuitivo e responsivo.

## 2. Atores do Sistema

- **Visitante:** Usuário não autenticado que acessa a página inicial e deseja criar uma conta para gerenciar seus veículos.
- **Usuário/Cliente:** Usuário autenticado que possui uma conta no AutoHub e realiza operações (registrar veículos, lançar manutenções, consultar FIPE).
- **O Sistema:** Ator responsável por aplicar regras de negócio, persistir dados e conectar-se à API pública da FIPE.

## 3. Histórias de Usuário e Escopo

Abaixo estão as funcionalidades principais do MVP (Minimum Viable Product), escritas sob a perspectiva do usuário final.

### 👤 Épico 1: Autenticação e Conta
- **US01 - Criação de Conta:** Como um Visitante, quero preencher um formulário com meus dados pessoais (Nome, E-mail, Senha) para criar uma nova conta no AutoHub.
  - _Critérios de Aceitação:_ O e-mail deve ser validado; campos obrigatórios preenchidos; dados devem ser persistidos localmente ou em API fake.
- **US02 - Acesso ao Sistema (Login):** Como um Visitante/Cliente, quero inserir meu E-mail e Senha para acessar minha garagem.
  - _Critérios de Aceitação:_ O sistema valida credenciais e redireciona ao dashboard em caso de sucesso.

### 🚘 Épico 2: Gestão de Frota e Valor
- **US03 - Cadastrar Veículo:** Como um Usuário, quero adicionar um carro informando placa, marca, modelo e ano.
  - _Critérios de Aceitação:_ Placa deve seguir o formato padrão (Mercosul/Antiga); o carro é vinculado ao usuário logado.
- **US04 - Consulta FIPE:** Como um Usuário, quero ver o valor de mercado atualizado do meu veículo no dashboard.
  - _Critérios de Aceitação:_ O sistema deve consumir a API externa da FIPE e exibir o valor em R$; deve atualizar dinamicamente.

### 🛠️ Épico 3: Controle de Manutenção
- **US05 - Registrar Manutenção:** Como um Usuário, quero registrar um serviço realizado (ex: troca de óleo) informando a quilometragem, data e descrição.
  - _Critérios de Aceitação:_ A quilometragem informada deve ser numérica; o serviço é atrelado a um veículo específico.
- **US06 - Histórico de Revisões:** Como um Usuário, quero visualizar uma lista cronológica de todas as manutenções feitas no carro.
  - _Critérios de Aceitação:_ A lista deve mostrar os itens mais recentes primeiro, exibindo data, KM, serviço e anotações.

## 4. Requisitos Funcionais

1. **Validação de Entrada de Dados:**
   - Placas de veículos e e-mails devem ser validados usando REGEX.
   - Quilometragem deve aceitar apenas números inteiros positivos.
2. **Persistência e Integração:**
   - Dados de usuários, veículos e manutenções armazenados em API fake (JSON Server).
   - Consulta em tempo real à API Brasil (ou similar) para obter preços da Tabela FIPE.
3. **Responsividade:**
   - Aplicação responsiva para mobile (≤600px) e desktop (≥1024px) utilizando Bootstrap 5.

## 5. Requisitos Não-Funcionais

- **Performance:** As chamadas para a API externa (FIPE) não devem travar a tela (uso correto de async/await e loaders).
- **Usabilidade:** Interface intuitiva com feedback visual claro (toasts/alerts) ao salvar um registro ou errar um campo.
- **Compatibilidade:** Funcionamento em navegadores modernos (Chrome, Edge, Firefox).

## 6. Design e Layout

- **Painel Principal (Minha Garagem):** Exibe cards com os veículos cadastrados e o valor FIPE atualizado em destaque.
- **Detalhes do Veículo:** Tela com a timeline/extrato de manutenções registradas e botão para novo registro.
- **Formulários:** Modais ou telas dedicadas com validação visual (vermelho para erro, verde para sucesso).

## 7. MVP - Escopo Mínimo para Primeira Versão

- ✅ Criação de conta e Login
- ✅ Cadastro e listagem de veículos na garagem
- ✅ Integração com API da FIPE
- ✅ Lançamento de registro de manutenção
- ✅ Visualização do histórico de manutenções
- ✅ Logout

## 8. Critérios de Aceitação Gerais

- Formulários devem bloquear submissão se houver erro e exibir mensagens de feedback.
- Requisições assíncronas devem tratar possíveis erros (ex: falha na API da FIPE).