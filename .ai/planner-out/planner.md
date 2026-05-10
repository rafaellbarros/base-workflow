# Planner: portfolio-profissional-2026

- Documento exclusivamente de planejamento.
- Nenhuma seção representa implementação,
- scaffold, provisionamento ou execução real.

---

# 🎯 Objetivo do Projeto

## Visão Geral

Criar um portfólio profissional extremamente rápido, minimalista, performático e simples de manter utilizando Next.js 15 com arquitetura declarativa baseada em JSON local. O projeto funciona como uma plataforma de conteúdo onde a manutenção é feita através de arquivos JSON sem necessidade de alterar componentes React.

## Problema Resolvido

- Reduzir drasticamente o tempo de atualização do portfólio
- Eliminar dependência de editores visuais ou CMS complexos
- Permitir que desenvolvedores atualizem conteúdo via JSON declarativo
- Manter performance máxima com mínimo consumo JavaScript

## Resultado Esperado

Um portfólio profissional que:
- Carrega instantaneamente em qualquer dispositivo
- É atualizado apenas editando arquivos JSON
- Transmite credibilidade técnica e organização
- Funciona como base para futuras expansões (blog, documentação)

## Público-Alvo

- Recrutadores técnicos
- Tech leads de empresas internacionais
- Consultorias especializadas em tecnologia
- Empresas que buscam validar competência técnica

## Critérios de Sucesso

- Lighthouse Performance ≥ 95
- Tempo de carregamento < 1s em redes móveis
- Zero erros de console após renderização completa
- Atualização de conteúdo via JSON sem rebuild do projeto
- Legibilidade imediata do conteúdo técnico

---

# 🧠 Contexto Estratégico

## Tipo de Projeto

- Portfolio profissional
- Personal branding para desenvolvedor sênior
- Plataforma AI-first com arquitetura moderna

## Prioridades Técnicas

1. **Performance** - Lighthouse score ≥ 95 em todas as métricas
2. **Simplicidade** - Arquitetura compreensível em < 30 minutos de leitura
3. **Legibilidade** - Conteúdo sempre prioritário sobre efeitos visuais
4. **Manutenção** - Atualização via JSON sem tocar no código
5. **Reutilização** - Componentes modulares para expansão futura

## Restrições

- Evitar overengineering e decisões arquiteturais prematuras
- Não utilizar CMS ou headless CMS
- Minimizar dependências desnecessárias
- Build process deve ser rápido (< 30s)
- Sem animações excessivas que comprometam performance

---

# 🎨 Diretrizes de Design

## Estilo Visual

- Dark mode como padrão
- Minimalismo técnico (estilo "software engineer senior")
- Alta legibilidade em todos os tamanhos de tela
- Foco total no conteúdo, sem elementos decorativos excessivos
- Paleta neutra com alto contraste para leitura

## Identidade Esperada

O visual deve comunicar:
- Senioridade técnica e experiência
- Clareza na organização profissional
- Organização metodológica
- Credibilidade técnica comprovada
- Abordagem pragmática e direta

## UX Goals

- Navegação fluida sem micro-interações desnecessárias
- Hierarquia visual clara para leitura rápida
- Acessibilidade WCAG 2.1 AA como mínimo
- Mobile-first com experiência igualitária
- Feedback imediato de interações essenciais

---

# 🏗️ Arquitetura Técnica Conceitual

## Estratégia Arquitetural

| Categoria          | Estratégia           |
| ------------------ | -------------------- |
| Rendering          | SSR + Static Generation para máxima performance e SEO |
| Data Flow          | Local JSON-driven com lazy loading de dados |
| Component Strategy | Reusable UI components com composition pattern |
| SEO                | Dynamic metadata via Next.js 15 App Router |
| State Management   | Server Components como padrão, client state mínimo |

---

## Stack Tecnológica Planejada

| Categoria       | Tecnologia      |
| --------------- | --------------- |
| Frontend        | Next.js 15 (App Router) |
| Backend         | N/A - Server-side rendering nativo |
| Database        | Local JSON files |
| Styling         | TailwindCSS + CSS variables para theming |
| UI Components   | Shadcn/UI (componentes acessíveis e tipados) |
| Animation       | Framer Motion (uso conservador, apenas quando necessário) |
| Infraestrutura  | Vercel ou hosting estático tradicional |
| Observabilidade | Lighthouse CI + Web Vitals no build |

---

# 📦 Estratégia de Dados

## Fonte de Dados

| Tipo       | Origem              |
| ---------- | ------------------- |
| Projects   | `projects.json` - Array declarativo com metadados técnicos e links |
| Experience | `experience.json` - Timeline cronológica de carreira |
| Skills     | `skills.json` - Taxonomia categorizada por domínio |

## Estratégia de Atualização

**Projects:**
- Novos projetos adicionados apenas via JSON
- Estrutura declarativa: título, descrição, tecnologias, links
- Sem necessidade de alterar componentes React
- Imagens lazy-loaded com placeholders otimizados

**Experience:**
- Experiências renderizadas dinamicamente via estrutura declarativa
- Formato timeline com períodos e descrições concisas
- Foco em impacto técnico e responsabilidades

## Estratégia de Persistência

Os dados persistem localmente como arquivos JSON no mesmo repositório:

```
/projects/
  projects.json    # Portfólio de projetos técnicos
  experience.json  # Histórico profissional
  skills.json      # Competências categorizadas
```

---

# 🧩 Funcionalidades Core

- **Hero Section** - Apresentação concisa com foto, nome e stack principal
- **Projects Grid** - Layout responsivo com filtros por tecnologia
- **Experience Timeline** - Linha do tempo vertical de carreira
- **Dynamic SEO** - Metadata programático por página e projeto
- **Responsive Layout** - Mobile-first com breakpoints semânticos
- **Mobile First** - Touch targets adequados, gestos intuitivos
- **Command Palette** - Atalhos rápidos para navegação (opcional)
- **Dark Mode** - Toggle persistente com preferência do sistema
- **Performance Optimization** - Image optimization, code splitting automático

---

# 📁 Estrutura Conceitual do Projeto

Representação apenas documental.
Não representa scaffold real, provisionamento
ou criação automática de arquivos.

```txt
portfolio-profissional-2026/
├── .ai/
│   ├── actions/
│   │   └── action-planner.md
│   ├── requests/
│   │   └── request-planner.md
│   └── planner-out/
│       └── planner.md          # Este arquivo
├── src/
│   ├── app/
│   │   ├── layout.tsx         # Root layout com metadata global
│   │   ├── page.tsx           # Hero section principal
│   │   ├── projects/
│   │   │   └── page.tsx       # Grid de projetos
│   │   ├── experience/
│   │   │   └── page.tsx       # Timeline profissional
│   │   └── skills/
│   │       └── page.tsx      # Taxonomia de habilidades
│   ├── components/
│   │   ├── ui/                # Shadcn/UI componentes
│   │   ├── layout/            # Layout components reutilizáveis
│   │   ├── projects/          # Project cards e grids
│   │   └── timeline/          # Experience timeline components
│   ├── data/
│   │   ├── projects.json
│   │   ├── experience.json
│   │   └── skills.json
│   └── lib/
│       ├── utils.ts           # Utility functions
│       └── seo.ts             # Metadata helpers
├── public/
│   └── images/                # Assets otimizados
├── package.json
├── tailwind.config.ts
└── tsconfig.json
```

---

# 📊 Roadmap de Implementação

## Fase 1: Fundação (Setup)
- [ ] Inicializar Next.js 15 com App Router
- [ ] Configurar TailwindCSS + Shadcn/UI
- [ ] Criar schemas JSON iniciais
- [ ] Estabelecer design system base

## Fase 2: Componentes Core
- [ ] Hero section com metadata dinâmico
- [ ] Projects grid responsivo
- [ ] Experience timeline component
- [ ] Layout wrapper reutilizável

## Fase 3: Dados e SEO
- [ ] Popular schemas JSON iniciais
- [ ] Configurar dynamic metadata
- [ ] Implementar image optimization

## Fase 4: Refinamento
- [ ] Performance tuning (Lighthouse)
- [ ] Acessibilidade audit
- [ ] Mobile testing completo

---

# ⚠️ Riscos e Mitigações

| Risco | Probabilidade | Impacto | Mitigação |
| ----- | ------------- | ------- | --------- |
| JSON mal formatado quebra layout | Baixa | Médio | Schema validation antes de renderizar |
| Imagens não otimizadas afetam performance | Média | Alto | Next.js Image API + placeholders automáticos |
| Expansão futura requer refatoração | Baixa | Baixo | Arquitetura modular desde o início |

---

# 📝 Decisões Operacionais

1. **JSON como fonte única da verdade** - Nunca editar componentes para conteúdo
2. **Server Components first** - Minimizar client-side JavaScript
3. **Lazy loading agressivo** - Carregar apenas o necessário por viewport
4. **No build complexo** - Keep dependencies minimalistas
5. **Progressive enhancement** - Funciona sem JS, melhora com ele

---

# 🔮 Expansão Futura

O projeto está preparado para:
- Blog técnico (adicionar posts.json)
- Documentação pessoal (mdx integration)
- Integração com headless CMS quando necessário
- Internacionalização (i18n) via JSON locale files
- Automações com IA para geração de conteúdo

---

*Documento gerado exclusivamente para planejamento técnico.*
*Nenhuma implementação, scaffold ou execução foi iniciada.*
