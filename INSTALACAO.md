# Guia de Instalação e Configuração

## 📋 Pré-requisitos

### Mínimos
- Navegador web moderno (Chrome, Firefox, Safari, Edge)
- Conexão com internet
- Nenhuma instalação adicional necessária para o protótipo

### Recomendados
- Node.js 14+ (para desenvolvimento futuro)
- npm ou yarn (para gerenciamento de pacotes)
- Git (para controle de versão)
- Visual Studio Code (editor de código)

## 🚀 Instalação Rápida

### Opção 1: Abrir Diretamente (Mais Simples)

1. **Localize o arquivo**
   ```bash
   cd /home/ubuntu/omnichannel_clinica
   ```

2. **Abra em um navegador**
   ```bash
   # No Linux
   firefox html/index.html
   # ou
   chromium html/index.html
   
   # No macOS
   open html/index.html
   
   # No Windows
   start html/index.html
   ```

### Opção 2: Usar Servidor Local (Recomendado)

1. **Com Python (Python 3)**
   ```bash
   cd /home/ubuntu/omnichannel_clinica
   python3 -m http.server 8080
   ```
   Acesse: `http://localhost:8080/html/index.html`

2. **Com Python (Python 2)**
   ```bash
   cd /home/ubuntu/omnichannel_clinica
   python -m SimpleHTTPServer 8080
   ```
   Acesse: `http://localhost:8080/html/index.html`

3. **Com Node.js (http-server)**
   ```bash
   npm install -g http-server
   cd /home/ubuntu/omnichannel_clinica
   http-server -p 8080
   ```
   Acesse: `http://localhost:8080/html/index.html`

4. **Com Node.js (Express)**
   ```bash
   npm init -y
   npm install express
   ```
   
   Crie `server.js`:
   ```javascript
   const express = require('express');
   const app = express();
   
   app.use(express.static(__dirname));
   
   app.listen(8080, () => {
       console.log('Servidor rodando em http://localhost:8080');
   });
   ```
   
   Execute:
   ```bash
   node server.js
   ```

### Opção 3: Usar Live Server (VS Code)

1. **Instale a extensão Live Server**
   - Abra VS Code
   - Vá para Extensions (Ctrl+Shift+X)
   - Procure por "Live Server"
   - Clique em "Install"

2. **Abra o arquivo HTML**
   - Clique com botão direito em `html/index.html`
   - Selecione "Open with Live Server"

## 📦 Estrutura de Arquivos

```
omnichannel_clinica/
├── html/
│   └── index.html              # Página principal
├── css/
│   ├── style.css               # Estilos principais (1000+ linhas)
│   └── responsive.css          # Estilos responsivos
├── js/
│   ├── main.js                 # Sistema principal
│   ├── navigation.js           # Navegação
│   ├── chat.js                 # Chat e mensagens
│   └── (outros scripts)
├── assets/                     # Imagens e recursos (opcional)
├── README.md                   # Documentação
├── ARQUITETURA.md             # Documentação técnica
├── INSTALACAO.md              # Este arquivo
└── GUIA_USO.md                # Guia de uso (opcional)
```

## ⚙️ Configuração

### Variáveis de Ambiente (Futuro)

Crie um arquivo `.env` na raiz do projeto:

```env
# Configurações da Aplicação
APP_NAME=Sistema Omnichannel
APP_VERSION=1.0.0
DEBUG=true

# Configurações de API
API_BASE_URL=http://localhost:3000/api
API_TIMEOUT=5000

# Configurações de Banco de Dados (Futuro)
DB_HOST=localhost
DB_PORT=5432
DB_NAME=omnichannel_clinica
DB_USER=admin
DB_PASSWORD=senha_segura

# Configurações de Autenticação (Futuro)
JWT_SECRET=sua_chave_secreta_aqui
JWT_EXPIRY=24h

# Configurações de Integração
WHATSAPP_API_KEY=sua_chave_aqui
FACEBOOK_API_KEY=sua_chave_aqui
SENDGRID_API_KEY=sua_chave_aqui
```

### Configurações de Cores

Edite `css/style.css` para personalizar as cores:

```css
:root {
    --primary-color: #2563eb;        /* Azul principal */
    --secondary-color: #10b981;      /* Verde secundário */
    --danger-color: #ef4444;         /* Vermelho de perigo */
    --warning-color: #f59e0b;        /* Amarelo de aviso */
    --dark-bg: #1f2937;              /* Fundo escuro */
    --light-bg: #f3f4f6;             /* Fundo claro */
    --card-bg: #ffffff;              /* Fundo de cards */
    --text-primary: #111827;         /* Texto primário */
    --text-secondary: #6b7280;       /* Texto secundário */
    --border-color: #e5e7eb;         /* Cor de bordas */
}
```

### Configurações de Usuário

Edite `js/main.js` para configurar o usuário padrão:

```javascript
const AppState = {
    usuarioAtual: {
        id: 1,
        nome: 'Ana Torres',              // Mude o nome
        email: 'ana.torres@clinica.com', // Mude o e-mail
        funcao: 'Atendente',             // Mude a função
        avatar: 'AT'                     // Mude as iniciais
    },
    // ... resto do código
};
```

## 🔧 Desenvolvimento

### Estrutura de Desenvolvimento

```bash
omnichannel_clinica/
├── src/                    # (Futuro) Código fonte
│   ├── components/
│   ├── pages/
│   ├── services/
│   └── utils/
├── public/                 # (Futuro) Arquivos estáticos
├── tests/                  # (Futuro) Testes
├── dist/                   # (Futuro) Build de produção
├── package.json            # (Futuro) Dependências
└── webpack.config.js       # (Futuro) Configuração de build
```

### Ferramentas Recomendadas

1. **Editor de Código**
   - Visual Studio Code
   - WebStorm
   - Sublime Text

2. **Extensões VS Code**
   - Live Server
   - Prettier
   - ESLint
   - HTML/CSS Support
   - JavaScript (ES6) code snippets

3. **Ferramentas de Debug**
   - Chrome DevTools (F12)
   - Firefox Developer Tools (F12)
   - VS Code Debugger

## 🧪 Testes

### Testes Manuais

1. **Navegação**
   - [ ] Clique em cada link do menu
   - [ ] Verifique se a página muda
   - [ ] Verifique se o título atualiza

2. **Filtros**
   - [ ] Clique em cada filtro da caixa de entrada
   - [ ] Verifique se os itens são filtrados corretamente

3. **Busca**
   - [ ] Digite na caixa de busca
   - [ ] Verifique se os resultados são filtrados em tempo real

4. **Chat**
   - [ ] Abra uma conversa
   - [ ] Envie uma mensagem
   - [ ] Verifique se a resposta automática aparece

5. **Responsividade**
   - [ ] Redimensione a janela do navegador
   - [ ] Verifique se o layout se adapta
   - [ ] Teste em dispositivos móveis

### Testes Automatizados (Futuro)

```bash
# Instalar dependências de teste
npm install --save-dev jest @testing-library/dom

# Executar testes
npm test
```

## 📊 Monitoramento

### Verificar Performance

1. **Chrome DevTools**
   - Abra DevTools (F12)
   - Vá para "Performance"
   - Clique em "Record"
   - Interaja com a aplicação
   - Clique em "Stop"

2. **Lighthouse**
   - Abra DevTools (F12)
   - Vá para "Lighthouse"
   - Clique em "Generate report"

### Verificar Erros

1. **Console**
   - Abra DevTools (F12)
   - Vá para "Console"
   - Verifique se há erros (vermelho)

2. **Network**
   - Abra DevTools (F12)
   - Vá para "Network"
   - Verifique requisições e respostas

## 🔒 Segurança

### Boas Práticas

1. **Sempre use HTTPS em produção**
   ```bash
   # Gerar certificado auto-assinado (desenvolvimento)
   openssl req -x509 -newkey rsa:4096 -nodes -out cert.pem -keyout key.pem -days 365
   ```

2. **Valide sempre no backend**
   - Nunca confie apenas em validação frontend

3. **Sanitize inputs**
   - Use bibliotecas como DOMPurify

4. **Proteção contra CSRF**
   - Use tokens CSRF em formulários

5. **Proteção contra XSS**
   - Evite usar `innerHTML`
   - Use `textContent` quando possível

## 🚀 Deploy

### Deploy Local
```bash
# Servidor Python
python3 -m http.server 8080

# Servidor Node.js
node server.js
```

### Deploy em Produção (Futuro)

1. **Heroku**
   ```bash
   heroku create seu-app
   git push heroku main
   ```

2. **Vercel**
   ```bash
   npm install -g vercel
   vercel
   ```

3. **AWS**
   - S3 + CloudFront
   - EC2 + Load Balancer
   - Lambda + API Gateway

4. **Docker**
   ```dockerfile
   FROM node:14
   WORKDIR /app
   COPY . .
   EXPOSE 8080
   CMD ["node", "server.js"]
   ```

## 📞 Suporte

### Troubleshooting

**Problema**: Página em branco
- **Solução**: Verifique o console (F12) para erros

**Problema**: Estilos não carregam
- **Solução**: Verifique se os arquivos CSS estão no caminho correto

**Problema**: JavaScript não funciona
- **Solução**: Verifique se os arquivos JS estão no caminho correto

**Problema**: Servidor recusa conexão
- **Solução**: Verifique se a porta está disponível

### Recursos Úteis

- [MDN Web Docs](https://developer.mozilla.org/)
- [Can I Use](https://caniuse.com/)
- [Stack Overflow](https://stackoverflow.com/)
- [GitHub](https://github.com/)

## 📝 Próximos Passos

1. [ ] Implementar backend com Node.js/Express
2. [ ] Configurar banco de dados PostgreSQL
3. [ ] Implementar autenticação com JWT
4. [ ] Integrar com APIs reais (WhatsApp, Facebook, etc.)
5. [ ] Adicionar testes automatizados
6. [ ] Configurar CI/CD com GitHub Actions
7. [ ] Deploy em produção
8. [ ] Monitoramento e análise

---

**Versão**: 1.0.0
**Última Atualização**: 18 de Novembro de 2025
