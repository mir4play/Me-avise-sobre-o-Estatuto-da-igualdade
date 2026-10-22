# 🔔 AutoAlertBot (Telegram / GitHub Actions)

Um sistema de alertas simples, de código aberto, 100% gratuito e sem necessidade de banco de dados ou servidores.

---

## 📌 Visão Geral do Projeto

Existem eventos, prazos ou ocorrências que acontecem raramente (uma vez por ano ou em intervalos longos). Como o tempo de espera é grande, é fácil esquecer a data.

Este projeto é um utilitário ultraleve para verificar diariamente se um evento/data aconteceu e disparar uma notificação direta no seu **Telegram**, sem precisar manter nenhum servidor ligado e sem a complexidade de gerenciar banco de dados.

---

## 🏗️ Como Funciona a Arquitetura (Sem Banco de Dados)

O projeto roda inteiramente na nuvem do GitHub usando uma estrutura *Serverless*:

[ Configuração Local / GitHub Secrets ] ──( ID do Telegram + Evento )
                                                     │
                                       (Verificação diária via Cron)
                                                     │
[ GitHub Actions ] ──( Executa Script Python )───────┘
        │
        └──( Envia Notificação HTTP )──> [ Telegram Bot API ] ──> [ Celular do Usuário ]

1. **Configuração Simples:** Você define a data/evento a ser monitorado e o seu Chat ID do Telegram no próprio código ou nas configurações privadas do repositório (GitHub Secrets).
2. **Execução Diária (Cron Job):** Uma vez por dia, o **GitHub Actions** "acorda" no horário programado e roda o script de verificação.
3. **Verificação:** O script testa se a condição do alerta foi atingida.
4. **Disparo:** Se a condição for verdadeira, o script faz uma chamada HTTP para a API do Telegram e a mensagem chega no seu celular.
5. **Finalização:** A máquina virtual é desligada sem gerar nenhum custo.

---

## 🛠️ Tecnologias Utilizadas

* **Linguagem Principal:** Python 3.x
* **Orquestração:** GitHub Actions (`.github/workflows/daily-check.yml`)
* **Notificações:** Telegram Bot API (100% gratuita e oficial)
* **Segurança:** GitHub Repository Secrets (para armazenar o Token do Bot e o Chat ID)

---

## 📂 Estrutura do Repositório

├── .github/
│   └── workflows/
│       └── daily-check.yml      # Configuração da execução diária do GitHub Actions
├── main.py                      # Script em Python com a lógica de verificação e envio
├── requirements.txt             # Dependências (ex: requests)
└── README.md                    # Documentação do projeto

---

## 🚀 Como Configurar e Usar

1. **Criar o Bot no Telegram:**
   * Fale com o `@BotFather` no Telegram para criar um novo bot e copie o **API Token**.
   * Abra o bot criado e envie qualquer mensagem (`/start`).
   * Descubra seu **Chat ID** enviando uma mensagem para o `@userinfobot`.

2. **Configurar o GitHub:**
   * Faça um fork deste repositório.
   * Vá em **Settings > Secrets and variables > Actions** e adicione duas secrets:
     * `TELEGRAM_BOT_TOKEN`: O token fornecido pelo BotFather.
     * `TELEGRAM_CHAT_ID`: O seu Chat ID obtido no Telegram.

3. **Pronto!** O GitHub Actions cuidará da verificação diária e avisará você quando o momento chegar.

---

## 🤝 Contribuição

Este é um projeto aberto! Sinta-se à vontade para abrir *Issues* ou enviar *Pull Requests* para propor melhorias na lógica de verificação dos eventos.
