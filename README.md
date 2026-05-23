# Orçamentos Express — Guia de Deploy

## Estrutura de arquivos

```
orcamentos-express/
├── index.html      ← Landing page com planos e preços
├── login.html      ← Tela de login
├── register.html   ← Cadastro com seleção de plano
├── app.html        ← App principal (protegido por login)
└── README.md       ← Este arquivo
```

---

## Como fazer deploy no Vercel (gratuito)

### Opção 1 — Arrastar e soltar (mais fácil)
1. Acesse https://vercel.com e crie uma conta gratuita
2. No dashboard, clique em **"Add New → Project"**
3. Escolha **"Deploy from existing files"** ou arraste a pasta `orcamentos-express`
4. Clique em **Deploy**
5. Em segundos seu app estará em `https://seu-app.vercel.app`

### Opção 2 — Via GitHub (recomendado para atualizações)
1. Crie um repositório no https://github.com
2. Faça upload dos arquivos HTML
3. No Vercel, importe o repositório
4. Toda vez que atualizar o GitHub, o Vercel faz deploy automático

### Domínio próprio
1. Compre um domínio em https://registro.br (~R$40/ano para .com.br)
2. No painel do Vercel → Settings → Domains
3. Adicione seu domínio e siga as instruções de DNS

---

## Como fazer deploy no Netlify (alternativa)

1. Acesse https://netlify.com
2. Arraste a pasta `orcamentos-express` direto na tela
3. Pronto! URL automática tipo `https://seuapp.netlify.app`

---

## Configuração para cobranças reais (Kiwify/Stripe)

O sistema de planos atual é simulado via localStorage.
Para cobranças reais, integre uma dessas plataformas:

### Kiwify (recomendado para Brasil)
- Acesse https://kiwify.com.br
- Crie um produto "Orçamentos Express Pro" com recorrência mensal
- Ao confirmar pagamento, chame a API do Kiwify para atualizar o plano do usuário
- Webhook URL: adicione lógica no backend para atualizar `orc_users` via API

### Stripe
- Crie conta em https://stripe.com/br
- Use Stripe Checkout para processar pagamentos
- Configure webhooks para `checkout.session.completed`

### Backend necessário para produção
Para autenticação e dados em nuvem, use uma dessas opções gratuitas:
- **Supabase** (https://supabase.com) — banco PostgreSQL + auth gratuito
- **Firebase** (https://firebase.google.com) — banco + auth do Google, gratuito

---

## Chave de API da IA

O app usa a API da Anthropic. No ambiente Claude.ai, a chave é injetada automaticamente.

Para hospedar em servidor próprio:
1. Crie conta em https://console.anthropic.com
2. Gere uma API key
3. Crie um backend simples (Node.js/Python) para fazer as chamadas com segurança
4. **NUNCA** exponha a API key no frontend em produção

---

## Suporte e dúvidas
Criado com IA pelo Claude (Anthropic). Personalize à vontade!
