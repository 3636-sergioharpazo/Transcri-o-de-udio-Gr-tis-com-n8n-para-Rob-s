# Transcrição de Áudio Grátis com n8n para Robôs

> Plataforma de automação para transcrição de áudio utilizando n8n, integrando robôs e fluxos de trabalho automatizados.

---

## Sumário

* [Sobre](#sobre)
* [Funcionalidades](#funcionalidades)
* [Requisitos](#requisitos)
* [Arquitetura](#arquitetura)
* [Instalação rápida (Docker)](#instalacao-rapida-docker)
* [Instalação em VPS](#instalacao-em-vps)
* [Configuração da API](#configuracao-da-api)
* [Endpoints principais](#endpoints-principais)
* [Exemplos de uso](#exemplos-de-uso)
* [Segurança](#seguranca)
* [Deploy / Produção](#deploy--producao)
* [Contribuição](#contribuicao)
* [Licença](#licenca)
* [Contato](#contato)

---

## Sobre

Este projeto oferece uma **API** e infraestrutura de automação usando **n8n** para permitir a transcrição automática de arquivos de áudio. Ideal para robôs que precisam processar e transcrever áudios de forma eficiente, com integração em pipelines automatizados.

---

## Funcionalidades

* Upload e gerenciamento de arquivos de áudio
* Transcrição automática de áudio em texto
* Integração com n8n para automação de fluxos
* Execução via Docker ou VPS
* Armazenamento seguro dos resultados
* API REST para controle de robôs e workflows

---

## Requisitos

* Docker >= 20.x
* Docker Compose >= 1.29.x
* Node.js 18+ (para serviços auxiliares, se houver)
* VPS com acesso root ou usuário com sudo (para deploy em produção)
* Certificado SSL para produção (Let's Encrypt recomendado)

---

## Arquitetura

Fluxo simplificado:

1. Usuário envia arquivo de áudio para API.
2. API envia arquivo para workflow n8n.
3. Workflow processa o áudio e gera transcrição.
4. Resultado é armazenado e retornado via API.

---

## Instalação rápida (Docker)

```bash
git clone https://github.com/seu-usuario/transcricao-de-audio-n8n.git
cd transcricao-de-audio-n8n
cp .env.example .env
# Edite variáveis do .env conforme necessário

docker compose up -d --build
```

---

## Instalação em VPS

1. Atualize o servidor:

```bash
sudo apt update && sudo apt upgrade -y
```

2. Instale Docker e Docker Compose.
3. Clone o repositório e configure `.env`.
4. Configure proxy reverso com HTTPS (Nginx ou Traefik).
5. Suba os serviços com `docker compose up -d`.

---

## Configuração da API

Exemplo de `.env`:

```
PORT=3000
JWT_SECRET=uma_chave_secreta
N8N_BASE_URL=http://n8n:5678
STORAGE_PATH=/dados/transcricoes
```

---

## Endpoints principais

* `POST /upload-audio` — Envia áudio para transcrição
* `GET /transcricoes/:id` — Recupera transcrição
* `GET /status/:id` — Verifica status do processamento
* `POST /trigger-workflow` — Executa workflow n8n manualmente

---

## Exemplos de uso (cURL)

Enviar arquivo de áudio:

```bash
curl -X POST https://seu-dominio.com/api/upload-audio \
  -H "Authorization: Bearer $TOKEN" \
  -F "file=@audio.mp3"
```

Recuperar transcrição:

```bash
curl -X GET https://seu-dominio.com/api/transcricoes/123 \
  -H "Authorization: Bearer $TOKEN"
```

---

## Segurança

* HTTPS obrigatório em produção
* Autenticação JWT para endpoints
* Armazenamento seguro de arquivos e transcrições

---

## Deploy / Produção

* Configure backups automáticos
* Monitore logs e filas
* Automatize deploy via CI/CD

---

## Contribuição

1. Fork do repositório
2. Crie branch feature/nome
3. Comite alterações
4. Abra PR

---

## Licença

Licença MIT — veja `LICENSE`

---



## Contato

📧 E-mail: `sergioharpazo@gmail.com`
🌐 Site: https://loja.antoniooliveira.shop
