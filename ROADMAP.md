# Roadmap

Manter o projeto deliberadamente pequeno. Só acrescentar componentes quando forem necessários para fiabilidade ou privacidade.

## 1. Confirmar a fonte oficial
- [ ] Identificar a página oficial onde são publicadas as emissões/listagens relevantes.
- [ ] Confirmar se existe pesquisa, página HTML, ficheiro ou endpoint oficial reutilizável.
- [ ] Verificar condições de utilização, limitações de acesso e frequência adequada.
- [ ] Documentar a URL pública e o método de consulta, sem dados pessoais.

**Concluído quando:** o método for reproduzível e não depender de contornar controlos de acesso.

## 2. Implementar a verificação
- [ ] Criar um script Python pequeno que devolva um de três resultados: correspondência, sem correspondência ou erro.
- [ ] Definir timeouts e tratamento de erros; nunca confundir erro com resultado negativo.
- [ ] Normalizar espaços e maiúsculas/minúsculas sem assumir que nomes semelhantes identificam a mesma pessoa.
- [ ] Não registar o nome pesquisado, o token ou o Chat ID nos logs.
- [ ] Testar com respostas fictícias, sem nomes reais.

## 3. Integrar o Telegram
- [ ] Enviar uma mensagem de teste pela Telegram Bot API.
- [ ] Ler token, Chat ID e nome apenas de GitHub Actions Secrets.
- [ ] Incluir uma ligação para a fonte oficial na mensagem.
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
