Utilize o agente tech-lead.

Objetivo:
Transformar o conteúdo presente em:

`.ai/architect-out/architect.md`

em direcionamento técnico operacional baseado no template:

`.ai/templates/techlead-template.md`

Output obrigatório:

`.ai/techlead-out/techlead.md`

---

# Regras Operacionais

O arquivo:

`.ai/architect-out/architect.md`

é a fonte única da verdade.

O agente deve:

1. Ler integralmente o architect.md
2. Extrair:
   - arquitetura
   - módulos
   - componentes
   - boundaries
   - integrações
   - fluxos
   - estratégias técnicas
   - riscos
   - restrições
   - decisões arquiteturais
3. Revisar coerência técnica
4. Consolidar padrões de engenharia
5. Converter arquitetura em direcionamento técnico operacional
6. Preencher semanticamente o template
7. Persistir EXCLUSIVAMENTE:
   `.ai/techlead-out/techlead.md`

---

# Regras de Conversão

O tech-lead deve:

- consolidar padrões de engenharia
- formalizar diretrizes técnicas
- definir convenções de implementação
- estruturar guidelines de backend
- estruturar guidelines de frontend
- definir padrões de APIs
- definir padrões de eventos
- formalizar estratégias de observabilidade
- formalizar estratégias de testes
- estruturar estratégias de resiliência
- formalizar estratégias de segurança
- consolidar riscos técnicos
- consolidar riscos operacionais
- preparar handoff para agentes posteriores

---

# Estratégia de Parsing

O parsing deve ocorrer diretamente do:

`.ai/architect-out/architect.md`

NÃO gerar:

`.ai/requests/request-techlead.md`

O próprio agente deve:

- inferir contexto
- mapear seções
- consolidar decisões técnicas
- preencher automaticamente o template

---

# Regras de Persistência

A persistência deve ocorrer SOMENTE utilizando
a tool oficial `write`.

O agente NÃO deve utilizar:

- bash
- shell
- heredoc
- cat
- echo
- redirection operators
- terminal commands
- filesystem commands manuais

O agente NÃO deve:

- executar comandos
- criar arquivos via shell
- utilizar terminal
- utilizar scripts
- utilizar comandos bash para persistência

O agente deve apenas:

1. gerar o conteúdo final
2. estruturar o markdown
3. utilizar a tool `write`
4. persistir exclusivamente:
   `.ai/techlead-out/techlead.md`

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
- guidelines
- riscos
- fluxos
- estratégias
- handoff
- documentação auxiliar

---

# Restrições

O documento gerado:

- deve ser técnico
- deve ser operacional
- deve ser declarativo
- não pode conter implementação
- não pode conter código funcional
- não pode conter provisioning
- não pode conter setup executável

O agente NÃO pode:

- implementar código
- gerar scaffold
- criar arquivos extras
- executar provisioning
- alterar requisitos funcionais
- modificar regras de negócio
- inventar requisitos inexistentes
- assumir tecnologias não especificadas

---

# Critério de Qualidade

O direcionamento técnico final deve:

- possuir leitura clara
- ser modular
- possuir consistência arquitetural
- minimizar ambiguidades
- possuir padrões reutilizáveis
- ser consumível por IA
- servir como entrada futura para:
  - backend
  - frontend
  - devops
  - qa
  - security
  - ai-coding-agents

---

# Output Final

Persistir exclusivamente:

`.ai/techlead-out/techlead.md`
