# Orbe — organização acadêmica

Esta versão transforma o app existente em uma plataforma acadêmica, sem substituir a infraestrutura de autenticação ou o banco já configurados.

## O que foi preservado e reutilizado
- Serviço Node no Render (`render.yaml`) e `npm start`.
- PostgreSQL existente via `DATABASE_URL`.
- Autenticação por e-mail/senha e tokens assinados em `server.js`.
- Tabela `users`, tabela genérica `entities` e isolamento obrigatório por `created_by_id` no back-end.
- Dados anteriores: o schema usa apenas migrações aditivas e não remove tabelas/linhas.

## Módulo acadêmico
A tabela genérica existente recebe as entidades `Subject`, `Teacher`, `Task`, `Assessment`, `Schedule`, `StudySession`, `CalendarEvent`, `Material` e `Notification`. Todas as consultas passam pelo usuário autenticado no servidor. O front-end é mobile-first, instalável como PWA, com dashboard, disciplinas, grade, tarefas, calendário, estudo, notas ponderadas, simulador de nota necessária, desempenho, professores, materiais, notificações e configurações.

## Deploy / variáveis
Não é necessário criar serviço novo no Render. Mantenha:
- `DATABASE_URL`: conexão PostgreSQL já existente.
- `AUTH_SECRET`: segredo de sessão já existente (defina um valor forte em produção).
- `PORT`: fornecido automaticamente pelo Render.

O `schema.sql` adiciona somente campos de perfil acadêmico em `users` (`institution`, `course`, `semester`, `shift`, `avatar_url`) usando `ADD COLUMN IF NOT EXISTS`.

## Limitações honestas
Notificações locais dependem da permissão do navegador. A aplicação oferece o caminho PWA/atalhos para a tela inicial; widgets nativos reais só podem ser ativados quando o sistema operacional e o navegador oferecerem essa API. Não há dados de demonstração inseridos automaticamente em produção.
