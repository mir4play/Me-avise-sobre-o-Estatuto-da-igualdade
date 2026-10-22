# Me Avise sobre o Estatuto da Igualdade

Receba uma mensagem no Telegram quando o seu nome aparecer na publicação oficial relacionada com a emissão do Estatuto da Igualdade em Portugal.

O objetivo é manter uma solução pequena: consulta diária de uma fonte oficial e alerta quando houver uma correspondência.

**Estado atual:** planeamento. A fonte oficial ainda precisa de ser confirmada; o bot e a execução diária ainda não estão implementados.

## Como deverá funcionar

1. Configurar um bot do Telegram e iniciar uma conversa com ele.
2. Guardar o nome a pesquisar em GitHub Actions Secrets, nunca no código ou nos logs.
3. O GitHub Actions executa a verificação uma vez por dia.
4. O script consulta a fonte oficial e distingue correspondência, ausência de correspondência e erro.
5. Quando confirmar uma correspondência, envia uma mensagem com ligação para a fonte oficial.

## Princípios

- **Simplicidade:** Python e GitHub Actions; sem servidor próprio nem dependências desnecessárias.
- **Sem base de dados:** não manter uma base de dados de utilizadores; guardar apenas o estado mínimo necessário para evitar alertas repetidos.
- **Privacidade:** nunca publicar nomes, tokens ou IDs de chat. Não registar o nome pesquisado nos logs.
- **Fonte oficial:** verificar se a página e o método de consulta são adequados e permitidos antes de automatizar pedidos.
- **Fiabilidade:** uma falha de rede ou uma página alterada nunca deve ser tratada como resultado negativo.
- **Cautela:** um nome pode corresponder a mais de uma pessoa. O alerta não substitui a confirmação na publicação oficial.
- **Custos:** usar o GitHub Actions dentro dos limites do plano aplicável; o horário agendado pode sofrer atrasos.

## Configuração prevista

A implementação deverá usar estes GitHub Actions Secrets:

- `TELEGRAM_BOT_TOKEN`: token criado pelo [@BotFather](https://t.me/BotFather).
- `TELEGRAM_CHAT_ID`: destino da mensagem no Telegram.
- `TARGET_NAME`: nome a pesquisar.

Não adicione estes valores ao código, a issues, a commits ou a mensagens de log. Nunca partilhe o token do bot.

## Limitações

- O serviço só deteta informação disponível na fonte consultada; não confirma o estado administrativo junto da entidade pública.
- O nome não é um identificador único.
- O agendamento do GitHub Actions não garante execução ao minuto exato.
- Evitar notificações repetidas requer guardar um pequeno estado persistente, mas não uma base de dados.

## Desenvolvimento

Consulte o [roadmap](ROADMAP.md) para as próximas etapas.

## Licença

Ainda não foi escolhida uma licença. Até ser adicionada, não assuma que o código pode ser reutilizado, redistribuído ou modificado livremente.
