# AI Implementation Handoff Template

> Specialized operational handoff generated from:
> `.ai/techlead-out/techlead.md`

---

# Contexto Operacional

## Objetivo Técnico

Implementar componentes UI, Server Components e layouts para os módulos do portfólio utilizando arquivos JSON como fonte única da verdade.

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

**Frontend & UI Components** - Componentes, Server Components, layouts, acessibilidade, estados e design system para todos os módulos do portfólio.

---

# Responsabilidades

- Implementar componentes de grid para projetos
- Criar timeline component para experiência profissional
- Desenvolver taxonomia component para habilidades
- Estabelecer layout wrapper com dark mode
- Definir estratégias de lazy loading por componente
- Configurar roteamento entre módulos

---

# Restrições

- Não criar lógica de negócio específica (deve ir para backend.md)
- Não definir estratégias de deploy (deve ir para devops.md)
- Manter foco em componentes e UI

---

# Boundaries

## Responsabilidade do Agente

Implementar componentes UI, layouts e estratégias de renderização que consomem os DTOs definidos no backend.md.

## Fora do Escopo

- Lógica de negócio específica por módulo
- Estratégias de deploy e CI/CD
- Configurações de ambiente específicas

---

# Padrões Obrigatórios

## Componentes Core

```typescript
// Componente Grid de Projetos
interface ProjectsGridProps {
  projects: ProjectDTO[];
  filters: {
    technologies?: string[];
    tags?: string[];
  };
}

const ProjectsGrid = ({ projects, filters }: ProjectsGridProps) => {
  // Implementação com lazy loading e SSR
};

// Componente Timeline de Experiência
interface ExperienceTimelineProps {
  experience: ExperienceDTO;
  viewMode?: 'chronological' | 'reverse';
}

const ExperienceTimeline = ({ experience, viewMode }: ExperienceTimelineProps) => {
  // Implementação com lazy loading por período
};

// Componente Taxonomia de Habilidades
interface SkillsTaxonomyProps {
  skills: SkillsDTO;
  categoryFilter?: string;
}

const SkillsTaxonomy = ({ skills, categoryFilter }: SkillsTaxonomyProps) => {
  // Implementação com lazy loading por categoria
};
```

## Server Components Strategy

```typescript
// Padrão de Server Components First
const SERVER_COMPONENTS_CONFIG = {
  priority: 'server-first',      // Sempre usar Server Components
  hydration: 'minimal',          // Minimizar JavaScript no cliente
  ssr: true,                     // SSR para todas as páginas
};
```

## Lazy Loading Strategy

```typescript
// Estratégia de Lazy Loading por Componente
const LAZY_LOAD_STRATEGY = {
  imageThreshold: 200,           // Carregar após scroll de 200px
  placeholderRatio: 0.8,         // 80% da imagem como placeholder
  chunkSize: 10,                 // Itens por carregamento progressivo
};
```

## Acessibilidade Standards

```typescript
// Padrão WCAG 2.1 AA para todos os componentes
const ACCESSIBILITY_CONFIG = {
  ariaLabels: true,              // Labels ARIA obrigatórios
  keyboardNavigation: true,      // Navegação por teclado
  screenReaderSupport: true,     // Suporte a leitores de tela
};
```

---

# Contratos

## Contratos Técnicos

### Contrato de Renderização

```typescript
// Padrão de Server Components First
const RENDER_CONTRACT = {
  priority: 'server-first',      // Sempre usar Server Components
  hydration: 'minimal',          // Minimizar JavaScript no cliente
  ssr: true,                     // SSR para todas as páginas
};
```

### Contrato de Componentes

```typescript
// Interface de Componente UI
interface UIComponentContract {
  name: string;
  props: Record<string, any>;
  serverProps: boolean;          // Sempre true para Server Components
  clientOnly?: boolean;          // Quando usar Client Components
};
```

## Contratos de Dados

### Contrato de Entrada (Input Contract)

```typescript
// Input Contract para Componentes UI
interface UIInputContract {
  source: 'json';                // Fonte dos dados
  schemaVersion: '1.0';          // Versão do schema
  requiredFields: ['data'];
};
```

### Contrato de Saída (Output Contract)

```typescript
// Output Contract para Renderização UI
interface UIRenderContract {
  component: React.ComponentType;
  props: Record<string, any>;
  metadata: {
    renderedAt: string;
    serverPropsUsed: boolean;
  };
};
```

---

# Entradas Esperadas

- DTOs conforme backend.md
- Configurações de lazy loading
- Padrões de acessibilidade

---

# Saídas Esperadas

- Handoffs especializados para devops, qa e security
- Componentes UI implementados

---

# Dependências

## Dependências Internas

- `.ai/architect-out/architect.md` (fonte primária)
- `.ai/techlead-out/techlead.md` (fonte secundária)

## Dependências Externas

- React 18+ com Server Components
- Next.js App Router
- Tailwind CSS ou similar para styling

---

# Critérios de Aceitação

- [ ] Grid component implementado e funcional
- [ ] Timeline component criado e validado
- [ ] Taxonomia component desenvolvido
- [ ] Layout wrapper com dark mode configurado
- [ ] Acessibilidade WCAG 2.1 AA atendida
- [ ] Lazy loading funcionando corretamente

---

# Ações Proibidas

- Não criar lógica de negócio específica
- Não definir estratégias de deploy
- Não assumir tecnologias não especificadas

---

# Estratégia Operacional

## Estratégia de Execução

1. Implementar componentes core (grid, timeline, taxonomia)
2. Criar layout wrapper com dark mode
3. Configurar lazy loading por componente
4. Validar acessibilidade WCAG 2.1 AA
5. Testar SSR e hydration

## Estratégia de Validação

- Verificar que todos os componentes são acessíveis
- Confirmar que lazy loading funciona corretamente
- Validar que SSR está funcionando como esperado

---

# Riscos Operacionais

| Risco | Probabilidade | Impacto | Mitigação |
|-------|--------------|---------|------------|
| Componentes não acessíveis | Média | Alto | Testes de acessibilidade rigorosos |
| Lazy loading falha | Baixa | Médio | Fallback strategy definida |

---

# Checklist Operacional

- [ ] Grid component implementado
- [ ] Timeline component criado
- [ ] Taxonomia component desenvolvido
- [ ] Layout wrapper configurado
- [ ] Dark mode funcionando
- [ ] Acessibilidade validada
- [ ] Lazy loading testado

---

# Handoff Metadata

| Campo              | Valor                          |
| ------------------ | ------------------------------ |
| Source Document    | `.ai/techlead-out/techlead.md` |
| Generated By       | `builder-input-generator`      |
| Output Type        | `implementation-handoff`       |
| Specialized Domain | **Frontend & UI Components**         |

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