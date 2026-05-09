---
PROJECT_NAME: portfolio-profissional-2026

PROJECT_TYPE:
  - portfolio
  - personal-brand
  - ai-first

PRIMARY_GOAL: >
  Criar um portfólio profissional extremamente rápido,
  minimalista, performático e simples de manter.

TARGET_AUDIENCE:
  - recrutadores
  - tech leads
  - consultorias
  - empresas internacionais

TECH_STACK:
  frontend:
    framework: Next.js 15
    styling:
      - TailwindCSS
      - Shadcn/UI
    animations:
      - Framer Motion

ARCHITECTURE:
  rendering: SSR + Static Generation
  data_strategy: local-json-driven
  component_strategy: reusable-ui
  seo_strategy: dynamic-metadata

DESIGN_SYSTEM:
  theme: dark-mode
  style:
    - minimalista
    - software-engineer-senior
    - alta-legibilidade
    - foco-em-conteudo
    - sem-elementos-excessivos

DATA_SOURCE:
  type: local-json
  files:
    - projects.json
    - experience.json
    - skills.json

CORE_FEATURES:
  - hero-section
  - projects-grid
  - experience-timeline
  - dynamic-seo
  - responsive-layout
  - mobile-first
  - command-palette
  - dark-mode
  - performance-optimization

NON_FUNCTIONAL_REQUIREMENTS:
  - alta-performance
  - baixo-consumo-js
  - lighthouse-95-plus
  - fácil-manutenção
  - atualização-via-json
  - acessibilidade
  - seo-friendly

UPDATE_STRATEGY:
  projects: >
    Novos projetos devem ser adicionados apenas via JSON,
    sem necessidade de alterar componentes React.

  experience: >
    Experiências profissionais devem ser renderizadas
    dinamicamente via estrutura declarativa.

CONSTRAINTS:
  - evitar-overengineering
  - evitar-cms
  - evitar-dependencias-desnecessarias
  - evitar-build-complexo

DELIVERABLES:
  - estrutura-base-nextjs
  - design-system
  - componentes-reutilizaveis
  - schemas-json
  - sistema-seo
  - estrutura-de-conteudo
  - documentação-de-atualização

PRIORITIES:
  - performance
  - simplicidade
  - legibilidade
  - manutenção
  - reutilização
---

# Intenção do Usuário

Quero um portfólio que funcione como uma plataforma declarativa de conteúdo.

A manutenção deve ser extremamente simples:

- adicionar um novo projeto alterando apenas o JSON
- atualizar experiências sem editar componentes
- manter arquitetura limpa e previsível

O visual deve transmitir:

- senioridade
- clareza técnica
- organização
- credibilidade profissional

O foco principal NÃO é animação exagerada ou design chamativo.
O foco é:

- performance
- leitura
- experiência fluida
- arquitetura limpa
- facilidade de evolução futura

O projeto deve ser preparado para:

- expansão futura
- internacionalização
- blog técnico
- integração futura com CMS/headless APIs
- automações com IA
