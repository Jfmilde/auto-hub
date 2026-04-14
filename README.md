# auto-hub# AutoHub

## Autor: João Felipe Mildemberger Pereira

Este projeto tem como objetivo implementar uma aplicação web responsiva para o gerenciamento de veículos e controle de manutenções. O AutoHub permite ao usuário registrar sua frota, lançar históricos de manutenções preventivas e corretivas, e acompanhar o valor de mercado atualizado do veículo através da consulta à Tabela FIPE.

## 📚 Documentação do Projeto

Em andamento

## 🎨 Design

Framework Front-end: Bootstrap v5.3.3

Prototipagem Responsiva Nativa: Para um sistema de gestão completo, é fundamental que as telas funcionem perfeitamente tanto no desktop quanto na tela de um celular. O sistema flexível de grids do Bootstrap resolve a responsividade de forma muito mais rápida do que criar media queries do zero.

Velocidade de Desenvolvimento: A biblioteca fornece componentes pré-construídos que se encaixam perfeitamente na temática do projeto. É possível usar Cards para exibir os veículos na garagem, Modals para os formulários de cadastro de novas peças ou manutenções, e Offcanvases para menus de navegação laterais.

Integração com Design Systems: A versão 5.3 abandonou dependências antigas (como o jQuery), tornando o projeto mais leve. Além disso, ela tem suporte total a variáveis CSS (Design Tokens). Isso significa que é muito simples pegar o escopo visual desenhado no Figma ou no Stitch e aplicar as cores e tipografias exatas no código, mantendo a consistência visual.

## 🌐 Site em Produção - GitHub Pages

[Em andamento] https://stitch.withgoogle.com/projects/80827565528750594

## 💻 Tecnologias e Dependências

Integração de Dados: Brasil API (Tabela FIPE)

Desempenho e Dados em Tempo Real: A escolha da Brasil API se dá pela sua arquitetura moderna, estabilidade e formato de código aberto. Como o objetivo central é ter um hub de gestão automotiva, o sistema precisa exibir o patrimônio atualizado da "garagem virtual" sem que o usuário precise digitar esses valores manualmente.

Escalabilidade: Optar por uma API externa em vez de manter um banco de dados local (como um db.json gigante) com os preços de todos os veículos evita a sobrecarga de armazenamento e a necessidade de criar rotinas complexas de atualização mensal.

Padronização: Os endpoints entregam respostas em JSON limpas e previsíveis, o que facilita muito o tratamento desses dados, seja no front-end ou processando isso em um back-end automatizado

## ✅ Checklist | Indicadores de Desempenho (ID) dos Resultados de Aprendizagem (RA)

Em andamento

### RA1 - Utilizar Frameworks CSS para estilização de elementos HTML e criação de layouts responsivos.
- [ ]	ID 01 - Prototipa interfaces adaptáveis para no mínimo os tamanhos de tela mobile e desktop, usando ferramentas de design tradicionais (Figma, Quant UX ou Sketch) ou IA (Stitch).
- [ ] ID 02 - Implementa layout responsivo com Framework CSS (Bootstrap, Materialize, Tailwind + DaisyUI) usando Flexbox ou Grid do próprio framework.
- [ ] ID 03 - Implementa layout responsivo com CSS puro, usando Flexbox ou Grid Layout.
- [ ] ID 04 - Utiliza componentes prontos de um Framework CSS (ex.: card, button) e componentes JavaScript do framework (ex.: modal, carousel).
- [ ] ID 05 - Cria layout fluido usando unidades relativas (vw, vh, %, em, rem) no lugar de unidades fixas (px).
- [ ] ID 06 - Aplica um Design System consistente (cores, tipografia, padrões de componentes) em toda a aplicação.
- [ ] ID 07 - Utiliza Sass (SCSS) com ou sem framework, aplicando variáveis, mixins e funções para modularizar o código.
- [ ] ID 08 - Aplica tipografia responsiva (media queries mobile first) ou tipografia fluida (função clamp() + unidades relativas).
- [ ] ID 09 – Aplica técnicas de responsividade de imagens usando CSS (object-fit, containers com unidades relativas).
- [ ] ID 10 – Otimiza imagens usando formatos modernos (WebP) e carregamento adaptativo (srcset, picture, ou parâmetros do Cloudinary).
### RA2 - Realizar tratamento de formulários e aplicar validações customizadas no lado cliente.
- [ ] ID 11 - Implementa validação HTML nativa (campos obrigatórios, tipos, limites de caracteres) com mensagens de erro/sucesso no lado cliente.
- [ ] ID 12 - Aplica expressões regulares (REGEX) para validações customizadas (e-mail, telefone, datas, etc.)
- [ ] ID 13 - Utiliza elementos de seleção em formulários (checkbox, radio, select) para coleta de dados.
- [ ] ID 14 - Implementa leitura e escrita no Web Storage (localStorage/sessionStorage) para persistir dados localmente.
### RA3 - Aplicar ferramentas para otimização do processo de desenvolvimento web.
- [ ] ID 15 - Configura ambiente com Node.js e NPM para gerenciamento de pacotes e dependências.
- [ ] ID 16 - Utiliza boas práticas de versionamento no Git/GitHub (branch main ou branches específicos, uso de .gitignore).
- [ ] ID 17 - Mantém um README.md padronizado, conforme template da disciplina, com checklist preenchido.
- [ ] ID 18 - Organiza arquivos do projeto de forma modular, seguindo padrão de exemplo fornecido.
- [ ] ID 19 - Configura linters e formatadores (ESLint, Prettier) para manter qualidade e padronização do código.
### RA4 - Aplicar bibliotecas de funções e componentes em JavaScript para aprimorar a interatividade de páginas web.
- [ ] ID 20 - Utiliza jQuery para manipulação do DOM e interatividade (eventos, animações, manipulação de elementos)
- [ ] ID 21 - Integra e configura um plugin jQuery relevante (ex.: jQuery Mask Plugin).
### RA5 - Efetuar requisições assíncronas para uma API fake e APIs públicas, permitindo a obtenção e manipulação de dados dinamicamente.
- [ ] ID 22 - Realiza requisições assíncronas para uma API fake (ex.: JSON Server) para persistir dados de um formulário.
- [ ] ID 23 - Realiza requisições assíncronas para uma API fake para exibir dados na página.
- [ ] ID 24 - Realiza requisições assíncronas para APIs públicas reais (OpenWeather, ViaCEP etc.), exibindo os dados e tratando erros.

## 🚀 Manual de execução

Em andamento

## 📱 Telas da aplicação

Em andamento
