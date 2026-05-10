Utilize o agente architect.

Objetivo:
Transformar o conteúdo presente em:

`.ai/planner-out/planner.md`

em documentação arquitetural completa baseada no template:

`.ai/templates/architect-template.md`

Output obrigatório:

`.ai/architect-out/architect.md`

---

# Regras Operacionais

O arquivo planner.md é a fonte única da verdade.

O agente deve:

1. Ler integralmente o planner
2. Extrair:
   - objetivos
   - stack
   - módulos
   - fluxos
   - decisões técnicas
   - restrições
   - roadmap
   - estratégias
3. Converter o conteúdo em documentação arquitetural formal
4. Preencher semanticamente o template arquitetural
5. NÃO inventar requisitos inexistentes
6. NÃO implementar código
7. NÃO gerar scaffold
8. NÃO criar arquivos extras
9. NÃO executar provisioning
10. NÃO modificar o planner original

---

# Regras de Conversão

O architect deve:

- Consolidar decisões técnicas
- Formalizar boundaries do sistema
- Definir responsabilidades por módulo
- Estruturar fluxos conceituais
- Formalizar data flow
- Organizar estratégia arquitetural
- Estruturar componentes macro
- Definir separação de responsabilidades
- Formalizar riscos arquiteturais
- Consolidar decisões operacionais

---

# Estratégia de Parsing

O parsing deve ocorrer diretamente do planner.md.

NÃO gerar:
`.ai/requests/request-architect.md`

O próprio agente deve:

- inferir contexto
- mapear seções
- preencher o template automaticamente

---

# Regras de Idioma

O idioma FINAL deve seguir:

`OUTPUT_LANGUAGE`

Mapeamento suportado:

- pt-BR → Português Brasileiro
- en-US → Inglês Americano

Caso inexistente:
usar `en-US`.

Todos os elementos devem respeitar o idioma:

- títulos
- tabelas
- decisões
- descrições
- roadmap
- riscos
- fluxos
- documentação auxiliar

---

# Restrições

O documento gerado:

- deve ser arquitetural
- deve ser técnico
- deve ser declarativo
- não pode conter implementação
- não pode conter código funcional
- não pode conter provisioning
- não pode conter setup executável

---

# Critério de Qualidade

A arquitetura final deve:

- possuir leitura clara
- ser modular
- ser expansível
- ser consistente com o planner
- minimizar ambiguidades
- servir como entrada futura para:
  - tech-lead
  - backend
  - frontend
  - devops
  - ai-coding-agents

---

# Output Final

Persistir exclusivamente:

`.ai/architect-out/architect.md`
