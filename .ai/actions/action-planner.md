Utilize o agente planner-engineer.

Input:
`.ai/requests/request-planner.md`

Template:
`.ai/templates/planner-template.md`

Destino documental:
`.ai/planner-out/planner.md`

---

# Regra Obrigatória de Idioma

O idioma FINAL do documento gerado
DEVE obrigatoriamente seguir o valor definido em:

`OUTPUT_LANGUAGE`

presente no request.

Mapeamento suportado:

- `pt-BR` → Português Brasileiro
- `en-US` → Inglês Americano

Esta regra possui prioridade máxima.

Todo o conteúdo textual gerado
DEVE seguir integralmente o idioma definido,
incluindo:

- títulos
- descrições
- tarefas
- tabelas
- roadmap
- decisões
- critérios
- documentação auxiliar

Caso o parâmetro não exista,
utilizar:

`en-US`
como padrão.
