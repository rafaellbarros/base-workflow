# AI Implementation Handoff Template

> Specialized operational handoff generated from:
> `.ai/techlead-out/techlead.md`

---

# Contexto Operacional

## Objetivo Técnico

Definir estratégias de teste, cobertura e validação para os módulos do portfólio utilizando arquivos JSON como fonte única da verdade.

## Escopo Operacional

- Testes unitários para componentes e lógica de negócio
- Testes de integração entre serviços e APIs
- Testes end-to-end (E2E) para fluxos críticos
- Testes de performance e carga
- Validação de contratos e schemas
- Testes de acessibilidade

## Fonte da Verdade

```text
.ai/techlead-out/techlead.md
```

## Domínio Especializado

**Quality Assurance & Testing** - Estratégia de testes, cobertura, integração, E2E, performance, validação contratos, schemas e critérios QA para todos os módulos do portfólio.

---

# Responsabilidades

- Definir estratégia de teste por tipo (unitário, integração, E2E)
- Estabelecer requisitos mínimos de cobertura
- Configurar testes de performance e carga
- Validar contratos e schemas de API
- Testar conformidade com acessibilidade WCAG 2.1 AA
- Implementar testes de regressão automática

---

# Restrições

- Não criar lógica de negócio específica (deve ir para backend.md)
- Não definir componentes UI específicos (deve ir para frontend.md)
- Manter foco em qualidade e validação

---

# Boundaries

## Responsabilidade do Agente

Definir estratégias de teste, requisitos de cobertura e critérios de qualidade que garantem software confiável e performático.

## Fora do Escopo

- Lógica de negócio específica por módulo
- Componentes UI específicos
- Configurações de ambiente específicas além dos padrões

---

# Padrões Obrigatórios

## Test Strategy

```typescript
// Estratégia de Teste Hierárquica
const TEST_STRATEGY = {
  pyramid: {
    unit: {                    // Base da pirâmide - mais testes
      coverageTarget: 80,       // Alvo de cobertura mínimo
      executionTime: 'fast',
    },
    integration: {              // Meio da pirâmide - testes de integração
      coverageTarget: 60,
      executionTime: 'medium',
    },
    e2e: {                     // Topo da pirâmide - menos testes, mais críticos
      coverageTarget: 40,
      executionTime: 'slow',
    },
  };
};
```

## Coverage Requirements

```typescript
// Requisitos de Cobertura por Camada
const COVERAGE_REQUIREMENTS = {
  components: {                // Componentes UI
    minimum: 70,               // Mínimo aceitável
    target: 85,                // Alvo ideal
  },
  services: {                  // Serviços e APIs
    minimum: 60,
    target: 80,
  },
  utils: {                     // Utilitários
    minimum: 90,
    target: 95,
  };
};
```

## Performance Testing

```typescript
// Requisitos de Performance
const PERFORMANCE_REQUIREMENTS = {
  lighthouseScore: {           // Pontuação Lighthouse
    accessibility: 90,         // Mínimo aceitável
    performance: 85,
    bestPractices: 90,
    seo: 85,
  },
  coreWebVitals: {
    largestContentfulPaint: '2.5s',
    firstInputDelay: '100ms',
    cumulativeLayoutShift: '0.1',
  };
};
```

## Contract Validation

```typescript
// Validação de Contratos e Schemas
const CONTRACT_VALIDATION = {
  openApiValidation: true,     // Validar OpenAPI specs
  jsonSchemaValidation: true,  // Validar JSON schemas
  payloadValidation: true,     // Validar payloads reais
};
```

---

# Contratos

## Contratos Técnicos

### Contrato de Teste Unitário

```typescript
// Padrão de Teste Unitário
interface UnitTestContract {
  testFilePattern: '**/*.test.{ts,tsx}';
  coverageTool: 'istanbul' | 'c8';
  reporter: ['json', 'html'];
};
```

### Contrato de Integração

```typescript
// Padrão de Teste de Integração
interface IntegrationTestContract {
  databaseIsolation: true;     // Isolar bancos de dados entre testes
  apiMocking: true;            // Mockar APIs externas
  timeoutMs: 30000;
};
```

### Contrato de E2E

```typescript
// Padrão de Teste End-to-End
interface E2ETestContract {
  browserStack: true,          // Usar BrowserStack ou similar
  parallelExecution: true,     // Execução paralela
  screenshotOnFailure: true;
};
```

## Contratos de Performance

### Contrato de Load Testing

```typescript
// Padrão de Teste de Carga
interface LoadTestContract {
  tool: 'k6' | 'artillery';
  baselineRps: 100;            // Requests por segundo base
  peakRps: 500;
};
```

---

# Entradas Esperadas

- Requisitos de teste por módulo
- Critérios de qualidade definidos
- Configurações de performance

---

# Saídas Esperadas

- Handoffs especializados para security
- Estratégias de teste implementadas
- Critérios de qualidade definidos

---

# Dependências

## Dependências Internas

- `.ai/architect-out/architect.md` (fonte primária)
- `.ai/techlead-out/techlead.md` (fonte secundária)

## Dependências Externas

- Jest ou Vitest para testes unitários
- Playwright ou Cypress para E2E
- k6 ou Artillery para load testing
- Lighthouse CI para performance

---

# Critérios de Aceitação

- [ ] Estratégia de teste definida para todos os módulos
- [ ] Requisitos de cobertura estabelecidos
- [ ] Testes de integração configurados
- [ ] E2E tests implementados
- [ ] Performance testing definido
- [ ] Validação de contratos funcionando
- [ ] Acessibilidade testada

---

# Ações Proibidas

- Não criar lógica de negócio específica
- Não definir componentes UI específicos
- Não assumir tecnologias não especificadas

---

# Estratégia Operacional

## Estratégia de Execução

1. Definir estratégia de teste hierárquica
2. Estabelecer requisitos de cobertura
3. Configurar testes de integração e E2E
4. Implementar performance testing
5. Validar contratos e schemas
6. Testar acessibilidade

## Estratégia de Validação

- Verificar que todos os testes estão passando
- Confirmar que cobertura atinge mínimos estabelecidos
- Validar que performance requirements são atendidos

---

# Riscos Operacionais

| Risco | Probabilidade | Impacto | Mitigação |
|-------|--------------|---------|------------|
| Testes lentos bloqueando pipeline | Média | Médio | Timeout configurado adequadamente |
| Cobertura abaixo do mínimo | Baixa | Alto | Alertas automáticos de cobertura |

---

# Checklist Operacional

- [ ] Estratégia de teste definida
- [ ] Requisitos de cobertura estabelecidos
- [ ] Testes de integração configurados
- [ ] E2E tests implementados
- [ ] Performance testing definido
- [ ] Validação de contratos funcionando
- [ ] Acessibilidade testada

---

# Handoff Metadata

| Campo              | Valor                          |
| ------------------ | ------------------------------ |
| Source Document    | `.ai/techlead-out/techlead.md` |
| Generated By       | `builder-input-generator`      |
| Output Type        | `implementation-handoff`       |
| Specialized Domain | **Quality Assurance & Testing**         |

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