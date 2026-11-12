# Exemplo de Changelog p
com sprints e issues para o projeto Dashboard de Controle Financeiro Inteligente

## Fase 1: MVP Estrutural (Alimentação por Formulário)
*Objetivo: Estabelecer a infraestrutura core, o banco de dados e a interface gráfica para que o sistema funcione de ponta a ponta com inserção manual de dados.*

### Backend (Cloudflare Workers & D1)
- [ ] **Issue 1.1:** Configurar o ambiente do Cloudflare Workers (`wrangler.toml`) e provisionar o banco de dados D1 (SQLite) com as tabelas iniciais (`Usuarios`, `Transacoes`, `Categorias`).
- [ ] **Issue 1.2:** Desenvolver endpoints de CRUD (Create, Read, Update, Delete) para gerenciar as transações enviadas pelo formulário web.
- [ ] **Issue 1.3:** Criar uma rota de consolidação financeira que retorne os totais de receitas, despesas e o saldo mensal calculado para o dashboard.
- [ ] **Issue 1.4:** Implementar autenticação simples (JWT) para proteger a API contra acessos não autorizados.

### Frontend (SPA JS)
- [ ] **Issue 1.5:** Inicializar o projeto frontend utilizando o arquivo base para estabelecer o layout base e o roteamento.
- [ ] **Issue 1.6:** Desenvolver o formulário de inserção manual de transações, validando os campos de Data, Valor, Categoria e Descrição.
- [ ] **Issue 1.7:** Construir a tabela de listagem do histórico de lançamentos, incluindo filtros básicos (por mês e categoria).
- [ ] **Issue 1.8:** Integrar uma biblioteca de gráficos (ex: Chart.js ou ECharts) para consumir a API de consolidação e exibir visualmente a saúde financeira.

---

## Fase 2: Mensageria (O Bot do WhatsApp)
*Objetivo: Integrar a aplicação com o WhatsApp para permitir o recebimento de mensagens e arquivos, preparando o terreno para a automação.*

### Backend (Cloudflare Workers & Integrações)
- [ ] **Issue 2.1:** Configurar aplicativo no Meta for Developers e validar o Webhook no Cloudflare Worker para escutar mensagens.
- [ ] **Issue 2.2:** Desenvolver o parser para identificar o tipo de mensagem recebida (Texto, Imagem ou Documento PDF).
- [ ] **Issue 2.3:** Criar o fluxo de download e armazenamento temporário de mídias (imagens e PDFs) dos servidores do Meta para um storage local (ex: Cloudflare R2 ou buffer).
- [ ] **Issue 2.4:** Desenvolver respostas automatizadas básicas do bot (ex: "Arquivo recebido, processando...").

### Frontend (SPA JS)
- [ ] **Issue 2.5:** Atualizar a tabela de transações para exibir a origem do registro através de tags visuais (ex: "Manual" ou "WhatsApp").
- [ ] **Issue 2.6:** Criar visualizador simples (modal) que permita anexar e visualizar manualmente um comprovante em uma transação já existente.

---

## Fase 3: Automação via Visão Computacional (OCR e PDF)
*Objetivo: Eliminar o atrito da digitação manual através do processamento inteligente das imagens e PDFs recebidos via chat.*

### Backend (APIs Próprias & Workers)
- [ ] **Issue 3.1:** Desenvolver e integrar o endpoint da API própria para leitura de PDFs (extração de texto e uso de expressões regulares para valores e datas).
- [ ] **Issue 3.2:** Desenvolver e integrar o endpoint da API própria para processamento de imagens (motor de OCR para leitura de notas fiscais).
- [ ] **Issue 3.3:** Criar o "Sanitizador de Dados": formatar o texto bruto do OCR/PDF em um JSON unificado (`{ valor, data, descricao }`) e salvar no banco de dados.
- [ ] **Issue 3.4:** Atualizar a lógica do bot para responder ao usuário com o resultado final do processamento ("Despesa de R$ 50,00 salva com sucesso!").

### Frontend (SPA JS)
- [ ] **Issue 3.5:** Desenvolver um visualizador (modal ou painel lateral) para exibir a foto do recibo ou PDF atrelada à transação automatizada.
- [ ] **Issue 3.6:** Criar o "Painel de Auditoria": uma interface onde o usuário possa visualizar os dados extraídos lado a lado com a imagem, permitindo revisar, corrigir rapidamente (edição inline) ou descartar leituras imprecisas antes de consolidar.
