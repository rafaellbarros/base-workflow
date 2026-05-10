# AI Implementation Handoff Template

> Specialized operational handoff generated from:
> `.ai/techlead-out/techlead.md`

---

# Contexto Operacional

## Objetivo Técnico

Definir pipelines CI/CD, estratégias de deploy e observabilidade para os módulos do portfólio utilizando arquivos JSON como fonte única da verdade.

## Escopo Operacional

- Pipeline CI/CD para build e testes
- Estratégias de deploy com rollback automático
- Configuração de observabilidade (tracing, métricas, logs)
- Infraestrutura containerizada com Docker/Kubernetes
- Gestão de ambientes (dev, staging, production)

## Fonte da Verdade

```text
.ai/techlead-out/techlead.md
```

## Domínio Especializado

**DevOps & Infrastructure** - CI/CD, deploy, observabilidade, tracing, métricas, logs, rollback, infra, containers e ambientes para todos os módulos do portfólio.

---

# Responsabilidades

- Configurar pipeline CI/CD com testes automatizados
- Definir estratégias de deploy com rollback automático
- Estabelecer observabilidade (tracing, métricas, logs)
- Especificar infraestrutura containerizada
- Gerenciar múltiplos ambientes (dev, staging, production)
- Implementar health checks e readiness probes

---

# Restrições

- Não criar lógica de negócio específica (deve ir para backend.md)
- Não definir componentes UI específicos (deve ir para frontend.md)
- Manter foco em infraestrutura e deploy

---

# Boundaries

## Responsabilidade do Agente

Definir pipelines CI/CD, estratégias de deploy e configurações de observabilidade que garantem entrega contínua e estabilidade operacional.

## Fora do Escopo

- Lógica de negócio específica por módulo
- Componentes UI específicos
- Configurações de ambiente específicas além dos padrões

---

# Padrões Obrigatórios

## CI/CD Pipeline

```yaml
# Estrutura Base do Pipeline CI/CD
const PIPELINE_CONFIG = {
  stages: [
    'checkout',                  // Checkout do código
    'lint',                      // Linting e formatação
    'test',                      // Testes unitários e integração
    'build',                     // Build da aplicação
    'security-scan',             // Scans de segurança
    'deploy-staging',            // Deploy para staging
    'e2e-tests',                 // Testes end-to-end
    'deploy-production'          // Deploy para production
  ];
};
```

## Deployment Strategy

```typescript
// Estratégia de Deploy com Blue-Green ou Canary
const DEPLOY_STRATEGY = {
  method: 'blue-green',          // Blue-Green ou Canary
  rollbackAutomated: true,       // Rollback automático em falha
  healthCheckInterval: 30,       // Intervalo de health check em segundos
};
```

## Observability Stack

```typescript
// Configuração de Observabilidade
const OBSERVABILITY_CONFIG = {
  tracing: {
    provider: 'jaeger',          // Jaeger ou similar
    samplingRate: 0.1,           // Taxa de amostragem
  },
  metrics: {
    exporter: 'prometheus',      // Prometheus para métricas
    scrapeInterval: 15,          // Intervalo de scraping em segundos
  },
  logs: {
    level: 'info',               // Nível de log padrão
    format: 'json',              // Formato JSON estruturado
  };
};
```

## Container Strategy

```typescript
// Estratégia de Containers
const CONTAINER_CONFIG = {
  baseImage: 'node:18-alpine',   // Imagem base otimizada
  multiStageBuild: true,         // Build multi-stage para redução
  healthCheck: {
    path: '/health',
    interval: 30,
    timeout: 5,
    retries: 3,
  },
};
```

---

# Contratos

## Contratos Técnicos

### Contrato de Build

```typescript
// Padrão de Build Otimizado
const BUILD_CONTRACT = {
  cacheStrategy: 'content-based', // Cache baseado em conteúdo
  parallelJobs: true,             // Jobs paralelos para velocidade
  artifactRetention: 30,          // Retenção de artifacts por dias
};
```

### Contrato de Deploy

```typescript
// Padrão de Deploy com Rollback
const DEPLOY_CONTRACT = {
  preDeployChecks: true,          // Checks pré-deploy obrigatórios
  postDeployValidation: true,     // Validação pós-deploy
  rollbackTrigger: 'health-fail', // Gatilho para rollback automático
};
```

## Contratos de Infraestrutura

### Contrato de Ambiente

```typescript
// Interface de Configuração de Ambiente
interface EnvironmentContract {
  name: string;                  // Nome do ambiente
  variables: Record<string, any>; // Variáveis de ambiente
  secrets: boolean;               // Uso de secrets gerenciados
};
```

### Contrato de Health Check

```typescript
// Padrão de Health Check
interface HealthCheckContract {
  endpoint: string;
  methods?: 'GET' | 'POST';
  expectedStatus: number;
  timeoutMs: number;
};
```

---

# Entradas Esperadas

- Configurações de pipeline CI/CD
- Estratégias de deploy definidas
- Requisitos de observabilidade

---

# Saídas Esperadas

- Handoffs especializados para qa e security
- Pipelines configurados
- Infraestrutura definida

---

# Dependências

## Dependências Internas

- `.ai/architect-out/architect.md` (fonte primária)
- `.ai/techlead-out/techlead.md` (fonte secundária)

## Dependências Externas

- GitHub Actions ou GitLab CI para pipelines
- Docker e Kubernetes para containers
- Prometheus, Jaeger para observabilidade

---

# Critérios de Aceitação

- [ ] Pipeline CI/CD configurado e funcional
- [ ] Estratégias de deploy implementadas
- [ ] Observabilidade stack configurada
- [ ] Containers otimizados criados
- [ ] Ambientes dev/staging/prod definidos
- [ ] Rollback automático funcionando

---

# Ações Proibidas

- Não criar lógica de negócio específica
- Não definir componentes UI específicos
- Não assumir tecnologias não especificadas

---

# Estratégia Operacional

## Estratégia de Execução

1. Configurar pipeline CI/CD com stages definidos
2. Implementar estratégias de deploy com rollback
3. Estabelecer observabilidade completa
4. Definir infraestrutura containerizada
5. Gerenciar múltiplos ambientes

## Estratégia de Validação

- Verificar que todos os pipelines estão funcionando
- Confirmar que rollback automático funciona corretamente
- Validar que observabilidade está capturando dados adequadamente

---

# Riscos Operacionais

| Risco | Probabilidade | Impacto | Mitigação |
|-------|--------------|---------|------------|
| Pipeline falha crítica | Baixa | Alto | Fallback strategy definida |
| Deploy não rollbackar | Média | Médio | Health checks rigorosos |

---

# Checklist Operacional

- [ ] Pipeline CI/CD configurado
- [ ] Estratégias de deploy implementadas
- [ ] Observabilidade stack configurada
- [ ] Containers otimizados criados
- [ ] Ambientes definidos
- [ ] Rollback automático funcionando

---

# Handoff Metadata

| Campo              | Valor                          |
| ------------------ | ------------------------------ |
| Source Document    | `.ai/techlead-out/techlead.md` |
| Generated By       | `builder-input-generator`      |
| Output Type        | `implementation-handoff`       |
| Specialized Domain | **DevOps & Infrastructure**         |

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