# 🛠️ Especificação Técnica (Tech Spec) - AutoHub

Este documento detalha a arquitetura técnica, o modelo de dados e os contratos de API (via JSON Server e APIs externas) necessários para o funcionamento do AutoHub.

## 1. Modelo de Dados (Diagrama ER)

Abaixo está o Diagrama Entidade-Relacionamento (DER) que representa a estrutura do nosso "banco de dados" (`db.json`) e como as informações se conectam.

mermaid
erDiagram
USUARIO ||--o{ VEICULO : "possui"
VEICULO ||--o{ MANUTENCAO : "recebe"

USUARIO {
string id PK "Gerado automaticamente"
string nome
string email "Usado para o login"
string senha
}

VEICULO {
string id PK
string usuarioId FK "Vínculo com o Usuário"
string placa "Formato AAA-1234 ou Mercosul"
string marca "Ex: Chevrolet"
string modelo "Ex: Vectra GLS 2.2"
string ano "Ex: 2000"
string codigoFipe "Usado para consumo da API pública"
}

MANUTENCAO {
string id PK
string veiculoId FK "Vínculo com o Veículo"
int quilometragem "KM no momento do serviço"
string data "Formato ISO (YYYY-MM-DD)"
string servico "Ex: Troca de óleo e filtro"
string descricao "Anotações adicionais"
}

2. Dicionário de Dados
Breve explicação das tabelas principais:

Usuários: Armazena os dados de autenticação e identificação.

Veículos: Registro da frota do usuário. O campo codigoFipe é fundamental para alimentar a requisição externa assíncrona.

Manutenções: Histórico atrelado a um veículo específico, garantindo rastreabilidade do que foi feito e com qual quilometragem.

3. Rotas da API (JSON Server e Externas)
A aplicação consome a API local simulada pelo JSON Server e uma API pública.

JSON Server (Local)
GET /usuarios - Retorna a lista de usuários (para validação de login).

POST /usuarios - Cadastra um novo usuário.

GET /usuarios/{usuarioId}/veiculos - Retorna os veículos de um usuário específico.

POST /veiculos - Cadastra um veículo.

GET /veiculos/{veiculoId}/manutencoes - Retorna o histórico de um carro.

POST /manutencoes - Registra um novo serviço.

API Externa (Brasil API / Tabela FIPE)
GET https://brasilapi.com.br/api/fipe/preco/v1/{codigoFipe} - Retorna o valor atualizado do veículo.

4. Estrutura do Banco de Dados (db.json)
Esta é a representação em formato JSON do banco de dados simulado inicial.
{
  "usuarios": [
    {
      "id": "1",
      "nome": "João Felipe",
      "email": "milde@autohub.com",
      "senha": "senha_segura"
    }
  ],
  "veiculos": [
    {
      "id": "1",
      "usuarioId": "1",
      "placa": "ABC-1234",
      "marca": "Chevrolet",
      "modelo": "Vectra GLS 2.2",
      "ano": "2000",
      "codigoFipe": "004082-7"
    }
  ],
  "manutencoes": [
    {
      "id": "1",
      "veiculoId": "1",
      "quilometragem": 145000,
      "data": "2026-03-10",
      "servico": "Troca de óleo",
      "descricao": "Óleo 15w40 semi-sintético + Filtro de óleo"
    },
    {
      "id": "2",
      "veiculoId": "1",
      "quilometragem": 146500,
      "data": "2026-03-25",
      "servico": "Revisão de freios",
      "descricao": "Troca de pastilhas dianteiras"
    }
  ]
}

5. Fluxo de Consulta FIPE
O valor financeiro do carro não é salvo no banco, ele é consultado dinamicamente:

O Front-end carrega a lista de veículos (GET /veiculos).

Para cada veículo, o JavaScript extrai o codigoFipe.

O Front-end faz um fetch assíncrono para a API externa da FIPE.

O valor retornado é injetado no DOM (Card do veículo) formatado em BRL (R$).

6. Tecnologias e Dependências
Frontend: HTML5, CSS3, JavaScript (Vanilla).

API Fake: JSON Server (Node.js).

Framework CSS: Bootstrap 5.

Validação: Regex no cliente.

7. Fluxo de Registro de Manutenção
Usuário seleciona o carro na Garagem e clica em "Adicionar Manutenção".

Preenche KM, Data e Serviço.

Front-end valida se o KM digitado é válido.

Front-end faz POST /manutencoes enviando os dados e o veiculoId.

JSON Server registra o evento.

A tabela de histórico é atualizada assincronamente na tela.