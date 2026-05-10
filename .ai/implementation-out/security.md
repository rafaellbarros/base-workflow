# AI Implementation Handoff Template

> Specialized operational handoff generated from:
> `.ai/techlead-out/techlead.md`

---

# Contexto Operacional

## Objetivo Técnico

Definir requisitos de segurança, hardening e compliance para os módulos do portfólio utilizando arquivos JSON como fonte única da verdade.

## Escopo Operacional

- Configuração de CSP (Content Security Policy)
- Headers de segurança obrigatórios
- Hardening de servidor e aplicação
- Autenticação e autorização segura
- Gestão de secrets e credenciais
- Scanning de vulnerabilidades (SAST, DAST, dependency)

## Fonte da Verdade

```text
.ai/techlead-out/techlead.md
```

## Domínio Especializado

**Security & Hardening** - CSP, headers, hardening, auth, secrets, OWASP, scanning, SAST, DAST, dependency scanning e compliance para todos os módulos do portfólio.

---

# Responsabilidades

- Definir CSP e headers de segurança obrigatórios
- Estabelecer guidelines de hardening para servidor e aplicação
- Configurar estratégias de autenticação segura
- Implementar gestão adequada de secrets
- Validar conformidade com OWASP Top 10
- Configurar scanning automatizado (SAST, DAST, dependency)

---

# Restrições

- Não criar lógica de negócio específica (deve ir para backend.md)
- Não definir componentes UI específicos (deve ir para frontend.md)
- Manter foco em segurança e compliance

---

# Boundaries

## Responsabilidade do Agente

Definir requisitos de segurança, hardening e compliance que garantem proteção adequada contra vulnerabilidades conhecidas.

## Fora do Escopo

- Lógica de negócio específica por módulo
- Componentes UI específicos
- Configurações de ambiente específicas além dos padrões

---

# Padrões Obrigatórios

## Security Headers

```typescript
// Headers de Segurança Obrigatórios
const SECURITY_HEADERS = {
  contentSecurityPolicy: {
    defaultSrc: "'self'",
    scriptSrc: [
      "'self'",
      "'unsafe-inline'",           // Mínimo necessário para SSR
      "https://cdn.example.com",
    ],
    styleSrc: ["'self'", "'unsafe-inline'", 'https://fonts.googleapis.com'],
  },
  httpStrictTransportSecurity: {
    maxAge: 31536000,            // 1 ano
    includeSubDomains: true,
  },
  xFrameOptions: 'DENY',         // Previne clickjacking
};
```

## Hardening Guidelines

```typescript
// Guidelines de Hardening
const HARDENING_GUIDELINES = {
  server: {
    disableDirectoryListing: true,
    compressBrotli: true,        // Mais eficiente que gzip
    enableCompression: true,
  },
  application: {
    rateLimiting: {              // Proteção contra DDoS
      windowMs: 60000,
      maxRequests: 100,
    },
    inputValidation: true,       // Validação de todos os inputs
  };
};
```

## Authentication Strategy

```typescript
// Estratégia de Autenticação Segura
const AUTH_STRATEGY = {
  jwt: {                        // JWT com segurança adequada
    algorithm: 'RS256',         // Assinatura assimétrica
    expiresIn: '1h',            // Token curto para acesso
    refreshRotation: true,      // Rotação de tokens de refresh
  },
  passwordPolicy: {
    minLength: 12,
    requireSpecialChars: true,
    preventReuse: 12,           // Não reutilizar últimas 12 senhas
  };
};
```

## Secrets Management

```typescript
// Gestão de Secrets Segura
const SECRETS_CONFIG = {
  storage: 'vault',              // HashiCorp Vault ou similar
  rotationInterval: '90d',       // Rotação a cada 90 dias
  auditLogging: true,           // Logs de auditoria obrigatórios
};
```

---

# Contratos

## Contratos Técnicos

### Contrato de CSP

```typescript
// Padrão de Content Security Policy
interface CSPContract {
  directives: Record<string, string[]>;
  reportUri?: string;
};
```

### Contrato de Hardening

```typescript
// Padrão de Hardening de Servidor
interface HardeningContract {
  serverType: 'nginx' | 'apache';
  configurationFile: string;
  validationScript: string;
};
```

## Contratos de Scanning

### Contrato de SAST

```typescript
// Padrão de Static Application Security Testing
interface SASTContract {
  tool: 'sonarqube' | 'semgrep';
  threshold: 'BLOCKER' | 'CRITICAL';
};
```

### Contrato de DAST

```typescript
// Padrão de Dynamic Application Security Testing
interface DASTContract {
  tool: 'owasp-zap' | 'burp';
  scanFrequency: 'weekly';
};
```

---

# Entradas Esperadas

- Requisitos de segurança por módulo
- Guidelines de hardening definidas
- Políticas de compliance

---

# Saídas Esperadas

- Handoffs especializados para qa
- Configurações de segurança implementadas
- Guidelines de hardening estabelecidas

---

# Dependências

## Dependências Internas

- `.ai/architect-out/architect.md` (fonte primária)
- `.ai/techlead-out/techlead.md` (fonte secundária)

## Dependências Externas

- OWASP ZAP para DAST
- SonarQube ou Semgrep para SAST
- HashiCorp Vault para secrets management

---

# Critérios de Aceitação

- [ ] CSP configurado e validado
- [ ] Headers de segurança implementados
- [ ] Hardening guidelines estabelecidas
- [ ] Autenticação segura configurada
- [ ] Secrets management implementado
- [ ] Scanning automatizado funcionando
- [ ] Compliance OWASP verificado

---

# Ações Proibidas

- Não criar lógica de negócio específica
- Não definir componentes UI específicos
- Não assumir tecnologias não especificadas

---

# Estratégia Operacional

## Estratégia de Execução

1. Definir CSP e headers obrigatórios
2. Estabelecer guidelines de hardening
3. Configurar autenticação segura
4. Implementar secrets management
5. Validar compliance OWASP
6. Configurar scanning automatizado

## Estratégia de Validação

- Verificar que todos os headers estão sendo enviados corretamente
- Confirmar que CSP está bloqueando recursos maliciosos
- Validar que scanning está detectando vulnerabilidades conhecidas

---

# Riscos Operacionais

| Risco | Probabilidade | Impacto | Mitigação |
|-------|--------------|---------|------------|
| Configuração de CSP incorreta | Média | Alto | Testes automatizados de CSP |
| Secrets expostos em logs | Baixa | Crítico | Audit logging rigoroso |

---

# Checklist Operacional

- [ ] CSP configurado e validado
- [ ] Headers de segurança implementados
- [ ] Hardening guidelines estabelecidas
- [ ] Autenticação segura configurada
- [ ] Secrets management implementado
- [ ] Scanning automatizado funcionando
- [ ] Compliance OWASP verificado

---

# Handoff Metadata

| Campo              | Valor                          |
| ------------------ | ------------------------------ |
| Source Document    | `.ai/techlead-out/techlead.md` |
| Generated By       | `builder-input-generator`      |
| Output Type        | `implementation-handoff`       |
| Specialized Domain | **Security & Hardening**         |

---

# Consumption Rules

- seguir rigorosamente os padrões definidos
- não contradizer decisões técnicas
- respeitar boundaries definidos
- manter consistência operacional
- validar contratos antes da implementação
- não assumir requisitos inexistentes
- não expandir escopo sem definição explícita
- minimizar ambiguidades operacionais

---

# Integridade do Documento

O documento final NÃO deve conter:

- placeholders remanescentes
- TODO
- TBD
- FIXME
- seções vazias obrigatórias
- ambiguidades operacionais

Todas as seções devem conter conteúdo válido.

---

*Documento gerado exclusivamente para handoff operacional especializado.*
*Nenhuma implementação, scaffold ou execução foi iniciada.*