# Arquitetura do Sistema Omnichannel

## 📐 Visão Geral

O Sistema Omnichannel para Clínica Médica é uma aplicação web moderna que centraliza o atendimento de pacientes através de múltiplos canais de comunicação. A arquitetura foi projetada para ser escalável, responsiva e fácil de manter.

## 🏗️ Arquitetura em Camadas

```
┌─────────────────────────────────────────────────────────────┐
│                    CAMADA DE APRESENTAÇÃO                   │
│  (HTML5, CSS3, JavaScript - Interface do Usuário)          │
└─────────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────────┐
│                   CAMADA DE LÓGICA                          │
│  (JavaScript - Navegação, Filtros, Gerenciamento de Estado) │
└─────────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────────┐
│                   CAMADA DE DADOS                           │
│  (LocalStorage, Dados Simulados, APIs Futuras)             │
└─────────────────────────────────────────────────────────────┘
```

## 📁 Estrutura de Arquivos

### Frontend

#### HTML (`html/index.html`)
- **Responsabilidade**: Estrutura semântica da aplicação
- **Componentes**:
  - Sidebar de navegação
  - Header com busca e notificações
  - Seções de conteúdo (Dashboard, Inbox, Conversas, etc.)
  - Footer (opcional)

#### CSS (`css/style.css`)
- **Responsabilidade**: Estilos visuais e layout
- **Características**:
  - Variáveis CSS para cores e espaçamento
  - Grid layout para responsividade
  - Animações suaves
  - Design system consistente

#### CSS Responsivo (`css/responsive.css`)
- **Responsabilidade**: Adaptação para diferentes dispositivos
- **Breakpoints**:
  - Desktop: 1024px+
  - Tablet: 768px - 1024px
  - Mobile: até 768px
  - Small Mobile: até 480px

#### JavaScript Principal (`js/main.js`)
- **Responsabilidade**: Inicialização e gerenciamento central
- **Classes/Objetos**:
  - `CONFIG`: Configurações globais
  - `Utils`: Funções utilitárias
  - `AppState`: Estado da aplicação
  - `APIManager`: Gerenciamento de requisições
  - `EventManager`: Sistema de eventos customizados
  - `StorageManager`: Gerenciamento de LocalStorage
  - `ThemeManager`: Gerenciamento de temas
  - `PermissaoManager`: Controle de permissões
  - `App`: Classe principal

#### JavaScript de Navegação (`js/navigation.js`)
- **Responsabilidade**: Controle de navegação entre páginas
- **Funcionalidades**:
  - Alternância de páginas
  - Filtros de caixa de entrada
  - Busca em tempo real
  - Notificações
  - Seleção de conversas

#### JavaScript de Chat (`js/chat.js`)
- **Responsabilidade**: Funcionalidades de chat e mensagens
- **Classes**:
  - `ChatManager`: Gerenciamento de conversas
  - `MetricasManager`: Gerenciamento de métricas
  - `FiltroManager`: Gerenciamento de filtros
  - `NotificacaoManager`: Gerenciamento de notificações
  - `BuscaManager`: Gerenciamento de busca

## 🔄 Fluxo de Dados

```
Usuário Interage
    ↓
Event Listener (JavaScript)
    ↓
Validação de Permissões
    ↓
Atualização do AppState
    ↓
Chamada de API (simulada)
    ↓
Atualização do DOM
    ↓
Salvar em LocalStorage
    ↓
Exibir Resultado para Usuário
```

## 🎯 Padrões de Design

### 1. MVC (Model-View-Controller)
- **Model**: Dados em `AppState` e `window.conversas`, `window.pacientes`, `window.metricas`
- **View**: Elementos HTML e CSS
- **Controller**: Funções JavaScript em `navigation.js` e `chat.js`

### 2. Observer Pattern
- `EventManager` implementa o padrão Observer
- Permite comunicação entre componentes sem acoplamento

### 3. Singleton Pattern
- `AppState`, `APIManager`, `StorageManager` são singletons
- Garantem uma única instância durante a execução

### 4. Factory Pattern
- `ChatManager`, `MetricasManager` atuam como factories
- Criam e gerenciam instâncias de objetos

## 📊 Componentes Principais

### 1. Sidebar
- Navegação principal
- Informações do usuário
- Links para todas as seções

### 2. Header
- Busca global
- Notificações
- Logout

### 3. Dashboard
- Estatísticas gerais
- Canais de comunicação
- Atendimentos recentes

### 4. Caixa de Entrada
- Lista de mensagens
- Filtros por status
- Indicação de canal

### 5. Conversas
- Lista de chats
- Histórico de mensagens
- Área de input

### 6. Agenda
- Slots de atendimento
- Disponibilidade
- Agendamento

### 7. Relatórios
- Gráficos de desempenho
- Produtividade da equipe
- Satisfação do paciente

### 8. Usuários
- Tabela de usuários
- Gerenciamento de permissões
- Ações (editar, remover)

## 🔐 Segurança

### Implementações Atuais
1. **Validação de Input**: Verificação de campos vazios
2. **Proteção XSS**: Uso de `textContent` ao invés de `innerHTML`
3. **CORS**: Preparado para requisições cross-origin
4. **Permissões**: Sistema de controle de acesso baseado em funções

### Recomendações Futuras
1. **Autenticação**: JWT com refresh tokens
2. **Criptografia**: TLS/SSL para dados em trânsito
3. **Rate Limiting**: Proteção contra abuso
4. **Auditoria**: Log de todas as ações
5. **Validação Backend**: Sempre validar no servidor

## 📈 Performance

### Otimizações Atuais
1. **CSS Minificado**: Reduz tamanho do arquivo
2. **JavaScript Modular**: Carregamento sob demanda
3. **LocalStorage**: Cache de dados locais
4. **Lazy Loading**: Imagens carregadas conforme necessário

### Recomendações Futuras
1. **Bundling**: Webpack ou Vite para otimização
2. **Compressão**: Gzip para arquivos estáticos
3. **CDN**: Distribuição global de conteúdo
4. **Service Workers**: Cache offline
5. **Code Splitting**: Carregamento dinâmico de módulos

## 🔌 Integrações

### APIs Simuladas (Atuais)
```javascript
APIManager.getConversas()      // Retorna conversas
APIManager.getPacientes()      // Retorna pacientes
APIManager.getMetricas()       // Retorna métricas
APIManager.enviarMensagem()    // Simula envio
APIManager.agendar()           // Simula agendamento
APIManager.criarUsuario()      // Simula criação de usuário
```

### APIs Reais (Futuras)
1. **WhatsApp Business API**: Envio e recebimento de mensagens
2. **Facebook Graph API**: Messenger e Instagram DM
3. **SendGrid/Mailgun**: Gerenciamento de e-mails
4. **Google Calendar**: Integração de agenda
5. **Twilio**: Suporte a telefone
6. **Sistema de Prontuário**: Integração com EHR

## 🗄️ Modelo de Dados

### Conversa
```javascript
{
    id: number,
    paciente: string,
    avatar: string,
    canal: string,           // whatsapp, email, instagram, facebook
    status: string,          // ativo, inativo
    ultimaMensagem: string,
    hora: string,
    naoLidas: number,
    mensagens: Message[]
}
```

### Mensagem
```javascript
{
    tipo: string,            // enviada, recebida
    texto: string,
    hora: string,
    lida: boolean,
    anexos: File[]
}
```

### Paciente
```javascript
{
    id: number,
    nome: string,
    cpf: string,
    email: string,
    telefone: string,
    dataNascimento: string,
    endereco: string,
    especialidade: string,
    medico: string,
    ultimaConsulta: string,
    proximaConsulta: string
}
```

### Métrica
```javascript
{
    atendimentosHoje: number,
    tempoMedioResposta: number,  // em segundos
    taxaResolucao: number,       // em percentual
    consultasAgendadas: number,
    canais: {
        whatsapp: { total: number, naoLidas: number },
        email: { total: number, naoLidas: number },
        instagram: { total: number, naoLidas: number },
        facebook: { total: number, naoLidas: number }
    }
}
```

## 🚀 Escalabilidade

### Estratégias Atuais
1. **Modularização**: Código dividido em múltiplos arquivos
2. **Separação de Responsabilidades**: Cada arquivo tem um propósito
3. **Reutilização**: Funções e classes reutilizáveis

### Estratégias Futuras
1. **Microserviços**: Dividir em serviços independentes
2. **Load Balancing**: Distribuir carga entre servidores
3. **Caching**: Redis para cache distribuído
4. **Fila de Mensagens**: RabbitMQ ou Kafka
5. **Containerização**: Docker para deployment

## 📱 Responsividade

### Breakpoints
- **Desktop**: 1024px+ (layout completo)
- **Tablet**: 768px - 1024px (layout adaptado)
- **Mobile**: até 768px (layout mobile)
- **Small Mobile**: até 480px (layout compacto)

### Adaptações
- Sidebar colapsável em mobile
- Navegação horizontal em mobile
- Redimensionamento de componentes
- Ocultação de elementos não essenciais

## 🧪 Testes

### Testes Recomendados
1. **Unitários**: Testar funções individuais
2. **Integração**: Testar interação entre componentes
3. **E2E**: Testar fluxos completos
4. **Performance**: Medir tempo de carregamento
5. **Acessibilidade**: Verificar conformidade com WCAG

### Ferramentas Sugeridas
- Jest: Testes unitários
- Cypress: Testes E2E
- Lighthouse: Performance e acessibilidade
- Axe: Testes de acessibilidade

## 📚 Documentação

### Arquivos Inclusos
- `README.md`: Documentação geral
- `ARQUITETURA.md`: Este arquivo
- Comentários no código: Explicações inline

### Documentação Recomendada
- API Documentation: Swagger/OpenAPI
- Database Schema: Diagrama ER
- User Guide: Manual do usuário
- Developer Guide: Guia para desenvolvedores

## 🔄 Ciclo de Vida da Aplicação

```
1. Carregamento
   ├── Carregar HTML
   ├── Carregar CSS
   ├── Carregar JavaScript
   └── Inicializar aplicação

2. Inicialização
   ├── Criar instâncias de gerenciadores
   ├── Carregar dados do LocalStorage
   ├── Configurar event listeners
   └── Exibir dashboard

3. Execução
   ├── Aguardar interação do usuário
   ├── Processar eventos
   ├── Atualizar estado
   ├── Atualizar DOM
   └── Salvar dados

4. Encerramento
   ├── Limpar event listeners
   ├── Salvar estado
   └── Fechar conexões
```

## 🎓 Conclusão

Esta arquitetura fornece uma base sólida para o Sistema Omnichannel. É modular, escalável e fácil de manter. Com as integrações e melhorias futuras sugeridas, o sistema pode evoluir para uma solução robusta de nível empresarial.

---

**Versão**: 1.0.0
**Última Atualização**: 18 de Novembro de 2025
