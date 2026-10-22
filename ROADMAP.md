# Roadmap

Manter o projeto deliberadamente pequeno. Só acrescentar componentes quando forem necessários para fiabilidade ou privacidade.

## 1. Confirmar a fonte e o método

- [x] Identificar o Diário da República como fonte oficial.
- [x] Encontrar uma plataforma de terceiros que afirma indexar despachos e oferecer notificações Telegram.
- [ ] Verificar se o Diário da República disponibiliza um método estável de consulta automatizada (pesquisa, RSS, ficheiros ou endpoint público).
- [ ] Identificar os despachos da AIMA relevantes e confirmar como os nomes são apresentados.
- [ ] Verificar condições de utilização e limites de acesso antes de automatizar pedidos.

**Decisão provisória:** usar o Diário da República como fonte de verdade. O site de terceiros pode servir como referência para compreender o formato dos dados, mas não deve ser dependência do serviço sem avaliação adicional. Não foi confirmado um repositório público com o código dessa solução.

## 2. Implementar a verificação

- [ ] Criar um script Python pequeno que devolva um de três resultados: correspondência, sem correspondência ou erro.
- [ ] Consultar apenas as publicações relevantes, evitando descarregar e processar todo o arquivo a cada execução.
- [ ] Definir timeouts e tratamento de erros; nunca confundir erro com resultado negativo.
- [ ] Normalizar espaços e maiúsculas/minúsculas sem assumir que nomes semelhantes identificam a mesma pessoa.
- [ ] Não registar o nome pesquisado, o token ou o Chat ID nos logs.
- [ ] Testar com respostas fictícias, sem nomes reais.

## 3. Integrar o Telegram

- [ ] Enviar uma mensagem de teste pela Telegram Bot API.
- [ ] Ler token, Chat ID e nome apenas de GitHub Actions Secrets.
- [ ] Incluir uma ligação para a publicação oficial na mensagem.
- [ ] Tratar falhas de envio sem expor credenciais.

## 4. Agendar no GitHub Actions

- [ ] Criar workflow diário e permitir execução manual com `workflow_dispatch`.
- [ ] Definir permissões mínimas para o workflow.
- [ ] Usar uma versão suportada de Python e manter as dependências mínimas.
- [ ] Testar manualmente antes de confiar no agendamento.

## 5. Evitar alertas repetidos

- [ ] Escolher um mecanismo persistente e simples para registar que o alerta positivo foi enviado.
- [ ] Guardar apenas o estado mínimo, sem nome ou outros dados pessoais.
- [ ] Só marcar o alerta como enviado depois de o Telegram confirmar o envio.
- [ ] Documentar como reiniciar a monitorização.

## 6. Preparar para utilização

- [ ] Documentar instalação e configuração com um teste de ponta a ponta.
- [ ] Adicionar `.gitignore` se forem necessários ficheiros locais ou variáveis de ambiente.
- [ ] Escolher uma licença explícita se o projeto for publicado como open source.
- [ ] Confirmar que o repositório e os logs não contêm dados pessoais nem segredos.

## Fora do âmbito inicial

Base de dados, painel web, contas de utilizador, pagamentos, múltiplas fontes e infraestrutura própria.
