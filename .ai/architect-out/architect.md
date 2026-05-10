# Architect: portfolio-profissional-2026

> Documentação arquitetural declarativa para portfólio profissional AI-first.
> Baseada exclusivamente no planner `.ai/planner-out/planner.md`

---

# 📋 Visão Arquitetural

## Resumo Executivo

Arquitetura de software minimalista e performática para portfólio profissional, utilizando **Next.js 15** com estratégia **JSON-driven**. O sistema elimina a necessidade de editores visuais ou CMS complexos, permitindo atualização de conteúdo através de arquivos JSON declarativos.

### Características Principais

| Aspecto | Estratégia |
|---------|------------|
| **Rendering** | SSR + Static Generation via App Router |
| **Dados** | Local JSON files como fonte única da verdade |
| **JavaScript** | Minimizado - Server Components first |
| **SEO** | Dynamic metadata programático por página |
| **Performance** | Lighthouse ≥ 95 em todas as métricas |

---

# 🏛️ Boundaries do Sistema

## External Boundaries

```
┌─────────────────────────────────────────────────────────┐
│                    EXTERNAL BOUNDARIES                   │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌──────────────┐    ┌──────────────┐                   │
│  │   Recrutador │    │ Tech Lead    │                   │
│  │   Técnico    │◄──►│ Internacional│                   │
│  └──────────────┘    └──────────────┘                   │
│         ▲                    ▲                          │
│         │                    │                          │
│         ▼                    ▼                          │
│  ┌─────────────────────────────────────────┐            │
│  │           PORTFÓLIO PROFESSIONAL         │ ◄──► Vercel │
│  │   (Sistema de Conteúdo JSON-Driven)      │              │
│  └─────────────────────────────────────────┘            │
│                                                          │
│  ┌──────────────┐    ┌──────────────┐                   │
│  │ Consultoria  │    │ Empresa      │                   │
│  │ Técnica      │◄──►│ Técnica      │                   │
│  └──────────────┘    └──────────────┘                   │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

## Internal Boundaries

```
┌─────────────────────────────────────────────────────────┐
│                  INTERNAL BOUNDARIES                      │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌──────────────┐    ┌──────────────┐                   │
│  │   Projects   │    │ Experience   │                   │
│  │   Grid       │◄──►│ Timeline     │                   │
│  │ (Filtro por  │    │ (Linha do    │                   │
│  │  Tecnologia) │    │ Tempo)       │                   │
│  └──────────────┘    └──────────────┘                   │
│         ▲                    ▲                          │
│         │                    │                          │
│         ▼                    ▼                          │
│  ┌─────────────────────────────────┐                     │
│  │           DATA LAYER            │ ◄──► JSON Files     │
│  │   (projects.json,               │    (Fonte Única)    │
│  │    experience.json,             │                     │
│  │     skills.json)                │                     │
│  └─────────────────────────────────┘                     │
│                                                          │
│  ┌──────────────┐    ┌──────────────┐                   │
│  │   Skills     │    │   Hero      │                   │
│  │   Taxonomy   │    │   Section   │                   │
│  │ (Categoriza- │    │ (Apresenta- │                   │
│  │  ção)        │    │  ção)       │                   │
│  └──────────────┘    └──────────────┘                   │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

---

# 📦 Módulos Principais

## Módulo: `projects` (Grid de Projetos)

### Responsabilidades
- Renderizar grid responsivo de projetos técnicos
- Filtrar por tecnologias/tags
- Lazy loading de imagens com placeholders otimizados
- Exibir metadados técnicos e links externos

### Boundaries Internos
```
┌─────────────────────────────────────────┐
│         PROJECTS MODULE                  │
├─────────────────────────────────────────┤
│                                          │
│  ┌──────────────┐    ┌──────────────┐   │
│  │ Project Card │◄──►│ Filter Bar  │   │
│  │ (Individual) │    │ (Tags/      │   │
│  │              │    │ Technology) │   │
│  └──────────────┘    └──────────────┘   │
│         ▲                    ▲          │
│         │                    │          │
│         ▼                    ▼          │
│  ┌─────────────────────────────────┐   │
│  │     PROJECTS.JSON               │   │
│  │   (Fonte Declarativa)           │   │
│  └─────────────────────────────────┘   │
│                                          │
└─────────────────────────────────────────┘
```

### Estrutura de Dados
```typescript
interface Project {
  id: string;              // Unique identifier
  title: string;           // Título do projeto
  description: string;     // Descrição técnica concisa
  technologies: string[];  // Tags/tecnologias
  links: {                 // Links externos
    github?: string;
    demo?: string;
    documentation?: string;
  };
  image?: string;          // URL da imagem (lazy-loaded)
}
```

---

## Módulo: `experience` (Timeline Profissional)

### Responsabilidades
- Renderizar timeline cronológica de carreira
- Exibir períodos, responsabilidades e impacto técnico
- Visualização vertical com scroll suave

### Boundaries Internos
```
┌─────────────────────────────────────────┐
│         EXPERIENCE MODULE                │
├─────────────────────────────────────────┤
│                                          │
│  ┌──────────────┐    ┌──────────────┐   │
│  │ Timeline     │◄──►│ Period Card │   │
│  │ Component    │    │ (Individual)│   │
│  │              │    │             │   │
│  └──────────────┘    └──────────────┘   │
│         ▲                    ▲          │
│         │                    │          │
│         ▼                    ▼          │
│  ┌─────────────────────────────────┐   │
│  │     EXPERIENCE.JSON             │   │
│  │   (Timeline Declarativo)        │   │
│  └─────────────────────────────────┘   │
│                                          │
└─────────────────────────────────────────┘
```

### Estrutura de Dados
```typescript
interface Experience {
  id: string;              // Unique identifier
  periods: Array<{
    company: string;
    role: string;
    startDate?: string;
    endDate?: string;
    description: string;
    technologies?: string[];
  }>;
}
```

---

## Módulo: `skills` (Taxonomia de Habilidades)

### Responsabilidades
- Exibir habilidades categorizadas por domínio
- Filtros por área técnica
- Visualização clara e legível

### Boundaries Internos
```
┌─────────────────────────────────────────┐
│          SKILLS MODULE                   │
├─────────────────────────────────────────┤
│                                          │
│  ┌──────────────┐    ┌──────────────┐   │
│  │ Skills       │◄──►│ Category     │   │
│  │ Grid         │    │ Filter      │   │
│  │              │    │ (Domain)    │   │
│  └──────────────┘    └──────────────┘   │
│         ▲                    ▲          │
│         │                    │          │
│         ▼                    ▼          │
│  ┌─────────────────────────────────┐   │
│  │     SKILLS.JSON                 │   │
│  │   (Taxonomia Categorizada)      │   │
│  └─────────────────────────────────┘   │
│                                          │
└─────────────────────────────────────────┘
```

### Estrutura de Dados
```typescript
interface Skills {
  id: string;              // Unique identifier
  categories: Array<{
    domain: string;        // Domínio (ex: Frontend, Backend)
    skills: string[];      // Habilidades específicas
    level?: 'beginner' | 'intermediate' | 'expert';
  }>;
}
```

---

## Módulo: `layout` (Wrapper de Layout)

### Responsabilidades
- Estrutura base do layout do portfólio
- Dark mode como padrão com toggle persistente
- Responsive breakpoints semânticos
- Acessibilidade WCAG 2.1 AA

### Boundaries Internos
```
┌─────────────────────────────────────────┐
│          LAYOUT MODULE                   │
├─────────────────────────────────────────┤
│                                          │
│  ┌──────────────┐    ┌──────────────┐   │
│  │ Header       │    │ Footer      │   │
│  │ (Navigation) │    │ (Links)     │   │
│  └──────────────┘    └──────────────┘   │
│         ▲                    ▲          │
│         │                    │          │
│         ▼                    ▼          │
│  ┌─────────────────────────────────┐   │
│  │     THEME CONFIGURATION         │   │
│  │   (Dark mode + System Pref)    │   │
│  └─────────────────────────────────┘   │
│                                          │
└─────────────────────────────────────────┘
```

---

# 🔄 Fluxo Conceitual

## Fluxo de Renderização

```mermaid
graph TD
    A[Request HTTP] --> B{Next.js App Router}
    B --> C[Server Components]
    C --> D[Carregar JSON Files]
    D --> E[Validar Schema]
    E --> F[Renderizar Componentes]
    F --> G[SSR/Static Generation]
    G --> H[Response HTML]
    
    D -.-> I[Image Optimization]
    I --> J[Placeholders + Lazy Load]
```

## Fluxo de Dados

```mermaid
graph LR
    JSON[JSON Files] --> VALIDATE{Validar Schema}
    VALIDATE -- Valid --> PARSE[Parse & Transform]
    VALIDATE -- Invalid --> LOG[Log Warning]
    
    PARSE --> RENDER[Renderizar Componentes]
    RENDER --> CACHE[Cache Edge/CDN]
    CACHE --> USER[Usuário Final]
```

## Fluxo de Atualização de Conteúdo

```mermaid
sequenceDiagram
    participant Dev as Desenvolvedor
    participant JSON as Arquivos JSON
    participant App as Portfólio
    
    Dev->>JSON: Editar arquivo (ex: projects.json)
    Note over Dev,App: Sem rebuild necessário
    
    Dev->>App: Navegar para página
    App->>JSON: Ler dados atualizados
    JSON-->>App: Retornar novo conteúdo
    App-->>Dev: Renderizar com novos dados
```

---

# 🎯 Estratégia Arquitetural

## Decisões de Design

| Decisão | Racional | Impacto |
|---------|----------|----------|
| **Server Components First** | Minimiza JavaScript no cliente, melhora performance e SEO | Alto |
| **JSON como Fonte Única** | Elimina necessidade de CMS ou banco de dados complexo | Médio |
| **SSR + Static Generation** | Máxima performance com cache edge/CDN | Alto |
| **Dynamic Metadata** | SEO otimizado por página e projeto individualmente | Médio |
| **Lazy Loading Agressivo** | Carrega apenas o necessário para viewport atual | Alto |

## Trade-offs Aceitos

```
┌─────────────────────────────────────────────────────┐
│              TRADE-OFFS ARQUITETURAIS                  │
├─────────────────────────────────────────────────────┤
│                                                       │
│  ✅ SIMPLIFICADO                                    │
│     └── Não usar CMS/headless CMS                    │
│         → Perde: Automação de conteúdo                │
│         → Ganha: Controle total, zero overhead        │
│                                                       │
│  ⚠️ LIMITADO                                         │
│     └── JSON local como fonte de dados               │
│         → Perde: Multi-user collaboration             │
│         → Ganha: Simplicidade extrema                 │
│                                                       │
│  ✅ OTIMIZADO                                       │
│     └── SSR + Static Generation                     │
│         → Perde: Dinamismo em tempo real              │
│         → Ganha: Performance máxima, SEO perfeito    │
│                                                       │
└─────────────────────────────────────────────────────┘
```

---

# 📊 Estratégia de Dados

## Fonte Única da Verdade

```bash
portfolio-profissional-2026/
├── src/
│   ├── data/
│   │   ├── projects.json      # Portfólio técnico
│   │   ├── experience.json    # Timeline profissional
│   │   └── skills.json        # Taxonomia de habilidades
│   └── ...
```

## Schema Validation

```typescript
// Validador de schema antes da renderização
function validateProject(project: unknown): asserts project is Project {
  const schema = {
    required: ['id', 'title', 'description'],
    properties: {
      id: { type: 'string' },
      title: { type: 'string' },
      description: { type: 'string' },
      technologies: { type: 'array', items: { type: 'string' } },
      links: { type: 'object' },
    },
  };
  
  // Implementação de validador (ex: zod, yup)
}
```

## Lazy Loading de Dados

```typescript
// Carregamento progressivo por viewport
const DATA_CHUNK_SIZE = 10;  // Itens por carregamento

function loadProjects(page: number) {
  const start = (page - 1) * DATA_CHUNK_SIZE;
  return projects.slice(start, start + DATA_CHUNK_SIZE);
}
```

---

# ⚠️ Riscos e Mitigações

## Matriz de Riscos

| Risco | Probabilidade | Impacto | Mitigação |
|-------|--------------|---------|------------|
| **JSON mal formatado** | Baixa | Médio | Schema validation antes renderizar |
| **Imagens não otimizadas** | Média | Alto | Next.js Image API + placeholders |
| **Expansão futura complexa** | Baixa | Baixo | Arquitetura modular desde início |
| **Performance degradada** | Baixa | Médio | Web Vitals no build process |

## Plano de Contingência

```mermaid
graph TD
    A[Risco Detectado] --> B{Tipo de Risco}
    
    B -- JSON Invalido --> C[Validar Schema]
    C --> D[Fallback: Dados Padrão]
    
    B -- Performance Baixa --> E[Web Vitals Check]
    E --> F[Otimizar Imagens]
    
    B -- Expansão Necessária --> G[Módulo Novo]
    G --> H[JSON File Novo]
```

---

# 🚀 Estratégia de Escalabilidade

## Horizontal Scaling (Nativo)

```mermaid
graph LR
    A[Request] --> B{Edge Network}
    B --> C[Vercel Edge Location]
    C --> D[Static Cache]
    D --> E[HTML Response]
    
    F[Build Process] --> G[Generate Static]
    G --> H[Distributed CDN]
```

## Vertical Scaling (Via JSON)

```typescript
// Estrutura escalável para novos módulos
interface Module {
  id: string;
  name: string;
  schema: SchemaDefinition;  // Definição de dados
  component: ComponentType;  // Renderizador
}

const MODULES: Record<string, Module> = {
  projects: { /* ... */ },
  experience: { /* ... */ },
  skills: { /* ... */ },
  // Adicionar novos módulos sem alterar código
};
```

---

# 🛠️ Estratégia de Manutenção

## Atualização de Conteúdo

```bash
# Fluxo recomendado para atualizar conteúdo
1. Editar arquivo JSON (ex: projects.json)
2. Validar schema manualmente ou via tooling
3. Navegar ao conteúdo na aplicação
4. Renderizado automático sem rebuild
```

## Checklist de Manutenção

- [ ] Validar JSON files antes commit
- [ ] Monitorar Web Vitals no build
- [ ] Testar em dispositivos móveis reais
- [ ] Revisar schema quando adicionar novo módulo
- [ ] Limpar cache de navegador periodicamente

---

# 🔮 Expansão Futura

## Roadmap de Expansão

| Fase | Módulo Adicional | JSON File |
|------|------------------|------------|
| 1 | Blog Técnico | `posts.json` |
| 2 | Documentação | `docs/` (MDX) |
| 3 | Internacionalização | `locales/*.json` |
| 4 | Automação IA | Geração de conteúdo |

## Estrutura Preparada para Expansão

```bash
src/
├── data/
│   ├── projects.json      # ✅ Existente
│   ├── experience.json    # ✅ Existente
│   ├── skills.json        # ✅ Existente
│   └── posts.json         # 📦 Pronto para uso
├── app/
│   ├── blog/
│   │   └── page.tsx       # 📦 Componente pronto
│   └── docs/
│       └── page.tsx       # 📦 Componente pronto
```

---

# 📝 Decisões Arquiteturais Consolidadas

## DAD (Decisions As Data)

```typescript
const ARCHITECTURAL_DECISIONS = {
  // DECISÃO 001: JSON como fonte única da verdade
  id: 'DAD-001',
  title: 'JSON as Single Source of Truth',
  decision: 'Utilizar arquivos JSON locais como fonte exclusiva de dados',
  rationale: 'Elimina CMS overhead, simplifica manutenção, permite controle total',
  status: 'APPROVED',
  
  // DECISÃO 002: Server Components First
  id: 'DAD-002',
  title: 'Server Components Priority',
  decision: 'Priorizar Server Components em todas as páginas',
  rationale: 'Minimiza JavaScript no cliente, melhora performance e SEO',
  status: 'APPROVED',
  
  // DECISÃO 003: SSR + Static Generation
  id: 'DAD-003',
  title: 'Rendering Strategy',
  decision: 'SSR para páginas dinâmicas, Static para conteúdo fixo',
  rationale: 'Balanceia performance com dinamismo necessário',
  status: 'APPROVED',
};
```

---

# 📊 Métricas de Qualidade

## Lighthouse Targets

| Métrica | Target Mínimo | Status |
|---------|---------------|--------|
| Performance | ≥ 95 | ✅ Definido |
| Accessibility | ≥ 90 | ✅ WCAG 2.1 AA |
| Best Practices | ≥ 90 | ✅ Definido |
| SEO | ≥ 90 | ✅ Dynamic Metadata |

## Web Vitals Targets

```typescript
const WEB_VITALS_TARGETS = {
  LCP: { target: '2.5s', description: 'Largest Contentful Paint' },
  FID: { target: '100ms', description: 'First Input Delay' },
  CLS: { target: '0.1', description: 'Cumulative Layout Shift' },
};
```

---

# 📋 Checklist de Arquitetura

## Pré-Implementação

- [x] Planner analisado integralmente
- [x] Boundaries definidos claramente
- [x] Módulos identificados e documentados
- [x] Fluxos conceituais mapeados
- [ ] Schema JSONs criados (Fase 1)
- [ ] Componentes core implementados (Fase 2)

## Pós-Arquitetura

- [ ] Documentação persistida em `.ai/architect-out/architect.md`
- [ ] Nenhum artefato executável criado
- [ ] Decisões registradas no DAD
- [ ] Métricas de qualidade definidas

---

# 📖 Histórico de Versão

| Versão | Data | Autor | Mudanças |
|--------|------|-------|----------|
| 1.0.0 | 2026-05-09 | Architect Agent | Documentação inicial baseada no planner |

---

*Documento gerado exclusivamente para documentação arquitetural.*
*Nenhuma implementação, scaffold ou execução foi iniciada.*
