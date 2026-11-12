# 📊 Dashboard de Controle Financeiro Inteligente

Um sistema de gestão financeira modular, de baixo custo e escalável, construído com uma arquitetura 100% serverless. A plataforma evolui de um controle manual para um ecossistema autônomo, capaz de receber recibos em imagens e faturas em PDF via WhatsApp, extraindo e categorizando os dados automaticamente.

## 🚀 Arquitetura e Stack Tecnológico

O projeto é dividido em microsserviços para facilitar o desenvolvimento paralelo:

- **Frontend:** Single Page Application (SPA) referenciada no arquivo "dashboard para controle financeiro em js", responsável pela visualização de dados, gráficos e gestão de transações.
- **Backend Core:** Cloudflare Workers (Edge Computing com latência zero) atuando como a API principal.
- **Banco de Dados:** Cloudflare D1 (SQLite serverless nativo no edge) para armazenar transações, categorias e usuários.
- **Mensageria:** Webhook integrado à API Oficial do WhatsApp (Meta for Developers) para interações via chat.
- **Inteligência e Processamento:** APIs próprias modularizadas para reconhecimento de imagem (OCR) e extração de dados de PDFs.

## 🗺️ Fases de Desenvolvimento

O projeto está estruturado em 3 fases principais para isolar as complexidades:

### Fase 1: MVP Estrutural (Controle Manual)
Foco na infraestrutura base. Construção do banco de dados D1, das APIs CRUD no Cloudflare Workers e da interface gráfica web com formulários para inserção manual e gráficos de consolidação financeira.

### Fase 2: Mensageria (O Bot do WhatsApp)
Integração do sistema com o Meta. Criação do Webhook para escutar mensagens, responder comandos básicos do usuário e realizar o download temporário de mídias (imagens de cupons e PDFs) enviadas no chat.

### Fase 3: Automação via Visão Computacional (OCR)
Conexão do fluxo do WhatsApp com os motores de OCR e PDF. Extração de dados brutos e conversão para um JSON estruturado. Criação de um painel de auditoria no frontend para revisar os dados extraídos antes da consolidação.