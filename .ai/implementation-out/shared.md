# AI Implementation Handoff Template

> Specialized operational handoff generated from:
> `.ai/techlead-out/techlead.md`

---

# Contexto Operacional

## Objetivo Técnico

Transformar arquitetura de portfólio profissional em componentes modulares renderizados via Server Components do Next.js App Router, utilizando arquivos JSON como fonte única da verdade.

## Escopo Operacional

- Grid responsivo de projetos com filtragem por tecnologias/tags
- Timeline cronológica de experiência profissional
- Taxonomia categorizada de habilidades técnicas
- Layout wrapper com dark mode e acessibilidade WCAG 2.1 AA

## Fonte da Verdade

```text
.ai/techlead-out/techlead.md
```

## Domínio Especializado

**Shared Patterns & Global Standards** - Padrões globais, convenções de nomenclatura, contratos compartilhados e guidelines aplicáveis a todos os módulos do portfólio.

---

# Responsabilidades

- Definir padrões globais de nomenclatura para projetos, experiência e habilidades
- Estabelecer contratos de dados entre módulos
- Documentar convenções de lazy loading e placeholders
- Especificar guidelines de acessibilidade aplicáveis globalmente
- Definir padrões de observabilidade compartilhados
- Estabelecer versionamento semântico para JSON files

---

# Restrições

- Não criar lógica de negócio específica de módulo
- Não definir componentes UI específicos (deve ir para frontend.md)
- Não especificar estratégias de deploy (deve ir para devops.md)
- Manter foco em padrões aplicáveis globalmente

---

# Boundaries

## Responsabilidade do Agente

Definir padrões globais, contratos compartilhados e guidelines que serão aplicados consistentemente em todos os módulos do portfólio.

## Fora do Escopo

- Implementação de componentes UI específicos
- Estratégias de deploy e CI/CD
- Lógica de negócio específica por módulo
- Configurações de ambiente específicas

---

# Padrões Obrigatórios

## Nomenclatura

```typescript
// JSON Files Naming Convention
const JSON_FILES = {
  projects: 'projects.json',      // Portfólio técnico
  experience: 'experience.json',  // Timeline profissional
  skills: 'skills.json',          // Taxonomia de habilidades
};
```

## Lazy Loading & Placeholders

```typescript
// Padrão Global de Lazy Loading
const LAZY_LOAD_CONFIG = {
  imageThreshold: 200,           // Carregar após scroll de 200px
  placeholderRatio: 0.8,         // 80% da imagem como placeholder
  chunkSize: 10,                 // Itens por carregamento progressivo
};
```

## Observabilidade Compartilhada

```typescript
// Padrão de Logging Global
const LOG_LEVELS = {
  info: 'INFO',                  // Operações normais
  warn: 'WARN',                  // Condições anormais
  error: 'ERROR',                // Falhas críticas
};
```

---

# Contratos

## Contratos Técnicos

### Contrato de Dados entre Módulos

```typescript
// Interface de Projeto (Contrato de Entrada)
interface ProjectContract {
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

// Interface de Experiência (Contrato de Entrada)
interface ExperienceContract {
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

// Interface de Habilidades (Contrato de Entrada)
interface SkillsContract {
  id: string;                    // Unique identifier (required)
  categories: Array<{
    domain: string;              // Domínio técnico
    skills: string[];
    level?: 'beginner' | 'intermediate' | 'expert';
  }>;
}
```

## Contratos de Integração

### Contrato de Renderização

```typescript
// Padrão de Server Components First
const RENDER_CONTRACT = {
  priority: 'server-first',      // Sempre usar Server Components
  hydration: 'minimal',          // Minimizar JavaScript no cliente
  ssr: true,                     // SSR para todas as páginas
};
```

---

# Entradas Esperadas

- Arquivos JSON conforme contratos definidos
- Configurações globais de lazy loading
- Padrões de observabilidade compartilhados

---

# Saídas Esperadas

- Handoffs especializados para backend, frontend, devops, qa e security
- Documentação de padrões globais aplicáveis

---

# Dependências

## Dependências Internas

- `.ai/architect-out/architect.md` (fonte primária)
- `.ai/techlead-out/techlead.md` (fonte secundária)

## Dependências Externas

- Next.js App Router
- TypeScript para tipagem de contratos

---

# Critérios de Aceitação

- [ ] Todos os padrões globais documentados
- [ ] Contratos de dados claramente definidos
- [ ] Nomenclatura consistente estabelecida
- [ ] Guidelines de lazy loading especificadas
- [ ] Padrões de observabilidade compartilhados
- [ ] Sem ambiguidades nos contratos

---

# Ações Proibidas

- Não criar componentes UI específicos (frontend.md)
- Não definir estratégias de deploy (devops.md)
- Não implementar lógica de negócio específica
- Não assumir tecnologias não especificadas

---

# Estratégia Operacional

## Estratégia de Execução

1. Extrair padrões globais do techlead.md
2. Definir contratos de dados entre módulos
3. Estabelecer convenções de nomenclatura
4. Documentar guidelines aplicáveis globalmente
5. Validar consistência com architect.md

## Estratégia de Validação

- Verificar que todos os padrões são aplicáveis globalmente
- Confirmar que contratos são consistentes entre módulos
- Validar que guidelines não contradizem decisões técnicas

---

# Riscos Operacionais

| Risco | Probabilidade | Impacto | Mitigação |
|-------|--------------|---------|------------|
| Padrões inconsistentes | Baixa | Médio | Revisão com architect.md |
| Contratos ambíguos | Média | Alto | Schema validation rigoroso |

---

# Checklist Operacional

- [ ] Padrões globais definidos
- [ ] Contratos de dados estabelecidos
- [ ] Nomenclatura consistente documentada
- [ ] Guidelines aplicáveis globalmente especificadas
- [ ] Lazy loading padrão definido
- [ ] Observabilidade compartilhada configurada

---

# Handoff Metadata

| Campo              | Valor                          |
| ------------------ | ------------------------------ |
| Source Document    | `.ai/techlead-out/techlead.md` |
| Generated By       | `builder-input-generator`      |
| Output Type        | `implementation-handoff`       |
| Specialized Domain | **Shared Patterns & Global Standards**         |

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