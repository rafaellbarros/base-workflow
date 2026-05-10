Utilize o agente builder-input-generator.

Objetivo:
Transformar o conteúdo presente em:

`.ai/techlead-out/techlead.md`

em handoffs especializados consumíveis pelos
agentes de implementação da pipeline AI-First.

Utilizar como base:

`.ai/templates/builder-input-template.md`

Outputs obrigatórios:

```text
.ai/implementation-out/
├── shared.md
├── backend.md
├── frontend.md
├── devops.md
├── qa.md
└── security.md
```

---

# Regras Operacionais

O arquivo:

`.ai/techlead-out/techlead.md`

é a fonte única da verdade.

O agente deve:

1. Ler integralmente o techlead.md
2. Extrair:
   - responsabilidades técnicas
   - boundaries
   - constraints
   - padrões obrigatórios
   - contratos
   - guidelines
   - riscos
   - dependências
   - critérios de aceitação
3. Separar responsabilidades por domínio
4. Eliminar ruído contextual
5. Reduzir contexto desnecessário
6. Consolidar handoffs especializados
7. Preencher semanticamente o template
8. Persistir EXCLUSIVAMENTE os outputs finais

---

# Estratégia de Decomposição

O agente deve distribuir responsabilidades em:

| Arquivo     | Responsabilidade                 |
| ----------- | -------------------------------- |
| shared.md   | padrões globais compartilhados   |
| backend.md  | APIs, contratos, persistência    |
| frontend.md | UI, SSR, componentes             |
| devops.md   | CI/CD, deploy, observabilidade   |
| qa.md       | testes, cobertura, validações    |
| security.md | segurança, hardening, compliance |

Cada output deve conter SOMENTE
o contexto necessário para seu domínio.

---

# Regras de Conversão

O builder-input-generator deve:

- consolidar handoffs especializados
- separar responsabilidades operacionais
- remover contexto irrelevante
- reduzir ambiguidades
- maximizar determinismo operacional
- consolidar boundaries
- formalizar restrições
- formalizar contratos
- estruturar critérios de aceitação
- estruturar ações proibidas
- estruturar dependências técnicas
- preparar execução especializada por agentes

---

# Estrutura Obrigatória dos Outputs

Cada output deve conter:

- contexto operacional
- responsabilidades
- restrições
- boundaries
- padrões obrigatórios
- contratos
- entradas esperadas
- saídas esperadas
- critérios de aceitação
- ações proibidas
- dependências
- checklist operacional

---

# Estratégia de Parsing

O parsing deve ocorrer diretamente do:

`.ai/techlead-out/techlead.md`

NÃO gerar:

```text
.ai/requests/request-backend.md
.ai/requests/request-frontend.md
.ai/requests/request-devops.md
.ai/requests/request-qa.md
.ai/requests/request-security.md
```

O próprio agente deve:

- inferir contexto
- mapear responsabilidades
- consolidar estratégias
- separar boundaries
- preencher automaticamente os outputs

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
- utilizar append
- escrever parcialmente
- persistir incrementalmente

O agente deve apenas:

1. gerar TODOS os outputs primeiro
2. estruturar os markdowns
3. validar consistência estrutural
4. utilizar a tool `write`
5. persistir exclusivamente:

```text
.ai/implementation-out/
├── shared.md
├── backend.md
├── frontend.md
├── devops.md
├── qa.md
└── security.md
```

---

# Estratégia de Geração

Todos os outputs devem ser gerados
COMPLETAMENTE em memória antes da persistência.

O agente NÃO deve:

- escrever parcialmente
- escrever incrementalmente
- utilizar append
- sobrescrever por etapas
- persistir seções isoladas

O agente deve:

1. gerar TODOS os documentos
2. validar consistência global
3. persistir os outputs finais

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
- responsabilidades
- restrições
- guidelines
- contratos
- critérios
- dependências
- documentação auxiliar

---

# Restrições

Os documentos gerados:

- devem ser técnicos
- devem ser operacionais
- devem ser declarativos
- devem ser especializados
- devem possuir baixo ruído contextual

Os outputs NÃO podem conter:

- implementação completa
- código funcional extenso
- provisioning
- setup executável
- scripts bash
- pipelines executáveis
- configurações completas
- exemplos longos
- lógica de negócio inventada

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

# Regras de Formatação

Os outputs devem priorizar:

- legibilidade
- clareza
- estrutura modular
- parsing eficiente
- baixo custo de contexto
- consumo otimizado por IA

Preferir:

- markdown simples
- bullets objetivos
- listas curtas
- headings consistentes
- tabelas pequenas

Evitar:

- diagramas extensos
- tabelas gigantes
- redundâncias
- blocos longos de código
- exemplos excessivos

---

# Critério de Qualidade

Os handoffs finais devem:

- possuir leitura clara
- ser altamente estruturados
- ser modulares
- minimizar ambiguidades
- reduzir hallucinations
- possuir boundaries explícitos
- possuir responsabilidades claras
- ser consumíveis por IA
- servir como entrada futura para:
  - backend agents
  - frontend agents
  - devops agents
  - qa agents
  - security agents
  - implementation agents

---

# Validação de Integridade

Antes da persistência final,
o agente deve validar que:

- TODOS os placeholders foram resolvidos
- NÃO existem tokens remanescentes
- NÃO existem seções vazias obrigatórias
- NÃO existem marcadores temporários

O agente NÃO pode persistir documentos contendo:

- [PLACEHOLDER]
- TODO
- TBD
- FIXME

Caso alguma seção não possua contexto suficiente:

- gerar direcionamento declarativo mínimo
- manter consistência estrutural
- evitar placeholders

---

# Output Final

Persistir exclusivamente:

```text
.ai/implementation-out/
├── shared.md
├── backend.md
├── frontend.md
├── devops.md
├── qa.md
└── security.md
```
