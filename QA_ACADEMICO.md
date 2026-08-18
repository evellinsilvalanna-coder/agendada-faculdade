# QA — Orbe acadêmico

## Revisão executada
- Estrutura do app e render.yaml preservados.
- Migrações do schema são aditivas.
- Rotas genéricas filtram sempre por usuário autenticado e `created_by_id`.
- Front-end não acessa banco diretamente.
- PWA inclui manifest, ícone e service worker.
- Layout usa breakpoints mobile-first e menu inferior.
- Fórmulas simples e ponderadas são armazenadas por disciplina.
- Busca global considera apenas entidades carregadas do usuário autenticado.

## Observação de publicação
O endereço Render existente ainda apresenta a aplicação antiga de precificação. A nova interface está pronta no diretório `precocerto-clone`, mas não foi publicada por esta etapa porque a credencial do Render está pendente e publicar seria uma ação externa.

## Checklist para o próximo deploy
- [ ] Configurar/confirmar `DATABASE_URL` existente.
- [ ] Confirmar `AUTH_SECRET` existente.
- [ ] Executar deploy sem substituir o serviço.
- [ ] Abrir `/` e validar login.
- [ ] Criar disciplina, tarefa, avaliação e aula.
- [ ] Confirmar que outro usuário não acessa esses registros.
- [ ] Testar instalação da PWA em Android/iPhone.
- [ ] Testar layout em 390px, 768px e desktop.
- [ ] Validar migração no banco de produção.
- [ ] Conferir logs do Render após o deploy.
