# AI Implementation Handoff Template

> Specialized operational handoff generated from:
> `.ai/techlead-out/techlead.md`

---

# Contexto Operacional

## Objetivo Técnico

Implementar APIs, contratos de dados e estratégias de persistência para os módulos do portfólio utilizando arquivos JSON como fonte única da verdade.

## Escopo Operacional

- Definição de DTOs (Data Transfer Objects) para projetos, experiência e habilidades
- Estratégias de validação de schema antes renderização
- Contratos de mensageria entre componentes
- Padrões de integração com sistemas externos (quando aplicável)

## Fonte da Verdade

```text
.ai/techlead-out/techlead.md
```

## Domínio Especializado

**Backend & Data Contracts** - APIs, persistência, DTOs, validação e contratos de dados para todos os módulos do portfólio.

---

# Responsabilidades

- Definir DTOs para projetos, experiência e habilidades
- Estabelecer estratégias de validação de schema
- Documentar contratos de mensageria entre componentes
- Especificar padrões de integração com sistemas externos
- Implementar estratégias de cache para JSON files
- Definir políticas de versionamento de dados

---

# Restrições

- Não criar lógica de negócio específica por módulo (deve ir para frontend.md)
- Não definir componentes UI específicos
- Manter foco em contratos e persistência

---

# Boundaries

## Responsabilidade do Agente

Definir DTOs, estratégias de validação e contratos de dados que serão consumidos pelos componentes de renderização.

## Fora do Escopo

- Implementação de componentes UI específicos
- Estratégias de deploy e CI/CD
- Configurações de ambiente específicas

---

# Padrões Obrigatórios

## DTOs (Data Transfer Objects)

```typescript
// DTO de Projeto com Schema Validation
interface ProjectDTO {
  id: string;                    // Unique identifier (required)
  title: string;                 // Título do projeto (required)
  description: string;           // Descrição técnica concisa (required)
  technologies: string[];        // Tags/tecnologias
  links?: {                      // Links externos opcionais
    github?: string;
    demo?: string;
    documentation?: string;
  };
  image?: string;                // URL da imagem lazy-loaded
}

// DTO de Experiência com Periodos
interface ExperienceDTO {
  id: string;                    // Unique identifier (required)
  periods: Array<{
    company: string;
    role: string;
    startDate?: string;
    endDate?: string;
    description: string;
    technologies?: string[];
  }>;
}

// DTO de Habilidades com Categorias
interface SkillsDTO {
  id: string;                    // Unique identifier (required)
  categories: Array<{
    domain: string;              // Domínio técnico
    skills: string[];
    level?: 'beginner' | 'intermediate' | 'expert';
  }>;
}
```

## Schema Validation Strategy

```typescript
// Estratégia de Validação Antes Renderização
const VALIDATION_CONFIG = {
  validateOnMount: true,         // Validar ao montar componente
  showErrorBoundary: true,       // Mostrar boundary em caso de erro
  fallbackToDefault: false,      // Não usar fallback por padrão
};
```

## Cache Strategy for JSON Files

```typescript
// Estratégia de Cache para Arquivos JSON
const CACHE_CONFIG = {
  ttl: 3600,                     // Time to live em segundos (1 hora)
  staleWhileRevalidate: 86400,   // Tempo de cache estale enquanto valida
};
```

---

# Contratos

## Contratos Técnicos

### Contrato de Persistência

```typescript
// Padrão de Leitura de JSON Files
const PERSISTENCE_CONTRACT = {
  readStrategy: 'streaming',     // Ler como stream para performance
  parseStrategy: 'lazy',         // Parse lazy conforme necessário
  validateBeforeRender: true,    // Validar antes renderizar
};
```

### Contrato de Mensageria

```typescript
// Padrão de Comunicação entre Componentes
const MESSAGING_CONTRACT = {
  eventBus: 'global',            // Event bus global para comunicação
  messageFormat: 'json',         // Formato JSON para mensagens
};
```

## Contratos de Dados

### Contrato de Entrada (Input Contract)

```typescript
// Input Contract para Projetos
interface ProjectInputContract {
  source: 'json';                // Fonte dos dados
  schemaVersion: '1.0';          // Versão do schema
  requiredFields: ['id', 'title', 'description'];
  optionalFields: ['technologies', 'links', 'image'];
}
```

### Contrato de Saída (Output Contract)

```typescript
// Output Contract para Renderização
interface ProjectOutputContract {
  data: ProjectDTO;
  metadata: {
    validatedAt: string;
    schemaVersion: string;
  };
};
```

---

# Entradas Esperadas

- Arquivos JSON conforme DTOs definidos
- Configurações de cache e validação

---

# Saídas Esperadas

- Handoffs especializados para frontend, devops, qa e security
- Documentação de contratos de dados

---

# Dependências

## Dependências Internas

- `.ai/architect-out/architect.md` (fonte primária)
- `.ai/techlead-out/techlead.md` (fonte secundária)

## Dependências Externas

- Zod ou Yup para schema validation
- Next.js App Router APIs

---

# Critérios de Aceitação

- [ ] DTOs claramente definidos para todos os módulos
- [ ] Estratégias de validação documentadas
- [ ] Contratos de mensageria especificados
- [ ] Cache strategy implementada
- [ ] Schema validation configurado

---

# Ações Proibidas

- Não criar lógica de negócio específica por módulo
- Não definir componentes UI específicos
- Não assumir tecnologias não especificadas

---

# Estratégia Operacional

## Estratégia de Execução

1. Extrair DTOs do techlead.md
2. Definir estratégias de validação
3. Estabelecer contratos de mensageria
4. Configurar cache para JSON files
5. Validar consistência com architect.md

## Estratégia de Validação

- Verificar que todos os DTOs são consistentes
- Confirmar que contratos são aplicáveis globalmente
- Validar que estratégias não contradizem decisões técnicas

---

# Riscos Operacionais

| Risco | Probabilidade | Impacto | Mitigação |
|-------|--------------|---------|------------|
| DTOs inconsistentes | Baixa | Médio | Revisão com architect.md |
| Schema validation falha | Média | Alto | Fallback strategy definida |

---

# Checklist Operacional

- [ ] DTOs definidos para todos os módulos
- [ ] Estratégias de validação estabelecidas
- [ ] Contratos de mensageria documentados
- [ ] Cache strategy configurada
- [ ] Schema validation implementado

---

# Handoff Metadata

| Campo              | Valor                          |
| ------------------ | ------------------------------ |
| Source Document    | `.ai/techlead-out/techlead.md` |
| Generated By       | `builder-input-generator`      |
| Output Type        | `implementation-handoff`       |
| Specialized Domain | **Backend & Data Contracts**         |

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